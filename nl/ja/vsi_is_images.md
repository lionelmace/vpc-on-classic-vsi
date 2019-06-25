---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# イメージ
{: #images}

{{site.data.keyword.vsi_is_full}} のプロビジョン時には、サポートされているストック・イメージの中からイメージを選択します。選択するイメージによって、インスタンス用にプロビジョンされるオペレーティング・システムが決まります。 
{:shortdesc}

## ストック・イメージ
{: #stock-images}

仮想サーバーを作成する際は、ストック・イメージとして提供されている以下のオペレーティング・システムを選択することができます。
* CentOS 7.x
* Debian 8.x、9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04、18.04
* Windows 2012、2012 R2、2016

インスタンスをオーダーする際、プロビジョニング時間を最適化するためにイメージは cloud-init 対応になっています。 cloud-init 対応のイメージでは、ユーザー・データの提供が可能です。 オーダー・フォームの**「ユーザー・データ」**フィールドに、サーバーのオプションの cloud-init ユーザー・データを入力できます。 ユーザー・データと自動化について詳しくは、[ユーザー・データ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)を参照してください。

## 仮想化
{: #virtualization}
インスタンスには、ハードウェア仮想化マシン (HVM) ブート・モードをサポートするイメージが必要です。 HVM の仮想化タイプを使用すると、仮想サーバー上でイメージを直接実行できます。これは拡張ネットワーキング機能や GPU 機能にとって必須です。
