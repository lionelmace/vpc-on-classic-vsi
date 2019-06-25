---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 連接至 Linux 實例
{: #connecting-to-your-linux-instance}

建立 {{site.data.keyword.vsi_is_full}} Linux 實例之後，您可以完成下列步驟來連接它。
{:shortdesc}

## 尋找浮動 IP 位址
{: #locating-floating-ip-address}

如果您需要尋找要連接之實例的浮動 IP 位址，請完成下列步驟。如果您已經知道浮動 IP 位址，您可以跳到[開始使用](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected)。 

1. 您需要先識別浮動 IP ID，才能找到您的浮動 IP 位址。請執行下列指令以識別浮動 IP ID：

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應（因為範例的緣故，只使用一般的 x 和 123 值）：

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. 既然您已有浮動 IP ID，便可以執行下列指令來尋找浮動 IP 位址。

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應（因為範例的緣故，只使用一般的 x 和 123 值）：

   ```
   ID               12345x67-8901-234x-5678-9xx01xx23x4x   
   Address          123.45.678.90   
   Name             my-instance   
   Target           primary(1xx2x34x-.)   
   Target Type      intf   
   Target IP        12.345.6.78   
   Created          1 week ago   
   Status           available   
   Zone             us-south-1   
   Resource Group   -   
   Tags             -   
   ```
   {:screen}

您可以選擇性地透過 {{site.data.keyword.cloud_notm}} 主控台尋找與您要連接之實例相關聯的浮動 IP 位址。
{:tip}

## 取得連線
{: #getting-connected}

底下的傳回值僅供範例之用。

1. 若要連接至實例，請使用您的私密金鑰，並執行下列指令：

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   您會收到類似下列範例的回應。提示繼續連接時，請鍵入 `yes`。
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   您現在正在存取伺服器。

2. 當您準備好結束連線時，請執行下列指令：

   ```
   # exit
   ```
   {:codeblock}

## 後續步驟
{: #next-managing-instances}

在連接至實例之後，您可以[使用 {{site.data.keyword.cloud_notm}} 主控台管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)或[使用 CLI 管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)。
