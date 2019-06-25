---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Profile
{: #profiles}

Bei der Bereitstellung von {{site.data.keyword.vsi_is_full}} stehen drei Profilfamilien namens 'Ausgewogen', 'Datenverarbeitung' und 'Hauptspeicher' zur Auswahl. Ein Profil ist eine Kombination aus vCPU und RAM, die schnell instanziiert werden kann, um eine virtuelle Serverinstanz zu starten. In der {{site.data.keyword.Bluemix_notm}}-Konsole können Sie eine Auswahl unter gängigen Profilkonfigurationen oder in einer Liste von Profilen treffen, die für Ihre Anforderungen die beste Lösung darstellen.
{: shortdesc}

Die folgenden Familien sind verfügbar:

| Familien | Beschreibung |
| -------- | ----------- |
| [Ausgewogen](#balanced) | Diese Familie ist am besten für Cloud-Workloads geeignet, die ein ausgeglichenes Verhältnis von Leistung und Skalierbarkeit benötigen. Die Profile der Familie 'Ausgewogen' (mit NAS) bieten eine höhere Leistung, da Ressourcen nicht übersubskribiert sind. |
| [Datenverarbeitung](#compute)  | Diese Familie eignet sich am besten für Workloads mit mittlerem bis hohem Webdatenverkehr. Profile der Familie 'Datenverarbeitung' sind optimal für Workloads mit intensivem CPU-Bedarf, beispielsweise Workloads mit hohem Webdatenverkehr, Produktionsstapelverarbeitung und Front-End-Web-Server. |
| [Hauptspeicher](#memory) | Diese Familie ist für Workloads mit Cacheverarbeitung und Echtzeitanalyse die beste Wahl. Profile der Familie 'Hauptspeicher' eignen sich optimal für speicherintensive Workloads wie Workloads mit umfangreicher Cachenutzung, intensive Datenbankanwendungen oder speicherinterne Analyseworkloads. |
{: caption="Tabelle 1. Auswahlmöglichkeiten für Familie des virtuellen Servers" caption-side="top"}

## Ausgewogen
{: #balanced}

Die Profile der Familie 'Ausgewogen' bieten eine höhere Leistung, da Ressourcen nicht übersubskribiert sind. Die Netzleistung reicht vom Standard- bis zum Premiumniveau.

Das Angebot ist in den folgenden Profilen verfügbar:

| Profil | vCPU | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="Tabelle 2. Optionen des Profils 'Ausgewogen' für virtuelle Server" caption-side="top"}

**Hinweise zum Speicher:**

* Wenn Sie eine Instanz bereitstellen, wird automatisch ein primärer SAN-Bootdatenträger (100 GB) erstellt und zugeordnet.
* Optional können Sie einen sekundären Datendatenträger erstellen. Datenträgerprofile sind als drei vordefinierte IOPS-Schichten oder als angepasste IOPS verfügbar. Ein [Universalschichtprofil mit 3 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) bietet eine IOPS/GB-Leistung, die für ein VSI-Profil des Typs 'Ausgewogen' geeignet ist.
* Die Preisstruktur für öffentliche virtuelle Server mit Verwendung von SAN-Speicher umfasst die virtuelle CPU, den Hauptspeicher und den primären Bootdatenträger. Sekundäre Datendatenträger werden separat berechnet.

Bei diesem Angebot sind alle unterstützten Betriebssysteme (wie CentOS, Debian, Ubuntu und Windows) verfügbar.

## Datenverarbeitung
{: #compute}

Profile der Familie 'Datenverarbeitung' sind optimal für Workloads mit intensivem CPU-Bedarf, beispielsweise Workloads mit hohem Webdatenverkehr, Produktionsstapelverarbeitung und Front-End-Web-Server.

Das Angebot ist in den folgenden Profilen verfügbar:

| Profil | vCPU | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="Tabelle 3. Optionen des Profils 'Datenverarbeitung' für virtuelle Server" caption-side="top"}

**Hinweise zum Speicher:** 

* Wenn Sie eine Instanz bereitstellen, wird automatisch ein primärer SAN-Bootdatenträger (100 GB) erstellt und zugeordnet.
* Optional können Sie einen sekundären Datendatenträger erstellen. Datenträgerprofile sind als drei vordefinierte IOPS-Schichten oder als angepasste IOPS verfügbar. Ein  Profil mit [5-IOPS-Schichten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) bietet eine IOPS/GB-Leistung, die für ein VSI-Profil des Typs 'Datenverarbeitung' geeignet ist.
* Die Preisstruktur für öffentliche virtuelle Server mit Verwendung von SAN-Speicher umfasst die virtuelle CPU, den Hauptspeicher und den primären Bootdatenträger. Sekundäre Datendatenträger werden separat berechnet.

Bei diesem Angebot sind alle unterstützten Betriebssysteme (wie CentOS, Debian, Ubuntu und Windows) verfügbar. 

## Hauptspeicher 
{: #memory}

Profile der Familie 'Hauptspeicher' eignen sich optimal für speicherintensive Workloads wie Workloads mit umfangreicher Cachenutzung, intensive Datenbankanwendungen oder speicherinterne Analyseworkloads.

Das Angebot ist in den folgenden Profilen verfügbar:

| Profil | vCPU | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="Tabelle 4. Optionen des Profils 'Hauptspeicher' für virtuelle Serverinstanzen" caption-side="top"}

**Hinweise zum Speicher:** 

* Wenn Sie eine Instanz bereitstellen, wird automatisch ein primärer SAN-Bootdatenträger (100 GB) erstellt und zugeordnet.
* Optional können Sie einen sekundären Datendatenträger erstellen. Datenträgerprofile sind als drei vordefinierte IOPS-Schichten oder als angepasste IOPS verfügbar. Ein  Profil mit [10-IOPS-Schichten](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) bietet eine IOPS/GB-Leistung, die für ein VSI-Profil des Typs 'Hauptspeicher' geeignet ist.
* Die Preisstruktur für öffentliche virtuelle Server mit Verwendung von SAN-Speicher umfasst die virtuelle CPU, den Hauptspeicher und den primären Bootdatenträger. Sekundäre Datendatenträger werden separat berechnet.

Bei diesem Angebot sind alle unterstützten Betriebssysteme (wie CentOS, Debian, Ubuntu und Windows) verfügbar. 

## Profilkonfigurationen anzeigen
{: #popularprofiles}

Sie können die verfügbaren Profilkonfigurationen mit der {{site.data.keyword.cloud_notm}}-Konsole oder der CLI (Command Line Interface, Befehlszeilenschnittstelle) anzeigen. In der {{site.data.keyword.cloud_notm}}-Konsole können Sie eine Auswahl unter gängigen Profilkonfigurationen treffen, von denen die meisten Anwendungsfälle unterstützt werden.

### IBM Cloud-Konsole verwenden
1. Navigieren Sie in der {{site.data.keyword.cloud_notm}}-Konsole zum **Menü ![Menüsymbol](../icons/icon_hamburger.svg) > VPC-Infrastruktur > Datenverarbeitung > Virtuelle Serverinstanzen**.
2. Klicken Sie auf dieser Seite auf **Neue Instanz**.
3. Sie können entweder in der Liste **Gängige Profile** eine Auswahl treffen oder auf **Alle Profile** klicken, um zusätzliche Konfigurationen anzuzeigen.

### CLI verwenden
Führen Sie zum Anzeigen der Liste mit verfügbaren Profilen in der CLI den folgenden Befehl aus:
```
$ ibmcloud is instance-profiles
```
{:codeblock}

Die folgenden Informationen beschreiben, was die Ausgabe darstellt, wenn Sie die Befehlszeile verwenden. Die Profilgrößen weisen unterschiedliche Verhältnisse von CPU und Speicher auf, die für verschiedene Workloads  konzipiert sind:

*  'b' (balanced) steht für 'Ausgewogen' und ein Verhältnis von 1:2 oder 1:4.
*  'c' (compute) steht für 'Datenverarbeitung (mit einem höheren Anteil an CPUs) und ein Verhältnis von 1:1.
*  'm' (memory) steht für 'Hauptspeicher' (mit einem höheren Anteil an Hauptspeicher) und ein Verhältnis von 1:8.
