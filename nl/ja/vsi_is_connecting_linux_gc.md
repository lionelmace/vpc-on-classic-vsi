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

# Linux インスタンスへの接続
{: #connecting-to-your-linux-instance}

{{site.data.keyword.vsi_is_full}} Linux インスタンスを作成した後、以下のステップを実行してそのインスタンスに接続できます。
{:shortdesc}

## 浮動 IP アドレスの検索
{: #locating-floating-ip-address}

接続先のインスタンスの浮動 IP アドレスを知る必要がある場合は、以下のステップを実行します。 浮動 IP アドレスが既に分かっている場合は、[接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected)にスキップできます。 

1. 浮動 IP アドレスを見つけるには、その前に浮動 IP の ID を特定する必要があります。 浮動 IP の ID を特定するには、以下のコマンドを実行します。

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   この例では、以下の出力のような応答が表示されます (汎用値の x および 123 は、例示のためにのみ使用しています)。

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

2. これで、浮動 IP の ID を特定できました。次に、以下のコマンドを実行して、浮動 IP アドレスを見つけます。

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   この例では、以下の出力のような応答が表示されます (汎用値の x および 123 は、例示のためにのみ使用しています)。

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

任意で、{{site.data.keyword.cloud_notm}} コンソールでも、接続先インスタンスに関連付けられた浮動 IP アドレスを探すことができます。
{:tip}

## 接続
{: #getting-connected}

以下の戻り値は、例としてのみ表示しています。

1. インスタンスに接続するには、秘密鍵を使用して以下のコマンドを実行します。

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   以下の例のような応答を受け取ります。 接続の継続を求めるプロンプトが出されたら、`yes` と入力します。
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   これで、サーバーにアクセスできました。

2. 接続を終了する準備ができたら、以下のコマンドを実行します。

   ```
   # exit
   ```
   {:codeblock}

## 次のステップ
{: #next-managing-instances}

インスタンスに接続した後は、[{{site.data.keyword.cloud_notm}} コンソールを使用してインスタンスを管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)したり、[CLI を使用してインスタンスを管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)したりできます。
