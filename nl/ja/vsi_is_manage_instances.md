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

# 仮想サーバー・インスタンスの管理
{: #managing-virtual-server-instances}
[comment]: # (リンクされているヘルプ・トピック)

{{site.data.keyword.cloud_notm}} コンソール内の*「Virtual Server インスタンス」*ページから、{{site.data.keyword.vsi_is_full}} インスタンスを表示したり管理したりできます。
{:shortdesc}

インスタンスを管理するには、以下のステップを実行します。
1. [{{site.data.keyword.cloud_notm}} コンソール ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.cloud.ibm.com/vpc) で、**「メニュー」アイコン ![「メニュー」アイコン](../icons/icon_hamburger.svg) >「VPC インフラストラクチャー」>「コンピュート」>「Virtual Server インスタンス」**にナビゲートします。
2. ここから、特定のインスタンスのタスクを管理したり、インスタンスをクリックしてそのプロパティーを表示して編集したりすることができます。

## リブート

リブート・アクションは、インスタンスを即時にパワーオフにしてから、再びパワーオンにします。

## 停止と開始

停止と開始アクションは、リモートでインスタンスをオフまたはオンにします。 インスタンスを停止すると、そのインスタンスは停止状態のままになるので、手動で開始する必要があります。 インスタンスの停止中は、一部のコンピュート・リソースに対する課金が[中断](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing)されます。 停止されているインスタンスとは対話できません。 そのデバイスを開始すれば、正常な対話が続行されます。

## 削除

削除アクションは、インスタンスとそのインスタンスに接続している vNIC、ブート・ボリューム、データをアカウントから永久に削除します。 削除アクションを確定すると、インスタンスとその関連 vNIC、ブート・ボリューム、データを削除するプロセスが開始されます。 削除アクションには最大で 30 分かかることがありますが、このプロセスが完了すると、「Virtual Server インスタンス」ページにそのインスタンスは表示されなくなります。 仮想サーバー・インスタンスに関連付けられている浮動 IP アドレスは関連付け解除されますが、アカウントには残ります。

## インスタンスの詳細の表示
インスタンスと対話するには、*「Virtual Server インスタンス」*ページですべてのインスタンスのサマリーを表示するか、個々のインスタンスをクリックして詳細を表示したり変更を加えたりします。 インスタンスの詳細ページから、関連付けられているネットワーク・インターフェースを表示したり、そのサブネットにアクセスしたり、浮動 IP アドレスの予約や削除を行ったりすることもできます。

CLI を使用してインスタンスを管理することをご希望の場合は、[仮想サーバー・インスタンスの管理 (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli) を参照してください。
{: tip}
