---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# 仮想サーバー・インスタンスの作成
{: #creating-virtual-servers}
[comment]: # (リンクされているヘルプ・トピック)

{{site.data.keyword.vsi_is_full}} は、{{site.data.keyword.cloud_notm}} コンソールの*「Virtual Server インスタンス」* ページから作成できます。
{:shortdesc}

始める前に、[IBM Cloud VPC を作成](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)しておく必要があります。
{:important}

インスタンスを作成するには、以下のインスタンスの詳細を選択します。
1. [{{site.data.keyword.cloud_notm}} コンソール ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.cloud.ibm.com/vpc)で、**「メニュー」アイコン![「メニュー」アイコン](../icons/icon_hamburger.svg)>「VPC インフラストラクチャー」>「コンピュート」>「Virtual Server インスタンス」**にナビゲートします。
2. **「新規インスタンス (New instance)」**をクリックして、以下の情報を入力します。

    <table>
    <CAPTION>表 1. インスタンスのプロビジョニングの選択</CAPTION>
    <THEAD>
    <TR>
    <th>フィールド</th>
    <th>値</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>名前 </td>
    <td>仮想サーバー・インスタンスには、名前が必要です。</td>
    </tr>
    <tr>
    <td>仮想プライベート・クラウド</td>
    <td>インスタンスを作成する IBM Cloud VPC を指定します。</td>
    </tr>
    <tr>
    <td>場所</td>
    <td>場所は、地域 (特定の地理的領域) およびゾーン (地域内のフォールト・トレラント・データ・センター) で構成されます。 仮想サーバー・インスタンスを作成する場所を選択します。</td>
    </tr>
    <tr>
    <td>プロファイル</td>
    <td><p>
    一般的なプロファイル、または使用可能なすべての vCPU と RAM の組み合わせから選択します。 以下のファミリーがサポートされています。
    <ul>
    <li>平衡型</li>
    <li>コンピュート</li>
    <li>メモリー</li>
    </ul>
    </p>
    <p>サーバー上の各物理的コアは、ハイパースレッディング処理されており、2 つの仮想 CPU (vCPU) として表されます。 仮想サーバー・オファリングは、1 つの vCPU につき 2.0 GHz 以上を提供し、1 台の仮想サーバーで最大 48 個の vCPU が利用可能です。</p>

    <p>メモリーの場合、インスタンスに最大 256 GB の完全専用 RAM を設定できます。</p>
    <p><note>注: 最大値はファミリーによって異なります。</note></p>
    <p>詳しくは、[プロファイル](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)を参照してください。</p>
    </td>
    </tr>
    <tr>
    <td>イメージ</td>
    <td><p>すべてのイメージは cloud-init を使用します。これにより、ポスト・プロビジョニング・スクリプト用にインスタンスに関連付けられたユーザー・メタデータを入力できます。</p>
    <p>詳しくは、[イメージ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)を参照してください。</p>
    </td>
    </tr>
    <td>SSH 鍵</td>
    <td>
    <p>インスタンスを作成する前に、既存の SSH 鍵を選択するか、使用する新規 SSH 鍵をアップロードする必要があります。 SSH 鍵は、実行中になったインスタンスにセキュアに接続するために使用されます。 インスタンスに SSH 鍵を追加できるのは、インスタンスの初回作成時のみです。</p>
    <p>注: 英数字の組み合わせは 100 文字に制限されています。</p>
    <p>詳しくは、[SSH 鍵](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)を参照してください。</p></td>
    </tr>
    <tr>
    <td>ユーザー・データ</td>
    <td>
    <p>一般的な構成タスクを自動的に実行するユーザー・データや、スクリプトを実行するユーザー・データを追加することができます。 <p>詳しくは、[ユーザー・データ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)を参照してください。</p>
    </td>
    </tr>
    <tr>
    <td>ブート・ボリューム</td>
    <td><p>すべてのプロファイルのデフォルトのブート・ボリューム・サイズは 100 GB です。 デフォルトでは、ブート・ボリュームにはプロバイダーが管理する暗号化が含まれます。 顧客管理の暗号化を使用する場合は、ブート・ボリュームの詳細を編集できます。 詳しくは、[ストレージ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage)を参照してください。</p>
    </td>
    </tr>
    <tr>
    <td>アタッチされたブロック・ストレージ・ボリューム</td>
    <td><p>インスタンスのプロビジョン時に含める 2 次データ・ボリュームを 1 つ以上追加できます。 ボリュームを追加するには、**「新規ブロック・ストレージ・ボリューム (New block storage volume)」**をクリックします。 詳しくは、[ブロック・ストレージ・ボリュームの作成](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)を参照してください。</p>
    </td>
    </tr>
    <tr>
    <td>ネットワーク・インターフェース</td>
    <td>IBM Cloud VPC に接続するためのネットワーク・オプションを割り当てます。 各インスタンスに最大 5 つのネットワーク・インターフェース・カードを作成して割り当てることができます。 詳しくは、[複数の IP アドレス](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options)を参照してください。</td>
    </tr>
    </TBODY>
    </table>

    *「新規仮想サーバー・インスタンス (New virtual server instance)」*ページの右側に*「コスト・サマリー (Cost summary)」*が表示されます。

3. プロビジョンの準備ができたら、**「Virtual Server インスタンスを作成します」**をクリックします。 一連の E メール (仮想サーバー・インスタンス・オーダーの確認応答、オーダーの承認と処理、およびインスタンスが作成されたことを示すメッセージ) が管理者に送信されます。

CLI を使用してインスタンスを作成しますか? 詳細については、[CLI を使用したインスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)を参照してください。
{: tip}

## 浮動 IP アドレスの予約
{: #reserving-a-floating-ip-address}

浮動 IP アドレスを予約してインスタンスに関連付けて、インターネット・ロケーションから接続できるようにすることができます。

浮動 IP アドレスを関連付けるには、インスタンスが実行されている必要があります。 インスタンスが稼働中になるまで数分かかることがあります。
{: note} 

浮動 IP アドレスを予約して関連付けるには、以下の手順を実行します。
1. **「Virtual Server インスタンス」**ページで、インスタンスをクリックして詳細を表示します。
2. **「ネットワーク・インターフェース」**セクションで、**「予約 + (Reserve +)」**をクリックして、浮動 IP アドレスをインスタンスに関連付けます。

## 次のステップ
{: #next-connecting-to-instance}

これで、インスタンスに接続できます。 詳しくは、[Linux インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)または [Windows インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)を参照してください。
