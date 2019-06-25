---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# 入門チュートリアル
{: #getting-started}

{{site.data.keyword.vsi_is_full}} (VPC) を使用して、スケーラブルなコンピュート・リソースを IBM Cloud にプロビジョンします。
{:shortdesc}

必要な数の仮想サーバーを作成し、ネットワークとセキュリティーを構成し、ストレージを管理することができます。 これらの操作はすべて、改善された IBM Cloud コンソールから行えます。 このコンソールは、変化するワークロードの要求に合わせてご使用の環境を調整するために迅速かつ簡単にアクセスできるよう構築されています。 早速、始めるための具体的な手順に進みましょう。

始める前に、[IBM Cloud VPC を作成して](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)おく必要があります。
{:important}

{{site.data.keyword.vsi_is_short}} には、クラシック仮想サーバー・オファリングとの互換性がありません。 クラシック・インフラストラクチャーの {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} オファリングに関心がある場合は、[IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial)を参照してください。
{:note}

<p>インスタンスの作成とインスタンスへの接続を早速始めるために、以下の手順に従ってください。
<table>
   <CAPTION>表 1. クイック・スタート・ステップ</CAPTION>
   <THEAD>
   <TR>
   <th>タスク</th>
   <th>詳細</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. 実装環境に役立つコンテンツを確認する</td>
   <td>IBM Cloud と仮想サーバーは初めてですか? 以下のサイトに、ご使用の環境を計画するために役立つ有益な情報が記載されています。
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">IBM Cloud とは</a></li>
      <li><a href="https://ibm.com/cloud/get-started">IBM Cloud の概要</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. IBM Cloud に登録する</td>
   <td>IBM Cloud アカウントのセットアップ方法については、<a href="/docs/account?topic=account-signup#signup">IBM Cloud への登録</a>を参照してください。</td>
 <tr>
   <td>3. ワークロード仕様を決定する</td>
   <td>インスタンスを作成する前に、インスタンスの用途と、正常に作動させるために必要なインスタンスのサイズを決定します。 例えば、開発とテスト用か、それとも実動用か、ユーザー・エクスペリエンスをテストするか、長いアルゴリズムを処理するか、データをバックアップおよびリストアするか、待ち時間の速度を上げるか、などを決定します。</td>  
 <tr>
   <td>4. インスタンスのサイズと料金を決める</td>
   <td>インスタンスを作成する際は、平衡型、コンピュート、メモリーの 3 つのファミリー・オプションの中から選択することができます。 これらのファミリーには、ほとんどのお客様のニーズを満たす、プロファイルと呼ばれる事前構成済みインスタンスが含まれており、それらはほんの 5 分程度で構成可能な状態にすることができます。  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">平衡型</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">コンピュート</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">メモリー</a></li>
     </ul>
  <p>インスタンスのサイズと料金を決めるにあたっては、[料金](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)の情報を参考にすることができます。</p></td>
 <tr>
   <td>5. IBM Cloud アカウントにログインする</td>
   <td><a href="https://console.bluemix.net/catalog/">IBM Cloud カタログ</a>から {{site.data.keyword.vsi_is_short}} 注文フォームにアクセスします。 <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBMid とパスワード</a>が必要になります。
   </td>
 <tr>
   <td>6. {{site.data.keyword.vpc_short}} エクスペリエンスへのアクセスを要求する</td>
   <td>まだ {{site.data.keyword.vpc_short}} へのアクセスを要求していない場合は、アクセスを要求してください。</td>
<tr>
<td>7. SSH 鍵を生成する</td>
<td> 詳しくは、[SSH 鍵](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)を参照してください。</td>
<tr>
<td>8. インスタンスの計画を立てる</td>
<td> リソースの計画、プロビジョン、および構成について詳しくは、[インスタンスの計画](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances)を参照してください。</td>
<tr>
<td>9. インスタンスを作成する</td>
<td>
<p>
インスタンスの作成を開始するには、[インスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)を参照してください。
</td>  
<tr>
<td>10. インスタンスへの接続</td>
<td>これでインスタンスの準備ができました。 *「接続」*の項にある以下のトピックを参照して、インスタンスが正常に作成されたことを確認してください。
   <ul>
   <li>[Linux インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Windows インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. インスタンスをクリーンアップする</td>
<td>不要になったインスタンスを、削除できます。 </td>
</tr>
</TBODY>
</table>
</p>

## 次のステップ
インスタンスがプロビジョンされた後、オプションを検討します。
* [インスタンスの管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [{{site.data.keyword.vsi_is_short}}の許可](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [IBM Cloud VPC におけるセキュリティー](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* [IBM Cloud 仮想プライベート・クラウド](/docs/vpc-on-classic?topic=vpc-on-classic-about)の詳細
