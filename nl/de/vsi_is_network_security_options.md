---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Netzbetrieb und Sicherheit bei virtuellen Servern
{: #network-security-options}

Wenn Sie {{site.data.keyword.vsi_is_full}} implementieren, haben Sie Zugriff auf die neuesten Funktionen für Netzbetrieb und Sicherheit.  
{:shortdesc}

## Instanz-vNICs verwenden
{: #using-instance-vnics}

Eine virtuelle Netzschnittstellenkarte (vNIC) wird verwendet, um einen virtuellen Server mit einem Netz zu verbinden. Wenn Sie eine VSI-Instanz erstellen, können Sie mithilfe einer vNIC mehrere IP-Adressen zuordnen. Die folgende Liste vermittelt Ihnen einen Überblick darüber, wie vNICs mit Ihrer Instanz zusammenarbeiten.

* Sie können für jede Instanz bis zu 5 vNICs erstellen und zuweisen. Jeder vNIC wird eine private IP-Adresse aus dem verbundenen Teilnetz zugewiesen; optional können Sie eine variable IP-Adresse und Sicherheitsgruppen zuordnen.
* Sie können jede vNIC einem Teilnetz in derselben Zone zuordnen.
* Jede vNIC erhält eine private IP-Adresse aus dem Teilnetzbereich.
* Sie können jeder vNIC variable IP-Adressen zuordnen bzw. deren Zuordnung zu einer vNIC aufheben.
* Sie können jeder vNIC Sicherheitsgruppen zuordnen.
* Sie können den Namen einer vorhandenen vNIC ändern.

Die Bandbreite ist der Instanz selbst zugeordnet und stellt keinen konfigurierbaren Aspekt einer einzelnen vNIC dar. Die Standardbandbreite für eine Instanz beträgt 100 MB/s, mit der Option eines Upgrades auf 1 GB/s.

## Optionen für den Netzbetrieb
{: #networking-options}

Weitere Informationen zu den allgemeinen Netzfunktionen in der {{site.data.keyword.vpc_short}}-Umgebung finden Sie im Abschnitt [Informationen zum Netzbetrieb für VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc).

## Optionen für die Sicherheit
{: #security-options}

{{site.data.keyword.vsi_is_short}} enthält integrierte Sicherheitsoptionen:
* Zugriffssteuerungslisten (Access Control Lists, ACLs) können den Datenverkehr in ein und aus einem Teilnetz begrenzen.
* Sicherheitsgruppen fungieren als virtuelle Firewall für virtuelle Serverinstanzen.
* SSH-Schlüssel auf Ihrer virtuellen Serverinstanz authentifizieren einen sicheren Kanal für die Netzkommunikation.

Weitere Informationen zu diesen Sicherheitsoptionen enthalten die Abschnitte [Sicherheit in Ihrer IBM Cloud-VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) und [SSH-Schlüssel verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
