---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

keywords: Windows instance, encrypt password, decrypt password, retrieve password

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

# Connexion à votre instance Windows
{: #connecting-to-your-windows-instance}

Une fois que vous avez créé votre instance Windows {{site.data.keyword.vsi_is_full}}, vous pouvez vous y connecter en procédant comme suit.
{:shortdesc}

## Avant de commencer
{: #prereqs-connect-windows}

Veillez à remplir les conditions préalables suivantes avant de commencer :

1. Demandez à votre administrateur de compte de vous accorder l'accès pour extraire le mot de passe de votre instance de serveur virtuel. Pour plus d'informations, consultez les [droits d'utilisateur](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources).
2. Créez un groupe de sécurité ou ajoutez une règle au groupe de sécurité par défaut pour activer l'accès entrant pour le port par défaut du bureau à distance, 3389. Pour plus d'informations, voir [Utilisation des groupes de sécurité](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups).
3. Vérifiez que le trafic entrant via le port TCP/IP 3389 est autorisé sur la liste de contrôle d'accès par défaut du VPC. Pour plus d'informations, voir [Configuration des listes de contrôle d'accès du réseau](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls).
4. Vérifiez que vous avez installé OpenSSL. Pour déchiffrer votre mot de passe, vous devez exécuter OpenSSL et non LibreSSL. Pour plus d'informations, voir [le site Web de téléchargements OpenSSL ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.openssl.org/source/){: new_window}.

LibreSSL n'est pas compatible pour le déchiffrement du mot de passe. Vous devez exécuter OpenSSL pour déchiffrer votre mot de passe.
{:important}

## Connexion
{: #getting-connected-windows}

Une fois que vous avez créé votre instance Windows et rempli les conditions préalables, procédez comme suit pour vous connecter à votre instance Windows.

1. Demandez le statut de l'instance en exécutant la commande suivante :
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  Lorsque l'instance indique qu'elle est `en cours d'exécution`, vous êtes prêt à extraire les valeurs d'initialisation pour obtenir votre mot de passe. 

2. Exécutez la commande suivante pour initialiser votre instance :

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  Cette commande affiche votre mot de passe chiffré, qui est généré automatiquement lorsque vous créez une instance à l'aide d'une image Windows.

3. Vous devez maintenant déchiffrer votre mot de passe via un processus de déchiffrement manuel. Pour déchiffrer votre mot de passe, exécutez la commande suivante :

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  où `~/examplepwd` est le fichier dans lequel vous avez enregistré votre mot de passe chiffré, comme indiqué à l'étape 2.  
  
  LibreSSL, fourni avec macOS, ne prend pas en charge les algorithmes de hachage SHA2 nécessaires pour déchiffrer le mot de passe, ce qui entraîne des erreurs `d'opérations de clé publique`. Vous pouvez obtenir des bibliothèques OpenSSL standard à l'aide d'un outil de gestion de packages ou en les installant manuellement. 
  {:note}

4. Après avoir déchiffré votre mot de passe, vous pouvez éventuellement associer une adresse IP flottante à votre instance Windows afin de pouvoir vous y connecter à partir d'un site Internet. Exécutez la commande suivante pour associer une adresse IP flottante à votre instance :

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. Vous disposez maintenant des éléments nécessaires pour vous connecter à votre instance Windows : mot de passe déchiffré et adresse IP flottante. Utilisez votre client Remote Desktop préféré pour vous connecter à votre instance. Pour vous connecter à votre instance, indiquez l'adresse IP flottante et le mot de passe déchiffré. Le nom d'utilisateur est `Administrator` par défaut.

## Etapes suivantes
{: #next-manage-instances}

Une fois que vous êtes connecté à votre instance, vous pouvez [gérer vos instances à l'aide de la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) ou [gérer vos instances à l'aide de l'interface CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
