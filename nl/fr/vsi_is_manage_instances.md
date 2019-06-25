---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Gestion des instances de serveur virtuel
{: #managing-virtual-server-instances}
[comment]: # (rubrique d'aide liée)

Vous pouvez afficher et gérer vos instances {{site.data.keyword.vsi_is_full}} à partir de la page *Instances de serveur virtuel* de la console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Pour gérer vos instances, procédez comme suit.
1. Dans la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.cloud.ibm.com/vpc), accédez à **l’icône Menu ![Icône Menu](../icons/icon_hamburger.svg) > Infrastructure VPC > Compute > Instances de serveur virtuel**.
2. A partir de là, vous pouvez gérer des tâches pour une instance spécifique ou cliquer sur une instance pour afficher et modifier ses propriétés.

## Réamorçage

L'action de réamorçage met immédiatement une instance hors tension, puis à nouveau sous tension.

## Arrêt et démarrage

L'action d'arrêt et démarrage active ou désactive une instance à distance. Si l'instance est arrêtée, elle reste à l'état arrêté et doit être démarrée manuellement. La facturation est [suspendue](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing) pour certaines ressources de calcul lorsque l'instance est arrêtée. Vous ne pouvez pas interagir avec une instance si elle est arrêtée. Si l'appareil est démarré, l'interaction normale continue.

## Suppression

L'action de suppression supprime définitivement de votre compte une instance ainsi que sa carte vNIC connectée, son volume d'amorçage et ses données. Une fois que vous avez confirmé l'action de suppression, le processus de suppression de l'instance et de la carte vNIC, du volume d'amorçage et des données associés commence. L'action de suppression peut durer jusqu'à 30 minutes, mais lorsque le processus est terminé, l'instance n'apparaît plus sur la page d'instances de serveur virtuel. L'adresse IP flottante associée à l'instance de serveur virtuel n'est pas associée, mais reste sur votre compte.

## Affichage des détails d'instance
Vous pouvez interagir avec des instances en affichant le récapitulatif de toutes les instances sur la page *Instances de serveur virtuel* ou en cliquant sur une instance individuelle pour afficher les détails et apporter des modifications. Dans la page de détails de l'instance, vous pouvez également afficher l'interface réseau associée, accéder à son sous-réseau et réserver ou supprimer une adresse IP flottante.

Si vous préférez gérer vos instances à l'aide de l'interface CLI, voir [Gestion des instances à l'aide de l'interface CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
{: tip}
