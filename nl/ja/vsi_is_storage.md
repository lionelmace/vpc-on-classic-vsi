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


# ストレージ
{: #storage}

{{site.data.keyword.vsi_is_full}} インスタンスをプロビジョンする場合、100 GB の汎用 IOPS (3 IOPS/GB) ブロック・ストレージ・ボリュームがプライマリー・ブート・ボリュームとして自動的に作成され、インスタンスにアタッチされます。 2 次データ・ボリュームを作成することもできます。これは、インスタンスに自動的にアタッチされます。
{:shortdesc}

- VPC のブロック・ストレージ・ボリュームについて詳しくは、[VPC のブロック・ストレージについて](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)を参照してください。  
- 仮想サーバー・インスタンスのプロビジョンに関係なくボリュームの作成を開始するには、[{{site.data.keyword.block_storage_is_short}}の概要](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started)を参照してください。

デフォルトでは、ブート・ボリュームとデータ・ボリュームは IBM 管理の暗号化で暗号化されます。 インスタンスのプロビジョニング中、または[スタンドアロン・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)時に、独自の暗号鍵を使用してボリュームを暗号化することもできます。  

仮想サーバー・インスタンスを削除すると、ブート・ボリュームは削除されます。 デフォルトでは、データ・ボリュームはインスタンスからデタッチされても存続します。後からそのボリュームを新規インスタンスにアタッチすることが可能です。 また、インスタンスの削除時にデータ・ボリュームを自動的に削除するよう指定することもできます。  

## ブロック・ストレージの顧客管理の暗号化  
{: #customer-managed-encryption-keys}

ブロック・ストレージの暗号化、および自分が管理する独自のデータ暗号鍵を使用して、{{site.data.keyword.vsi_is_full}}を作成できます。 開始するには、{{site.data.keyword.keymanagementservicelong_notm}} サービスと独自のデータ暗号鍵が必要です。 詳しくは、[顧客管理の暗号化を使用する仮想サーバー・インスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok)を参照してください。
{:shortdesc}

