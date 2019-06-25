---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-24"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Stockage
{: #storage}

Lorsque vous configurez une instance {{site.data.keyword.vsi_is_full}}, un volume de stockage par blocs d'E-S/s (3 E-S/s/Go) à usage général de 100 Go est automatiquement créé en tant que volume d'amorçage principal et connecté à l'instance. Vous pouvez également créer des volumes de données secondaires, qui sont automatiquement connectés à l'instance.
{:shortdesc}

- Pour plus d'informations sur les volumes de stockage par blocs pour le VPC, voir [A propos de Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).  
- Pour commencer à créer des volumes indépendants de la mise à disposition d'instances de serveur virtuel, voir [Initiation à {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started).

Par défaut, les volumes d'amorçage et de données sont chiffrés avec le chiffrement géré par IBM. Vous pouvez également chiffrer vos volumes à l'aide de vos propres clés de chiffrement, lors de la mise à disposition d'instances ou de la [création d'un volume autonome](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

Les volumes de démarrage sont supprimés lorsque vous supprimez l'instance de serveur virtuel. Par défaut, les volumes de données sont conservés lorsqu'ils sont déconnectés de l'instance ; vous pouvez ensuite connecter le volume à une nouvelle instance. Vous pouvez également spécifier que les volumes de données sont automatiquement supprimés lorsque vous supprimez l'instance.  

## Chiffrement géré par le client pour le stockage par blocs  
{: #customer-managed-encryption-keys}

Vous pouvez créer des instances {{site.data.keyword.vsi_is_full}} avec le chiffrement de stockage par blocs et vos propres clés de chiffrement de données que vous gérez. Vous avez simplement besoin du service {{site.data.keyword.keymanagementservicelong_notm}} et de votre propre clé de chiffrement de données pour commencer. Pour plus d'informations, voir [Création d'instances de serveur virtuel avec chiffrement géré par le client](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).
{:shortdesc}

