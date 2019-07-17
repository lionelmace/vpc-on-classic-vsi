---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 管理 SSH 密钥
{: #managing-ssh-keys}

## 开始之前
{: #prereq-ssh-key-available}

要访问 {{site.data.keyword.vsi_is_full}} 实例，您必须有 SSH 密钥可供使用。可以在 {{site.data.keyword.cloud_notm}} 控制台中以及使用 CLI 来管理 SSH 密钥。 

使用 {{site.data.keyword.cloud_notm}} 控制台或 CLI 管理密钥对已创建实例中的密钥不起作用。（对于现有 Linux 实例，可以直接在实例的 `~/.ssh/` 目录中编辑密钥。）

有关查找或生成 SSH 密钥的更多信息，请参阅 [SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)。
{: tip}

## 使用 IBM Cloud 控制台管理 SSH 密钥
{: #managing-ssh-keys-with-ibm-cloud-console}

供应虚拟服务器时，可以从可用的 SSH 密钥中进行选择，也可以上传新的 SSH 密钥。不能在 {{site.data.keyword.cloud_notm}} 控制台中生成 SSH 密钥。
{:shortdesc}

可以使用 {{site.data.keyword.cloud_notm}} 控制台来管理和删除 SSH 密钥。
1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.cloud.ibm.com/vpc) 中，导航至**“菜单”图标 ![“菜单”图标](../icons/icon_hamburger.svg) > VPC 基础架构 > 计算 > SSH 密钥**。
2. 在其中，可以添加或删除 SSH 密钥。

## 使用 CLI 管理 SSH 密钥
{: #managing-ssh-keys-by-using-the-cli}

还可以使用 CLI 来管理 SSH 密钥。

|操作|命令|后续操作|
| ---------------- | --------------------------- | ----------------- |
|创建 SSH 密钥|`ibmcloud is key-create`|创建 SSH 密钥后，会将其添加到密钥列表中。|
|查看密钥详细信息|`ibmcloud is key`|可以查看密钥的名称和密钥的标识。|
|列出密钥|`ibmcloud is keys`|可以查看所有现有 SSH 密钥。|
|更新密钥|`ibmcloud is key-update`|更新现有密钥后，密钥会立即重命名。|
|删除密钥|`ibmcloud is key-delete`|除去 SSH 密钥后，在供应新实例或在现有实例上执行操作系统重装时，无法再使用该密钥。但是，在使用该密钥供应的任何实例上该密钥仍可用，并且可以使用该密钥进行登录。|
{: caption="表 1. SSH 密钥操作" caption-side="top"}
