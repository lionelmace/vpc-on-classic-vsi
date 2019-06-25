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

# 使用客戶管理的加密建立虛擬伺服器實例
{: #creating-instances-byok}

當您有一個佈建時包含您專屬資料加密金鑰的金鑰管理服務時，您可以建立 {{site.data.keyword.vsi_is_full}}，針對區塊儲存空間磁區使用客戶管理的加密。依預設，佈建實例時會使用包括提供者管理之加密的開機磁區。您可以從 {{site.data.keyword.cloud_notm}} 主控台或使用指令行介面 (CLI)，佈建針對區塊儲存空間磁區，使用客戶管理加密的實例。
{:shortdesc}

## 客戶管理的加密所支援的金鑰管理服務
{: #kms-for-byok}

您可以使用最適合您需求的金鑰管理服務。{{site.data.keyword.keymanagementserviceshort}} 和 {{site.data.keyword.hscrypto}}（在某些[地區](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)提供）使用一般金鑰提供者 API 來提供一致的加密金鑰管理方法。在幕後，{{site.data.keyword.cloud_notm}} 資料中心會提供專用的 Hardware Security Module (HSM) 來保護您的金鑰。對於區塊儲存空間磁區的客戶管理加密，支援下列金鑰管理服務： 

|金鑰管理服務|HSM 加密憑證|
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) |FIPS 140-2*Level 2* 遵循|
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) |FIPS 140-2*Level 4* 遵循|
{: caption="表 1. 可用的金鑰管理服務選項" caption-side="top"}

## 必要條件
{: #byok-vsi-prereqs}

若要建立針對區塊儲存空間磁區使用客戶管理加密的虛擬伺服器實例，您必須佈建金鑰管理服務並新增客戶根金鑰。您還必須在 Cloud Block Storage 與金鑰管理服務之間進行存取權的授權。當您完成這些必要條件時，可以開始建立針對區塊儲存空間磁區，使用客戶管理加密的實例。 

下列步驟範例專用於 {{site.data.keyword.keymanagementserviceshort}}，但一般流程也適用於 {{site.data.keyword.hscrypto}}。如果您使用 {{site.data.keyword.hscrypto}}，請參閱 [{{site.data.keyword.hscrypto}} 資訊](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)以取得對應的指示。
{:note}

1. 佈建 [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) 服務。 
   
   佈建新的 {{site.data.keyword.keymanagementserviceshort}} 服務實例可確保它包含區塊儲存空間磁區之客戶管理加密所需的最新更新。
   {: tip}
   
2. 在 {{site.data.keyword.keymanagementservicelong_notm}} 中[建立](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)或[匯入](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys)根金鑰 (CRK)。
3. 從 IBM {{site.data.keyword.iamshort}} (IAM)，對 **Cloud
Block Storage**（來源服務）與 **{{site.data.keyword.keymanagementserviceshort}}**（目標服務）之間的[存取權進行授權](/docs/iam?topic=iam-serviceauth#serviceauth)。

## 佈建具有使用客戶管理加密之磁區的虛擬伺服器實例
{: #provision-byok-ui}

當您佈建虛擬伺服器實例時，可以針對您的開機磁區以及在佈建時想要新增的任何資料磁區，指定客戶管理的加密。如果想要的話，您可以針對與實例相關聯的磁區，使用提供者管理加密及客戶管理加密的組合。

1. 在 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.cloud.ibm.com/vpc) 中，導覽至**功能表圖示 ![功能表圖示](../icons/icon_hamburger.svg) > VPC 基礎架構 > 運算 > 虛擬伺服器實例**。按一下**新建實例**，然後完成必要欄位。（如需建立實例的相關資訊，請參閱[建立虛擬伺服器實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)。） 
2. 在**開機磁區**區段中，預設加密模式是_提供者管理_ 的加密。若要指定客戶管理的加密，請按一下開機磁區列中的鉛筆圖示。在**編輯開機磁區**頁面上，更新**加密**區段中的欄位。請參閱下表，以取得相關資訊。當您完成變更時，請按一下**套用**。
3. 在**連接的區塊儲存空間磁區**區段中，您可以按一下**新建區塊儲存空間磁區**來新增資料磁區，並指定客戶管理的加密（如果您選擇的話）。在**新建區塊儲存空間磁區**頁面上，更新**加密**區段中的欄位。請參閱下表，以取得相關資訊。當您完成變更時，請按一下**連接**。

|欄位|值|
| ----- | ----- |
| 加密 |_提供者管理_ 是預設加密模式。如果要使用客戶管理的加密，請從下拉清單中選取金鑰管理服務。金鑰管理服務實例應該包含要用於客戶管理加密的客戶根金鑰。|
|加密服務實例|如果您的帳戶中佈建了多個金鑰管理服務實例，請選取包含您要用於客戶管理加密之客戶根金鑰的實例。|
|金鑰名稱|選取金鑰管理服務實例中您要用來加密磁區的資料加密金鑰。| 
|金鑰 ID|顯示與所選資料加密金鑰相關聯的金鑰 ID。| 
{: caption="表 1. 指定磁區之客戶管理加密的值" caption-side="top"}

## 使用 CLI 佈建實例及使用客戶管理加密的磁區
{: #provision-byok-cli}

若要使用 CLI 來建立具有使用客戶管理加密之磁區的虛擬伺服器實例，您可以使用 `ibmcloud is instance-create` 指令，並參照 JSON 來連接使用客戶管理加密的磁區。 

1. 取得您想要之金鑰管理服務實例中的根金鑰 CRN。下列範例專用於 {{site.data.keyword.keymanagementserviceshort}}。 
    
    1. 如果您尚未安裝 {{site.data.keyword.keymanagementserviceshort}} CLI 外掛程式，請執行下列指令來安裝它：
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. 執行下列指令，列出您帳戶的 {{site.data.keyword.keymanagementserviceshort}} 服務實例：
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       針對此範例，您會看到類似下列輸出的回應：
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. 執行下列指令，擷取儲存客戶根金鑰之 {{site.data.keyword.keymanagementserviceshort}} 服務實例的實例 ID。  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       其中 _Key Protect-17_ 是您想要的 {{site.data.keyword.keymanagementserviceshort}} 服務實例。
    
       針對此範例，您會看到類似下列輸出的回應：
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       其中實例 ID 是 CRN `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7` 中，在最後 `::` 之後的字串。 
    
    4. 執行下列指令，列出您想要的 {{site.data.keyword.keymanagementserviceshort}} 服務實例內，可用的金鑰及其相關聯的 CRN：
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       其中 _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ 是您想要之 {{site.data.keyword.keymanagementserviceshort}} 服務實例的實例 ID。
       
       針對此範例，您會看到類似下列輸出的回應：
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
       
2. 使用 [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) 指令，並附加必要的 JSON 檔，為開機磁區以及您要包含的任何次要資料磁區，指定客戶管理的加密。`encryption_key` 參數必須為 Key Protect 服務中的根金鑰包含有效的 CRN。請參閱開機磁區 JSON 及次要磁區 JSON 的下列 [JSON 檔案範例](#vsi-vol-attachment-json)。（如需建立實例的相關資訊，請參閱[建立虛擬伺服器實例 (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)。）

## 以 JSON 格式建立磁區附件
{: #vsi-vol-attachment-json}

在 VSI 佈建期間建立開機磁區或資料磁區時，您必須指定用於定義磁區參數的 JSON 檔案。請參閱下列 JSON 檔案範例。

### 開機磁區 JSON 檔案範例
{: #boot-volume-byok-json}

下列範例會定義通用的開機磁區，並指定客戶管理之加密的`加密金鑰`參數。

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

### 次要磁區 JSON 檔案範例
{: #secondary-volume-byok-json}

下列範例會定義通用的次要（資料）磁區，並指定客戶管理之加密的`加密金鑰`參數。

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
