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


# 存储器
{: #storage}

供应 {{site.data.keyword.vsi_is_full}} 实例时，会自动将 100 GB 通用 IOPS (3 IOPS/GB) 块存储卷创建为主引导卷并将其连接到实例。您还可以创建辅助数据卷，这些卷会自动连接到实例。
{:shortdesc}

- 有关 VPC 的块存储卷的更多信息，请参阅[关于 Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)。  
- 要开始独立于虚拟服务器实例供应来创建卷，请参阅 [{{site.data.keyword.block_storage_is_short}} 入门](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started)。

缺省情况下，引导卷和数据卷会使用 IBM 管理的加密进行加密。您还可以使用自己的加密密钥在实例供应期间或在[创建独立卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)时对卷进行加密。  

删除虚拟服务器实例时，会删除引导卷。缺省情况下，数据卷在从实例拆离后仍会存在；以后可以将该卷连接到新实例。或者，可以指定在删除实例时自动删除数据卷。  

## 对块存储器进行客户管理的加密  
{: #customer-managed-encryption-keys}

可以使用块存储器加密和您管理的自己的数据加密密钥来创建 {{site.data.keyword.vsi_is_full}}。只需要 {{site.data.keyword.keymanagementservicelong_notm}} 服务和您自己的数据加密密钥即可开始。有关更多信息，请参阅[使用客户管理的加密创建虚拟服务器实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok)。
{:shortdesc}

