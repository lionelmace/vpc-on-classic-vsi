---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 管理虚拟服务器实例 (CLI)
{: #managing-virtual-servers-cli}

您可以使用命令行界面 (CLI) 来查看和管理 {{site.data.keyword.vsi_is_full}} 实例。
{:shortdesc}

## 开始之前
{: #prereq-managing-instances}

1. 确保已下载、安装并初始化以下 CLI 插件：
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 插件

   有关更多信息，请参阅 [IBM Cloud CLI for VPC 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)。
   
   首次安装 vpc-infrastructure 插件时，必须将目标生成设置为 gen 1：`ibmcloud is target --gen 1`。
   {:important}
   
2. 确保您已[创建 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 查看实例操作
{: #viewing-instance-actions}

要查看对实例执行的管理操作，请运行以下命令：

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

您将看到类似于以下输出的列表：

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## 管理实例
{: #managing-your-instances}

需要一些帮助吗？可随时运行 `ibmcloud is help` 命令来查看各个命令。

### 重置  

```
ibmcloud is instance-reset
```
{:codeblock}

这将关闭实例的电源，然后再打开电源。  

### 重新启动

```
ibmcloud is instance-reboot
```
{:codeblock}

这将重新启动实例的操作系统。  

### 停止和启动

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

如果设备已停止，那么设备将保持处于停止状态，必须手动启动。无法与处于停止状态的实例进行交互。如果设备已启动，那么可继续进行正常交互。 

### 更新

```
ibmcloud is instance-update
```
{:codeblock}

重命名设备后，将自动更新其名称。执行搜索时，请在尝试查找与实例关联的内容时使用其新名称。 

### 删除

```
ibmcloud is instance-delete
```
{:codeblock}

确认删除操作后，删除实例及其关联的 vNIC、引导卷和数据的过程随即开始。删除操作可能需要几分钟时间，但是此过程完成后，该实例不会再显示在“虚拟服务器实例”页面上。与该虚拟服务器实例关联的浮动 IP 地址已取消关联，但仍保留在帐户上。

如果您更倾向于使用 {{site.data.keyword.cloud}} 控制台来管理实例，请参阅[管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)。
{: tip}
