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

# 使用客户管理的加密创建虚拟服务器实例
{: #creating-instances-byok}

供应了包含您自己的数据加密密钥的密钥管理服务时，可以创建对块存储卷使用客户管理的加密的 {{site.data.keyword.vsi_is_full}}。缺省情况下，会为实例供应包含提供者管理的加密的引导卷。可以通过 {{site.data.keyword.cloud_notm}} 控制台或使用命令行界面 (CLI) 来供应对块存储卷使用客户管理的加密的实例。
{:shortdesc}

## 支持密钥管理服务用于客户管理的加密
{: #kms-for-byok}

您可以使用最适合自己需要的密钥管理服务。{{site.data.keyword.keymanagementserviceshort}} 和 {{site.data.keyword.hscrypto}}（在特定[区域](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)中可用）使用通用密钥提供者 API 来提供一致的加密密钥管理方法。{{site.data.keyword.cloud_notm}} 数据中心在幕后提供专用硬件安全模块 (HSM) 来保护密钥。以下密钥管理服务支持对块存储卷使用客户管理的加密： 

|密钥管理服务|HSM 加密证书|
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) |符合 FIPS 140-2 *二级*认证|
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) |符合 FIPS 140-2 *四级*认证|
{: caption="表 1. 可用的密钥管理服务选项" caption-side="top"}

## 先决条件
{: #byok-vsi-prereqs}

要创建对块存储卷使用客户管理的加密的虚拟服务器实例，必须已供应密钥管理服务并添加了客户根密钥。您还必须授予 Cloud Block Storage 与密钥管理服务之间的访问权。完成这些先决条件后，可以开始创建对块存储卷使用客户管理的加密的实例。 

以下示例步骤特定于 {{site.data.keyword.keymanagementserviceshort}}，但常规流程也适用于 {{site.data.keyword.hscrypto}}。如果使用的是 {{site.data.keyword.hscrypto}}，请参阅 [{{site.data.keyword.hscrypto}} 信息](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)以获取相应的指示信息。
{:note}

1. 供应 [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) 服务。 
   
   供应新的 {{site.data.keyword.keymanagementserviceshort}} 服务实例可确保该实例包含对块存储卷进行客户管理的加密所需的最新更新。
   {: tip}
   
2. 在 {{site.data.keyword.keymanagementservicelong_notm}} 中[创建](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)或[导入](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys)根密钥 (CRK)。
3. 从 IBM {{site.data.keyword.iamshort}} (IAM)，在 **Cloud Block Storage**（源服务）与 **{{site.data.keyword.keymanagementserviceshort}}**（目标服务）之间[授予访问权](/docs/iam?topic=iam-serviceauth#serviceauth)。

## 通过使用客户管理的加密的卷供应虚拟服务器实例
{: #provision-byok-ui}

供应虚拟服务器实例时，可以针对引导卷以及在供应时要添加的任何数据卷，指定客户管理的加密。如果需要，可以对与实例关联的卷，组合使用提供者管理的加密和客户管理的加密。

1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.cloud.ibm.com/vpc) 中，导航至**“菜单”图标 ![“菜单”图标](../icons/icon_hamburger.svg) > VPC 基础架构 > 计算 > 虚拟服务器实例**。单击**新建实例**，然后填写必填字段。（有关创建实例的更多信息，请参阅[创建虚拟服务器实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)。） 
2. 在**引导卷**部分中，缺省加密方式为_提供者管理_的加密。要指定客户管理的加密，请单击引导卷行中的“画笔”图标。在**编辑引导卷**页面上，更新**加密**部分中的字段。有关更多信息，请参阅下表。更改完成后，单击**应用**。
3. 在**连接的块存储卷**部分中，可以单击**新建块存储卷**以添加数据卷，然后指定客户管理的加密（如果选择使用此项）。在**新建块存储卷**页面上，更新**加密**部分中的字段。有关更多信息，请参阅下表。更改完成后，单击**连接**。

|字段|值|
| ----- | ----- |
|加密|_提供者管理_的加密是缺省加密方式。要使用客户管理的加密，请从下拉列表中选择密钥管理服务。密钥管理服务实例应该包含要用于客户管理的加密的客户根密钥。|
|加密服务实例|如果帐户中供应了多个密钥管理服务实例，请选择包含要用于客户管理的加密的客户根密钥的实例。|
|密钥名称|选择密钥管理服务实例中要用于加密卷的数据加密密钥。| 
|密钥标识|显示与所选数据加密密钥关联的密钥标识。| 
{: caption="表 1. 用于指定对卷进行客户管理的加密的值" caption-side="top"}

## 使用 CLI 通过客户管理的加密供应实例和卷
{: #provision-byok-cli}

要使用 CLI 通过使用客户管理的加密的卷创建虚拟服务器实例，可以使用 `ibmcloud is instance-create` 命令并引用 JSON 来连接使用客户管理的加密的卷。 

1. 获取所需的密钥管理服务实例中根密钥的 CRN。以下示例特定于 {{site.data.keyword.keymanagementserviceshort}}。 
    
    1. 如果尚未安装 {{site.data.keyword.keymanagementserviceshort}} CLI 插件，请通过运行以下命令进行安装：
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. 通过运行以下命令，列出帐户的 {{site.data.keyword.keymanagementserviceshort}} 服务实例：
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       对于此示例，您会看到类似于以下输出的响应：
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. 通过运行以下命令，检索存储客户根密钥的 {{site.data.keyword.keymanagementserviceshort}} 服务实例的实例标识。  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       其中，_Key Protect-17_ 是所需的 {{site.data.keyword.keymanagementserviceshort}} 服务实例。
    
       对于此示例，您会看到类似于以下输出的响应：
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       其中，实例标识是 CRN 中最后的 `::` 之后的字符串：`7mxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`。 
    
    4. 通过运行以下命令，列出所需 {{site.data.keyword.keymanagementserviceshort}} 服务实例中的可用密钥及其关联的 CRN：
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       其中，_7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ 是所需 {{site.data.keyword.keymanagementserviceshort}} 服务实例的实例标识。
       
       对于此示例，您会看到类似于以下输出的响应：
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
       
2. 使用 [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) 命令并附加必需的 JSON 文件，这些文件为引导卷以及要包含的任何辅助数据卷指定客户管理的加密。`encryption_key` 参数必须包含 Key Protect 服务中根密钥的有效 CRN。请参阅引导卷 JSON 和辅助卷 JSON 的以下 [JSON 文件示例](#vsi-vol-attachment-json)。（有关创建实例的更多信息，请参阅[创建虚拟服务器实例 (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli)。）

## 创建 JSON 格式的卷连接
{: #vsi-vol-attachment-json}

在 VSI 供应期间创建引导卷或数据卷时，必须指定 JSON 文件以定义卷参数。请参阅以下 JSON 文件示例。

### 示例引导卷 JSON 文件
{: #boot-volume-byok-json}

以下示例定义了通用引导卷，并指定了用于客户管理的加密的 `encryption key` 参数。

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

### 示例辅助卷 JSON 文件
{: #secondary-volume-byok-json}

以下示例定义了通用辅助（数据）卷，并指定了用于客户管理的加密的 `encryption key` 参数。

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
