---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# Lernprogramm 'Einführung'
{: #getting-started}

Mit {{site.data.keyword.vsi_is_full}} (VPC) können Sie skalierbare Rechenressourcen in der IBM Cloud bereitstellen.
{:shortdesc}

Sie können so viele virtuelle Server wie benötigt erstellen, das Netz und die Sicherheit konfigurieren sowie den Speicher verwalten. Die gesamte hierzu benötigte Funktionalität ist in einer verbesserten IBM Cloud-Konsole verfügbar. Die Konsole ist so aufgebaut, dass Sie Ihre Umgebung schnell und ohne großen Aufwand an einen geänderten Workloadbedarf anpassen können. Machen Sie sich keine Sorgen über die ersten Schritte - es geht direkt los.

Stellen Sie vor Beginn sicher, dass Sie eine [IBM Cloud-VPC erstellt haben](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

{{site.data.keyword.vsi_is_short}} ist nicht mit den klassischen Angeboten für virtuelle Server kompatibel. Falls Sie eines der {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}}-Angebote in der klassischen Infrastruktur nutzen wollen, finden Sie unter [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial) weiterführende Informationen.
{:note}

<p>Anhand der folgenden Informationen können Sie Ihre Instanzen umgehend erstellen und verbinden.
<table>
   <CAPTION>Tabelle 1. Schritte für den Schnelleinstieg</CAPTION>
   <THEAD>
   <TR>
   <th>Task</th>
   <th>Details</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Zur Implementierung hilfreichen Inhalt prüfen</td>
   <td>Kennen Sie IBM Cloud und virtuelle Server noch nicht? Auf den folgenden Sites finden Sie Informationen, die Sie bei der Planung Ihrer Umgebung unterstützen.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">Was ist IBM Cloud?</a></li>
      <li><a href="https://ibm.com/cloud/get-started">Einführung in IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. Bei IBM Cloud registrieren</td>
   <td>Informationen zur Einrichtung Ihres IBM Cloud-Kontos finden Sie unter <a href="/docs/account?topic=account-signup#signup">Für IBM Cloud registrieren</a>.</td>
 <tr>
   <td>3. Workloadspezifikationen ermitteln</td>
   <td>Ermitteln Sie vor der Erstellung Ihrer Instanz, wie Sie die Instanz verwenden wollen und welche Instanzgröße für eine erfolgreiche Nutzung erforderlich ist. Wollen Sie sie beispielsweise für Entwicklung und Tests oder die Produktion verwenden? Wollen Sie die Funktionalität für den Benutzer testen, lange Algorithmen verarbeiten, Daten sichern und wiederherstellen oder die Latenzgeschwindigkeit erhöhen?</td>  
 <tr>
   <td>4. Größe und Preis der Instanz bestimmen</td>
   <td>Sobald es an die Erstellung Ihrer Instanzen geht, stehen Ihnen für die Produktfamilie die drei Optionen 'Ausgewogen', 'Datenverarbeitung' und 'Hauptspeicher' zur Auswahl. Die Produktfamilien enthalten als so genannte 'Profile' vorkonfigurierte Instanzen, die die Anforderungen der meisten Kunden erfüllen und in weniger als fünf Minuten für die Konfiguration vorbereitet werden können.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Ausgewogen</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Datenverarbeitung</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Hauptspeicher</a></li>
     </ul>
  <p>Im Abschnitt [Preisstruktur](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) finden Sie Informationen, die Ihnen bei der Größen- und Preisbestimmung für Ihre Instanz helfen.</p></td>
 <tr>
   <td>5. Beim IBM Cloud-Konto anmelden</td>
   <td>Greifen Sie im <a href="https://console.bluemix.net/catalog/">IBM Cloud-Katalog</a> auf das Bestellformular für {{site.data.keyword.vsi_is_short}} zu. Sie benötigen <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started"> eine IBMid und ein Kennwort</a>.
   </td>
 <tr>
   <td>6. Zugriff auf {{site.data.keyword.vpc_short}} anfordern</td>
   <td>Falls Sie den Zugriff auf {{site.data.keyword.vpc_short}} noch nicht angefordert haben, müssen Sie in diesem Schritt den Zugriff anfordern.</td>
<tr>
<td>7. SSH-Schlüssel generieren</td>
<td> Anweisungen finden Sie unter [SSH-Schlüssel](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</td>
<tr>
<td>8. Instanz planen</td>
<td> Weitere Informationen, die Sie bei der Planung, Bereitstellung und Konfiguration Ihrer Ressourcen unterstützen, finden Sie unter [Instanzen planen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances).</td>
<tr>
<td>9. Instanz erstellen</td>
<td>
<p>
Im Abschnitt [Instanz erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers) können Sie sich darüber informieren, wie Sie mit der Erstellung einer Instanz beginnen.
</td>  
<tr>
<td>10. Verbindung zu Ihrer Instanz herstellen</td>
<td>Ihre Instanz ist jetzt einsatzbereit! Mithilfe der Informationen in den folgenden Abschnitten unter *Verbindung herstellen* können Sie prüfen, ob die Instanz erfolgreich erstellt wurde.
   <ul>
   <li>[Verbindung zu Ihrer Linux-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Verbindung zu Ihrer Windows-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. Instanz bereinigen</td>
<td>Wenn Sie Ihre Instanz nicht mehr benötigen, können Sie sie löschen. </td>
</tr>
</TBODY>
</table>
</p>

## Nächste Schritte
Nachdem Ihre Instanz bereitgestellt worden ist, können Sie sich damit beschäftigen, welche Möglichkeiten sie Ihnen bietet.
* [Instanz verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [Berechtigungen für{{site.data.keyword.vsi_is_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Sicherheit in Ihrer IBM Cloud-VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* Weitere Informationen zu [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
