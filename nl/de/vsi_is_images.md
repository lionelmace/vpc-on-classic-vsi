---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Images
{: #images}

Bei der Bereitstellung von {{site.data.keyword.vsi_is_full}} können Sie eines der unterstützten Bestandsimages auswählen. Das von Ihnen ausgewählte Image bestimmt das Betriebssystem, das für Ihre Instanz bereitgestellt wird. 
{:shortdesc}

## Bestandsimages
{: #stock-images}

Die folgenden Betriebssysteme sind als Bestandsimages verfügbar, wenn Sie einen virtuellen Server erstellen.
* CentOS 7.x
* Debian 8.x, 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04, 18.04
* Windows 2012, 2012 R2, 2016

Wenn Sie eine Instanz bestellen, sind die Images für Cloud-init aktiviert, um die Bereitstellungszeit zu optimieren. Mit einem für Cloud-init aktivierten Image können Sie Benutzerdaten bereitstellen. Im Feld **Benutzerdaten** des Bestellformulars können Sie optionale Cloud-init-Benutzerdaten für den Server eingeben. Weitere Informationen zu Benutzerdaten und Automatisierung finden Sie unter [Benutzerdaten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).

## Virtualisierung
{: #virtualization}
Instanzen benötigen ein Image, das den Bootmodus HVM (Hardware Virtualization Machine, Hardwarevirtualisierungsmaschine) unterstützt. Der HVM-Virtualisierungstyp ermöglicht die direkte Ausführung eines Image auf einem virtuellen Server, was für erweiterte Netzbetriebs- und GPU-Funktionen erforderlich ist.
