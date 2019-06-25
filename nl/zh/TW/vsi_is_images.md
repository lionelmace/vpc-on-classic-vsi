---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 映像檔
{: #images}

當您佈建 {{site.data.keyword.vsi_is_full}} 時，可以從受支援的庫存映像檔進行選取。您選取的映像檔決定為實例所佈建的作業系統。
{:shortdesc}

## 庫存映像檔
{: #stock-images}

建立虛擬伺服器時，下列作業系統會以庫存映像檔提供。
* CentOS 7.x
* Debian 8.x、9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04、18.04
* Windows 2012、2012 R2、2016

當您訂購實例時，映像檔已啟用 cloud-init 功能，使佈建時間最佳化。使用已啟用 cloud-init 功能的映像檔，您可以提供使用者資料。在訂單表單上的**使用者資料**欄位中，您可以輸入伺服器的選用性 cloud-init 使用者資料。如需使用者資料和自動化的相關資訊，請參閱[使用者資料](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)。

## 虛擬化
{: #virtualization}
實例需要支援「硬體虛擬化機器 (HVM)」開機模式的映像檔。HVM 虛擬化類型可讓映像檔直接在虛擬伺服器上執行，而進階網路和 GPU 功能需要這點。
