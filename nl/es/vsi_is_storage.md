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


# Almacenamiento
{: #storage}

Cuando se suministra una instancia de {{site.data.keyword.vsi_is_full}}, se crea automáticamente un volumen de almacenamiento en bloques IOPS (3 IOPS/GB) de propósito general de 100 GB como volumen de arranque primario y se conecta a la instancia. También puede crear volúmenes de datos secundarios, que se conectan automáticamente a la instancia.
{:shortdesc}

- Para obtener más información sobre los volúmenes de almacenamiento en bloques de VPC, consulte [Acerca de Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).  
- Para empezar a crear volúmenes independientes del suministro de instancias de servidor virtual, consulte [Cómo empezar con {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started).

De forma predeterminada, los volúmenes de arranque y de datos se cifran con el cifrado gestionado por IBM. También puede cifrar los volúmenes utilizando sus propias claves de cifrado, durante el suministro de instancias o al [crear un volumen autónomo](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

Los volúmenes de arranque se suprimen cuando se suprime la instancia de servidor virtual. De forma predeterminada, los volúmenes de datos persisten cuando se desconectan de la instancia; más adelante puede adjuntar el volumen a una instancia nueva. De forma alternativa, puede especificar que los volúmenes de datos se supriman automáticamente cuando se suprima la instancia.  

## Cifrado gestionado por el cliente para almacenamiento en bloques  
{: #customer-managed-encryption-keys}

Puede crear {{site.data.keyword.vsi_is_full}} con cifrado de almacenamiento en bloques y sus propias claves de cifrado de datos que gestiona usted mismo. Sólo necesita el servicio {{site.data.keyword.keymanagementservicelong_notm}} y su propia clave de cifrado de datos para empezar. Para obtener más información, consulte [Creación de instancias de servidor virtual con cifrado gestionado por el cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).
{:shortdesc}

