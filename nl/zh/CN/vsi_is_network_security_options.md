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

# 虚拟服务器上的联网和安全性
{: #network-security-options}

实现 {{site.data.keyword.vsi_is_full}} 后，您有权访问联网和安全性的最新功能。  
{:shortdesc}

## 使用实例 vNIC
{: #using-instance-vnics}

虚拟网络接口卡 (vNIC) 用于将虚拟服务器连接到网络。创建 VSI 实例时，可以使用 vNIC 来分配多个 IP 地址。以下列表重点说明了 vNIC 如何用于实例。

* 可以为每个实例创建并分配最多 5 个 vNIC。对于每个 vNIC，会从连接的子网中为其分配一个专用 IP，并且可以选择连接浮动 IP 和安全组。
* 可以将每个 vNIC 连接到同一专区中的子网。
* 每个 vNIC 接收子网范围中的一个专用 IP。
* 可以将浮动 IP 与每个 vNIC 相关联或取消关联。
* 可以向每个 vNIC 分配多个安全组。
* 可以更改任何现有 vNIC 的名称。

带宽与实例本身相关联，不是单个 vNIC 的可配置项。实例的缺省带宽为 100 Mbps，可选择升级到 1 Gbps。

## 联网选项
{: #networking-options}

有关 {{site.data.keyword.vpc_short}} 环境中总体联网功能的更多信息，请参阅[关于 VPC 联网](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)。

## 安全选项
{: #security-options}

{{site.data.keyword.vsi_is_short}} 包含内置安全选项：
* 访问控制表 (ACL) 可以限制进出子网的流量。
* 安全组充当虚拟服务器实例的虚拟防火墙。
* 虚拟服务器实例上的 SSH 密钥认证用于网络通信的安全通道。

有关这些安全选项的更多信息，请参阅 [IBM Cloud VPC 中的安全性](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)和[管理 SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)。
