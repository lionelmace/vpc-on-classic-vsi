---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# A propos de Virtual Servers for VPC
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}} vous donne accès à tous les avantages d'{{site.data.keyword.vpc_short}}, notamment l'isolement, la sécurité et la flexibilité du réseau. 
{:shortdesc}

## Qu'est-ce qu'{{site.data.keyword.vpc_short}} ?
{{site.data.keyword.vpc_short}} est un réseau virtuel lié à votre compte client. Il vous offre un point d’entrée économique qui assure la sécurité du cloud et la capacité de s’adapter de manière dynamique à la croissance. Il vous permet d'obtenir un contrôle précis de votre infrastructure virtuelle et de la segmentation de votre trafic réseau.
{: shortdesc}

Pour plus d'informations sur {{site.data.keyword.vpc_short}}, voir [A propos d'IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about).

## Qu'est-ce que {{site.data.keyword.vsi_is_short}} ?
Avec {{site.data.keyword.vsi_is_short}}, vous pouvez créer une instance constituée de vos ressources de calcul virtuelles et de la capacité obtenue au sein d'un cloud {{site.data.keyword.vpc_short}}. Lorsque vous mettez à disposition une instance, vous sélectionnez un profil d'instance correspondant à la quantité de mémoire et à la puissance de calcul dont vous avez besoin pour l'application ou le logiciel que vous prévoyez d'exécuter sur l'instance. Après avoir mis à disposition une instance, vous contrôlez et gérez ces ressources d'infrastructure. Chaque compte a une limite sur le nombre d'instances en cours d'exécution sur les serveurs. Pour plus d'informations sur cette limite, voir les [FAQ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). 

## En quoi les instances de serveur virtuel pour {{site.data.keyword.vpc_short}} sont-elles différentes des autres offres de serveur virtuel IBM ?

Dans l'offre IBM Cloud Virtual Server actuelle, les instances utilisent un réseau natif de sous-réseaux et de réseau VLAN pour communiquer entre elles au sein d'un centre de données (et d'un pod unique). L'utilisation de la mise en réseau de sous-réseaux et de réseau VLAN dans un seul pod fonctionne bien jusqu'à ce que vous deviez augmenter la taille de votre système ou que vos besoins en ressources virtuelles soient importants et nécessitent la création de ressources entre les pods. (L'ajout d'appareils pour l'extension du VLAN peut devenir coûteux et compliqué.) 

{{site.data.keyword.vpc_short}} ajoute une couche d'orchestration réseau qui élimine la limite du pod, créant une capacité infinie pour la mise à l'échelle d'instances. La couche d'orchestration du réseau gère l'ensemble du réseau pour toutes les instances de serveur virtuel qui se trouvent dans un {{site.data.keyword.vpc_short}}, au sein de différentes régions et zones. Avec les fonctionnalités réseau définies par logiciel fournies par {{site.data.keyword.vpc_short}}, vous disposez de davantage d'options pour les [VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc), les instances multicartes vNIC et les tailles de [sous-réseau](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets) plus grandes. Pour plus d'informations, voir [A propos de la mise en réseau pour VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc). 

{{site.data.keyword.vsi_is_short}} dispose également des fonctionnalités suivantes qui simplifient l'expérience utilisateur et permettent de réaliser des économies :
* Nouvelle console {{site.data.keyword.cloud_notm}}
* Nouvelle API Virtual Private Cloud et interface CLI
* Nouveau modèle de facturation avec des niveaux de réduction pour l'utilisation soutenue, comme décrit dans [Tarification](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)

{{site.data.keyword.vsi_is_short}} n'est pas compatible avec les offres de serveur virtuel classiques. Si vous êtes intéressé par l'une des offres {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} sur l'infrastructure classique, voir [Serveurs virtuels IBM Cloud](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial).
{:note}




