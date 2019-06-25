---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Gestion des instances de serveur virtuel (interface CLI)
{: #managing-virtual-servers-cli}

Vous pouvez afficher et gérer des instances {{site.data.keyword.vsi_is_full}} à l'aide de l'interface de ligne de commande (CLI).
{:shortdesc}

## Avant de commencer
{: #prereq-managing-instances}

1. Vérifiez que vous avez téléchargé, installé et initialisé les plug-ins de CLI suivants :
    * Interface CLI d'{{site.data.keyword.cloud_notm}}
    * Plug-in infrastructure-service

   Pour plus d'informations, voir [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Lorsque vous installez le plug-in vpc-infrastructure pour la première fois, vous devez définir la génération cible sur gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assurez-vous que vous avez déjà [créé une instance {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Affichage des actions sur l'instance
{: #viewing-instance-actions}

Pour afficher les actions de gestion effectuées sur votre instance, exécutez la commande suivante :

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

Une liste similaire à la sortie suivante apparaît :

```
ID                                     Type     Statut      Créé       Démarré            Terminé   123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Terminé   Il y a 6 heures   Il y a longtemps   Il y a longtemps         
```
{:screen}

## Gestion des instances
{: #managing-your-instances}

Vous avez besoin d'aide ? Exécutez la commande `ibmcloud is help` pour afficher les commandes à tout moment.

### Réinitialisation  

```
ibmcloud is instance-reset
```
{:codeblock}

L'instance est mise hors tension, puis remise sous tension.  

### Redémarrage

```
ibmcloud is instance-reboot
```
{:codeblock}

Le système d'exploitation de l'instance est redémarré.  

### Arrêt et démarrage

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

Si l'appareil a été arrêté, il reste à l'état arrêté et doit être démarré manuellement. Vous ne pouvez pas interagir avec une instance si elle est arrêtée. Si l'appareil est démarré, l'interaction normale continue. 

### Mise à jour

```
ibmcloud is instance-update
```
{:codeblock}

Après avoir renommé l'appareil, le nom est automatiquement mis à jour. Lors de la recherche, utilisez le nom de la nouvelle instance lorsque vous tentez de localiser le contenu qui lui est associé. 

### Suppression

```
ibmcloud is instance-delete
```
{:codeblock}

Une fois que vous avez confirmé l'action de suppression, le processus de suppression de l'instance et de la carte vNIC, du volume d'amorçage et des données associés commence. L'action de suppression peut durer plusieurs minutes, mais lorsque le processus est terminé, l'instance n'apparaît plus sur la page d'instances de serveur virtuel. L'adresse IP flottante associée à l'instance de serveur virtuel n'est pas associée, mais reste sur votre compte.

Si vous préférez gérer les instances à l'aide de la console {{site.data.keyword.cloud}}, voir [Gestion des instances](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).
{: tip}
