---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Planification d'instances
{: #planning-for-instances}
[comment]: # (rubrique d'aide liée)


Lorsque vous envisagez de mettre à disposition {{site.data.keyword.vsi_is_full}}, cette liste de contrôle de configuration peut vous être utile pour tirer le meilleur parti de votre déploiement de serveur virtuel.
{:shortdesc}

Avant de commencer, veillez à [créer un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Planification de la mise à disposition d'instances
{: #planning-for-provisioning-instances}

Dès qu'un {{site.data.keyword.vpc_short}} est disponible, tenez compte des points suivants avant de mettre à disposition votre instance.

|        Considérations à prendre en compte|
|-------------------|
|__ 1. Assurez-vous que votre compte dispose des [droits utilisateur](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions) requis. Si vous disposez de droits en tant qu'éditeur ou administrateur sur une ressource {{site.data.keyword.vpc_short}}, vous héritez également de droits de création, de suppression et de modification d'instances de serveur virtuel dans ce cloud privé virtuel.|
|__ 2. Recherchez les instances simultanées dans les [limites du compte](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). |
|__ 3. Assurez-vous que votre [clé SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) est disponible.
|__ 4. Déterminez quel emplacement d'instance sélectionner.|
|__ 5. Prenez en compte les [options de profil](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) courantes des combinaisons d'UC virtuelle et de RAM pour votre charge de travail. Les profils contiennent des instances préconfigurées prêtes à être utilisées en quelques minutes. Il est important de vous assurer que vos instances disposent des ressources nécessaires pour que vos charges de travail et votre environnement restent opérationnels.|
|__ 6. Déterminez l'image du système d'exploitation que vous sélectionnez pour votre instance. Vous pouvez choisir parmi les [images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images) du stock en cours. |
|__ 7. Veillez à indiquer un nom unique pour l'instance. Si vous disposez d'une méthode pour nommer les instances de serveur virtuel, il est beaucoup plus facile de les filtrer et de les rechercher ultérieurement. |

## Etapes suivantes
{: #next-create-instance}

Lorsque vous êtes prêt à commencer, consultez les ressources suivantes pour créer votre instance :
* [Création d'une instance à l'aide de la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Création d'une instance à l'aide de l'interface de ligne de commande](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
