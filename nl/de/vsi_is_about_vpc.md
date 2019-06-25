---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# Informationen zu Virtual Servers for VPC
{: #virtual-private-cloud}

Mit {{site.data.keyword.vsi_is_full}} können Sie alle Vorzüge von {{site.data.keyword.vpc_short}} nutzen, einschließlich Isolation, Sicherheit und Flexibilität. 
{:shortdesc}

## Was ist {{site.data.keyword.vpc_short}}?
Eine {{site.data.keyword.vpc_short}} (Virtual Private Cloud, virtuelle private Cloud) ist ein virtuelles Netz, das an Ihr Kundenkonto gebunden ist. Sie bietet Ihnen einen kosteneffizienten Einstiegspunkt für die Cloudsicherheit und Möglichkeiten für eine wachstumsabhängige dynamische Skalierung. Sie erhalten eine differenzierte Kontrolle über Ihre virtuelle Infrastruktur und die Segmentierung des Netzverkehrs.
{: shortdesc}

Mehr über {{site.data.keyword.vpc_short}} erfahren Sie im Abschnitt [Informationen zu IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about).

## Was ist {{site.data.keyword.vsi_is_short}}?
Mit {{site.data.keyword.vsi_is_short}} können Sie eine Instanz erstellen, die Ihre virtuellen Rechenressourcen und die daraus resultierende Kapazität in einer {{site.data.keyword.vpc_short}} umfasst. Beim Bereitstellen einer Instanz wählen Sie ein Instanzprofil aus, das dem Umfang der Hauptspeicher- und Rechenleistung entspricht, den Sie für die Anwendung oder Software benötigen, die in der Instanz ausgeführt werden soll. Nachdem Sie eine Instanz bereitgestellt haben, können Sie diese Infrastrukturressourcen steuern und verwalten. Die Anzahl der serverübergreifend ausgeführten Instanzen ist bei jedem Konto begrenzt. Weitere Informationen zu dieser Begrenzung finden Sie unter [Häufig gestellte Fragen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). 

## Worin unterscheiden sich virtuelle Serverinstanzen für {{site.data.keyword.vpc_short}} von anderen IBM Angeboten für virtuelle Server?

Im aktuellen Angebot von IBM Cloud Virtual Server verwenden die Instanzen ein natives Teilnetz und den VLAN-Netzbetrieb, um miteinander in einem Rechenzentrum (und einem einzigen Pod) zu kommunizieren. Der Einsatz von Teilnetz und VLAN-Netzbetrieb in einem einzigen Pod funktioniert bis zu dem Zeitpunkt gut, an dem Sie ein Scale-up durchführen müssen oder ein großer Bedarf an virtuellen Ressourcen besteht, die podübergreifend erstellt werden müssen. (Das Hinzufügen von Appliances für das VLAN-Spanning kann teuer und kostenintensiv werden!) 

{{site.data.keyword.vpc_short}} fügt eine Netzkoordinationsschicht hinzu, die die Podgrenzen aufhebt und somit unbegrenzte Kapazität für die Skalierung von Instanzen herstellt. Die Netzkoordinationsschicht wickelt den gesamten Netzbetrieb für alle virtuellen Serverinstanzen ab, die sich regionen- und zonenübergreifend in einer {{site.data.keyword.vpc_short}} befinden. Die softwaredefinierten Leistungsmerkmale für den Netzbetrieb von {{site.data.keyword.vpc_short}} bieten Ihnen zusätzliche Möglichkeiten für [VPNs](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc), Multi-vNIC-Instanzen und höhere [Teilnetz](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets)größen. Weitere Informationen finden Sie unter [Informationen zum Netzbetrieb für VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc). 

{{site.data.keyword.vsi_is_short}} besitzt darüber hinaus die folgenden Funktionen, die eine einfachere Funktionalität für den Benutzer und Kosteneinsparungen bieten:
* Neue {{site.data.keyword.cloud_notm}}-Konsole
* Neue API und CLI für Virtual Private Cloud
* Neues Abrechnungsmodell mit Rabattstufen für die kontinuierliche Nutzung (siehe hierzu den Abschnitt [Preisstruktur](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc))

{{site.data.keyword.vsi_is_short}} sind nicht mit den klassischen Angeboten für virtuelle Server kompatibel. Falls Sie eines der {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}}-Angebote in der klassischen Infrastruktur nutzen wollen, finden Sie unter [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial) weiterführende Informationen.
{:note}




