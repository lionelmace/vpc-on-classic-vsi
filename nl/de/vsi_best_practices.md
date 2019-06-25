---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Instanzen planen
{: #planning-for-instances}
[comment]: # (Verlinktes Hilfethema)


Wenn Sie {{site.data.keyword.vsi_is_full}} bereitstellen möchten, kann Sie die Konfigurationsprüfliste in diesem Abschnitt dabei unterstützen, Ihre Bereitstellung eines virtuellen Servers so optimal wie möglich zu nutzen.
{:shortdesc}

Stellen Sie vor Beginn sicher, dass Sie eine [{{site.data.keyword.vpc_short}} erstellt haben](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Bereitstellung von Instanzen planen
{: #planning-for-provisioning-instances}

Nachdem Ihnen eine {{site.data.keyword.vpc_short}} zur Verfügung steht, sollten Sie vor der Bereitstellung Ihrer Instanz die folgenden Punkte berücksichtigen.

|        Hinweise|
|-------------------|
|__ 1. Stellen Sie sicher, dass Ihr Konto die notwendigen [Benutzerberechtigungen](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions) besitzt. Falls Sie für eine {{site.data.keyword.vpc_short}}-Ressource als Bearbeiter oder Administrator berechtigt sind, übernehmen Sie ebenfalls die Berechtigung zum Erstellen, Löschen und Ändern von virtuellen Serverinstanzen innerhalb dieser virtuellen privaten Cloud.|
|__ 2. Überprüfen Sie Ihre [Kontolimits](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) für gleichzeitig aktive Instanzen. |
|__ 3. Stellen Sie sicher, dass Ihr [SSH-Schlüssel](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) verfügbar ist.
|__ 4. Ermitteln Sie, welcher Standort für die Instanz ausgewählt werden soll.|
|__ 5. Berücksichtigen Sie die gängigen [Profiloptionen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) aus vCPU/RAM-Kombinationen für Ihre Workload. Profile enthalten vorkonfigurierte Instanzen, die in Minutenschnelle einsatzbereit sind. Sie müssen unbedingt sicherstellen, dass Ihre Instanzen über die erforderlichen Ressourcen verfügen, damit Ihre Workloads und Ihre Umgebung betriebsbereit bleiben.|
|__ 6. Legen Sie fest, welches Betriebssystemimage Sie für Ihre Instanz auswählen wollen. Zur Auswahl steht der aktuelle Bestand von [Images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images). |
|__ 7. Vergeben Sie unbedingt einen eindeutigen Namen für die Instanz. Wenn  Sie ein Verfahren für die Benennung von virtuellen Serverinstanzen aufstellen, können diese später viel leichter gefiltert und gesucht werden. |

## Nächste Schritte
{: #next-create-instance}

Sobald Sie für den Einstieg bereit sind, können Sie sich in den folgenden Abschnitten über das Erstellen Ihrer Instanz informieren:
* [Instanz über die {{site.data.keyword.cloud_notm}}-Konsole erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Instanz über die CLI erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
