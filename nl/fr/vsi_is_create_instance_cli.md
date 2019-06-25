---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: virtual server instances, command line interface, creating virtual server instances

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Création d'instances de serveur virtuel (CLI)
{: #creating-virtual-servers-cli}

Vous pouvez créer des instances {{site.data.keyword.vsi_is_full}} à l'aide de l'interface de ligne de commande (CLI).
{:shortdesc}

## Avant de commencer
{: #prereq-creating-virtual-servers-cli}

1. Vérifiez que vous avez téléchargé, installé et initialisé les plug-ins de CLI suivants :
    * Interface CLI d'{{site.data.keyword.cloud_notm}}
    * Plug-in de vpc-infrastructure

   Pour plus d'informations, voir [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Lorsque vous installez le plug-in vpc-infrastructure pour la première fois, vous devez définir la génération cible sur gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
   
2. Assurez-vous que vous avez déjà [créé une instance {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Collecte d'informations pour créer une instance à l'aide de la CLI
{: #gathering-information-to-create-an-instance-using-the-cli}

Vous êtes prêt à créer une instance ? Avant d'exécuter la commande `ibmcloud is instances`, vous devez connaître les détails de l'instance, tels que le profil ou l'image que vous souhaitez utiliser.

Rassemblons d'abord les informations suivantes :

|    Détails de l'instance   |  Affichage des options                |  Copiez vos valeurs                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| Image                 | `ibmcloud is images`            |                           |
| Profil               | `ibmcloud is instance-profiles` |                           |
| Clé                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| Sous-réseau                | `ibmcloud is subnets`           |                           |
| Zone                  | `ibmcloud is zones`             |                           |   
{: caption="Tableau 1. Détails requis sur l'instance" caption-side="top"}   

Utilisez les commandes suivantes afin de déterminer les informations requises pour créer une nouvelle instance.

1. Répertoriez les régions associées à votre compte.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   Nom       Noeud final              Statut
   us-south   /v1/regions/us-south   disponible
   ```
   {:screen}

2. Répertoriez les zones associées à la région souhaitée.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   Nom        Région     Statut
   us-south-2   us-south   disponible
   ```
   {:screen}

3. Répertoriez les instances {{site.data.keyword.vpc_short}} associées à votre compte.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   ID                                     Nom                                  Par défaut  Créé       Statut      Etiquettes
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                oui il y a 1 mois   disponible  -
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          non        il y a 4 jours    disponible   -   
   ```
   {:screen}

   Si vous n'en disposez pas, vous pouvez créer une instance {{site.data.keyword.vpc_short}} à l'aide de la commande `ibmcloud is vpc-create`. Pour plus d'informations sur la création d'une instance {{site.data.keyword.vpc_short}}, voir [IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create).

4. Répertoriez les sous-réseaux associés à {{site.data.keyword.vpc_short}}.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   ID                                     Nom                                    IPv*   Routage CIDR de sous-réseau         Adresses    Gen   Liste de contrôle d'accès (ACL)  Passerelle   Créé       Statut     VPC                        Zone         Groupe de ressources   Etiquettes
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         Il y a 1 semaine    disponible   my-vpc(xxx1xx23-.)         us-south-2   -                -
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         Il y a 1 jour     disponible   my-vpc(xxx1xx23-.)         us-south-2   -                -
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         Il y a 1 jour      disponible    my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   Si vous n'en disposez pas, vous pouvez créer un sous-réseau à l'aide de la commande `ibmcloud is subnet-create`. Pour plus d'informations sur la création d'un sous-réseau, voir [IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets).

5. Répertoriez les profils disponibles pour créer votre instance.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   Nom            Architecture de l'UC   Coeurs d'UC   Fréquence de l'UC   Mémoire  Modèle de processeur graphique   Coeurs de processeur graphique   Nombre de processeurs graphiques   Mémoire de l'UC   Nombre maximal de volumes   Nb max d'E-S/s  Nombre maximal d'interfaces   Bande passante maximale
   BC1_2X4       amd64      2           2000            4                    0           0           0            25            0          0                0
   BC1_4X8       amd64      4           2000            8                    0           0           0            100           0          0                0
   MC1_16X128    amd64      16          2000            128                  0           0           0            25            0          0                0
   BC1_48X192    amd64      48          2000            192                  0           0           0            100           0          0                0
   BC1_8X32      amd64      8           2000            32                   0           0           0            100           0          0                0
   CC1_16X16     amd64      16          2000            16                   0           0           0            25            0          0                0
   MC1_4X32      amd64      4           2000            32                   0           0           0            100           0          0                0     
   ```
   {:screen}

6. Répertoriez les images disponibles pour créer votre instance.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   ID                                     Nom                 Système d'exploitation                                                      Arch    Créé       Statut   Visibilité  Etiquettes
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Installation minimale)                           amd64   Il y a 9 heures   PRET   public       -
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Installation minimale)    amd64   Il y a 9 heures   PRET   public       -   
   ```
   {:screen}

7. Répertoriez les clés SSH disponibles que vous pouvez associer à votre instance.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse similaire à la sortie suivante :
   ```
   ID                                     Nom          Type   Longueur   Empreinte digitale         Créé        Groupe de ressources   Etiquettes
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   Il y a 5 jours     -                -
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   Il y a 2 jours    -                -    
   ```
   {:screen}

   Si vous n'en disposez pas, vous pouvez créer une clé SSH à l'aide de la commande `ibmcloud is key-create`. Vous pouvez ajouter des clés SSH à votre instance uniquement lors de sa création initiale. Pour plus d'informations sur la gestion des clés SSH, voir [Gestion des clés SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

## Création d'une instance à l'aide de l'interface de ligne de commande
{: #creating-an-instance-using-the-cli}

Une fois que vous connaissez ces valeurs, utilisez-les pour exécuter la commande `instance-create`. Outre les informations que vous avez collectées, vous devez spécifier un nom pour l'instance. L'exemple suivant montre la commande en action (utilisation de valeurs génériques x et 123 à titre d'exemple uniquement).  

Lorsque vous mettez à disposition une instance, un volume de stockage par blocs de 100 Go est automatiquement créé en tant que volume d'amorçage principal et connecté à l'instance. L'exemple suivant montre comment inclure un volume secondaire avec le paramètre `--volume-attach`. L'inclusion d'un volume secondaire est facultative.
{:note}

1. Créez une instance.
   ```
   $ ibmcloud is instance-create \
       <INSTANCE_NAME> \
       <VPC_ID> \
       <ZONE_NAME> \
       <PROFILE_ID> \
       <SUBNET_ID> \
       --image <IMAGE_ID> \
       --keys <KEY_IDS>
       --volume-attach <VOLUME_ATTACH_JSON or JSON file>
   ```
   {:codeblock}

   Par exemple, si vous créez une instance appelée _my-instance_ dans _us-south-2_ et utilisez le profil _bc1-2x4_, votre commande `instance-create` se présente comme suit :

   ```
   $ ibmcloud is instance-create \
       my-instance \
       xxx1xx23-4xx5-6789-12x3-456xx7xx123x \
       us-south-2 \
       bc1-2x4 \
       1234x12x-345x-1x23-45x6-x7x891011x1x \
       --image 1xx2x34x-5678-12x3-x4xx-567x81234567 \
       --keys 1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx
       --volume-attach @/Users/myname/myvolume-attachment_create.json
   ```
   {:codeblock}

   où :
   - `INSTANCE_NAME` est _my-instance_
   - `VPC_ID` est _VPC_ID_
   - `ZONE_NAME` est _us-south-2_
   - `PROFILE_ID` est _bc1-2x4_
   - `SUBNET_ID` est _SUBNET_ID_
   - `IMAGE_ID` est _IMAGE_ID_
   - `KEY_IDS` est _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` est la spécification de connexion de volume au format JSON, fournie dans la commande ou sous forme de fichier. Pour obtenir un exemple de fichier JSON de connexion d'un volume de données, voir [Exemple de fichier JSON de volume secondaire](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json).

   Pour cet exemple, les réponses suivantes apparaîtraient. 
   
   La réponse suivante varie en fonction des valeurs facultatives que vous utilisez.
   {:note}
   
   ```
   ID                     2x12xxx5-xx11-1234-x4x5-1xxx12345678
   Nom                    my-instance
   Profil                 BC1_2X4
   Gen
   Architecture de l'UC   amd64
   Coeurs d'UC            2
   Fréquence de l'UC      2000
   Mémoire                4
   Intf principal         great-scott-stride-lilac-captivate-filtrate(xx12x345-5bxx-1x23-458x-1x2xxx345x6x)   
   Adresse principale     192.16.1.4
   Image                  ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
   Profil           -
   Statut                 pending
   Créé                   now
   VPC                    my-vpc(xxx1xx23-4xx5-6789-12x3-456xx7xx123x)
   Zone                   us-south-2
   Connexion de volume    my-volume-attachment (xx55xx44-3xx1-1234-42x1-234xx5x678xx)
   Groupe de ressources    -
   Etiquettes              -   
   ```
   {:screen}

   Le statut est en attente jusqu'à la création de l'instance.
   {: tip}

2. Lorsque le statut devient *en cours d'exécution*, vérifiez que vous pouvez voir votre nouvelle instance.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Pour cet exemple, les réponses suivantes apparaîtraient.
   ```
   ID                     2x12xxx5-xx11-1234-x4x5-1xxx12345678
   Nom                    my-instance
   Profil                 BC1_2X4
   Gen
   Architecture de l'UC   amd64
   Coeurs d'UC            2
   Fréquence de l'UC      2000
   Mémoire                4
   Intf principal         great-scott-stride-lilac-captivate-filtrate(xx12x345-5bxx-1x23-458x-1x2xxx345x6x)   
   Adresse principale     192.16.1.4
   Image                  ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
   Profil          -
   Statut                 en cours d'exécution
   Créé                   Il y a 5 minutes
   VPC                    my-vpc(xxx1xx23-4xx5-6789-12x3-456xx7xx123x)   
   Zone                   us-south-2
   Connexion de volume    my-volume-attachment (xx55xx44-3xx1-1234-42x1-234xx5x678xx)
   Groupe de ressources    -
   Etiquettes              -
   ```
   {:screen}

3. Affichez les interfaces réseau qui ont été créées pour votre nouvelle instance.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Pour cet exemple, les réponses suivantes apparaîtraient.
   ```
   ID                                     Nom                                           Type       Routage CIDR de sous-réseau                    Adresse principale   Vitesse  Adr. sec.   Groupes. sec.   IP flottantes   Créé          Statut   Groupe de ressources
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      Il y a 10 secondes -   
   ```
   {:screen}

4. Demandez une adresse IP flottante à associer à votre instance.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   Pour cet exemple, les réponses suivantes apparaîtraient.
   ```
     Adresse               xxx.xxx.xxx.xxx
     Nom                   my-floatingip
     Cible                 great-scott-stride-lilac-captivate-filtrate(xx12x345-.)   
     Type de cible         intf
     IP cible              192.0.2.25
     Créé                  Il y a 1 seconde
     Statut                disponible
     Zone                  us-south-2
     Groupe de ressources   -
     Etiquettes            -  
    ```
    {:screen}

    Retenez l'`adresse` IP flottante pour les opérations ultérieures.  

Vous avez besoin d'aide supplémentaire ? Vous pouvez exécuter `ibmcloud is instance-create --help` pour afficher l'aide à la création d'une instance.
{: tip}

Vous préférez créer une instance à l'aide de la console {{site.data.keyword.cloud_notm}} ? Pour plus d'informations, voir [Création d'une instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
{: tip}

## Etapes suivantes
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

Une fois le serveur créé, vous pouvez vous connecter à votre instance. Pour plus d'informations, voir [Connexion à votre instance Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) ou [Connexion à votre instance Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).




