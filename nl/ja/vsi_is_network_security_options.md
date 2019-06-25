---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# 仮想サーバー上のネットワーキングとセキュリティー
{: #network-security-options}

{{site.data.keyword.vsi_is_full}} を実装しているときは、ネットワーキングとセキュリティーのための最新の機能にアクセスできます。  
{:shortdesc}

## インスタンスの vNIC の使用
{: #using-instance-vnics}

仮想ネットワーク・インターフェース・カード (vNIC) は、仮想サーバーをネットワークに接続するのに使用します。 VSI インスタンスの作成時に、vNIC を使用して複数の IP アドレスを割り当てることができます。 vNIC がインスタンスでどのような動作をするのかについて、主立った点を以下に示します。

* 各インスタンスには、最大 5 つの vNIC を作成して割り当てることができます。 各 vNIC には、接続しているサブネットからプライベート IP が割り当てられます。オプションで、浮動 IP とセキュリティー・グループを割り当てることができます。
* 各 vNIC は、同じゾーン内の 1 つのサブネットに接続できます。
* 各 vNIC には、サブネットの範囲からプライベート IP が割り当てられます。
* 各 vNIC には、浮動 IP を関連付けたり、その関連付けを解除したりすることができます。
* 各 vNIC には、セキュリティー・グループを割り当てることができます。
* 既存の vNIC の名前を変更することができます。

帯域幅は、インスタンス自体に関連付けられるので、個々の vNIC で構成できる要素ではありません。 インスタンスのデフォルトの帯域幅は 100 Mbps で、オプションで 1 Gbps までアップグレード可能です。

## ネットワーキング・オプション
{: #networking-options}

{{site.data.keyword.vpc_short}} 環境内のネットワーキング機能全般について詳しくは、[VPC のネットワーキングについて](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)を参照してください。

## セキュリティー・オプション
{: #security-options}

{{site.data.keyword.vsi_is_short}} には、以下の組み込みのセキュリティー・オプションが含まれています。
* アクセス制御リスト (ACL) で、サブネットとの間のトラフィックを制限できます。
* セキュリティー・グループは、仮想サーバー・インスタンスの仮想ファイアウォールとして機能します。
* 仮想サーバー・インスタンス上の SSH 鍵が、ネットワーク通信用のセキュア・チャネルを認証します。

これらのセキュリティー・オプションについて詳しくは、[IBM Cloud VPC でのセキュリティー](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)および [SSH 鍵の管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)を参照してください。
