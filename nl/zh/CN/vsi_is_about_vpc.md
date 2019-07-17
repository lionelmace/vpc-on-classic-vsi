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

# 关于 Virtual Servers for VPC
{: #virtual-private-cloud}

通过 {{site.data.keyword.vsi_is_full}}，您可利用 {{site.data.keyword.vpc_short}} 的所有优点，包括网络隔离、安全性和灵活性。
{:shortdesc}

## 什么是 {{site.data.keyword.vpc_short}}？
{{site.data.keyword.vpc_short}} 是一种与客户帐户绑定的虚拟网络。VPC 作为高性价比入口点，提供了云安全性以及随增长动态缩放的能力。此外，还支持您对虚拟基础架构和网络流量分段进行细颗粒度控制。
{: shortdesc}

有关 {{site.data.keyword.vpc_short}} 的更多信息，请参阅[关于 IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about)。

## 什么是 {{site.data.keyword.vsi_is_short}}？
通过 {{site.data.keyword.vsi_is_short}}，您可以在 {{site.data.keyword.vpc_short}} 中创建实例，其中包含虚拟计算资源以及相应的容量。供应实例时，可选择与计划在实例上运行的应用程序或软件所需的内存量和计算能力相匹配的实例概要文件。供应实例后，您可控制和管理这些基础架构资源。每个帐户都会对各个服务器中运行的实例数进行限制。有关此限制的更多信息，请参阅[常见问题](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)。 

## 用于 {{site.data.keyword.vpc_short}} 的虚拟服务器实例与其他 IBM 虚拟服务器产品有何不同？

在如今的 IBM Cloud 虚拟服务器产品中，实例是使用本机子网和 VLAN 联网在一个数据中心（和单个 pod）内相互通信。在一个 pod 中使用子网和 VLAN 联网就能实现良好运作，除非您必须扩展或有较大的虚拟资源需求，需要在 pod 之间创建资源。（添加设备进行 VLAN 生成会增加费用并使部署变得复杂！） 

{{site.data.keyword.vpc_short}} 添加了网络编排层，用于消除 pod 边界，从而为缩放实例创建无限容量。网络编排层可处理各个区域和专区中一个 {{site.data.keyword.vpc_short}} 内的所有虚拟服务器实例的所有联网。通过 {{site.data.keyword.vpc_short}} 提供的软件定义的联网功能，您将有更多 [VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc)、[LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc)、多 vNIC 实例和更大[子网](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets)大小的选项。有关更多信息，请参阅[关于 VPC 联网](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)。 

{{site.data.keyword.vsi_is_short}} 还具有以下功能，简化了用户体验并节省了成本：
* 新的 {{site.data.keyword.cloud_notm}} 控制台
* 新的 Virtual Private Cloud API 和 CLI
* 具有持续使用折扣层的新计费模型，如[定价](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)中所述

{{site.data.keyword.vsi_is_short}} 与经典虚拟服务器产品不兼容。如果您对经典基础架构上的任何 {{site.data.keyword.cloud_notm}}{{site.data.keyword.BluVirtServers_short}} 产品感兴趣，请参阅 [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial)。
{:note}




