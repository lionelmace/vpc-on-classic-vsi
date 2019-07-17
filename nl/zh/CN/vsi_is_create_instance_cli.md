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

# 创建虚拟服务器实例 (CLI)
{: #creating-virtual-servers-cli}

您可以使用命令行界面 (CLI) 来创建 {{site.data.keyword.vsi_is_full}} 实例。
{:shortdesc}

## 开始之前
{: #prereq-creating-virtual-servers-cli}

1. 确保已下载、安装并初始化以下 CLI 插件：
    * {{site.data.keyword.cloud_notm}} CLI
    * vpc-infrastructure 插件

   有关更多信息，请参阅 [IBM Cloud CLI for VPC 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)。
   
   首次安装 vpc-infrastructure 插件时，必须将目标生成设置为 gen 1：`ibmcloud is target --gen 1`。
   {:important}
   
   
2. 确保您已[创建 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 使用 CLI 收集信息以创建实例
{: #gathering-information-to-create-an-instance-using-the-cli}

准备好创建实例了吗？要能够运行 `ibmcloud is instances` 命令，您需要先了解有关实例的详细信息，例如要使用的概要文件或映像。

首先收集以下信息：

|实例详细信息|列出选项|复制值|
| --------------------- | --------------------------------|---------------------------------------------- |
|映像|`ibmcloud is images`|                           |
|概要文件|`ibmcloud is instance-profiles`|                           |
|密钥|`ibmcloud is keys`|                           |
|VPC|`ibmcloud is vpcs`|                           |
|子网|`ibmcloud is subnets`|                           |
|专区|`ibmcloud is zones`|                           |   
{: caption="表 1. 必需的实例详细信息" caption-side="top"}   

使用以下命令来确定创建新实例所需的信息。

1. 列出与帐户关联的区域。
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. 列出与所需区域关联的专区。
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. 列出与帐户关联的 {{site.data.keyword.vpc_short}}。
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   如果没有可用的 {{site.data.keyword.vpc_short}}，可以使用 `ibmcloud is vpc-create` 命令进行创建。有关创建 {{site.data.keyword.vpc_short}} 的更多信息，请参阅 [IBM Cloud VPC CLI 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create)。

4. 列出与 {{site.data.keyword.vpc_short}} 关联的子网。
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   如果没有可用的子网，可以使用 `ibmcloud is subnet-create` 命令进行创建。有关创建子网的更多信息，请参阅 [IBM Cloud VPC CLI 参考](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets)。

5. 列出可用于创建实例的概要文件。
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
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

6. 列出可用于创建实例的映像。
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. 列出可以与实例关联的可用 SSH 密钥。
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   对于此示例，您会看到类似于以下输出的响应：
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   如果没有可用的 SSH 密钥，可以使用 `ibmcloud is key-create` 命令进行创建。仅当初始创建实例时，才能将 SSH 密钥添加到实例。有关管理 SSH 密钥的更多信息，请参阅[管理 SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)。

## 使用 CLI 创建实例
{: #creating-an-instance-using-the-cli}

了解这些值后，使用这些值来运行 `instance-create` 命令。除了收集的信息外，还必须指定实例的名称。以下示例显示命令的工作方式（通用 x 和 123 值仅用于示例目的）。  

供应实例时，会自动将 100 GB 块存储卷创建为主引导卷并将其连接到实例。以下示例显示了如何使用 `--volume-attach` 参数包含辅助卷。包含辅助卷是可选的。
{:note}

1. 创建新实例。
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

   例如，如果要在 _us-south-2_ 中创建名为 _my-instance_ 的实例并使用 _bc1-2x4_ 概要文件，那么 `instance-create` 命令将类似于以下样本：

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
   - `INSTANCE_NAME` 为 _my-instance_
   - `VPC_ID` 为 _VPC_ID_
   - `ZONE_NAME` 为 _us-south-2_
   - `PROFILE_ID` 为 _bc1-2x4_
   - `SUBNET_ID` 为 _SUBNET_ID_
   - `IMAGE_ID` 为 _IMAGE_ID_
   - `KEY_IDS` 为 _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` 为 JSON 格式的卷连接规范，此项在命令中提供或作为文件提供。有关数据卷的卷连接 JSON 的示例，请参阅[示例辅助卷 JSON 文件](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json)。

   对于此示例，您将看到以下响应。 
   
   根据您使用的可选值，以下响应将有所不同。
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

   Status 会一直显示为 pending，直到实例创建为止。
   {: tip}

2. Status 更改为 *running* 时，验证是否可以看到新实例。

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   对于此示例，您将看到以下响应。
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

3. 查看为新实例创建的网络接口。
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   对于此示例，您将看到以下响应。
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. 请求要与实例关联的浮动 IP 地址。

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   对于此示例，您将看到以下响应。
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

    请记住浮动 IP `Address` 以供稍后使用。  

需要更多帮助吗？您可以随时运行 `ibmcloud is instance-create --help` 来显示有关创建实例的帮助。
{: tip}

您更倾向于使用 {{site.data.keyword.cloud_notm}} 控制台来创建实例吗？有关更多信息，请参阅[创建实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)。
{: tip}

## 后续步骤
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

创建服务器后，可以连接到实例。有关更多信息，请参阅[连接到 Linux 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)或[连接到 Windows 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)。




