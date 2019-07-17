---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# 规划实例
{: #planning-for-instances}
[comment]: # (链接的帮助主题)


规划供应 {{site.data.keyword.vsi_is_full}} 时，您可能会发现此配置核对表有助于最充分地了解虚拟服务器部署。
{:shortdesc}

开始之前，请确保您已[创建 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

## 规划供应实例
{: #planning-for-provisioning-instances}

{{site.data.keyword.vpc_short}} 可用后，在供应实例之前，请考虑以下注意事项。

|注意事项|
|-------------------|
|__ 1. 确保您的帐户具有必需的[用户许可权](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)。如果您对 {{site.data.keyword.vpc_short}} 资源具有编辑者或管理员权限，那么您同时会继承在该虚拟私有云中创建、删除和修改虚拟服务器实例的权限。|
|__ 2. 检查[帐户限制](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)以了解并发实例数。|
|__ 3. 确保 [SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)可用。
|__ 4. 确定要选择的实例位置。|
|__ 5. 考虑工作负载的 vCPU 和 RAM 组合的常用[概要文件选项](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)。概要文件包含预配置的实例，这些实例在几分钟内就可供使用。务必确保实例具有必要的资源，可使工作负载和环境保持正常运行。|
|__ 6. 确定将为实例选择哪个操作系统映像。可以在当前库存[映像](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)中进行选择。|
|__ 7. 确保实例具有唯一名称。如果您采用一种方法来命名虚拟服务器实例，那么日后对实例进行过滤和搜索会轻松得多。|

## 后续步骤
{: #next-create-instance}

准备好开始使用时，请参阅以下资源以创建实例：
* [使用 {{site.data.keyword.cloud_notm}} 控制台创建实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [使用 CLI 创建实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
