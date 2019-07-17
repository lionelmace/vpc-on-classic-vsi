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

# 고객 관리 암호화로 가상 서버 인스턴스 작성
{: #creating-instances-byok}

데이터 암호화 키를 포함하는 키 관리 서비스가 프로비저닝된 경우 블록 스토리지 볼륨에 대해 고객 관리 암호화를 사용하는 {{site.data.keyword.vsi_is_full}}를 작성할 수 있습니다. 기본적으로 인스턴스는 제공자 관리 암호화가 포함된 부트 볼륨으로 프로비저닝됩니다. {{site.data.keyword.cloud_notm}} 콘솔에서 또는 명령행 인터페이스(CLI)를 사용하여 블록 스토리지 볼륨에 대해 고객 관리 암호화를 사용하는 인스턴스를 프로비저닝할 수 있습니다.
{:shortdesc}

## 고객 관리 암호화에 대해 지원되는 키 관리 서비스
{: #kms-for-byok}

요구사항에 최적으로 작동하는 키 관리 서비스를 사용할 수 있습니다. {{site.data.keyword.keymanagementserviceshort}} 및 {{site.data.keyword.hscrypto}}(특정 [지역](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)에서 사용 가능함)에서는 공통 키 제공자 API를 사용하여 암호화 키 관리를 위한 일관성 있는 접근 방법을 제공합니다.  한편 {{site.data.keyword.cloud_notm}} 데이터 센터는 전용 하드웨어 보안 모듈 (HSM)을 제공하여 키를 보호합니다.  다음의 키 관리 서비스가 블록 스토리지 볼륨의 고객 관리 암호화에서 지원됩니다. 

| 키 관리 서비스 | HSM 암호화 인증 |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 *레벨 2* 준수 |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 *레벨 4* 준수 |
{: caption="표 1. 사용 가능한 키 관리 서비스 옵션" caption-side="top"}

## 전제조건
{: #byok-vsi-prereqs}

블록 스토리지 볼륨에 대해 고객 관리 암호화를 사용하는 가상 서버 인스턴스를 작성하려면 키 볼륨 서비스를 프로비저닝하고 고객 루트 키를 추가해야 합니다. 또한 Cloud Block Storage 및 키 관리 서비스 간의 액세스 권한도 부여해야 합니다. 이러한 선행조건이 충족되면 블록 스토리지 볼륨에 대해 고객 관리 암호화를 사용하는 인스턴스의 작성을 시작할 수 있습니다. 

다음의 예제 단계는 {{site.data.keyword.keymanagementserviceshort}}에만 해당되지만, 일반 플로우 역시 {{site.data.keyword.hscrypto}}에 적용됩니다. {{site.data.keyword.hscrypto}}를 사용 중인 경우에는 [{{site.data.keyword.hscrypto}} 정보](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)에서 관련 지시사항을 참조하십시오.
{:note}

1. [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) 서비스를 프로비저닝하십시오. 
   
   새 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스를 프로비저닝하면 블록 스토리지 볼륨의 고객 관리 암호화에 필요한 최신 업데이트가 이에 포함됩니다. 
   {: tip}
   
2. {{site.data.keyword.keymanagementservicelong_notm}}에서 루트 키(CRK)를 [작성](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)하거나 [가져오십시오](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys).
3. IBM {{site.data.keyword.iamshort}}(IAM)에서 **Cloud Block Storage**(소스 서비스) 및 **{{site.data.keyword.keymanagementserviceshort}}**(대상 서비스) 간의 [액세스 권한을 부여](/docs/iam?topic=iam-serviceauth#serviceauth)하십시오.

## 고객 관리 암호화를 사용하는 볼륨의 가상 서버 인스턴스 프로비저닝
{: #provision-byok-ui}

가상 서버 인스턴스를 프로비저닝하는 경우 프로비저닝 시에 추가할 데이터 볼륨과 부트 볼륨에 대해 고객 관리 암호화를 지정할 수 있습니다. 원하면 인스턴스와 연관된 볼륨에 대해 제공자 관리 암호화와 고객 관리 암호화를 조합하여 사용할 수 있습니다.

1. [{{site.data.keyword.cloud_notm}} 콘솔 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.cloud.ibm.com/vpc)에서 **메뉴 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg) > VPC 인프라 > 컴퓨팅 > 가상 서버 인스턴스**로 이동하십시오. **새 인스턴스** 클릭하고 필수 필드를 채우십시오. (인스턴스 작성에 대한 자세한 정보는 [가상 서버 인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)을 참조하십시오.) 
2. **부트 볼륨** 섹션에서 암호화의 기본 모드는 _제공자 관리_ 암호화입니다. 고객 관리 암호화를 지정하려면 부트 볼륨 행에서 연필 아이콘을 클릭하십시오. **부트 볼륨 편집** 페이지에서 **암호화** 섹션의 필드를 업데이트하십시오. 자세한 정보는 아래의 표를 참조하십시오. 변경이 완료되면 **적용**을 클릭하십시오.
3. **연결된 블록 스토리지 볼륨** 섹션에서 **새 블록 스토리지 볼륨**을 클릭하여 데이터 볼륨을 추가하고 고객 관리 암호화를 지정할 수 있습니다(선택하는 경우). **새 블록 스토리지 볼륨** 페이지에서 **암호화** 섹션의 필드를 업데이트하십시오. 자세한 정보는 아래의 표를 참조하십시오. 변경이 완료되면 **연결**을 클릭하십시오.

| 필드 |값 |
| ----- | ----- |
| 암호화 | _제공자 관리_가 기본 암호화 모드입니다. 고객 관리 암호화를 사용하려면 드롭 다운 목록에서 키 관리 서비스를 선택하십시오. 키 관리 서비스 인스턴스에는 고객 관리 암호화에 사용할 고객 루트 키가 포함되어 있어야 합니다. |
| 암호화 서비스 인스턴스 |계정에서 다수의 키 관리 서비스 인스턴스가 프로비저닝되어 있으면 고객 관리 암호화에 사용할 고객 루트 키가 포함된 인스턴스를 선택하십시오. |
| 키 이름 | 볼륨 암호화에 사용할 키 관리 서비스 인스턴스 내에서 데이터 암호화 키를 선택하십시오. | 
| 키 ID | 선택한 데이터 암호화 키와 연관된 키 ID를 표시합니다. | 
{: caption="표 1. 볼륨의 고객 관리 암호화를 지정하기 위한 값" caption-side="top"}

## CLI를 사용하여 고객 관리 암호화의 볼륨 및 인스턴스 프로비저닝
{: #provision-byok-cli}

CLI를 사용하여 고객 관리 암호화를 사용하는 볼륨의 가상 서버 인스턴스를 작성하려면 `ibmcloud is instance-create` 명령을 사용하고 JSON을 참조하여 고객 관리 암호화를 사용하는 볼륨을 연결할 수 있습니다. 

1. 원하는 키 관리 서비스 인스턴스에서 루트 키의 CRN을 가져오십시오. 다음 예제는 {{site.data.keyword.keymanagementserviceshort}}에만 해당됩니다. 
    
    1. {{site.data.keyword.keymanagementserviceshort}} CLI 플러그인을 아직 설치하지 않았으면 다음 명령을 실행하여 이를 설치하십시오. 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. 다음 명령을 실행하여 계정에 대한 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스를 나열하십시오.
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. 다음 명령을 실행하여 고객 루트 키가 저장된 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스의 인스턴스 ID를 검색하십시오.  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       여기서 _Key Protect-17_은 원하는 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스입니다.
    
       이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       여기서 인스턴스 ID는 CRN에서 마지막 `::` 이후의 문자열(`7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`)입니다. 
    
    4. 다음 명령을 실행하여 원하는 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스 내의 사용 가능한 키 및 이와 연관된 CRN을 나열하십시오.
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       여기서 _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_은 원하는 {{site.data.keyword.keymanagementserviceshort}} 서비스 인스턴스의 인스턴스 ID입니다.
       
       이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
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
       
2. [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) 명령을 사용하고 포함하고자 하는 2차 데이터 볼륨과 부트 볼륨에 대해 고객 관리 암호화를 지정하는 필수 JSON 파일을 연결하십시오. `encryption_key` 매개변수는 키 보호 서비스에서 루트 키의 올바른 CRN을 포함해야 합니다. 부트 볼륨 JSON과 2차 볼륨 JSON의 다음 [JSON 파일 예제](#vsi-vol-attachment-json)를 참조하십시오. (인스턴스 작성에 대한 자세한 정보는 [가상 서버 인스턴스 작성(CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)을 참조하십시오.)

## JSON 형식의 볼륨 연결 작성
{: #vsi-vol-attachment-json}

VSI 프로비저닝 중에 부트 볼륨이나 데이터 볼륨을 작성하는 경우 볼륨 매개변수를 정의하기 위한 JSON 파일을 지정해야 합니다. 다음의 JSON 파일 예제를 참조하십시오.

### 예제 부트 볼륨 JSON 파일
{: #boot-volume-byok-json}

다음 예제는 범용 부트 볼륨을 정의하고 고객 관리 암호화를 위한 `encryption key` 매개변수를 지정합니다.

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

### 예제 2차 볼륨 JSON 파일
{: #secondary-volume-byok-json}

다음 예제는 범용 2차(데이터) 볼륨을 정의하고 고객 관리 암호화를 위한 `encryption key` 매개변수를 지정합니다.

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
