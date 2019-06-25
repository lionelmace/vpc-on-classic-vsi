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

# ユーザー・データ
{: #user-data}
[comment]: # (リンクされているヘルプ・トピック)

{{site.data.keyword.vsi_is_full}} インスタンスを作成する際に、一般的な構成タスクを自動的に実行したりスクリプトを稼働したりするユーザー・データを追加できます。 オーダー・フォームの**「ユーザー・データ」**フィールドに、サーバーのオプションの cloud-init ユーザー・データを入力できます。
{:shortdesc}

## Linux の場合のユーザー・データの例 
{: #user-data-examples-for-linux}

以下の例は、Linux ユーザーが新しいユーザーを追加し、許可された SSH 鍵をそのユーザーに提供する方法を示しています。 **name** フィールドに、`~/.ssh/authorized_keys` に追加された公開鍵が示されます。 

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

以下に示す別のシェル・スクリプトの例では、Linux ユーザーが現行ユーザーの SSH 鍵を追加する方法を示しています。

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

これらのいずれかの例を**「ユーザー・データ」**フィールドに直接貼り付けることができます。 貼り付けると、プロビジョニング中に仮想サーバー・インスタンスでこのユーザー・データを使用できるようになります。 

Linux ユーザー・データの例と情報について詳しくは、[Cloud 構成の例 ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window} を参照してください。

## Windows の場合のユーザー・データの例
{: #user-data-example-for-windows}

以下の例は、ユーザー・データを Windows インスタンスに渡す方法を示しています。 この例を**「ユーザー・データ」**フィールドに直接コピーして貼り付けることができます。

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

Windows ユーザー・データの例と情報について詳しくは、[Cloudbase-init 1.0 の資料 ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window} を参照してください。
