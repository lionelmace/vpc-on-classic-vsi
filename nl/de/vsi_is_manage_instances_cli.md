---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Virtuelle Serverinstanzen verwalten (CLI)
{: #managing-virtual-servers-cli}

Sie können {{site.data.keyword.vsi_is_full}}-Instanzen über die CLI (Command Line Interface, Befehlszeilenschnittstelle) verwalten.
{:shortdesc}

## Vorbereitende Schritte
{: #prereq-managing-instances}

1. Stellen Sie sicher, dass Sie die folgenden CLI-Plug-ins heruntergeladen, installiert und initialisiert haben:
    * {{site.data.keyword.cloud_notm}}-CLI
    * Plug-in 'infrastructure-service'

   Weitere Angaben enthalten die [Referenzinformationen zur IBM Cloud-CLI für VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Bei der erstmaligen Installation des Plug-ins 'vpc-infrastructure' müssen Sie die Zielgenerierung auf 'gen 1' setzen (`ibmcloud is target --gen 1`).
   {:important}
   
2. Stellen Sie sicher, dass Sie bereits [eine {{site.data.keyword.vpc_short}} erstellt haben](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Instanzenaktionen anzeigen
{: #viewing-instance-actions}

Führen Sie den folgenden Befehl aus, um die Verwaltungsaktionen anzuzeigen, die für Ihre Instanz ausgeführt werden:

```
ibmcloud is instance-actions <server-id>
```
{:codeblock}

Es wird eine Liste angezeigt, die Ähnlichkeit mit der folgenden Ausgabe hat:

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## Instanzen verwalten
{: #managing-your-instances}

Benötigen Sie etwas Unterstützung? Mit dem Befehl `ibmcloud is help` können Sie jederzeit die verfügbaren Befehle anzeigen.

### Zurücksetzen  

```
ibmcloud is instance-reset
```
{:codeblock}

Die Instanz wird aus- und dann wieder eingeschaltet.  

### Neustart

```
ibmcloud is instance-reboot
```
{:codeblock}

Das Betriebssystem der Instanz wird erneut gestartet.  

### Stoppen und starten

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

Wenn die Einheit gestoppt wurde, verbleibt sie im Stoppstatus und muss manuell gestartet werden. Die Interaktion mit einer gestoppten Instanz ist nicht möglich. Falls die Einheit gestartet wird, wird die normale Interaktion fortgesetzt. 

### Aktualisieren

```
ibmcloud is instance-update
```
{:codeblock}

Nachdem die Einheit umbenannt wurde, wird der Name automatisch aktualisiert. Verwenden Sie den neuen Instanznamen beim Durchführen einer Suche, wenn Sie versuchen, mit der Instanz verbundenen Inhalt zu ermitteln. 

### Löschen

```
ibmcloud is instance-delete
```
{:codeblock}

Nachdem Sie die Löschaktion bestätigt haben, wird der Prozess zum Löschen der Instanz und der zugehörigen vNIC, des Bootdatenträgers und der Daten gestartet. Die Löschaktion kann mehrere Minuten dauern. Sobald der Prozess jedoch abgeschlossen ist, wird die Instanz nicht mehr auf der Seite 'Virtuelle Serverinstanzen' angezeigt. Die variable IP-Adresse, die der virtuellen Serverinstanz zugeordnet war, ist nicht mehr zugeordnet, verbleibt jedoch in Ihrem Konto.

Wenn Sie zur Verwaltung Ihrer Instanzen lieber die {{site.data.keyword.cloud}}-Konsole verwenden möchten, lesen Sie den Abschnitt [Instanz verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).
{: tip}
