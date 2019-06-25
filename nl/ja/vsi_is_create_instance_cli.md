---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: virtual server instances, command line interface, creating virtual server instances

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

# 仮想サーバー・インスタンスの作成 (CLI)
{: #creating-virtual-servers-cli}

コマンド・ライン・インターフェース (CLI) を使用して {{site.data.keyword.vsi_is_full}} インスタンスを作成することもできます。
{:shortdesc}

## 始める前に
{: #prereq-creating-virtual-servers-cli}

1. 以下の CLI プラグインのダウンロード、インストール、初期化を行っていることを確認します。
    * {{site.data.keyword.cloud_notm}} CLI
    * vpc-infrastructure プラグイン

   詳しくは、[IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference) を参照してください。
   
   vpc-infrastructure プラグインを初めてインストールする場合は、ターゲット世代を gen 1 に設定して、`ibmcloud is target -gen 1` とする必要があります。
   {:important}
   
   
2. 既に [{{site.data.keyword.vpc_short}} を作成している](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)ことを確認します。

## CLI を使用したインスタンス作成のための情報の収集
{: #gathering-information-to-create-an-instance-using-the-cli}

インスタンスを作成する準備ができましたか? `ibmcloud is instances` コマンドを実行するには、その前に、使用するプロファイルやイメージなど、インスタンスに関する詳細情報を知っておく必要があります。

まずこの情報を収集しましょう。

|    インスタンスの詳細   |  リスト・オプション                |  該当する値をここにコピーする                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| イメージ                 | `ibmcloud is images`            |                           |
| プロファイル               | `ibmcloud is instance-profiles` |                           |
| キー                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| サブネット                | `ibmcloud is subnets`           |                           |
| ゾーン                  | `ibmcloud is zones`             |                           |   
{: caption="表 1. 必要なインスタンスの詳細情報" caption-side="top"}   

以下のコマンドを使用して、新しいインスタンスを作成するのに必要な情報を判別します。

1. ご使用のアカウントに関連付けられている地域をリストします。
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. 望ましい地域に関連付けられているゾーンをリストします。
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. ご使用のアカウントに関連付けられている {{site.data.keyword.vpc_short}} をリストします。
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   使用可能な {{site.data.keyword.vpc_short}} がない場合は、`ibmcloud is vpc-create` コマンドを使用して作成できます。 {{site.data.keyword.vpc_short}} の作成について詳しくは、[IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create) を参照してください。

4. {{site.data.keyword.vpc_short}} に関連付けられているサブネットをリストします。
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   使用可能なサブネットがない場合は、`ibmcloud is subnet-create` コマンドを使用してサブネットを作成できます。 サブネットの作成について詳しくは、[IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets) を参照してください。

5. インスタンスを作成するために使用できるプロファイルをリストします。
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   Name            CPU Arch   CPU Cores   CPU Frequency   Memory   GPU Model   GPU Cores   GPU Count   CPU Memory   Max Volumes   Max IOPS   Max Interfaces   Max Bandwidth   
   BC1_2X4       amd64      2           2000            4                    0           0           0            25            0          0                0   
   BC1_4X8       amd64      4           2000            8                    0           0           0            100           0          0                0   
   MC1_16X128    amd64      16          2000            128                  0           0           0            25            0          0                0   
   BC1_48X192    amd64      48          2000            192                  0           0           0            100           0          0                0   
   BC1_8X32      amd64      8           2000            32                   0           0           0            100           0          0                0   
   CC1_16X16     amd64      16          2000            16                   0           0           0            25            0          0                0   
   MC1_4X32      amd64      4           2000            32                   0           0           0            100           0          0                0     
   ```
   {:screen}

6. インスタンスを作成するために使用できるイメージをリストします。
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. インスタンスに関連付けることができる使用可能な SSH 鍵をリストします。
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   この例の場合、以下の出力のような応答が表示されます。
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   使用可能な SSH 鍵がない場合は、`ibmcloud is key-create` コマンドを使用して SSH 鍵を作成できます。 インスタンスに SSH 鍵を追加できるのは、インスタンスの初回作成時のみです。 SSH 鍵の管理について詳しくは、[SSH 鍵の管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)を参照してください。

## CLI を使用したインスタンスの作成
{: #creating-an-instance-using-the-cli}

上記の値が判明したら、これらの値を使用して `instance-create` コマンドを実行します。 収集した情報に加えて、インスタンスの名前を指定する必要があります。 コマンドの実行例を以下に示します (汎用値の x および 123 は、例示のためにのみ使用しています)。  

インスタンスをプロビジョンすると、自動的に 100 GB のブロック・ストレージ・ボリュームが 1 次ブート・ボリュームとして作成され、インスタンスにアタッチされます。 以下の例は、`--volume-attach` パラメーターを使用して 2 次ボリュームを組み込む方法を示しています。 2 次ボリュームの組み込みはオプションです。
{:note}

1. 新しいインスタンスを作成します。
   ```
   $ ibmcloud is instance-create \
       <INSTANCE_NAME> \
       <VPC_ID> \
       <ZONE_NAME> \
       <PROFILE_ID> \
       <SUBNET_ID> \
       --image <IMAGE_ID> \
       --keys <KEY_IDS>
       --volume-attach <VOLUME_ATTACH_JSON or JSON file>
   ```
   {:codeblock}

   例えば、_us-south-2_ に _my-instance_ と呼ばれるインスタンスを作成し、_bc1-2x4_ プロファイルを使用する場合は、`instance-create` コマンドは次のサンプルのようになります。

   ```
   $ ibmcloud is instance-create \
       my-instance \
       xxx1xx23-4xx5-6789-12x3-456xx7xx123x \
       us-south-2 \
       bc1-2x4 \
       1234x12x-345x-1x23-45x6-x7x891011x1x \
       --image 1xx2x34x-5678-12x3-x4xx-567x81234567 \
       --keys 1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx
       --volume-attach @/Users/myname/myvolume-attachment_create.json
   ```
   {:codeblock}

   各部の意味は、次のとおりです。
   - `INSTANCE_NAME` は _my-instance_
   - `VPC_ID` は _VPC_ID_
   - `ZONE_NAME` は _us-south-2_
   - `PROFILE_ID` は _bc1-2x4_
   - `SUBNET_ID` は _SUBNET_ID_
   - `IMAGE_ID` は _IMAGE_ID_
   - `KEY_IDS` は _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` は、コマンドまたはファイルで提供される JSON 形式のボリューム・アタッチメント仕様です。 データ・ボリュームのボリューム・アタッチメントの JSON の例については、[2 次ボリューム JSON ファイルの例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json)を参照してください。

   この例の場合、以下の応答が表示されます。 
   
   以下の応答は、使用するオプション値に応じて異なります。
   {:note}
   
   ```
   ID                2x12xxx5-xx11-1234-x4x5-1xxx12345678
   Name              my-instance
   Profile           BC1_2X4
   Gen               
   CPU Arch          amd64
   CPU Cores         2
   CPU Frequency     2000
   Memory            4
   Primary Intf      great-scott-stride-lilac-captivate-filtrate(xx12x345-5bxx-1x23-458x-1x2xxx345x6x)   
   Primary Address   192.16.1.4
   Image             ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
   Profile           -
   Status            pending
   Created           now
   VPC               my-vpc(xxx1xx23-4xx5-6789-12x3-456xx7xx123x)
   Zone              us-south-2
   Volume Attachment my-volume-attachment (xx55xx44-3xx1-1234-42x1-234xx5x678xx)
   Resource Group    -   
   Tags              -   
   ```
   {:screen}

   インスタンスが作成されるまで、状況として pending が表示されます。
   {: tip}

2. 状況が *running* に変わったら、新しいインスタンスが表示されることを確認します。

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   この例の場合、以下の応答が表示されます。
   ```
   ID                2x12xxx5-xx11-1234-x4x5-1xxx12345678   
   Name              my-instance   
   Profile           BC1_2X4   
   Gen                  
   CPU Arch          amd64   
   CPU Cores         2   
   CPU Frequency     2000   
   Memory            4   
   Primary Intf      great-scott-stride-lilac-captivate-filtrate(xx12x345-5bxx-1x23-458x-1x2xxx345x6x)   
   Primary Address   192.16.1.4  
   Image             ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
   Profile           -   
   Status            running   
   Created           5 minutes ago   
   VPC               my-vpc(xxx1xx23-4xx5-6789-12x3-456xx7xx123x)   
   Zone              us-south-2
   Volume Attachment my-volume-attachment (xx55xx44-3xx1-1234-42x1-234xx5x678xx)
   Resource Group    -   
   Tags              -
   ```
   {:screen}

3. 新しいインスタンス用に作成されたネットワーク・インターフェースを表示します。
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   この例の場合、以下の応答が表示されます。
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. インスタンスに関連付ける浮動 IP アドレスを要求します。

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   この例の場合、以下の応答が表示されます。
   ```
     Address          xxx.xxx.xxx.xxx   
     Name             my-floatingip   
     Target           great-scott-stride-lilac-captivate-filtrate(xx12x345-.)   
     Target Type      intf   
     Target IP        192.0.2.25  
     Created          1 second ago   
     Status           available   
     Zone             us-south-2   
     Resource Group   -   
     Tags             -  
    ```
    {:screen}

    この浮動 IP `アドレス`を、後で使用するために記録しておきます。  

さらに詳しい情報が必要な場合は、 いつでも `ibmcloud is instance-create -help` を実行して、インスタンスの作成に関するヘルプを表示できます。
{: tip}

{{site.data.keyword.cloud_notm}} コンソールを使用してインスタンスを作成する場合、 詳細については、[仮想サーバー・インスタンスの作成](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)を参照してください。
{: tip}

## 次のステップ
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

サーバーを作成し終えたら、インスタンスに接続できます。 詳しくは、[Linux インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)または [Windows インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)を参照してください。




