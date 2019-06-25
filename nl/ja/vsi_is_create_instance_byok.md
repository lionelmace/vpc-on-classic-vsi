---

copyright:
  years: 2019
lastupdated: "2019-06-05"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 顧客管理の暗号化を使用した仮想サーバー・インスタンスの作成
{: #creating-instances-byok}

独自のデータ暗号鍵を含む鍵管理サービスがプロビジョンされている場合、ブロック・ストレージ・ボリュームに対して顧客管理の暗号化を使用する {{site.data.keyword.vsi_is_full}}を作成できます。 デフォルトで、インスタンスは、プロバイダー管理の暗号化を含むブート・ボリュームを使用してプロビジョンされます。 {{site.data.keyword.cloud_notm}} コンソールから、またはコマンド・ライン・インターフェース (CLI) を使用して、ブロック・ストレージ・ボリュームに対して顧客管理の暗号化を使用するインスタンスをプロビジョンできます。
{:shortdesc}

## 顧客管理の暗号化に対応する鍵管理サービス
{: #kms-for-byok}

ニーズに最も適した鍵管理サービスを使用できます。 {{site.data.keyword.keymanagementserviceshort}} および {{site.data.keyword.hscrypto}} (特定の[地域](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)で利用可能) は、一般的な鍵プロバイダー API を使用して、暗号鍵を管理するための一貫した方法を提供します。  背後では、{{site.data.keyword.cloud_notm}} データ・センターが、鍵を保護するための専用ハードウェア・セキュリティー・モジュール (HSM) を提供します。  ブロック・ストレージ・ボリュームに対する顧客管理の暗号化に対応している鍵管理サービスは、以下のとおりです。 

| 鍵管理サービス | HSM 暗号化認証 |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 *レベル 2* 準拠 |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 *レベル 4* 準拠 |
{: caption="表 1. 使用可能な鍵管理サービスのオプション" caption-side="top"}

## 前提条件
{: #byok-vsi-prereqs}

ブロック・ストレージ・ボリュームに対して顧客管理の暗号化を使用する仮想サーバー・インスタンスを作成するには、鍵管理サービスをプロビジョンし、顧客のルート鍵を追加する必要があります。 クラウド・ブロック・ストレージと鍵管理サービスの間のアクセスを許可する必要もあります。 これらの前提条件を満たしたら、ブロック・ストレージ・ボリュームに対して顧客管理の暗号化を使用するインスタンスの作成を開始できます。 

以下のサンプル・ステップは {{site.data.keyword.keymanagementserviceshort}} に固有のものですが、全体的なフローは {{site.data.keyword.hscrypto}} にも適用されます。 {{site.data.keyword.hscrypto}} を使用している場合は、[{{site.data.keyword.hscrypto}}の情報](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)を参照して、対応する手順を確認してください。
{:note}

1. [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) サービスをプロビジョンします。 
   
   新規 {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンスをプロビジョンすることで、ブロック・ストレージ・ボリュームの顧客管理の暗号化に必要な最新の更新を確実に組み込むことができます。 
   {: tip}
   
2. {{site.data.keyword.keymanagementservicelong_notm}} にルート鍵 (CRK) を
[作成](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)または
[インポート](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys)します。
3. IBM {{site.data.keyword.iamshort}} (IAM) から、**クラウド・ブロック・ストレージ
** (ソース・サービス) と **{{site.data.keyword.keymanagementserviceshort}}** (ターゲット・サービス) の間の[アクセスを許可](/docs/iam?topic=iam-serviceauth#serviceauth)します。

## 顧客管理の暗号化を使用するボリュームを持つ仮想サーバー・インスタンスのプロビジョン
{: #provision-byok-ui}

仮想サーバー・インスタンスをプロビジョンするときに、プロビジョン時に追加するブート・ボリュームとデータ・ボリュームに対して、顧客管理の暗号化を指定できます。 必要に応じて、インスタンスに関連付けられているボリュームに対して、プロバイダー管理の暗号化と顧客管理の暗号化を組み合わせて使用することができます。

1. [{{site.data.keyword.cloud_notm}} コンソール ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.cloud.ibm.com/vpc)で、**「メニュー」アイコン![「メニュー」アイコン](../icons/icon_hamburger.svg)>「VPC インフラストラクチャー」>「コンピュート」>「Virtual Server インスタンス」**にナビゲートします。 **「新規インスタンス」**をクリックし、必要なフィールドに入力します。 (インスタンスの作成について詳しくは、[仮想サーバー・インスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)を参照してください。) 
2. **「ブート・ボリューム」**セクションのデフォルトの暗号化モードは、_プロバイダー管理_の暗号化です。 顧客管理の暗号化を指定するには、ブート・ボリューム行の鉛筆アイコンをクリックします。 **「ブート・ボリュームの編集 (Edit boot volume)」**ページで、**「暗号化」**セクションのフィールドを更新します。 詳しくは、以下の表を参照してください。 変更が完了したら、**「適用」**をクリックします。
3. **「アタッチされたブロック・ストレージ・ボリューム (Attached block storage volume)」** セクションで、**「新規ブロック・ストレージ・ボリューム (New block storage volume)」**をクリックしてデータ・ボリュームを追加し、任意で顧客管理の暗号化を指定できます。 **「新規ブロック・ストレージ・ボリューム (New block storage volume)」**ページで、**「暗号化」**セクションのフィールドを更新します。 詳しくは、以下の表を参照してください。 変更が完了したら、**「アタッチ (Attach)」**をクリックします。

| フィールド | 値 |
| ----- | ----- |
| 暗号化 | _プロバイダー管理_がデフォルトの暗号化モードです。 顧客管理の暗号化を使用するには、ドロップダウン・リストから鍵管理サービスを選択します。 鍵管理サービス・インスタンスには、顧客管理の暗号化に使用する顧客ルート鍵を含める必要があります。 |
| 暗号化サービス・インスタンス | ご使用のアカウントに複数の鍵管理サービス・インスタンスがプロビジョンされている場合は、顧客管理の暗号化に使用する顧客ルート鍵が含まれているインスタンスを選択します。 |
| 鍵名 | ボリュームの暗号化に使用する鍵管理サービス・インスタンス内のデータ暗号鍵を選択します。 | 
| 鍵 ID | 選択したデータ暗号鍵に関連付けられている鍵 ID を表示します。 | 
{: caption="表 1. ボリュームの顧客管理の暗号化を指定するための値" caption-side="top"}

## CLI を使用した、インスタンスと、顧客管理の暗号化を使用するボリュームのプロビジョン
{: #provision-byok-cli}

CLI を使用して、顧客管理の暗号化を使用するボリュームを持つ仮想サーバー・インスタンスを作成するには、`ibmcloud is instance-create` コマンドを使用し、JSON を参照して顧客管理の暗号化を使用するボリュームをアタッチします。 

1. 使用する適切な鍵管理サービス・インスタンスのルート鍵の CRN を取得します。 次の例は {{site.data.keyword.keymanagementserviceshort}} に固有の例です。 
    
    1. {{site.data.keyword.keymanagementserviceshort}} CLI プラグインがまだインストールされていない場合は、以下のコマンドを実行してインストールします。 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. 以下のコマンドを実行して、ご使用のアカウントの {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンスをリストします。
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       この例の場合、以下の出力のような応答が表示されます。
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. 以下のコマンドを実行して、顧客ルート鍵が格納されている {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンスのインスタンス ID を取得します。  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       ここで、_Key Protect-17_ は使用する適切な {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンスです。
    
       この例の場合、以下の出力のような応答が表示されます。
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       ここで、インスタンス ID は CRN 内の最後の `::` に続くストリング `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7` です。 
    
    4. 以下のコマンドを実行して、使用する適切な {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンス内で使用可能な鍵と、それらに関連付けられている CRN をリストします。
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       ここで、_7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ は使用する適切な {{site.data.keyword.keymanagementserviceshort}} サービス・インスタンスのインスタンス ID です。
       
       この例の場合、以下の出力のような応答が表示されます。
       ```
       Retrieving keys...
              
       SUCCESS
               
       Key ID                                 Key Name               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) コマンドを使用して、必要な JSON ファイル (ブート・ボリュームと任意で含める 2 次データ・ボリュームに対して顧客管理の暗号化を指定するもの) をアタッチします。 `encryption_key` パラメーターには、鍵の保護サービスのルート鍵に対応する有効な CRN が含まれている必要があります。 以下に示す、ブート・ボリュームの JSON および 2 次ボリュームの JSON の [JSON ファイルの例](#vsi-vol-attachment-json)を参照してください。 (インスタンスの作成について詳しくは、[仮想サーバー・インスタンスの作成 (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli) を参照してください。)

## JSON 形式でのボリューム・アタッチメントの作成
{: #vsi-vol-attachment-json}

VSI のプロビジョン中にブート・ボリュームまたはデータ・ボリュームを作成する場合、ボリューム・パラメーターを定義する JSON ファイルを指定する必要があります。 以下の JSON ファイルの例を参照してください。

### ブート・ボリュームの JSON ファイルの例
{: #boot-volume-byok-json}

以下の例では、汎用ブート・ボリュームを定義し、顧客管理の暗号化の `encryption key` パラメーターを指定しています。

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      },
      "encryption_key":{  
         "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### 2 次ボリュームの JSON ファイルの例
{: #secondary-volume-byok-json}

以下の例では、汎用 2 次 (データ) ボリュームを定義し、顧客管理の暗号化の `encryption key` パラメーターを指定しています。

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         },
         "encryption_key":{  
            "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}
