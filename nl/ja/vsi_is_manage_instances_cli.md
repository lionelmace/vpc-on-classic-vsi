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


# 仮想サーバー・インスタンスの管理 (CLI)
{: #managing-virtual-servers-cli}

コマンド・ライン・インターフェース (CLI) を使用して、{{site.data.keyword.vsi_is_full}} インスタンスを表示して管理できます。
{:shortdesc}

## 始める前に
{: #prereq-managing-instances}

1. 以下の CLI プラグインのダウンロード、インストール、初期化を行っていることを確認します。
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service プラグイン

   詳しくは、[IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference) を参照してください。
   
   vpc-infrastructure プラグインを初めてインストールする場合は、ターゲット世代を gen 1 に設定して、`ibmcloud is target -gen 1` とする必要があります。
   {:important}
   
2. 既に [{{site.data.keyword.vpc_short}} を作成している](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)ことを確認します。

## インスタンス・アクションの表示
{: #viewing-instance-actions}

インスタンスに対して実行される管理アクションを表示するには、以下のコマンドを実行します。

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

以下の出力のようなリストが表示されます。

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## インスタンスの管理
{: #managing-your-instances}

もう少し詳しい情報が必要な場合は、 いつでも `ibmcloud is help` コマンドを実行して、コマンドを表示することができます。

### リセット  

```
ibmcloud is instance-reset
```
{:codeblock}

インスタンスがパワーオフにされてから、パワーオンにされます。  

### 再始動

```
ibmcloud is instance-reboot
```
{:codeblock}

インスタンスのオペレーティング・システムが再始動されます。  

### 停止と開始

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

デバイスが停止されると、そのデバイスは停止状態のままになるので、手動で開始する必要があります。 停止されているインスタンスとは対話できません。 そのデバイスを開始すれば、正常な対話が続行されます。 

### 更新

```
ibmcloud is instance-update
```
{:codeblock}

デバイスの名前を変更すると、その名前が自動的に更新されます。 検索を実行する場合、このインスタンスに関連付けられた内容を検索するときは新しいインスタンス名を使用してください。 

### 削除

```
ibmcloud is instance-delete
```
{:codeblock}

削除アクションを確定すると、インスタンスとその関連 vNIC、ブート・ボリューム、データを削除するプロセスが開始されます。 削除アクションには数分かかることがありますが、このプロセスが完了すると、「Virtual Server インスタンス」ページにそのインスタンスは表示されなくなります。 仮想サーバー・インスタンスに関連付けられている浮動 IP アドレスは関連付け解除されますが、アカウントには残ります。

{{site.data.keyword.cloud}} コンソールを使用してインスタンスを管理することをご希望の場合は、[仮想サーバー・インスタンスの管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)を参照してください。
{: tip}
