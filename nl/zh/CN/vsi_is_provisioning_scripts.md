---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 用户数据
{: #user-data}
[comment]: # (链接的帮助主题)

创建 {{site.data.keyword.vsi_is_full}} 实例时，可以添加用于自动执行常见配置任务或运行脚本的用户数据。在订购表单上的**用户数据**字段中，可以输入服务器的可选 cloud-init 用户数据。
{:shortdesc}

## Linux 的用户数据示例 
{: #user-data-examples-for-linux}

以下示例显示了 Linux 用户可以如何添加新用户，并向用户提供授权的 SSH 密钥。**名称**字段将公用密钥添加到 `~/.ssh/authorized_keys`。 

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

下面是 shell 脚本的另一个示例，显示了 Linux 用户可以如何为当前用户添加 SSH 密钥。

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

可以将其中一个示例直接粘贴到**用户数据**字段中。然后，在供应期间，用户数据可用于虚拟服务器实例。 

有关更多 Linux 用户数据示例和信息，请参阅 [Cloud config examples ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}。

## Windows 的用户数据示例
{: #user-data-example-for-windows}

以下示例显示了用户数据可以如何传递到 Windows 实例。可以将此示例直接复制并粘贴到**用户数据**字段中。

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

有关更多 Windows 用户数据示例和信息，请参阅 [Cloudbase-init 1.0 文档 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}。
