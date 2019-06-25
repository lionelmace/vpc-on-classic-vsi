---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Connexion à votre instance Linux
{: #connecting-to-your-linux-instance}

Une fois que vous avez créé votre instance Linux {{site.data.keyword.vsi_is_full}}, vous pouvez vous y connecter en procédant comme suit.
{:shortdesc}

## Localisation d'une adresse IP flottante
{: #locating-floating-ip-address}

Si vous devez localiser votre adresse IP flottante pour l'instance à laquelle vous souhaitez vous connecter, procédez comme suit. Si vous connaissez déjà votre adresse IP flottante, vous pouvez passer à [Connexion](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected). 

1. Vous devez identifier votre ID d'adresse IP flottante avant de pouvoir localiser votre adresse IP flottante. Exécutez la commande suivante pour identifier votre ID d'adresse IP flottante :

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse semblable à la sortie suivante (en utilisant les valeurs génériques x et 123 à des fins d'exemple uniquement) :

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. A présent que vous disposez de l'ID d'adresse IP flottante, vous pouvez localiser votre adresse IP flottante en exécutant la commande suivante.

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   Pour cet exemple, vous obtenez une réponse semblable à la sortie suivante (en utilisant les valeurs génériques x et 123 à des fins d'exemple uniquement) :

   ```
   ID                    12345x67-8901-234x-5678-9xx01xx23x4x
   Adresse               123.45.678.90
   Nom                   my-instance
   Cible                 primary(1xx2x34x-.)   
   Type de cible         intf
   IP cible              12.345.6.78
   Créé                  Il y a 1 semaine
   Statut                disponible
   Zone                  us-south-1
   Groupe de ressources   -
   Etiquettes            -   
   ```
   {:screen}

Vous pouvez éventuellement localiser l'adresse IP flottante associée à l'instance à laquelle vous souhaitez vous connecter via la console {{site.data.keyword.cloud_notm}}.
{:tip}

## Connexion
{: #getting-connected}

Les valeurs renvoyées ci-dessous sont fournies à titre d'exemple uniquement.

1. Pour vous connecter à votre instance, utilisez votre clé privée et exécutez la commande suivante :

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   Vous recevez une réponse similaire à l'exemple suivant. Lorsque vous êtes invité à continuer la connexion, entrez `yes`.
   ```
   L'authenticité de l'hôte 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' n'a pas pu être établie.
   L’empreinte de la clé ECDSA est SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Voulez-vous poursuivre la connexion (yes/no) ? yes
   Avertissement : ajout permanent de 'xxx.xxx.xxx.xxx' (ECDSA) à la liste des hôtes connus.
   ```
   {:screen}

   Vous accédez maintenant à votre serveur.

2. Lorsque vous êtes prêt à mettre fin à votre connexion, exécutez la commande suivante :

   ```
   # exit
   ```
   {:codeblock}

## Etapes suivantes
{: #next-managing-instances}

Une fois que vous êtes connecté à votre instance, vous pouvez [gérer vos instances à l'aide de la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) ou [gérer vos instances à l'aide de l'interface CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
