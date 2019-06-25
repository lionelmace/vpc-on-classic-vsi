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

# 建立虛擬伺服器實例 (CLI)
{: #creating-virtual-servers-cli}

您可以使用指令行介面 (CLI) 來建立 {{site.data.keyword.vsi_is_full}} 實例。
{:shortdesc}

## 開始之前
{: #prereq-creating-virtual-servers-cli}

1. 確定您已下載、安裝及起始設定下列 CLI 外掛程式：
    * {{site.data.keyword.cloud_notm}} CLI
    * vpc-infrastructure 外掛程式

   如需相關資訊，請參閱 [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)。
   
   第一次安裝 vpc-infrastructure 外掛程式時，您必須將目標世代設為 gen 1，`ibmcloud is target --gen 1`。
   {:important}
   
   
2. 確定您已經[建立了 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 使用 CLI 收集資訊以建立實例
{: #gathering-information-to-create-an-instance-using-the-cli}

準備要建立實例了嗎？您需要知道實例的相關詳細資料，例如，您想要使用的設定檔或映像檔，才可以執行 `ibmcloud is instances` 指令。

讓我們先收集該資訊：

|實例詳細資料|列出選項|複製您的值|
| --------------------- | --------------------------------|---------------------------------------------- |
|映像檔| `ibmcloud is images`            |                           |
|設定檔| `ibmcloud is instance-profiles` |                           |
|金鑰| `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
|子網路| `ibmcloud is subnets`           |                           |
|區域| `ibmcloud is zones`             |                           |   
{: caption="表 1. 必要的實例詳細資料" caption-side="top"}   

使用下列指令來決定建立新實例所需的資訊。

1. 列出與您帳戶相關聯的地區。
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. 列出與想要地區相關聯的區域。
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. 列出與您帳戶相關聯的 {{site.data.keyword.vpc_short}}。
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   如果您沒有可用者，可以使用 `ibmcloud is vpc-create` 指令建立 {{site.data.keyword.vpc_short}}。如需建立 {{site.data.keyword.vpc_short}} 的相關資訊，請參閱 [IBM Cloud VPC CLI 參考資料](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create)。

4. 列出與 {{site.data.keyword.vpc_short}} 相關聯的子網路。
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   如果您沒有可用者，可以使用 `ibmcloud is subnet-create` 指令建立子網路。如需建立子網路的相關資訊，請參閱 [IBM Cloud VPC CLI 參考資料](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets)。

5. 列出可用來建立實例的設定檔。
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
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

6. 列出可用來建立實例的映像檔。
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. 列出可以與實例相關聯的可用 SSH 金鑰。
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   針對此範例，您會看到類似下列輸出的回應：
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   如果您沒有可用者，可以使用 `ibmcloud is key-create` 指令建立 SSH 金鑰。只有在您最初建立實例時，才可以將 SSH 金鑰新增至實例。如需管理 SSH 金鑰的相關資訊，請參閱[管理 SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)。

## 使用 CLI 建立實例
{: #creating-an-instance-using-the-cli}

知道這些值之後，請利用它們來執行 `instance-create` 指令。除了您收集的資訊之外，您還必須指定實例的名稱。下列範例顯示動作中的指令（因為範例的緣故，只使用一般的 x 和 123 值）。  

當您佈建實例時，會自動建立 100 GB 的區塊儲存空間磁區作為主要開機磁區並連接至實例。下列範例顯示如何使用 `--volume-attach` 參數包含次要磁區。包含次要磁區是選用的作業。
{:note}

1. 建立新實例。
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

   例如，如果您在 _us-south-2_ 使用 _bc1-2x4_ 設定檔，建立稱為 _my-instance_ 的實例，則您的 `instance-create` 指令會類似下列範例：

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

   其中：
   - `INSTANCE_NAME` 是 _my-instance_
   - `VPC_ID` 是 _VPC_ID_
   - `ZONE_NAME` 是 _us-south-2_
   - `PROFILE_ID` 是 _bc1-2x4_
   - `SUBNET_ID` 是 _SUBNET_ID_
   - `IMAGE_ID` 是 _IMAGE_ID_
   - `KEY_IDS` 是 _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` 是 JSON 格式的磁區連接規格，在指令中提供，或以檔案形式提供。如需資料磁區的磁區連接 JSON 範例，請參閱[次要磁區 JSON 檔範例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json)。

   針對此範例，您會看到下列回應。 
   
   下列回應視您所使用的選用值而有所不同。
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

   在建立實例之前，狀態會顯示 pending。
   {: tip}

2. 當狀態變更為 *running* 時，請驗證您是否可以看到您的新實例。

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   針對此範例，您會看到下列回應。
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

3. 檢視為新實例建立的網路介面。
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   針對此範例，您會看到下列回應。
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. 要求浮動 IP 位址，以與您的實例產生關聯。

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   針對此範例，您會看到下列回應。
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

    請記住浮動 IP `位址`以供稍後使用。  

需要更多協助嗎？您隨時可以執行 `ibmcloud is instance-create --help` 來顯示建立實例的說明。
{: tip}

您偏好使用 {{site.data.keyword.cloud_notm}} 主控台來建立實例嗎？如需相關資訊，請參閱[建立實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)。
{: tip}

## 後續步驟
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

建立伺服器之後，您可以連接至實例。如需相關資訊，請參閱[連接至 Linux 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)或[連接至 Windows 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)。




