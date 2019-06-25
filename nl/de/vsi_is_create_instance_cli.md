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

# Virtuelle Serverinstanzen erstellen (CLI)
{: #creating-virtual-servers-cli}

Sie können {{site.data.keyword.vsi_is_full}} -Instanzen über die CLI (Command Line Interface, Befehlszeilenschnittstelle) erstellen.
{:shortdesc}

## Vorbereitende Schritte
{: #prereq-creating-virtual-servers-cli}

1. Stellen Sie sicher, dass Sie die folgenden CLI-Plug-ins heruntergeladen, installiert und initialisiert haben:
    * {{site.data.keyword.cloud_notm}}-CLI
    * Plug-in 'vpc-infrastructure'

   Weitere Angaben enthalten die [Referenzinformationen zur IBM Cloud-CLI für VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Bei der erstmaligen Installation des Plug-ins 'vpc-infrastructure' müssen Sie die Zielgenerierung auf 'gen 1' setzen (`ibmcloud is target --gen 1`).
   {:important}
   
   
2. Stellen Sie sicher, dass Sie bereits [eine {{site.data.keyword.vpc_short}} erstellt haben](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Informationen zur Erstellung einer Instanz über die CLI zusammenstellen
{: #gathering-information-to-create-an-instance-using-the-cli}

Sind Sie zum Erstellen einer Instanz bereit? Bevor Sie den Befehl `ibmcloud is instances` ausführen können, müssen Sie die Details über die Instanz kennen, beispielsweise welches Profil oder welches Image Sie verwenden möchten.

Sie sollten daher zunächst die folgenden Informationen zusammenstellen:

|    Instanzdetails   |  Liste der Optionen                |  Ihre Werte                             |
| --------------------- | --------------------------------|---------------------------------------------- |
| Image                 | `ibmcloud is images`            |                           |
| Profil               | `ibmcloud is instance-profiles` |                           |
| Schlüssel                   | `ibmcloud is keys`              |                           |
| VPC                   | `ibmcloud is vpcs`              |                           |
| Teilnetz                | `ibmcloud is subnets`           |                           |
| Zone                  | `ibmcloud is zones`             |                           |   
{: caption="Tabelle 1. Erforderliche Instanzdetails" caption-side="top"}   

Verwenden Sie die folgenden Befehle, um die erforderlichen Informationen zum Erstellen einer neuen Instanz zu ermitteln.

1. Listen Sie die Regionen auf, die Ihrem Konto zugeordnet sind.
   ```
   $ ibmcloud is regions
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
   ```
   Name       Endpoint               Status
   us-south   /v1/regions/us-south   available
   ```
   {:screen}

2. Listen Sie die Zonen auf, die der gewünschten Region zugeordnet sind.
   ```
   $ ibmcloud is zones us-south
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
   ```
   Name         Region     Status
   us-south-2   us-south   available
   ```
   {:screen}

3. Listen Sie die {{site.data.keyword.vpc_short}}s auf, die Ihrem Konto zugeordnet sind.
   ```
   $ ibmcloud is vpcs
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
   ```
   ID                                     Name                                  Default   Created       Status      Tags
   xxx1xx23-4xx5-6789-12x3-456xx7xx123x   my-vpc                                yes       1 month ago   available   -
   xxxx1234-5678-9x12-x34x-567x8912x3xx   my-other-vpc                          no        4 days ago    available   -   
   ```
   {:screen}

   Wenn keine {{site.data.keyword.vpc_short}} verfügbar ist, können Sie mit dem Befehl `ibmcloud is vpc-create` eine VPC erstellen. Weitere Angaben über das Erstellen einer {{site.data.keyword.vpc_short}} finden Sie in den [Referenzinformationen zur CLI für IBM Cloud- VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#vpc-create).

4. Listen Sie die Teilnetze auf, die der {{site.data.keyword.vpc_short}} zugeordnet sind.
   ```
   $ ibmcloud is subnets
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
   ```
   ID                                     Name                                     IPv*   Subnet CIDR         Addresses   Gen   ACL   Gateway   Created       Status      VPC                        Zone         Resource Group   Tags
   1234x12x-345x-1x23-45x6-x7x891011x1x   my-subnet                                ipv4   192.16.1.0/24       0/0         -     -     -         1 week ago    available   my-vpc(xxx1xx23-.)         us-south-2   -                -
   12xx345x-6789-1xxx-x2x3-x4x56xx78x9x   my-subnet-2                              ipv4   192.20.28.0/24      0/0         -     -     -         1 day ago     available   my-vpc(xxx1xx23-.)         us-south-2   -                -
   1x2x3xx4-xx56-7891-234x-xx5678x9x123   my-other-subnet                          ipv4   192.168.88.0/24     0/0         -     -     -         1 day ago     available   my-other-vpc(xxxx1234-.)   us-south-2   -                -   
   ```
   {:screen}

   Falls kein Teilnetz verfügbar ist, können Sie mit dem Befehl `ibmcloud is subnet-create` ein Teilnetz erstellen. Weitere Angaben über die Erstellung eines Teilnetzes enthalten die [Referenzinformationen zur CLI für IBM Cloud-VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#subnets).

5. Listen Sie die verfügbaren Profile zum Erstellen der Instanz auf.
   ```
   $ ibmcloud is instance-profiles
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
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

6. Listen Sie die verfügbaren Images zum Erstellen der Instanz auf.
   ```
   $ ibmcloud is images   
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
   ```
   ID                                     Name                 OS                                                       Arch    Created       Status   Visibility   Tags
   cc8debe0-1b30-6e37-2e13-744bfb2a0c11   centos-7.x-amd64     CentOS (7.x - Minimal Install)                           amd64   9 hours ago   READY    public       -
   7eb4e35b-4257-56f8-d7da-326d85452591   ubuntu-16.04-amd64   Ubuntu Linux (16.04 LTS Xenial Xerus Minimal Install)    amd64   9 hours ago   READY    public       -   
   ```
   {:screen}

7. Listen Sie die verfügbaren SSH-Schlüssel auf, die Sie Ihrer Instanz zuordnen können.
   ```
   $ ibmcloud is keys
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
   ```
   ID                                     Name           Type   Length   FingerPrint          Created        Resource Group   Tags
   1234xxxx-x12x-xxxx-34xx-xx1234xxxxxx   my-key         RSA    2048     PHcP/zyw/PNGIe/u..   5 days ago     -                -
   12xx3456-x78x-9123-4x56-78xx9xxx1x2x   my-other-key   RSA    2048     +rvkRMBhdFmz1dlT..   2 days ago     -                -    
   ```
   {:screen}

   Falls kein SSH-Schlüssel verfügbar ist, können Sie mit dem Befehl `ibmcloud is key-create` einen SSH-Schlüssel erstellen. SSH-Schlüssel können zu Ihrer Instanz nur bei ihrer erstmaligen Erstellung hinzugefügt werden. Weitere Informationen zum Verwalten von SSH-Schlüsseln finden Sie im Abschnitt [SSH-Schlüssel verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

## Instanz über die CLI erstellen
{: #creating-an-instance-using-the-cli}

Nachdem Sie diese Werte ermittelt haben, verwenden Sie sie zur Ausführung des Befehls `instance-create`. Neben den von Ihnen zusammengestellten Informationen müssen Sie einen Namen für die Instanz angeben. Das folgende Beispiel zeigt die Ausführung des Befehls (mit Verwendung der generischen Werte x und 123 ausschließlich zu Beispielzwecken).  

Wenn Sie eine Instanz bereitstellen, wird automatisch ein 100 GB-Blockspeicherdatenträger als primärer Bootdatenträger erstellt und der Instanz zugeordnet. Das folgende Beispiel zeigt, wie ein sekundärer Datenträger mit dem Parameter `--volume-attach` einbezogen wird. Die Einbeziehung eines sekundären Datenträgers ist optional.
{:note}

1. Erstellen Sie eine neue Instanz.
   ```
   $ ibmcloud is instance-create \
       <INSTANZNAME> \
       <VPC-ID> \
       <ZONENNAME> \
       <PROFIL-ID> \
       <TEILNETZ-ID> \
       --image <IMAGE-ID> \
       --keys <SCHLÜSSEL-IDS>
       --volume-attach <JSON-CODE_oder_JSON-DATEI_FÜR_DATENTRÄGERZUORDNUNG>
   ```
   {:codeblock}

   Falls Sie beispielsweise eine Instanz namens _my-instance_ in _us-south-2_ erstellen und das Profil _bc1-2x4_ verwenden, hat Ihr Befehl `instance-create` Ähnlichkeit mit dem folgenden Beispiel:

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

   Hierbei gilt Folgendes:
   - `INSTANZNAME` ist _my-instance_
   - `VPC-ID` ist _VPC_ID_
   - `ZONENNAME` ist _us-south-2_
   - `PROFIL-ID` ist _bc1-2x4_
   - `TEILNETZ-ID` ist _SUBNET_ID_
   - `IMAGE-ID` ist _IMAGE_ID_
   - `SCHLÜSSEL-IDS` ist _KEY_ID1, KEY_ID2, ..._
   - `JSON-DATEI_FÜR_DATENTRÄGERZUORDNUNG` ist die Datenträgerzuordnungsspezifikation im JSON-Format, die im Befehl oder als Datei angegeben ist. Ein Beispiel für eine JSON-Datenträgerzuordnung für einen Datendatenträger finden Sie unter [JSON-Beispieldatei für sekundären Datenträger](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#secondary-volume-byok-json).

   Bei diesem Beispiel werden die folgenden Antworten angezeigt. 
   
   Die nachstehenden Antworten variieren abhängig von den verwendeten optionalen Werten.
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

   Als Status wird 'pending' (= anstehend) angezeigt, bis die Instanz erstellt worden ist.
   {: tip}

2. Sobald sich der Status in *running* (= aktiv) ändert, prüfen Sie, ob Ihre neue Instanz angezeigt wird.

   ```
   $ ibmcloud is instance 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Bei diesem Beispiel werden die folgenden Antworten angezeigt.
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

3. Zeigen Sie die Netzschnittstellen an, die für Ihre neue Instanz erstellt wurden.
   ```
   $ ibmcloud is instance-network-interfaces 2x12xxx5-xx11-1234-x4x5-1xxx12345678
   ```
   {:codeblock}

   Bei diesem Beispiel werden die folgenden Antworten angezeigt.
   ```
   ID                                     Name                                            Type       Subnet CIDR                    Primary Address   Speed   SecAddr   SecGrps   FloatIPs   Created          Status   Resource Group
   xx12x345-6xxx-7x89-123x-4x5xxx678x9x   great-scott-stride-lilac-captivate-filtrate                my-subnet(1234x12x-.)          192.0.2.25        100     -         -         {...}      10 seconds ago   -   
   ```
   {:screen}

4. Fordern Sie eine variable IP-Adresse für die Zuordnung zu Ihrer Instanz an.

   ```
   $ ibmcloud is floating-ip-reserve \
       my-floatingip \
       --nic xx12x345-6xxx-7x89-123x-4x5xxx678x9x
   ```
   {:codeblock}

   Bei diesem Beispiel werden die folgenden Antworten angezeigt.
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

    Merken Sie sich die `variable IP-Adresse` für später.  

Benötigen Sie weitere Unterstützung? Mit dem Befehl `ibmcloud is instance-create --help` können Sie jederzeit den Hilfetext für die Erstellung einer Instanz anzeigen.
{: tip}

Möchten Sie zum Erstellen einer Instanz lieber die {{site.data.keyword.cloud_notm}}-Konsole verwenden? Weitere Informationen finden Sie in diesem Fall unter [Instanz erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
{: tip}

## Nächste Schritte
{: #next-cli-connecting-to-instance}

<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

Nachdem der Server erstellt wurde, können Sie eine Verbindung zu Ihrer Instanz herstellen. Weitere Informationen enthält der Abschnitt [Verbindung zu Ihrer Linux-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) bzw. [Verbindung zu Ihrer Windows-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).




