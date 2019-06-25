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

# SSH 鍵の管理
{: #managing-ssh-keys}

## 始める前に
{: #prereq-ssh-key-available}

{{site.data.keyword.vsi_is_full}} インスタンスにアクセスするには、使用可能な SSH 鍵が必要です。 SSH 鍵を {{site.data.keyword.cloud_notm}} コンソールで管理するか CLI を使用して管理することができます。 

{{site.data.keyword.cloud_notm}} コンソールまたは CLI を使用した鍵の管理は、既に作成済みのインスタンス内の鍵には無効です。 (既存の Linux インスタンスの場合、インスタンスの `~/.ssh/` ディレクトリー内で鍵を直接編集できます。)

SSH 鍵の検索や生成について詳しくは、[SSH 鍵](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)を参照してください。
{: tip}

## IBM Cloud コンソールを使用した SSH 鍵の管理
{: #managing-ssh-keys-with-ibm-cloud-console}

仮想サーバーのプロビジョン時に、使用可能な SSH 鍵の中から選択するか、新しい SSH 鍵をアップロードすることができます。 {{site.data.keyword.cloud_notm}} コンソールで SSH 鍵を生成することはできません。
{:shortdesc}

{{site.data.keyword.cloud_notm}} コンソールを使用して SSH 鍵を管理したり削除したりできます。
1. [{{site.data.keyword.cloud_notm}} コンソール ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.cloud.ibm.com/vpc) で、**「メニュー」アイコン ![「メニュー」アイコン](../icons/icon_hamburger.svg) >「VPC インフラストラクチャー」>「コンピュート」>「SSH 鍵」**にナビゲートします。
2. ここから、SSH 鍵を追加したり削除したりできます。

## CLI を使用した SSH 鍵の管理
{: #managing-ssh-keys-by-using-the-cli}

CLI を使用して SSH 鍵を管理することもできます。

| アクション           | コマンド                     | 次に生じること |
| ---------------- | --------------------------- | ----------------- |
| SSH 鍵の作成   | `ibmcloud is key-create`    | SSH 鍵を作成し終えると、その鍵が鍵のリストに追加されます。 |
| 鍵の詳細の表示 | `ibmcloud is key`           | 鍵の名前と鍵の ID を表示できます。 |
| 鍵のリスト        | `ibmcloud is keys`          | 既存の SSH 鍵をすべて表示できます。 |
| キーの更新       | `ibmcloud is key-update`    | 既存の鍵を更新し終えると、その鍵の名前が即時に変更されます。 |
| キーの削除       | `ibmcloud is key-delete`    | SSH 鍵を削除し終えると、新しいインスタンスをプロビジョンする際や既存のインスタンス上で OS の再ロードを実行する際にこの鍵を使用できなくなります。 しかし、この鍵を使用してプロビジョンしたインスタンス上ではこの鍵を引き続き使用でき、この鍵を使用してログインできます。 |
{: caption="表 1. SSH 鍵のアクション" caption-side="top"}
