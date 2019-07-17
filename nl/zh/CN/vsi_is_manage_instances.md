---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 管理虚拟服务器实例
{: #managing-virtual-server-instances}
[comment]: # (链接的帮助主题)

您可以在 {{site.data.keyword.cloud_notm}} 控制台的*虚拟服务器实例*页面中查看和管理 {{site.data.keyword.vsi_is_full}} 实例。
{:shortdesc}

要管理实例，请完成以下步骤。
1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.cloud.ibm.com/vpc) 中，导航至**“菜单”图标 ![“菜单”图标](../icons/icon_hamburger.svg) > VPC 基础架构 > 计算 > 虚拟服务器实例**。
2. 在其中，可以管理特定实例的任务，或者单击实例以查看和编辑其属性。

## 重新引导

重新引导操作会立即关闭实例的电源，然后重新打开其电源。

## 停止和启动

停止和启动操作可远程关闭或打开实例。如果实例已停止，那么实例将保持处于停止状态，必须手动启动。在实例停止期间，对于某些计算资源，计费会处于[已暂挂](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing)状态。无法与处于停止状态的实例进行交互。如果设备已启动，那么可继续进行正常交互。

## 删除

删除操作会从帐户中永久除去实例及其连接的 vNIC、引导卷和数据。确认删除操作后，删除实例及其关联的 vNIC、引导卷和数据的过程随即开始。删除操作可能最长需要 30 分钟时间，但是此过程完成后，该实例不会再显示在“虚拟服务器实例”页面上。与该虚拟服务器实例关联的浮动 IP 地址已取消关联，但仍保留在帐户上。

## 查看实例详细信息
可以通过在*虚拟服务器实例*页面上查看所有实例的摘要，或者通过单击单个实例来查看详细信息并进行更改，从而与实例进行交互。在实例详细信息页面中，还可以查看关联的网络接口，访问其子网以及保留或删除浮动 IP 地址。

如果您希望使用 CLI 来管理实例，请参阅[使用 CLI 管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)。
{: tip}
