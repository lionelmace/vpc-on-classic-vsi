---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# 概要文件
{: #profiles}

供应 {{site.data.keyword.vsi_is_full}} 时，可以从三个概要文件系列（均衡、计算和内存）中进行选择。概要文件是 vCPU 和 RAM 的组合，可以快速实例化以启动虚拟服务器实例。在 {{site.data.keyword.Bluemix_notm}} 控制台中，可以从常用的概要文件配置中进行选择，也可以从概要文件列表中选择最符合您需求的概要文件。
{: shortdesc}

以下系列可用：

|系列|描述|
| -------- | ----------- |
|[均衡](#balanced)|最适合用于需要均衡性能和可伸缩性的常用云工作负载。均衡概要文件（使用网络连接存储器）能避免资源需求过量，因而可提高性能。|
|[计算](#compute)|最适合用于中高 Web 流量的工作负载。计算概要文件最适合具有密集 CPU 需求的工作负载，例如高 Web 流量工作负载、生产批量处理和前端 Web 服务器。|
|[内存](#memory)|最适合用于内存高速缓存和实时分析工作负载。内存概要文件最适合内存密集型工作负载，例如大型高速缓存工作负载、密集型数据库应用程序或内存中分析工作负载。|
{: caption="表 1. 虚拟服务器系列选择" caption-side="top"}

## 均衡
{: #balanced}

均衡概要文件能避免资源需求过量，因而可提高性能。网络性能的范围从标准到高端。

此系列通过以下概要文件来提供：

|概要文件|vCPU|RAM|
|---------|---------|---------|
|bc1-2x8|2|8|
|bc1-4x16|4|16|
|bc1-8x32|8|32|
|bc1-16x64|16|64|
|bc1-32x128|32|128|
|bc1-48x192|48 |192|
|bc1-62x248|62|248|
{: caption="表 2. 虚拟服务器均衡概要文件选项" caption-side="top"}

**存储器说明**：

* SAN 主引导卷 (100 GB) 在供应实例时会自动创建并连接。
* （可选）创建辅助数据卷。卷概要文件可作为三个预定义的 IOPS 层或作为定制 IOPS 提供。[3 IOPS 通用层概要文件](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)提供适用于 VSI 均衡概要文件的 IOPS/GB 性能。
* 使用 SAN 存储器的公共虚拟服务器的定价包括虚拟 CPU、内存和主引导卷。辅助数据卷单独定价。

所有支持的操作系统（例如，CentOS、Debian、Ubuntu 和 Windows）都可用于此系列。

## 计算
{: #compute}

计算概要文件最适合具有密集 CPU 需求的工作负载，例如高 Web 流量工作负载、生产批量处理和前端 Web 服务器。

此系列通过以下概要文件来提供：

|概要文件|vCPU|RAM|
|---------|---------|---------|
|cc1-2x4|2|4|
|cc1-4x8|4|8| 
|cc1-8x16|8|16|
|cc1-16x32|16|32|
|cc1-32x64|32|64|
{: caption="表 3. 虚拟服务器实例计算概要文件选项" caption-side="top"}

**存储器说明**： 

* SAN 主引导卷 (100 GB) 在供应实例时会自动创建并连接。
* （可选）创建辅助数据卷。卷概要文件可作为三个预定义的 IOPS 层或作为定制 IOPS 提供。[5 IOPS 层](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)概要文件提供适用于 VSI 计算概要文件的 IOPS/GB 性能。
* 使用 SAN 存储器的公共虚拟服务器的定价包括虚拟 CPU、内存和主引导卷。辅助数据卷单独定价。

所有支持的操作系统（例如，CentOS、Debian、Ubuntu 和 Windows）都可用于此系列。 

## 内存 
{: #memory}

内存概要文件最适合内存密集型工作负载，例如大型高速缓存工作负载、密集型数据库应用程序或内存中分析工作负载。

此系列通过以下概要文件来提供：

|概要文件|vCPU|RAM|
|---------|---------|---------|
|mc1-2x16|2|16|
|mc1-4x32|4|32|
|mc1-8x64|8|64|
|mc1-16x128|16|128|
|mc1-32x256|32|256|
{: caption="表 4. 虚拟服务器实例内存概要文件选项" caption-side="top"}

**存储器说明**： 

* SAN 主引导卷 (100 GB) 在供应实例时会自动创建并连接。
* （可选）创建辅助数据卷。卷概要文件可作为三个预定义的 IOPS 层或作为定制 IOPS 提供。[10 IOPS 层](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)概要文件提供适用于 VSI 内存概要文件的 IOPS/GB 性能。
* 使用 SAN 存储器的公共虚拟服务器的定价包括虚拟 CPU、内存和主引导卷。辅助数据卷单独定价。

所有支持的操作系统（例如，CentOS、Debian、Ubuntu 和 Windows）都可用于此系列。 

## 查看概要文件配置
{: #popularprofiles}

可以使用 {{site.data.keyword.cloud_notm}} 控制台或 CLI 来查看可用的概要文件配置。在 {{site.data.keyword.cloud_notm}} 控制台中，可以从支持最常见用例的常用概要文件配置中进行选择。

### 使用 IBM Cloud 控制台
1. 在 {{site.data.keyword.cloud_notm}} 控制台中，导航至**“菜单”图标 ![“菜单”图标](../icons/icon_hamburger.svg) > VPC 基础架构 > 计算 > 虚拟服务器实例**。
2. 在此页面中，单击**新建实例**。
3. 可以从**常用概要文件**中选择概要文件配置，或者单击**所有概要文件**以查看其他配置。

### 使用 CLI
要使用 CLI 来查看可用概要文件的列表，请运行以下命令：
```
$ ibmcloud is instance-profiles
```
{:codeblock}

使用命令行时，以下信息描述了输出表示的内容。不同的概要文件大小具有不同的 CPU 与内存比率，是针对不同的工作负载而设计的：

*  “b”表示均衡，该比率为 1:2 或 1:4
*  “c”表示计算（CPU 更高），该比率为 1:1
*  “m”表示内存（内存更高），该比率为 1:8
