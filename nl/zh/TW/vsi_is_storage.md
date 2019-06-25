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


# 儲存空間
{: #storage}

當您佈建 {{site.data.keyword.vsi_is_full}} 實例時，會自動建立 100 GB、一般用途 IOPS (3 IOPS/GB) 的區塊儲存空間磁區作為主要開機磁區並連接至實例。您也可以建立次要資料磁區，它們會自動連接至實例。
{:shortdesc}

- 如需 VPC 之區塊儲存空間磁區的相關資訊，請參閱[關於 Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)。  
- 若要開始建立與虛擬伺服器實例佈建無關的磁區，請參閱[開始使用 {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started)。

依預設，會使用 IBM 管理的加密來將開機和資料磁區加密。您也可以在實例佈建期間，或在[建立獨立式磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption)時，使用您自己的虛擬金鑰來加密磁區。  

當您刪除虛擬伺服器實例時，會刪除開機磁區。依預設，從實例分離時，資料磁區會持續保存；您可以稍後將磁區連接至新的實例。或者，您可以指定在刪除實例時自動刪除該資料磁區。  

## 區塊儲存空間的客戶管理加密  
{: #customer-managed-encryption-keys}

您可以使用區塊儲存空間加密，及您所管理的專屬資料加密金鑰，來建立 {{site.data.keyword.vsi_is_full}}。您只需要 {{site.data.keyword.keymanagementservicelong_notm}} 服務和您自己的資料加密金鑰，即可開始進行。如需相關資訊，請參閱[建立使用客戶管理加密的虛擬伺服器實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok)。
{:shortdesc}

