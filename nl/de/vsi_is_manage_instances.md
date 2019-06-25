---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Virtuelle Serverinstanzen verwalten
{: #managing-virtual-server-instances}
[comment]: # (Verlinktes Hilfethema)

Sie können Ihre {{site.data.keyword.vsi_is_full}}-Instanzen ausgehend von der Seite *Virtuelle Serverinstanzen* in der {{site.data.keyword.cloud_notm}}-Konsole anzeigen und verwalten.
{:shortdesc}

Führen Sie zum Verwalten Ihrer Instanzen die folgenden Schritte aus.
1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.cloud.ibm.com/vpc) zum **Menü ![Menüsymbol](../icons/icon_hamburger.svg) > VPC-Infrastruktur > Datenverarbeitung > Virtuelle Serverinstanzen**.
2. Auf dieser Seite können Sie Tasks für eine bestimmte Instanz verwalten oder auf eine Instanz klicken, um ihre Eigenschaften anzuzeigen und zu bearbeiten.

## Warmstart

Die Aktion 'Warmstart' schaltet eine Instanz sofort ab und anschließend wieder ein.

## Stoppen und starten

Die Aktion 'Stoppen und starten' aktiviert oder inaktiviert eine Instanz über Fernzugriff. Falls die Instanz gestoppt wird, verbleibt sie im Stoppstatus und muss manuell gestartet werden. Für einige Rechenressourcen wird die Abrechnung [ausgesetzt](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing), während die Instanz gestoppt ist. Die Interaktion mit einer gestoppten Instanz ist nicht möglich. Falls die Einheit gestartet wird, wird die normale Interaktion fortgesetzt.

## Löschen

Die Aktion 'Löschen' entfernt eine Instanz und die mit ihr verbundene vNIC, ihren Bootdatenträger und ihre Daten dauerhaft aus Ihrem Konto. Nachdem Sie die Löschaktion bestätigt haben, wird der Prozess zum Löschen der Instanz und der zugehörigen vNIC, des Bootdatenträgers und der Daten gestartet. Die Löschaktion kann bis zu 30 Minuten dauern. Sobald der Prozess jedoch abgeschlossen ist, wird die Instanz nicht mehr auf der Seite 'Virtuelle Serverinstanzen' angezeigt. Die variable IP-Adresse, die der virtuellen Serverinstanz zugeordnet war, ist nicht mehr zugeordnet, verbleibt jedoch in Ihrem Konto.

## Instanzdetails anzeigen
Zur Interaktion mit Instanzen können Sie die Übersicht über alle Instanzen auf der Seite *Virtuelle Serverinstanzen* anzeigen oder auf eine einzelne Instanz klicken, um Details anzuzeigen und Änderungen vorzunehmen. Ausgehend von der Seite mit den Instanzdetails können Sie außerdem die zugehörige Netzschnittstelle anzeigen, auf ihr Teilnetz zugreifen und eine variable IP-Adresse reservieren oder löschen.

Wenn Sie zur Verwaltung Ihrer Instanzen lieber die CLI verwenden möchten, lesen Sie den Abschnitt [Instanz über die CLI verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
{: tip}
