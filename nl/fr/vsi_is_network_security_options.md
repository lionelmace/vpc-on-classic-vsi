---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Mise en réseau et sécurité sur les serveurs virtuels
{: #network-security-options}

Lorsque vous implémentez une instance {{site.data.keyword.vsi_is_full}}, vous avez accès aux dernières fonctionnalités en matière de réseau et de sécurité.  
{:shortdesc}

## Utilisation des cartes vNIC d'instance
{: #using-instance-vnics}

Une carte d'interface de réseau virtuel (vNIC) permet de connecter un serveur virtuel à un réseau. Lorsque vous créez une instance VSI, vous pouvez utiliser une carte vNIC pour affecter plusieurs adresses IP. La liste suivante présente comment fonctionnent les cartes vNIC avec votre instance.

* Vous pouvez créer et attribuer jusqu'à 5 cartes vNIC à chaque instance. Chaque carte vNIC se voit attribuer une adresse IP privée à partir du sous-réseau connecté et vous pouvez éventuellement associer une adresse IP flottante et des groupes de sécurité.
* Vous pouvez connecter chaque carte vNIC à un sous-réseau de la même zone.
* Chaque carte vNIC reçoit une adresse IP privée issue de la plage de sous-réseau.
* Vous pouvez associer et dissocier des adresses IP flottantes à et de chaque carte vNIC.
* Vous pouvez affecter des groupes de sécurité à chaque carte vNIC.
* Vous pouvez modifier le nom de toute carte vNIC existante.

La bande passante est associée à l'instance elle-même et ne constitue pas un aspect configurable d'une carte vNIC individuelle. La bande passante par défaut d'une instance est de 100 Mb/s, avec une option de mise à niveau à 1 Gb/s.

## Options de mise en réseau
{: #networking-options}

Pour plus d'informations sur les fonctionnalités réseau globales dans l'environnement {{site.data.keyword.vpc_short}}, voir [A propos de la mise en réseau pour VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc).

## Options de sécurité
{: #security-options}

{{site.data.keyword.vsi_is_short}} inclut des options de sécurité intégrées :
* Les listes de contrôle d'accès (ACL) peuvent limiter le trafic en provenance et à destination d'un sous-réseau.
* Les groupes de sécurité fonctionnent comme un pare-feu virtuel pour les instances de serveur virtuel.
* Les clés SSH sur votre instance de serveur virtuel authentifient un canal sécurisé pour la communication réseau.

Pour plus d'informations sur ces options de sécurité, voir [Sécurité de votre instance IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) et [Gestion des clés SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
