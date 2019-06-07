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

# Creating virtual server instances (CLI)
{: #creating-virtual-servers-cli}

You can create {{site.data.keyword.vsi_is_full}} instances by using the command line interface (CLI).
{:shortdesc}

## Before you begin
{: #prereq-creating-virtual-servers-cli}

1. Ensure you have downloaded, installed, and initialized the following CLI plug-ins:
    * {{site.data.keyword.cloud_notm}} CLI
    * The vpc-infrastructure plugin

   For more information, see [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   When you install the vpc-infrastructure plugin for the first time, you must set the target generation to gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
   
2. Make sure you have already [created an {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Gathering information to create an instance using the CLI
{: #gathering-information-to-create-an-instance-using-the-cli}

Ready to create an instance? Before you can run the `ibmcloud is instances` command, you'll need to know the details about the instance, such as what profile or image you want to use.

Let's gather that information first:

|    Instance details   |  Listing options                |  Copy your values                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| Image                 | `ibmcloud is images`            |                           |
| Profile               | `ibmcloud is instance-profiles` |                           |
| Key                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| Subnet                | `ibmcloud is subnets`           |                           |
| Zone                  | `ibmcloud is zones`             |                           |   
{: caption="Table 1. Required instance details" caption-side="top"}   

Use the following commands to determine the required information for creating a new instance.

1. List the regions associated with your account.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. List the zones associated with the desired region.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. List the {{site.data.keyword.vpc_short}}s that are associated with your account.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   If you do not have one available, you can create an {{site.data.keyword.vpc_short}} by using the `ibmcloud is vpc-create` command. For more information about creating an {{site.data.keyword.vpc_short}}, see [IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create).

4. List the subnets that are associated with the {{site.data.keyword.vpc_short}}.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   If you do not have one available, you can create a subnet using the `ibmcloud is subnet-create` command. For more information about creating a subnet, see [IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets).

5. List the available profiles for creating your instance.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
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

6. List the available images for creating your instance.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. List the available SSH keys that you can associate with your instance.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   For this example, you'd see a response similar to the following output:
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   If you do not have one available, you can create an SSH key using the `ibmcloud is key-create` command. You can add SSH keys to your instance only when you initially create the instance. For more information about managing SSH keys, see [Managing SSH keys](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

## Creating an instance using the CLI
{: #creating-an-instance-using-the-cli}

After you know these values, use them to run the `instance-create` command. In addition to the information that you gathered, you must specify a name for the instance. The following example shows the command in action (using generic x and 123 values for example purposes only).  

When you provision an instance, a 100 GB block storage volume is automatically created as a primary boot volume and attached to the instance. The following example shows how to include a secondary volume with the `--volume-attach` parameter. Including a secondary volume is optional.
{:note}

1. Create a new instance.
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

   For example, if you are creating an instance called _my-instance_ in _us-south-2_ and using the _bc1-2x4_ profile, your `instance-create` command would look similar to the following sample:

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

   where:
   - `INSTANCE_NAME` is _my-instance_
   - `VPC_ID` is _VPC_ID_
   - `ZONE_NAME` is  _us-south-2_
   - `PROFILE_ID` is _bc1-2x4_
   - `SUBNET_ID` is _SUBNET_ID_
   - `IMAGE_ID` is _IMAGE_ID_
   - `KEY_IDS` is _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` is the volume attachment specification in JSON format, provided in the command or as a file. For an example of a volume attachment JSON for a data volume, see [Example secondary volume JSON file](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json).

   For this example, you'd see the following responses. 
   
   The following response will vary depending on what optional values you use.
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

   The status displays pending until the instance is created.
   {: tip}

2. When the status changes to *running*, verify that you can see your new instance.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   For this example, you'd see the following responses.
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

3. View the network interfaces that were created for your new instance.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   For this example, you'd see the following responses.
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. Request a floating IP address to associate to your instance.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   For this example, you'd see the following responses.
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

    Remember the floating IP `Address` for later.  

Need more help? You can always run `ibmcloud is instance-create --help` to display help for creating an instance.
{: tip}

Do you prefer to create an instance using the {{site.data.keyword.cloud_notm}} console? For more information, see [Creating an instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
{: tip}

## Next steps
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

After the server is created, you can connect to your instance. For more information, see [Connecting to your Linux instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) or [Connecting to your Windows instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).




