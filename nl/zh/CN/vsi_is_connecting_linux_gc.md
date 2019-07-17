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

# 连接到 Linux 实例
{: #connecting-to-your-linux-instance}

创建 {{site.data.keyword.vsi_is_full}} Linux 实例后，可以通过完成以下步骤来连接到该实例。
{:shortdesc}

## 查找浮动 IP 地址
{: #locating-floating-ip-address}

如果需要查找要连接到的实例的浮动 IP 地址，请完成以下步骤。如果您已经知道浮动 IP 地址，那么可以跳至[连接](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected)。 

1. 您需要先确定浮动 IP 标识，然后才能查找浮动 IP 地址。运行以下命令来确定浮动 IP 标识：

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应（通用 x 和 123 值仅用于示例目的）：

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

2. 既然您已知道了浮动 IP 标识，那么可以通过运行以下命令来查找浮动 IP 地址。

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应（通用 x 和 123 值仅用于示例目的）：

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

（可选）可以通过 {{site.data.keyword.cloud_notm}} 控制台来查找与要连接到的实例关联的浮动 IP 地址。
{:tip}

## 连接
{: #getting-connected}

下面返回的值仅用于示例目的。

1. 要连接到实例，请使用专用密钥并运行以下命令：

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   您会收到类似于以下示例的响应。系统提示您继续连接时，请输入 `yes`。
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   您现在正在访问服务器。

2. 准备好结束连接时，请运行以下命令：

   ```
   # exit
   ```
   {:codeblock}

## 后续步骤
{: #next-managing-instances}

连接到实例后，可以[使用 {{site.data.keyword.cloud_notm}} 控制台管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)或[使用 CLI 管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)。
