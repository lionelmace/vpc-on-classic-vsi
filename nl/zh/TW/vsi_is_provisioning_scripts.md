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

# 使用者資料
{: #user-data}
[comment]: # (鏈結的說明主題)

當您建立 {{site.data.keyword.vsi_is_full}} 實例時，可以新增自動執行一般配置作業或執行 Script 的使用者資料。在訂單表格上的**使用者資料**欄位中，您可以輸入伺服器的選用 cloud-init 使用者資料。
{:shortdesc}

## Linux 的使用者資料範例 
{: #user-data-examples-for-linux}

下列範例顯示 Linux 使用者如何新增使用者並為使用者提供授權的 SSH 金鑰。**名稱**欄位會將公開金鑰新增至 `~/.ssh/authorized_keys`。 

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

下面是另一個 Shell Script 範例，顯示 Linux 使用者如何為現行使用者新增 SSH 金鑰。

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

您可以將這些範例的其中一個直接貼到**使用者資料**欄位中。然後，使用者資料在佈建期間可供虛擬伺服器實例使用。 

如需其他 Linux 使用者資料範例和資訊，請參閱[雲端配置範例 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}。

## Windows 的使用者資料範例
{: #user-data-example-for-windows}

下列範例顯示如何將使用者資料傳遞給 Windows 實例。您可以將此範例直接複製並貼到**使用者資料**欄位中。

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

如需其他 Windows 使用者資料範例和資訊，請參閱 [Cloudbase-init 1.0 文件 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}。
