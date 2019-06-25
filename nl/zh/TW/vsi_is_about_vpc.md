---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# 關於 Virtual Servers for VPC
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}} 可讓您存取 {{site.data.keyword.vpc_short}} 的所有好處，包括網路隔離、安全性和彈性。
{:shortdesc}

## 何謂 {{site.data.keyword.vpc_short}}？
{{site.data.keyword.vpc_short}} 是關聯於您的客戶帳戶的虛擬網路。它提供符合成本效益的進入點，以提供雲端安全，並提供隨著成長而動態擴充的能力。它讓您能精細控制虛擬基礎架構和網路資料流量區隔。
{: shortdesc}

如需 {{site.data.keyword.vpc_short}} 的相關資訊，請參閱[關於 IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about)。

## 何謂 {{site.data.keyword.vsi_is_short}}？
使用 {{site.data.keyword.vsi_is_short}}，您可以建立一個實例，由您的虛擬運算資源和 {{site.data.keyword.vpc_short}} 中的結果容量所組成。當您佈建實例時，請選取實例設定檔，該設定檔要符合您計劃在實例上執行之應用程式或軟體所需要的記憶體數量及運算能力。佈建實例之後，請控制及管理那些基礎架構資源。每個帳戶都有跨伺服器執行實例的數量限制。如需此限制的相關資訊，請參閱[常見問題](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)。 

## {{site.data.keyword.vpc_short}} 的虛擬伺服器實例與其他 IBM 虛擬伺服器供應項目有什麼不同？

在現今的 IBM Cloud Virtual Server 供應項目中，實例會使用原生子網路和 VLAN 網路功能，而在資料中心（及單一 Pod）內彼此通訊。在一個 Pod 中使用子網路及 VLAN 網路功能會運作良好，直到您必須擴增或有大量的虛擬資源需求，需要在 Pod 之間建立資源。（新增 VLAN Spanning 的應用裝置可能很昂貴且複雜！） 

{{site.data.keyword.vpc_short}} 新增了一個網路編排層，它消除了 Pod 界限，並建立無限容量可以擴充實例。網路編排層會跨地區和區域，在 {{site.data.keyword.vpc_short}} 內為所有虛擬伺服器實例處理所有網路功能。有了 {{site.data.keyword.vpc_short}} 所提供的軟體定義網路功能，您可以有更多的
[VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc)、[LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc)、多 vNIC 實例的選項，以及較大的[子網路](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets)大小。如需相關資訊，請參閱[關於 Networking for VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)。 

{{site.data.keyword.vsi_is_short}} 也有下列特性，可提供更簡單的使用者體驗及成本節省：
* 新的 {{site.data.keyword.cloud_notm}} 主控台
* 新的 Virtual Private Cloud API 及 CLI
* 具有持續使用折扣層級的新計費模式，如[定價](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)中所述

{{site.data.keyword.vsi_is_short}} 與標準虛擬伺服器供應項目不相容。如果您對標準基礎架構上的任何 {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} 供應項目有興趣，請參閱 [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial)。
{:note}




