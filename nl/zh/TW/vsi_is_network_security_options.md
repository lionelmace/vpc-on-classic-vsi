---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# 虛擬伺服器上的網路功能和安全
{: #network-security-options}

實作 {{site.data.keyword.vsi_is_full}} 時，您可以存取網路功能及安全的最新特性。  
{:shortdesc}

## 使用實例 vNIC
{: #using-instance-vnics}

虛擬網路介面卡 (vNIC) 是用來將虛擬伺服器連接至網路。當您建立 VSI 實例時，可以使用 vNIC 來指派多個 IP 位址。下列清單強調顯示 vNIC 如何搭配您的實例運作。

* 您可以建立最多 5 個 vNIC 至每一個實例。每個 vNIC 都會從連接的子網路獲得指派一個專用 IP，您可以選擇性地連接浮動 IP 及安全群組。
* 您可以將每個 vNIC 連接至相同區域中的子網路。
* 每個 vNIC 會收到來自子網路範圍的專用 IP。
* 您可以將浮動 IP 與每個 vNIC 之間建立關聯和解除關聯。
* 您可以將安全群組指派給每個 vNIC。
* 您可以變更任何現有 vNIC 的名稱。

頻寬與實例本身相關聯，它不是個別 vNIC 的可配置層面。實例的預設頻寬是 100 Mbps（具有升級至 1 Gbps 的選項）。

## 網路功能選項
{: #networking-options}

如需 {{site.data.keyword.vpc_short}} 環境中整體網路功能特性的相關資訊，請參閱[關於 Networking for VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)。

## 安全選項
{: #security-options}

{{site.data.keyword.vsi_is_short}} 包含內建的安全選項：
* 存取控制清單 (ACL) 可以限制與子網路之間的資料流量。
* 安全群組會作為虛擬伺服器實例的虛擬防火牆。
* 虛擬伺服器實例上的 SSH 金鑰會鑑別網路通訊用的安全通道。

如需這些安全選項的相關資訊，請參閱 [IBM Cloud VPC 中的安全](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)和[管理 SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)。
