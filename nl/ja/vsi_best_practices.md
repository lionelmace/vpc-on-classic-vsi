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

# インスタンスの計画
{: #planning-for-instances}
[comment]: # (リンクされているヘルプ・トピック)


{{site.data.keyword.vsi_is_full}} のプロビジョンを計画するときは、ここに挙げる構成チェックリストを使用すると、仮想サーバーのデプロイメントから最大限のメリットを引き出すことができます。
{:shortdesc}

始める前に、[{{site.data.keyword.vpc_short}} を作成して](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)おく必要があります。
{:important}

## インスタンスのプロビジョンの計画
{: #planning-for-provisioning-instances}

{{site.data.keyword.vpc_short}} が使用可能になった後、インスタンスをプロビジョンする前に、以下を検討してください。

|        考慮事項|
|-------------------|
|__ 1. アカウントに必要な[ユーザー権限](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)があることを確認します。 {{site.data.keyword.vpc_short}} リソースの編集者または管理者の許可を持っている場合は、その仮想プライベート・クラウド内で仮想サーバー・インスタンスを作成、削除、および変更する権限も継承します。|
|__ 2. 同時インスタンスに関する[アカウント制限](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)を確認します。 |
|__ 3. [SSH 鍵](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)が使用可能であることを確認します。
|__ 4. 選択するインスタンス・ロケーションを決定します。|
|__ 5. ワークロードの vCPU と RAM の組み合わせの一般的な[プロファイル・オプション](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)を検討します。 プロファイルには、数分ですぐに使用できる事前構成済みインスタンスが含まれています。 ワークロードと環境を稼働状態に保つために、インスタンスに必要なリソースを確保することが重要です。|
|__ 6. インスタンスに選択するオペレーティング・システムのイメージを決定します。 現在のストック・[イメージ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)の中から選択することができます。 |
|__ 7. インスタンスに固有の名前を付けます。 仮想サーバー・インスタンスの命名方法を定めておくと、後でインスタンスをフィルタリングしたり検索したりするのが、ずっと簡単になります。 |

## 次のステップ
{: #next-create-instance}

開始する準備ができたら、以下のリソースを参照しながらインスタンスを作成してください。
* [{{site.data.keyword.cloud_notm}} コンソールを使用したインスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [CLI を使用したインスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
