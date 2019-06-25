---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Gestion des clés SSH
{: #managing-ssh-keys}

## Avant de commencer
{: #prereq-ssh-key-available}

Pour accéder aux instances {{site.data.keyword.vsi_is_full}}, vous devez disposer d'une clé SSH. Vous pouvez gérer les clés SSH dans la console {{site.data.keyword.cloud_notm}} et à l'aide de l'interface de ligne de commande (CLI). 

La gestion des clés à l'aide de la console {{site.data.keyword.cloud_notm}} ou de l'interface CLI n'a aucun effet sur les clés des instances déjà créées. (Pour une instance Linux existante, vous pouvez modifier les clés directement dans le répertoire `~/.ssh/` de l'instance.)

Pour plus d'informations sur la localisation ou la génération d'une clé SSH, voir [Clés SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).
{: tip}

## Gestion des clés SSH dans la console IBM Cloud
{: #managing-ssh-keys-with-ibm-cloud-console}

Lorsque vous mettez à disposition un serveur virtuel, vous pouvez sélectionner l'une des clés SSH disponibles ou en télécharger une nouvelle. Vous ne pouvez pas générer de clés SSH dans la console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Vous pouvez gérer et supprimer des clés SSH à l'aide de la console {{site.data.keyword.cloud_notm}}.
1. Dans la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.cloud.ibm.com/vpc), accédez à **l’icône Menu ![Icône Menu](../icons/icon_hamburger.svg) > Infrastructure VPC > Compute > Clés SSH**.
2. De là, vous pouvez ajouter ou supprimer une clé SSH.

## Gestion des clés SSH à l'aide de l'interface CLI
{: #managing-ssh-keys-by-using-the-cli}

Vous pouvez également gérer vos clés SSH à l'aide de l'interface CLI.

| Action           | Commande                     | Etapes suivantes |
| ---------------- | --------------------------- | ----------------- |
| Créer une clé SSH   | `ibmcloud is key-create`    | Une fois que vous avez créé une clé SSH, celle-ci est ajoutée à la liste des clés. |
| Afficher les détails de clé | `ibmcloud is key`           | Vous pouvez afficher le nom d'une clé et son ID. |
| Répertorier les clés        | `ibmcloud is keys`          | Vous pouvez afficher toutes vos clés SSH existantes. |
| Mettre à jour une clé       | `ibmcloud is key-update`    | Lorsqu'une clé existante est mise à jour, elle est renommée immédiatement. |
| Supprimer une clé       | `ibmcloud is key-delete`    | Lorsqu'une clé SSH a été supprimée, elle ne peut plus être utilisée lorsque vous mettez à disposition une nouvelle instance ou effectuez un rechargement du système d'exploitation sur une instance existante. Cependant, la clé est toujours disponible dans toutes les instances que vous avez configurées avec elle et vous pouvez l'utiliser pour vous connecter. |
{: caption="Tableau 1. Actions de clés SSH" caption-side="top"}
