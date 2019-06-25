---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

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

# Création d'instances de serveur virtuel
{: #creating-virtual-servers}
[comment]: # (rubrique d'aide liée)

Vous pouvez créer {{site.data.keyword.vsi_is_full}} à partir de la page *Instances de serveur virtuel* de la console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Avant de commencer, veillez à [créer un VPC IBM Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

Pour créer une instance, sélectionnez les détails d'instance suivants.
1. Dans la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.cloud.ibm.com/vpc), accédez à **l’icône Menu ![Icône Menu](../icons/icon_hamburger.svg) > Infrastructure VPC > Compute > Instances de serveur virtuel**.
2. Cliquez sur **Nouvelle instance** et entrez les informations suivantes :

    <table>
    <CAPTION>Tableau 1. Sélections de mise à disposition d'instance</CAPTION>
    <THEAD>
    <TR>
    <th>Zone</th>
    <th>Valeur</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Nom </td>
    <td>Un nom est requis pour votre instance de serveur virtuel.</td>
    </tr>
    <tr>
    <td>Cloud privé virtuel</td>
    <td>Spécifiez le VPC IBM Cloud sur lequel vous souhaitez créer votre instance.</td>
    </tr>
    <tr>
    <td>Emplacement</td>
    <td>Les emplacements sont composés de régions (zones géographiques spécifiques) et de zones (centres de données à tolérance de pannes dans une région). Sélectionnez l'emplacement où vous souhaitez créer votre instance de serveur virtuel.</td>
    </tr>
    <tr>
    <td>Profil</td>
    <td><p>
    Choisissez parmi les profils courants ou toutes les combinaisons de d'UC virtuelle et de RAM disponibles. Les familles suivantes sont prises en charge :
    <ul>
    <li>Balanced</li>
    <li>Compute</li>
    <li>Memory</li>
    </ul>
    </p>
    <p>Chaque coeur physique du serveur est hyper-threadé et présenté sous la forme de deux processeurs virtuels (UC virtuelle). L'offre de serveur virtuel fournit au moins 2,0 GHz par UC virtuelle, avec un maximum de 48 UC virtuelles disponibles sur un serveur virtuel unique.</p>

    <p>Pour la mémoire, une instance peut disposer d'un maximum de 256 Go de RAM entièrement dédiée.</p>
    <p><note>Remarque : les valeurs maximales varient selon les familles.</note></p>
    <p>Pour plus d'informations, voir [Profils](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).</p>
    </td>
    </tr>
    <tr>
    <td>Image</td>
    <td><p>Toutes les images utilisent cloud-init, ce qui vous permet de saisir les métadonnées de l'utilisateur associées à l'instance pour les scripts de post-mise à disposition.</p>
    <p>Pour plus d'informations, voir [Images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images).</p>
    </td>
    </tr>
    <td>Clé SSH</td>
    <td>
    <p>Vous devez sélectionner une clé SSH existante ou télécharger une nouvelle clé SSH à utiliser avant de pouvoir créer l'instance. Les clés SSH sont utilisées pour se connecter en toute sécurité à l'instance après son exécution. Vous pouvez ajouter des clés SSH à votre instance uniquement lors de sa création initiale.</p>
    <p>Remarque : les combinaisons alphanumériques sont limitées à 100 caractères.</p>
    <p>Pour plus d'informations, voir [Clés SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</p></td>
    </tr>
    <tr>
    <td>Données utilisateur</td>
    <td>
    <p>Vous pouvez ajouter des données utilisateur qui effectuent automatiquement des tâches de configuration courantes ou exécutent des scripts. <p>Pour plus d'informations, voir [Données utilisateur](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).</p>
    </td>
    </tr>
    <tr>
    <td>Volume d'amorçage</td>
    <td><p>La taille du volume d'amorçage par défaut pour tous les profils est de 100 Go. Par défaut, le volume d'amorçage comprend le chiffrement géré par le fournisseur. Si vous souhaitez utiliser le chiffrement géré par le client, vous pouvez modifier les détails du volume d'amorçage. Pour plus d'informations, voir [Stockage](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage).</p>
    </td>
    </tr>
    <tr>
    <td>Volume de stockage par blocs connecté</td>
    <td><p>Vous pouvez ajouter un ou plusieurs volumes de données secondaires à inclure lors de la mise à disposition de l'instance. Pour ajouter des volumes, cliquez sur **Nouveau volume de stockage par blocs**. Pour plus d'informations, voir [Création de volumes de stockage par blocs](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).</p>
    </td>
    </tr>
    <tr>
    <td>Interfaces réseau</td>
    <td>Attribuez des options réseau pour vous connecter au VPC IBM Cloud. Vous pouvez créer et attribuer jusqu'à 5 cartes d'interface réseau à chaque instance. Pour plus d'informations, voir [Adresses IP multiples](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options).</td>
    </tr>
    </TBODY>
    </table>

    Votre *Récapitulatif des coûts* s’affiche dans la partie droite de la page *Nouvelle instance de serveur virtuel*.

3. Cliquez sur **Créer une instance de serveur virtuel** lorsque vous êtes prêt pour la mise à disposition. Une série d'e-mails est envoyée à votre administrateur : accusé de réception de la commande de l'instance de serveur virtuel, approbation et traitement de la commande et message indiquant que l'instance est créée.

Vous préférez créer une instance à l'aide de l'interface de ligne de commande ? Pour plus d'informations, voir [Création d'une instance à l'aide de l'interface de ligne de commande](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli).
{: tip}

## Réservation d'une adresse IP flottante
{: #reserving-a-floating-ip-address}

Vous pouvez réserver et associer une adresse IP flottante à votre instance afin de pouvoir vous y connecter à partir d'un emplacement Internet.

Votre instance doit être démarrée pour que vous puissiez associer une adresse IP flottante. L'instance peut nécessiter quelques minutes pour être opérationnelle.
{: note} 

Pour réserver et associer une adresse IP flottante, procédez comme suit.
1. Dans la page **Instances de serveur virtuel** , cliquez sur votre instance pour afficher ses détails.
2. Dans la section **Interfaces réseau**, cliquez sur **Réserver +** pour associer une adresse IP flottante à votre instance.

## Etapes suivantes
{: #next-connecting-to-instance}

Vous êtes maintenant prêt à vous connecter à votre instance. Pour plus d'informations, voir [Connexion à votre instance Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) ou [Connexion à votre instance Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).
