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

# Criando instâncias de servidor virtual (CLI)
{: #creating-virtual-servers-cli}

É possível criar instâncias dos {{site.data.keyword.vsi_is_full}} usando a interface da linha de comandos (CLI).
{:shortdesc}

## Antes de iniciar
{: #prereq-creating-virtual-servers-cli}

1. Certifique-se de fazer download dos seguintes plug-ins da CLI, de instalá-los e de inicializá-los:
    * CLI do {{site.data.keyword.cloud_notm}}
    * O plug-in vpc-infrastructure

   Para obter mais informações, consulte [Referência da CLI do IBM Cloud para o VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Ao instalar o plug-in vpc-infrastructure pela primeira vez, deve-se configurar a geração de destino como gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
   
2. Certifique-se de que já tenha [criado um {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Reunindo informações para criar uma instância usando a CLI
{: #gathering-information-to-create-an-instance-using-the-cli}

Pronto para criar uma instância? Antes de poder executar o comando `ibmcloud is instances`, você precisará saber os detalhes sobre a instância, como qual perfil ou imagem você deseja usar.

Vamos reunir estas informações primeiro:

|    Detalhes da instância   |  Opções de listagem                |  Copie seus valores                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| Imagem                 | `ibmcloud is images`            |                           |
| Perfil               | `ibmcloud is instance-profiles` |                           |
| Key                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| Sub-rede                | `ibmcloud is subnets`           |                           |
| Zona                  | `ibmcloud is zones`             |                           |   
{: caption="Tabela 1. Detalhes necessários da instância" caption-side="top"}   

Use os comandos a seguir para determinar as informações necessárias para criar uma nova instância.

1. Liste as regiões associadas à sua conta.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
   ```
   Name       Endpoint               Status
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. Liste as zonas associadas à região desejada.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
   ```
   Name         Region     Status
   us-south-2   us-south   available
   ```
   {:screen}

3. Liste os {{site.data.keyword.vpc_short}}s que estão associados à sua conta.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   Se você não tiver um disponível, será possível criar um {{site.data.keyword.vpc_short}} usando o comando `ibmcloud is vpc-create`. Para obter mais informações sobre como criar um {{site.data.keyword.vpc_short}}, consulte [Referência de CLI do IBM Cloud VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create).

4. Liste as sub-redes que estão associadas ao {{site.data.keyword.vpc_short}}.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   Se você não tiver uma disponível, será possível criar uma sub-rede usando o comando `ibmcloud is subnet-create`. Para obter mais informações sobre a criação de uma sub-rede, consulte [Referência de CLI do IBM Cloud VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets).

5. Liste os perfis disponíveis para criar sua instância.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
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

6. Liste as imagens disponíveis para criar sua instância.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. Liste as chaves SSH disponíveis que podem ser associadas à sua instância.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   Se você não tiver uma disponível, será possível criar uma chave SSH usando o comando `ibmcloud is key-create`. É possível incluir chaves SSH em sua instância somente ao criar inicialmente a instância. Para obter mais informações sobre como gerenciar chaves SSH, consulte [Gerenciando chaves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

## Criando uma instância usando a CLI
{: #creating-an-instance-using-the-cli}

Depois de conhecer esses valores, use-os para executar o comando `instance-create`. Além das informações que você reuniu, deve-se especificar um nome para a instância. O exemplo a seguir mostra o comando em ação (usando valores genéricos x e 123 apenas para propósitos de exemplo).  

Ao provisionar uma instância, um volume de armazenamento de bloco de 100 GB é automaticamente criado como um volume de inicialização primário e conectado à instância. O exemplo a seguir mostra como incluir um volume secundário com o parâmetro `--volume-attach`. A inclusão de um volume secundário é opcional.
{:note}

1. Crie uma nova instância.
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

   Por exemplo, se você estiver criando uma instância chamada _my-instance_ em _us-south-2_ e usando o perfil _bc1-2x4_, seu comando `instance-create` será semelhante à amostra a seguir:

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

   em que:
   - `INSTANCE_NAME` é _my-instance_
   - `VPC_ID` é _VPC_ID_
   - `ZONE_NAME` é _us-south-2_
   - `PROFILE_ID` é _bc1-2x4_
   - `SUBNET_ID` é _SUBNET_ID_
   - `IMAGE_ID` é _IMAGE_ID_
   - `KEY_IDS` é _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` é a especificação de anexo de volume no formato JSON, fornecido no comando ou como um arquivo. Para obter um exemplo de um JSON de conexão de volume para um volume de dados, consulte [Exemplo de arquivo JSON de volume secundário](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json).

   Para esse exemplo, você veria as respostas a seguir. 
   
   A resposta a seguir irá variar dependendo de quais valores opcionais você usar.
   {:note}
   
   ```
   ID 2x12xxx5-xx11-1234-x4x5-1xxx12345678 Name my-instance Profile BC1_2X4 Gen CPU Arch amd64 CPU Cores 2 CPU Frequency 2000 Memory 4 Primary Intf great-scott-stride-lilac-captivate-filtrate(xx12x345-5bxx-1x23-458x-1x2xxx345x6x)   
   Primary Address 192.16.1.4 Image ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
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

   O status é exibido como pendente até que a instância seja criada.
   {: tip}

2. Quando o status mudar para *em execução*, verifique se é possível ver a sua nova instância.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Para esse exemplo, você veria as respostas a seguir.
   ```
   ID 2x12xxx5-xx11-1234-x4x5-1xxx12345678 Name my-instance Profile BC1_2X4 Gen CPU Arch amd64 CPU Cores 2 CPU Frequency 2000 Memory 4 Primary Intf great-scott-stride-lilac-captivate-filtrate(xx12x345-5bxx-1x23-458x-1x2xxx345x6x)   
   Primary Address 192.16.1.4 Image ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
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

3. Visualize as interfaces de rede que foram criadas para a sua nova instância.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Para esse exemplo, você veria as respostas a seguir.
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. Solicite um endereço IP flutuante para associar à sua instância.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   Para esse exemplo, você veria as respostas a seguir.
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

    Lembre-se do IP flutuante `Address` para mais tarde.  

Precisa de mais ajuda? É possível sempre executar o `ibmcloud is instance-create --help` para exibir a ajuda para criar uma instância.
{: tip}

Você prefere criar uma instância usando o console do {{site.data.keyword.cloud_notm}}? Para obter mais informações, consulte [Criando uma instância](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
{: tip}

## Próximas Etapas
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

Depois que o servidor é criado, é possível se conectar à sua instância. Para obter mais informações, consulte [Conectando-se à sua instância do Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) ou [Conectando-se à sua instância do Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).




