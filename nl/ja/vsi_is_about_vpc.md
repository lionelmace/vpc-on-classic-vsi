---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# VPC の仮想サーバーについて
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}} では、ネットワークの分離、セキュリティー、柔軟性など、{{site.data.keyword.vpc_short}} が提供するすべての利点を活用することができます。 
{:shortdesc}

## {{site.data.keyword.vpc_short}} とは
{{site.data.keyword.vpc_short}} は、お客様アカウントに関連付けられた仮想ネットワークです。 これは、セキュリティーを実装したクラウドを利用するためのコスト効率の高いエントリー・ポイントとなり、成長に応じた動的スケーリングの機能も提供します。 仮想インフラストラクチャーとネットワーク・トラフィックのセグメンテーションをお客様がきめ細かく制御することができます。
{: shortdesc}

{{site.data.keyword.vpc_short}} について詳しくは、[IBM Cloud VPC について](/docs/vpc-on-classic?topic=vpc-on-classic-about)を参照してください。

## {{site.data.keyword.vsi_is_short}} とは
{{site.data.keyword.vsi_is_short}}では、{{site.data.keyword.vpc_short}}内の仮想計算リソースと結果の容量で構成されるインスタンスを作成できます。 インスタンスをプロビジョンするときに、インスタンスで実行する予定のアプリケーションまたはソフトウェアに必要なメモリー量と計算能力に一致するインスタンス・プロファイルを選択します。 インスタンスをプロビジョンした後は、それらのインフラストラクチャー・リソースを制御および管理します。 各アカウントには、サーバー間で実行されるインスタンス数の制限があります。 この制限について詳しくは、[FAQ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) を参照してください。 

## {{site.data.keyword.vpc_short}} の仮想サーバー・インスタンスは、他の IBM 仮想サーバー・オファリングとどこが違いますか?

現在の IBM Cloud Virtual Server オファリングでは、インスタンス同士は、データ・センター (および単一のポッド) 内でネイティブ・サブネットと VLAN ネットワーキングを使用して相互に通信します。 1 つのポッドでサブネットと VLAN ネットワーキングを使用するこの方法が効果的なのは、スケール・アップが必要になったり、大規模な仮想リソースの要求が生じて複数のポッド間でリソースを作成しなければならなくなったりしないうちだけです。 (VLAN スパンニングのためにアプライアンスを追加するのでは、コストがかかり複雑になる可能性があります。) 

{{site.data.keyword.vpc_short}} では、ポッドの限界を取り払うネットワーク・オーケストレーション層が追加され、インスタンスのスケーリングのために無限の容量が利用できるようになっています。 ネットワーク・オーケストレーション層は、複数の地域およびゾーンにわたる {{site.data.keyword.vpc_short}} 内にあるすべての仮想サーバー・インスタンスのすべてのネットワーキングを処理します。 {{site.data.keyword.vpc_short}} では、ソフトウェア定義のネットワーキング機能が提供されるので、[VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc)、[LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc)、複数 vNIC のインスタンス、およびより大きな[サブネット](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets)・サイズについてのより多くの選択肢が与えられます。 詳しくは、[VPC のネットワーキングについて](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)を参照してください。 

{{site.data.keyword.vsi_is_short}} には、よりシンプルなユーザー・エクスペリエンスとコスト削減を実現する次のような機能も備えられています。
* 新しい {{site.data.keyword.cloud_notm}} コンソール
* 仮想プライベート・クラウドの新しい API および CLI
* 継続使用割引層による新しい請求モデル ([料金](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)を参照)。

{{site.data.keyword.vsi_is_short}} には、クラシック仮想サーバー・オファリングとの互換性がありません。 クラシック・インフラストラクチャーの {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} オファリングに関心がある場合は、[IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial)を参照してください。
{:note}




