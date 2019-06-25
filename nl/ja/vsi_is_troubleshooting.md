---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# VPC の仮想サーバーのトラブルシューティング
{: #troubleshooting-your-virtual-servers-for-vpc}
{{site.data.keyword.vsi_is_full}} インスタンスで問題が発生した場合は、考えられる以下の原因を確認してください。

## エラー: 409 インスタンス・アクションの作成時に競合が発生しました

ある一部のインスタンスのアクションは、インスタンスが別のアクションと競合する状況にあると、生成することができません。 例えば、インスタンスの状況が`「停止」`の場合に `「リブート」`のアクションを作成しようとすると、システムから 409 エラーが戻されます。

| 状況      | アクション     | 競合 |
| ----------- | ---------- | -------- |
| 実行中     | 開始      | はい      |
| 停止     | 未開始  | はい      |
| 未実行 | リブート     | はい      |

## インスタンスの状況が`「削除中」`状況のままになる

インスタンスをリストしているときに、インスタンスの状況が`「削除中」`状況のままになっていることに気付いた場合は、show instance api `/instances/{instance_id}` を使用して、特定の仮想サーバー・インスタンスのインスタンス状況を更新してください。 list api `/instances` を使用してすべてのインスタンスを表示するときには、最新の状況は表示されない場合があります。
