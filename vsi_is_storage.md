---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-21"

keywords: storage, virtual private cloud, virtual server, instance, block storage, volume, block storage volume, primary boot volume, secondary data volume, boot volume, data volume

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Storage
{: #storage}

When you provision a {{site.data.keyword.vsi_is_short}} instance, a 100 GB, general-purpose IOPS (3 IOPS/GB) block storage volume is 
automatically created as a primary boot volume and attached to the instance. You can also create and attach secondary data volumes when you create an instance.
{:shortdesc}

By default, boot and data volumes are encrypted with IBM-managed encryption. You can also encrypt your volumes by using your own encryption keys when you provision an instance or when you [create a stand-alone volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

Boot volumes are deleted when you delete the virtual server instance. By default, data volumes persist when detached from the instance; you can later attach the volume to a new instance. Alternatively, you can specify that data volumes are automatically deleted when you delete the instance. 

## Customer-managed encryption for {{site.data.keyword.block_storage_is_short}} volumes  
{: #customer-managed-encryption-keys}

You can create {{site.data.keyword.block_storage_is_short}} volumes during instance creation and encrypt them with your own encryption keys. You need a supported key management service and your own data encryption key to get started. For more information, see [Creating virtual server instances with customer-managed encryption](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).

## Additional information

For more information about {{site.data.keyword.block_storage_is_short}}, see [About {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).

To start creating volumes independent of virtual server instance provisioning, see [Getting Started with {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-getting-started).

