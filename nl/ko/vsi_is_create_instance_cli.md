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

# 가상 서버 인스턴스 작성(CLI)
{: #creating-virtual-servers-cli}

명령행 인터페이스(CLI)를 사용하여 {{site.data.keyword.vsi_is_full}} 인스턴스를 작성할 수 있습니다.
{:shortdesc}

## 시작하기 전에
{: #prereq-creating-virtual-servers-cli}

1. 다음의 CLI 플러그인을 다운로드, 설치 및 초기화했는지 확인하십시오.
    * {{site.data.keyword.cloud_notm}} CLI
    * vpc-infrastructure 플러그인

   자세한 정보는 [IBM Cloud VPC용 CLI 참조서](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)를 참조하십시오.
   
   vpc-infrastructure 플러그인을 처음 설치하는 경우에는 대상 생성을 gen 1로 설정해야 합니다(`ibmcloud is target --gen 1`).
   {:important}
   
   
2. 사전에 [{{site.data.keyword.vpc_short}}가 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)되었는지 확인하십시오.

## CLI를 사용하여 인스턴스를 작성하기 위한 정보 수집
{: #gathering-information-to-create-an-instance-using-the-cli}

인스턴스를 작성할 준비가 되었습니까? `ibmcloud is instances` 명령을 실행하려면 우선 인스턴스에 대한 세부사항(예: 사용할 프로파일 또는 이미지)을 알아야 합니다.

우선 해당 정보를 수집합니다.

|    인스턴스 세부사항   |  나열 옵션                |  값 복사                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| 이미지                 | `ibmcloud is images`            |                           |
| 프로파일               | `ibmcloud is instance-profiles` |                           |
| 키                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| 서브넷                | `ibmcloud is subnets`           |                           |
| 구역                  | `ibmcloud is zones`             |                           |   
{: caption="표 1. 필수 인스턴스 세부사항" caption-side="top"}   

다음 명령을 사용하여 새 인스턴스의 작성에 필요한 정보를 판별하십시오.

1. 계정과 연관된 지역을 나열하십시오.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. 원하는 지역과 연관된 구역을 나열하십시오.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. 계정과 연관된 {{site.data.keyword.vpc_short}}를 나열하십시오.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   사용 가능한 항목이 없는 경우에는 `ibmcloud is vpc-create` 명령을 사용하여 {{site.data.keyword.vpc_short}}를 작성할 수 있습니다. {{site.data.keyword.vpc_short}} 작성에 대한 자세한 정보는 [IBM Cloud VPC CLI 참조서](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create)를 참조하십시오.

4. {{site.data.keyword.vpc_short}}와 연관된 서브넷을 나열하십시오.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   사용 가능한 서브넷이 없는 경우에는 `ibmcloud is subnet-create` 명령을 사용하여 서브넷을 작성할 수 있습니다. 서브넷 작성에 대한 자세한 정보는 [IBM Cloud VPC CLI 참조서](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets)를 참조하십시오.

5. 인스턴스 작성을 위해 사용 가능한 프로파일을 나열하십시오.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
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

6. 인스턴스 작성을 위해 사용 가능한 이미지를 나열하십시오.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. 인스턴스와 연관시킬 수 있는 사용 가능한 SSH 키를 나열하십시오.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   이 예제에서는 다음 출력과 유사한 응답이 나타납니다.
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   사용 가능한 SSH 키가 없는 경우에는 `ibmcloud is key-create` 명령을 사용하여 SSH 키를 작성할 수 있습니다. 인스턴스를 처음 작성할 때만 인스턴스에 SSH 키를 추가할 수 있습니다. SSH 키 관리에 대한 자세한 정보는 [SSH 키 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)를 참조하십시오.

## CLI를 사용하여 인스턴스 작성
{: #creating-an-instance-using-the-cli}

이러한 값들이 파악되면 이를 사용하여 `instance-create` 명령을 실행하십시오. 수집한 정보 외에도 인스턴스의 이름을 지정해야 합니다. 다음 예제는 실행 중인 명령을 보여줍니다(예제 용도로만 일반 x 및 123 값 사용).  

인스턴스를 프로비저닝하면 100GB 블록 스토리지 볼륨이 1차 부트 볼륨으로 자동 작성되어 인스턴스에 연결됩니다. 다음 예제는 `--volume-attach` 매개변수로 2차 볼륨을 포함하는 방법을 보여줍니다. 2차 볼륨 포함은 선택사항입니다.
{:note}

1. 새 인스턴스를 작성하십시오.
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

   예를 들어, _us-south-2_에서 _my-instance_라는 인스턴스를 작성 중이며 _bc1-2x4_ 프로파일을 사용하는 경우 `instance-create` 명령은 다음 예제와 유사하게 나타납니다.

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

   여기서,
   - `INSTANCE_NAME`은 _my-instance_입니다.
   - `VPC_ID`는 _VPC_ID_입니다.
   - `ZONE_NAME`은 _us-south-2_입니다.
   - `PROFILE_ID`는 _bc1-2x4_입니다.
   - `SUBNET_ID`는 _SUBNET_ID_입니다.
   - `IMAGE_ID`는 _IMAGE_ID_입니다.
   - `KEY_IDS`는 _KEY_ID1, KEY_ID2, ..._입니다.
   - `VOLUME_ATTACH_JSON`은 파일로서 또는 명령에서 제공되는 JSON 형식의 볼륨 연결 스펙입니다. 데이터 볼륨에 대한 볼륨 연결 JSON의 예제는 [예제 데이터 볼륨 JSON 파일](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json)을 참조하십시오.

   이 예제의 경우에는 다음 응답이 나타납니다. 
   
   다음의 응답은 사용하는 선택적 값에 따라 서로 다를 수 있습니다.
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

   상태는 인스턴스가 작성될 때까지 '보류 중'을 표시합니다.
   {: tip}

2. 상태가 *실행 중*으로 변경되면 새 인스턴스가 보이는지 확인하십시오.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   이 예제의 경우에는 다음 응답이 나타납니다.
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

3. 새 인스턴스에 대해 작성된 네트워크 인터페이스를 보십시오.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   이 예제의 경우에는 다음 응답이 나타납니다.
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. 인스턴스와 연관시킬 유동 IP 주소를 요청하십시오.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   이 예제의 경우에는 다음 응답이 나타납니다.
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

    나중에 사용할 수 있도록 유동 IP `Address`를 기억해 두십시오.  

추가 도움이 필요하십니까? 언제든지 `ibmcloud is instance-create --help`를 실행하여 인스턴스 작성에 대한 도움말을 표시할 수 있습니다.
{: tip}

{{site.data.keyword.cloud_notm}} 콘솔을 사용한 인스턴스 작성을 원하십니까? 자세한 정보는 [인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)을 참조하십시오.
{: tip}

## 다음 단계
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

서버가 작성되면 인스턴스에 연결할 수 있습니다. 자세한 정보는 [Linux 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) 또는 [Windows 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)을 참조하십시오.




