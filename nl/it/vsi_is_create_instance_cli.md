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

# Creazione delle istanze del server virtuale (CLI)
{: #creating-virtual-servers-cli}

Puoi creare le istanze di {{site.data.keyword.vsi_is_full}} utilizzando l'interfaccia di riga comando (CLI).
{:shortdesc}

## Prima di cominciare
{: #prereq-creating-virtual-servers-cli}

1. Assicurati di aver scaricato, installato e inizializzato i seguenti plugin CLI:
    * CLI {{site.data.keyword.cloud_notm}}
    * Il plugin vpc-infrastructure

   Per ulteriori informazioni, vedi [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Quando installi il plugin vpc-infrastructure per la prima volta, devi configurare la generazione di destinazione su gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
   
2. Assicurati di aver già [creato un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Raccolta delle informazioni per creare un'istanza utilizzando la CLI.
{: #gathering-information-to-create-an-instance-using-the-cli}

Pronto per creare un'istanza? Prima di poter eseguire il comando `ibmcloud is instances`, dovrai conoscere i dettagli sull'istanza, ad esempio quale profilo o immagine vuoi utilizzare.

Raccogliamo prima tali informazioni:

|    Dettagli istanza   |  Opzioni di elenco                |  Copia i tuoi valori                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| Immagine                 | `ibmcloud is images`            |                           |
| Profilo               | `ibmcloud is instance-profiles` |                           |
| Chiave                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| Sottorete                | `ibmcloud is subnets`           |                           |
| Zona                  | `ibmcloud is zones`             |                           |   
{: caption="Tabella 1. Dettagli dell'istanza obbligatori" caption-side="top"}   

Utilizza i seguenti comandi per determinare le informazioni necessarie per creare una nuova istanza.

1. Elenca le regioni associate al tuo account.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
   ```
   Name       Endpoint               Status   
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. Elenca le zone associate alla regione desiderata.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
   ```
   Name         Region     Status   
   us-south-2   us-south   available
   ```
   {:screen}

3. Elenca i {{site.data.keyword.vpc_short}} associati al tuo account.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
   ```
   ID                                     Name                                  Default   Created       Status      Tags   
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -   
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   Se non ne hai uno disponibile, puoi creare un {{site.data.keyword.vpc_short}} utilizzando il comando `ibmcloud is vpc-create`. Per ulteriori informazioni sulla creazione di un {{site.data.keyword.vpc_short}}, vedi [IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create).

4. Elenca le sottoreti associate al {{site.data.keyword.vpc_short}}.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags   
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -   
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   Se non ne hai una disponibile, puoi creare una sottorete utilizzando il comando `ibmcloud is subnet-create`. Per ulteriori informazioni sulla creazione di una sottorete, vedi [IBM Cloud VPC CLI Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets).

5. Elenca i profili disponibili per la creazione della tua istanza.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
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

6. Elenca le immagini disponibili per la creazione della tua istanza.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags   
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -   
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. Elenca le chiavi SSH che puoi associare alla tua istanza.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output:
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -   
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   Se non ne hai una disponibile, puoi creare una chiave SSH utilizzando il comando `ibmcloud is key-create`. Puoi aggiungere le chiavi SSH alla tua istanza solo quando la crei inizialmente. Per ulteriori informazioni sulla gestione delle chiavi SSH, vedi [Gestione delle chiavi SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

## Creazione di un'istanza utilizzando la CLI
{: #creating-an-instance-using-the-cli}

Dopo che sei venuto a conoscenza di questi valori, utilizzali per eseguire il comando `instance-create`. In aggiunta alle informazioni che hai raccolto, devi specificare un nome per l'istanza. Il seguente esempio mostra il comando in azione (utilizzando una x generica e i valori 123 solo per gli scopi dell'esempio).  

Quando esegui il provisioning di un'istanza, viene automaticamente creato un volume di archiviazione blocchi di 100 GB come volume di avvio primario e viene collegato all'istanza. Il seguente esempio mostra come includere un volume secondario con il parametro `--volume-attach`. L'inclusione di un volume secondario è facoltativa.
{:note}

1. Crea una nuova istanza.
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

   Ad esempio, se stai creando un'istanza denominata _my-instance_ in _us-south-2_ e utilizzi il profilo _bc1-2x4_, il tuo comando `instance-create` sarà simile al seguente esempio:

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

   dove:
   - `INSTANCE_NAME` è _my-instance_
   - `VPC_ID` è _VPC_ID_
   - `ZONE_NAME` è _us-south-2_
   - `PROFILE_ID` è _bc1-2x4_
   - `SUBNET_ID` è _SUBNET_ID_
   - `IMAGE_ID` è _IMAGE_ID_
   - `KEY_IDS` è _KEY_ID1, KEY_ID2, ..._
   - `VOLUME_ATTACH_JSON` è la specifica di collegamento del volume in formato JSON, fornita nel comando o come un file. Per un esempio di un JSON di collegamento del volume per un volume di dati, vedi [File JSON del volume secondario di esempio](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json).

   Per questo esempio, vedrai le seguenti risposte. 
   
   La seguente risposta varierà in base a quali valori opzionali utilizzi.
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

   Lo stato visualizza pending finché non viene creata l'istanza.
   {: tip}

2. Quando lo stato viene modificato con *running*, verifica di poter visualizzare la nuova istanza.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Per questo esempio, vedrai le seguenti risposte.
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

3. Visualizza le interfacce di rete che sono state create per la tua nuova istanza.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Per questo esempio, vedrai le seguenti risposte.
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group   
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. Richiedi un indirizzo IP mobile da associare alla tua istanza.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   Per questo esempio, vedrai le seguenti risposte.
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

    Ricorda l'indirizzo (`Address`) IP mobile per dopo.  

Hai bisogno di ulteriore aiuto? Puoi sempre eseguire `ibmcloud is instance-create --help` per visualizzare la guida per la creazione di un'istanza.
{: tip}

Preferisci creare un'istanza utilizzando la console {{site.data.keyword.cloud_notm}}? Per ulteriori informazioni, vedi [Creazione di un'istanza](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
{: tip}

## Passi successivi
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

Dopo aver creato il server, puoi connetterti alla tua istanza. Per ulteriori informazioni, vedi [Connessione alla tua istanza Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) o [Connessione alla tua istanza Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).




