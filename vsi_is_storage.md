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


# Storage
{: #storage}

When you provision an {{site.data.keyword.vsi_is_full}} instance, a 100 GB, general purpose IOPS (3 IOPS/GB) block storage volume is 
automatically created as a primary boot volume and attached to the instance. You can also create secondary data volumes, which are automatically attached to the instance.
{:shortdesc}

- For more information about block storage volumes for the VPC, see [About Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).  
- To get started creating volumes independent of virtual server instance provisioning, see [Getting Started with {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-getting-started).

By default, boot and data volumes are encrypted with IBM-managed encryption. You can also encrypt your volumes using your own encyption keys, during instance provisioning or when [creating a standalone volume](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

Boot volumes are deleted when you delete the virtual server instance. By default, data volumes persist when detached from the instance; you can later attach the volume to a new instance. Alternatively, you can specify that data volumes are automatically deleted when you delete the instance.  

## Customer managed encryption for block storage  
{: #customer-managed-encryption-keys}

You can create {{site.data.keyword.vsi_is_full}} with block storage encryption and your own data encryption keys that you manage. You just need the {{site.data.keyword.keymanagementservicelong_notm}} service and your own data encryption key to get started. For more information, see [Creating virtual server instances with customer-managed encryption](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).
{:shortdesc}

