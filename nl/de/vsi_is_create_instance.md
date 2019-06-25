---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

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

# Virtuelle Serverinstanzen erstellen
{: #creating-virtual-servers}
[comment]: # (Verlinktes Hilfethema)

Sie können {{site.data.keyword.vsi_is_full}} ausgehend von der Seite *Virtuelle Serverinstanzen* in der {{site.data.keyword.cloud_notm}}-Konsole erstellen.
{:shortdesc}

Stellen Sie vor Beginn sicher, dass Sie eine [IBM Cloud-VPC erstellt haben](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

Wählen Sie zum Erstellen einer Instanz die folgenden Instanzdetails aus.
1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.cloud.ibm.com/vpc) zum **Menü ![Menüsymbol](../icons/icon_hamburger.svg) > VPC-Infrastruktur > Datenverarbeitung > Virtuelle Serverinstanzen**.
2. Klicken Sie auf **Neue Instanz** und geben Sie die folgenden Informationen ein:

    <table>
    <CAPTION>Tabelle 1. Optionen für die Instanzbereitstellung</CAPTION>
    <THEAD>
    <TR>
    <th>Feld</th>
    <th>Wert</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Name </td>
    <td>Für Ihre virtuelle Serverinstanz ist ein Name erforderlich.</td>
    </tr>
    <tr>
    <td>Virtuelle private Cloud</td>
    <td>Geben Sie die IBM Cloud-VPC an, in der Sie Ihre Instanz erstellen wollen.</td>
    </tr>
    <tr>
    <td>Standort</td>
    <td>Standorte setzen sich aus Regionen (also bestimmten geografischen Gebieten) und Zonen (dies sind fehlertolerante Rechenzentren in einer Region) zusammen. Wählen Sie den Standort aus, an dem Ihre virtuelle Serverinstanz erstellt werden soll.</td>
    </tr>
    <tr>
    <td>Profil</td>
    <td><p>
    Treffen Sie eine Auswahl unter den gängigen Profilen oder unter allen verfügbaren Kombinationen aus vCPU und RAM. Die folgenden Familien werden unterstützt:
    <ul>
    <li>Ausgewogen</li>
    <li>Datenverarbeitung</li>
    <li>Hauptspeicher</li>
    </ul>
    </p>
    <p>Jeder physische Kern auf dem Server ist mit Hyper-Thread-Funktionalität ausgestattet und wird als zwei virtuelle CPUs (vCPUs) dargestellt. Das Angebot für virtuelle Server bietet 2,0 GHz oder mehr pro vCPU mit bis zu 48 auf einem einzigen virtuellen Server verfügbaren vCPUs.</p>

    <p>In Bezug auf den Hauptspeicher kann eine Instanz bis zu 256 GB voll dedizierten RAM besitzen.</p>
    <p><note>Hinweis: Die Maximalwerte variieren je nach Familie.</note></p>
    <p>Weitere Informationen finden Sie unter [Profile](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).</p>
    </td>
    </tr>
    <tr>
    <td>Image</td>
    <td><p>Alle Images verwenden Cloud-init, was Ihnen die Eingabe von Benutzermetadaten ermöglicht, die der Instanz für Scripts nach der Bereitstellung zugeordnet werden.</p>
    <p>Weitere Informationen finden Sie unter [Images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images).</p>
    </td>
    </tr>
    <td>SSH-Schlüssel</td>
    <td>
    <p>Sie müssen einen vorhandenen SSH-Schlüssel auswählen oder einen neuen zu verwendenden SSH-Schlüssel hochladen, bevor Sie die Instanz erstellen können. Mithilfe von SSH-Schlüsseln wird eine sichere Verbindung zur Instanz hergestellt, nachdem ihre Ausführung begonnen hat. SSH-Schlüssel können zu Ihrer Instanz nur bei ihrer erstmaligen Erstellung hinzugefügt werden.</p>
    <p>Hinweis: Alphanumerische Kombinationen sind auf 100 Zeichen begrenzt.</p>
    <p>Weitere Informationen finden Sie unter [SSH-Schlüssel](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</p></td>
    </tr>
    <tr>
    <td>Benutzerdaten</td>
    <td>
    <p>Sie können Benutzerdaten hinzufügen, die automatisch allgemeine Konfigurationstasks oder Scripts ausführen. <p>Weitere Informationen finden Sie unter [Benutzerdaten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).</p>
    </td>
    </tr>
    <tr>
    <td>Bootdatenträger</td>
    <td><p>Die Standardgröße des Bootdatenträgers beträgt bei allen Profilen 100 GB. Der Bootdatenträger beinhaltet standardmäßig eine providerverwaltete Verschlüsselung. Falls Sie die kundenverwaltete Verschlüsselung verwenden wollen, können Sie die Details des Bootdatenträgers bearbeiten. Weitere Informationen finden Sie unter [Speicher](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage).</p>
    </td>
    </tr>
    <tr>
    <td>Zugeordneter Blockspeicherdatenträger</td>
    <td><p>Bei der Bereitstellung der Instanz können Sie einen oder mehrere einzubeziehende sekundäre Datendatenträger hinzufügen. Klicken Sie zum Hinzufügen von Datenträgern auf **Neuer Blockspeicherdatenträger**. Weitere Informationen finden Sie unter [Blockspeicherdatenträger erstellen](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).</p>
    </td>
    </tr>
    <tr>
    <td>Netzschnittstellen</td>
    <td>Weisen Sie Netzbetrieboptionen für Verbindungen in der IBM Cloud-VPC zu. Sie können für jede Instanz bis zu 5 Netzschnittstellenkarten erstellen und zuweisen. Weitere Informationen finden Sie unter [Mehrere IP-Adressen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options).</td>
    </tr>
    </TBODY>
    </table>

    Ihre *Kostenübersicht* wird rechts auf der Seite *Neue virtuelle Serverinstanz* angezeigt.

3. Klicken Sie auf **Virtuelle Serverinstanz erstellen**, wenn Sie zur Durchführung der Bereitstellung bereit sind. An Ihren Administrator werden eine Reihe von E-Mails (Auftragsbestätigung für die virtuelle Serverinstanz, Auftragsgenehmigung und Auftragsbearbeitung) sowie die Nachricht gesendet, dass die Instanz erstellt wurde.

Möchten Sie zum Erstellen einer Instanz lieber die CLI verwenden? Weitere Informationen finden Sie im Abschnitt [Instanz über die CLI erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli).
{: tip}

## Variable IP-Adresse reservieren
{: #reserving-a-floating-ip-address}

Sie können eine variable IP-Adresse reservieren und Ihrer Instanz zuordnen, damit Sie von einer Internetadresse aus eine Verbindung zur Instanz herstellen können.

Ihre Instanz muss aktiv sein, damit Sie eine variable IP-Adresse zuordnen können. Es kann einige Minuten dauern, bis die Instanz betriebsbereit ist.
{: note} 

Gehen Sie wie folgt vor, um eine variable IP-Adresse zu reservieren und zuzuordnen:
1. Klicken Sie auf der Seite **Virtuelle Serverinstanzen** auf Ihre Instanz, um deren Details anzuzeigen.
2. Klicken Sie im Abschnitt **Netzschnittstellen** auf **Reservieren +**, um Ihrer Instanz eine variable IP-Adresse zuzuordnen.

## Nächste Schritte
{: #next-connecting-to-instance}

Sie können nun eine Verbindung zu Ihrer Instanz herstellen. Weitere Informationen enthält der Abschnitt [Verbindung zu Ihrer Linux-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) bzw. [Verbindung zu Ihrer Windows-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).
