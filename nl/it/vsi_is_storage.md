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


# Archiviazione
{: #storage}

Quando esegui il provisioning di un'istanza {{site.data.keyword.vsi_is_full}}, viene automaticamente creato un volume di archiviazione blocchi di IOPS per utilizzo generico (3 IOPS/GB)
di 100 GB come volume di avvio primario e viene collegato all'istanza. Puoi anche creare dei volumi di dati secondari, che vengono automaticamente collegati all'istanza.
{:shortdesc}

- Per ulteriori informazioni sui volumi di archiviazione blocchi per VPC, vedi [Informazioni su Block Storage per VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).  
- Per iniziare a creare dei volumi indipendenti dal provisioning dell'istanza del server virtuale, vedi [Introduzione a {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started).

Per impostazione predefinita, i volumi di avvio e di dati sono crittografati con la crittografia gestita da IBM. Puoi anche crittografare i tuoi volumi utilizzando le tue chiavi di crittografia, durante il provisioning dell'istanza o quando [crei un volume autonomo](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

I volumi di avvio vengono eliminati quando elimini l'istanza del server virtuale. Per impostazione predefinita, i volumi di dati perdurano quando scollegati dall'istanza; puoi successivamente collegare il volume a una nuova istanza. In alternativa, puoi specificare che tali volumi di dati vengano automaticamente eliminati quando elimini l'istanza.  

## Crittografia gestita dal cliente per l'archiviazione blocchi  
{: #customer-managed-encryption-keys}

Puoi creare {{site.data.keyword.vsi_is_full}} con la crittografia di archiviazione blocchi e le chiavi di crittografia dei dati che gestisci. Per iniziare hai soltanto bisogno del servizio {{site.data.keyword.keymanagementservicelong_notm}} e della tua chiave di crittografia dei dati. Per ulteriori informazioni, vedi [Creazione delle istanze del server virtuale con la crittografia gestita dal cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).
{:shortdesc}

