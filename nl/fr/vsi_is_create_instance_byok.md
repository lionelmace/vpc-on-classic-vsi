---

copyright:
  years: 2019
lastupdated: "2019-06-05"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Création d'instances de serveur virtuel avec chiffrement géré par le client
{: #creating-instances-byok}

Vous pouvez créer des serveurs {{site.data.keyword.vsi_is_full}} qui utilisent le chiffrement géré par le client pour les volumes de stockage par blocs lorsque vous disposez d'un service de gestion de clés mis à disposition qui comprend votre propre clé de chiffrement de données. Par défaut, les instances sont mises à disposition avec un volume d'amorçage incluant le chiffrement géré par le fournisseur. Vous pouvez mettre à disposition des instances qui utilisent le chiffrement géré par le client pour les volumes de stockage par blocs à partir de la console {{site.data.keyword.cloud_notm}} ou à l'aide de l'interface de ligne de commande (CLI).
{:shortdesc}

## Services de gestion de clés pris en charge pour le chiffrement géré par le client
{: #kms-for-byok}

Vous pouvez utiliser le service de gestion de clés qui répond le mieux à vos besoins. Les services {{site.data.keyword.keymanagementserviceshort}} et {{site.data.keyword.hscrypto}} (disponibles dans certaines [régions](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)) utilisent une API de fournisseur de clés commune afin de fournir une approche cohérente de la gestion des clés de chiffrement.  En arrière-plan, les centres de données {{site.data.keyword.cloud_notm}} fournissent un module de sécurité matérielle (Hardware Security Module - HSM) dédié pour protéger vos clés.  Les services de gestion de clés suivants sont pris en charge avec le chiffrement géré par le client pour les volumes de stockage par blocs : 

| Service de gestion de clés | Certificat de chiffrement HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conformité FIPS 140-2 de *niveau 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conformité FIPS 140-2 de *niveau 4* |
{: caption="Tableau 1. Options de service de gestion de clés disponibles" caption-side="top"}

## Conditions préalables
{: #byok-vsi-prereqs}

Pour créer une instance de serveur virtuel qui utilise le chiffrement géré par le client pour les volumes de stockage par blocs, vous devez disposer d'un service de gestion de clés mis à disposition et d'une clé racine client ajoutée. Vous devez également autoriser l'accès entre Cloud Block Storage et le service de gestion de clés. Une fois ces conditions préalables remplies, vous pouvez commencer à créer des instances qui utilisent le chiffrement géré par le client pour les volumes de stockage par blocs. 

Les exemples suivants sont spécifiques à {{site.data.keyword.keymanagementserviceshort}}, mais le flux général s'applique également à {{site.data.keyword.hscrypto}}. Si vous utilisez {{site.data.keyword.hscrypto}}, reportez-vous aux [informations relatives à {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) pour obtenir les instructions correspondantes.
{:note}

1. Mettez à disposition le service [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision). 
   
   La mise à disposition d'une nouvelle instance de service {{site.data.keyword.keymanagementserviceshort}} garantit qu'elle inclut les dernières mises à jour requises pour le chiffrement géré par le client des volumes de stockage par blocs. 
   {: tip}
   
2. [Créez](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) ou
[importez](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) une clé racine (CRK) dans
{{site.data.keyword.keymanagementservicelong_notm}}.
3. Dans IBM {{site.data.keyword.iamshort}} (IAM), [autorisez l'accès](/docs/iam?topic=iam-serviceauth#serviceauth) entre **Cloud
Block Storage** (service source) et **{{site.data.keyword.keymanagementserviceshort}}** (service cible).

## Mise à disposition d'instances de serveur virtuel avec des volumes utilisant le chiffrement géré par le client
{: #provision-byok-ui}

Lorsque vous mettez à disposition une instance de serveur virtuel, vous pouvez spécifier un chiffrement géré par le client pour votre volume d'amorçage et tous les volumes de données que vous souhaitez ajouter au moment de la mise à disposition. Si vous le souhaitez, vous pouvez utiliser une combinaison de chiffrement géré par le fournisseur et de chiffrement géré par le client pour les volumes associés à votre instance.

1. Dans la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.cloud.ibm.com/vpc), accédez à **l’icône Menu ![Icône Menu](../icons/icon_hamburger.svg) > Infrastructure VPC > Compute > Instances de serveur virtuel**. Cliquez sur **Nouvelle instance** et complétez les zones obligatoires. (Pour plus d'informations sur la création d'instances, voir [Création d'instances de serveur virtuel](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).) 
2. Dans la section **Volume d'amorçage**, le mode de chiffrement par défaut est le chiffrement _géré par le fournisseur_. Pour spécifier le chiffrement géré par le client, cliquez sur l'icône en forme de crayon dans la ligne du volume d'amorçage. Sur la page **Editer le volume d'amorçage**, mettez à jour les zones de la section **Chiffrement**. Pour plus d'informations, voir le tableau suivant. Une fois les modifications terminées, cliquez sur **Appliquer**.
3. Dans la section **Volume de stockage par blocs connecté**, vous pouvez cliquer sur **Nouveau volume de stockage par blocs** pour ajouter un volume de données et spécifier le chiffrement géré par le client si vous le souhaitez. Sur la page **Nouveau volume de stockage par blocs**, mettez à jour les zones de la section **Chiffrement**. Pour plus d'informations, voir le tableau suivant. Une fois les modifications terminées, cliquez sur **Connecter**.

| Zone | Valeur |
| ----- | ----- |
| Chiffrement | _Géré par le fournisseur_ est le mode de chiffrement par défaut. Pour utiliser le chiffrement géré par le client, sélectionnez un service de gestion de clés dans la liste déroulante. L'instance de service de gestion de clés doit inclure la clé racine du client que vous souhaitez utiliser pour le chiffrement géré par le client. |
| Instance de service de chiffrement | Si plusieurs instances de service de gestion de clés sont mises à disposition dans votre compte, sélectionnez celle qui inclut la clé racine du client que vous souhaitez utiliser pour le chiffrement géré par le client. |
| Nom de clé | Sélectionnez la clé de chiffrement de données dans l'instance de service de gestion de clés que vous souhaitez utiliser pour chiffrer le volume. | 
| ID de clé | Affiche l'ID clé associé à la clé de chiffrement de données que vous avez sélectionnée.. | 
{: caption="Tableau 1. Valeurs permettant de spécifier le chiffrement de volumes géré par le client" caption-side="top"}

## Utilisation de l'interface CLI pour mettre à disposition des instances et des volumes avec un chiffrement géré par le client
{: #provision-byok-cli}

Pour utiliser la CLI afin de créer une instance de serveur virtuel avec des volumes utilisant le chiffrement géré par le client, vous pouvez utiliser la commande `ibmcloud is instance-create` et référencer un fichier JSON pour connecter des volumes utilisant le chiffrement géré par le client. 

1. Obtenez le numéro CRN de la clé racine dans l'instance de service de gestion de clés souhaitée. L'exemple suivant est spécifique à {{site.data.keyword.keymanagementserviceshort}}. 
    
    1. Si le plug-in d'interface CLI {{site.data.keyword.keymanagementserviceshort}} n'est pas déjà installé, installez-le en exécutant la commande suivante : 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. Répertoriez les instances de service {{site.data.keyword.keymanagementserviceshort}} pour votre compte en exécutant la commande suivante :
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
       ```
       Extraction de toutes les instances de tous les services du groupe de ressources Par défaut et de tous les emplacements
       sous le compte MyCompany sous le nom myuserid@mycompany.com...
       OK
       Nom             Emplacement  Etat    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. Extrayez l'ID de l'instance de service {{site.data.keyword.keymanagementserviceshort}} où vos clés racine client sont stockées à l'aide de la commande suivante.  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       où _Key Protect-17_ est l'instance de service {{site.data.keyword.keymanagementserviceshort}} souhaitée.
    
       Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
       ```
       Extraction de l'instance de service Key Protect-17 dans le groupe de ressources Défaut sous le compte
       MyCompany sous le nom myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       où l'ID d'instance est la chaîne qui suit le dernier signe `::` dans le CRN, `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`. 
    
    4. Répertoriez les clés disponibles et leurs CRN associés dans l'instance de service {{site.data.keyword.keymanagementserviceshort}} souhaitée en exécutant la commande suivante :
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       où _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ est l'ID de votre instance de service {{site.data.keyword.keymanagementserviceshort}} souhaitée.
       
       Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
       ```
       Extraction des clés...
              
       SUCCÈS
               
       ID de clé                                 Nom de clé               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. Utilisez la commande [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) et joignez les fichiers JSON nécessaires spécifiant le chiffrement géré par le client pour le volume d'amorçage et tous les volumes de données secondaires que vous souhaitez inclure. Le paramètre `encryption_key` doit inclure un numéro CRN valide pour la clé racine du service Key Protect. Consultez les [exemples de fichiers JSON](#vsi-vol-attachment-json) suivants d'un fichier JSON de volume d'amorçage et d'un fichier JSON de volume secondaire. (Pour plus d'informations sur la création d'instances, voir [Création d'instances de serveur virtuel (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli).)

## Création d'une connexion de volume au format JSON
{: #vsi-vol-attachment-json}

Lors de la création d'un volume d'amorçage ou d'un volume de données lors de la mise à disposition de l'instance VSI, vous devez spécifier un fichier JSON pour définir les paramètres du volume. Consultez les exemples de fichiers JSON suivants.

### Exemple de fichier JSON de volume d'amorçage
{: #boot-volume-byok-json}

L'exemple suivant définit un volume d'amorçage à usage général et spécifie le paramètre de `clé de chiffrement` pour le chiffrement géré par le client.

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      },
      "encryption_key":{  
         "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### Exemple de fichier JSON de volume secondaire
{: #secondary-volume-byok-json}

L'exemple suivant définit un volume secondaire (données) à usage général et spécifie le paramètre de `clé de chiffrement` pour le chiffrement géré par le client.

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         },
         "encryption_key":{  
            "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}
