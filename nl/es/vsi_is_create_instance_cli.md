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

# Creación de instancias de servidor virtual (CLI)
{: #creating-virtual-servers-cli}

Puede crear instancias de {{site.data.keyword.vsi_is_full}} utilizando la interfaz de línea de mandatos (CLI).
{:shortdesc}

## Antes de empezar
{: #prereq-creating-virtual-servers-cli}

1. Asegúrese de haber descargado, instalado e inicializado los siguientes plug-ins de CLI:
    * CLI de {{site.data.keyword.cloud_notm}}
    * El plug-in vpc-infrastructure

   Para obtener más información, consulte [Consulta de la CLI de IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Cuando instala el plug-in vpc-infrastructure por primera vez, debe establecer la generación de destino en gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
   
2. Asegúrese de haber [creado un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Obtención de información para crear una instancia utilizando la CLI
{: #gathering-information-to-create-an-instance-using-the-cli}

¿Preparado para crear una instancia? Para poder ejecutar el mandato `ibmcloud is instances`, tendrá que conocer los detalles sobre la instancia, por ejemplo, el perfil o imagen que desea utilizar.

Vamos a recopilar esa información primero:

|    Detalles de la instancia   |  Opciones de listado                |  Copie sus valores                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| Imagen                 | `ibmcloud is images`            |                           |
| Perfil               | `ibmcloud is instance-profiles` |                           |
| Clave                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| Subred                | `ibmcloud is subnets`           |                           |
| Zona                  | `ibmcloud is zones`             |                           |   
{: caption="Tabla 1. Detalles de instancia obligatorios" caption-side="top"}   

Utilice los mandatos siguientes para determinar la información necesaria para crear una instancia nueva.

1. Obtenga una lista de las regiones asociadas a su cuenta.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. Obtenga una lista de las zonas asociadas a la región deseada.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. Obtenga una lista de las {{site.data.keyword.vpc_short}} asociadas a su cuenta.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   Si no tiene una disponible, puede crear una {{site.data.keyword.vpc_short}} utilizando el mandato `ibmcloud is vpc-create`. Para obtener más información sobre cómo crear una {{site.data.keyword.vpc_short}}, consulte [Consulta de la CLI de VPC de IBM Cloud](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create).

4. Obtenga una lista de las subredes asociadas a la {{site.data.keyword.vpc_short}}.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   Si no tiene una disponible, puede crear una subred utilizando el mandato `ibmcloud is subnet-create`. Para obtener más información sobre cómo crear una subred, consulte [Consulta de la CLI de VPC de IBM Cloud](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets).

5. Obtenga una lista de los perfiles disponibles para crear la instancia.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
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

6. Obtenga una lista de las imágenes disponibles para crear la instancia.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. Obtenga una lista de las claves SSH disponibles que puede asociar a la instancia.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   Si no tiene una disponible, puede crear una clave SSH utilizando el mandato `ibmcloud is key-create`. Puede añadir claves SSH a la instancia sólo en el momento de crearla. Para obtener más información sobre cómo gestionar claves SSH, consulte [Gestión de claves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

## Creación de una instancia utilizando la CLI
{: #creating-an-instance-using-the-cli}

Una vez conozca estos valores, utilícelos para ejecutar el mandato `instance-create`. Además de la información que ha recopilado, debe especificar un nombre para la instancia. En el ejemplo siguiente se muestra el mandato en acción (utilizando valores genéricos x y 123, sólo a modo de ejemplo).  

Cuando se suministra una instancia, se crea automáticamente un volumen de almacenamiento en bloques de 100 GB como volumen de arranque primario y se conecta a la instancia. En el ejemplo siguiente se muestra cómo incluir un volumen secundario con el parámetro `--volume-attach`. La inclusión de un volumen secundario es opcional.
{:note}

1. Cree una nueva instancia.
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

   Por ejemplo, para crear una instancia denominada _my-instance_ en _us-south-2_ utilizando el perfil _bc1-2x4_, el mandato `instance-create` sería algo similar al ejemplo siguiente:

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

   donde:
   - `INSTANCE_NAME` es _my-instance_
   - `VPC_ID` es _VPC_ID_
   - `ZONE_NAME` es  _us-south-2_
   - `PROFILE_ID` es _bc1-2x4_
   - `SUBNET_ID` es _SUBNET_ID_
   - `IMAGE_ID` es _IMAGE_ID_
   - `KEY_IDS` es _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` es la especificación de conexión de volumen en formato JSON, proporcionada en el mandato o como archivo. Para ver un ejemplo de JSON de conexión de volumen para un volumen de datos, consulte [Ejemplo de archivo JSON de volumen secundario](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json).

   Para este ejemplo, vería las respuestas siguientes. 
   
   La respuesta siguiente variará según los valores opcionales que utilice.
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

   El estado se muestra como pending (pendiente) hasta que se crea la instancia.
   {: tip}

2. Cuando el estado cambie a *running* (en ejecución), verifique que puede ver la nueva instancia.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Para este ejemplo, vería las respuestas siguientes.
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

3. Vea las interfaces de red que se han creado para la instancia nueva.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Para este ejemplo, vería las respuestas siguientes.
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. Solicite una dirección IP flotante para asociar a la instancia.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   Para este ejemplo, vería las respuestas siguientes.
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

    Recuerde la dirección IP flotante (`Address`) para más adelante.  

¿Necesita más ayuda? Siempre puede ejecutar `ibmcloud is instance-create --help` para visualizar ayuda para crear una instancia.
{: tip}

¿Prefiere crear una instancia utilizando la consola de {{site.data.keyword.cloud_notm}}? Para obtener más información, consulte [Creación de una instancia](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
{: tip}

## Siguientes pasos
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

Una vez que se ha creado el servidor, puede conectarse a la instancia. Para obtener más información, consulte [Conexión con la instancia de Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) o [Conexión con la instancia de Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).




