---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-24"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Speicher
{: #storage}

Bei der Bereitstellung einer {{site.data.keyword.vsi_is_full}}-Instanz wird automatisch ein vielseitig einsetzbarer IOPS-Blockspeicherdatenträger (3 IOPS/GB) als primärer Bootdatenträger erstellt und der Instanz zugeordnet. Sie können außerdem sekundäre Datendatenträger erstellen, die der Instanz automatisch zugeordnet werden.
{:shortdesc}

- Weitere Informationen zu Blockspeicherdatenträgern für die virtuelle private Cloud finden Sie unter [Informationen zu Blockspeicherdatenträger für VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).  
- Angaben über den Einstieg in die Erstellung von Datenträgern unabhängig von der Bereitstellung virtueller Server enthält der Abschnitt [Einführung in {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started).

Bootdatenträger und Datendatenträger werden standardmäßig mit der von IBM verwalteten Verschlüsselung verschlüsselt. Ihre eigenen Datenträger können Sie auch mit Ihren eigenen Verschlüsselungsschlüsseln verschlüsseln, entweder während der Instanzbereitstellung oder bei der [Erstellung eines eigenständigen Datenträgers](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

Bootdatenträger werden beim Löschen der virtuellen Serverinstanz gelöscht. Datendatenträger bleiben beim Aufheben der Zuordnung von der Instanz standardmäßig bestehen; Sie können den Datenträger später einer neuen Instanz zuordnen. Alternativ können Sie aber auch angeben, dass Datendatenträger beim Löschen der Instanz automatisch gelöscht werden.  

## Kundenverwaltete Verschlüsselung für Blockspeicher  
{: #customer-managed-encryption-keys}

Sie können {{site.data.keyword.vsi_is_full}} mit Blockspeicherverschlüsselung und eigene, von Ihnen verwaltete Schlüssel zur Datenverschlüsselung erstellen. Zum Einstieg benötigen Sie lediglich den {{site.data.keyword.keymanagementservicelong_notm}}-Service und Ihren eigenen Schlüssel zur Datenverschlüsselung. Weitere Informationen finden Sie im Abschnitt [Instanzen virtueller Server mit kundenverwalteter Verschlüsselung erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).
{:shortdesc}

