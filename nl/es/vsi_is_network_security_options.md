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

# Redes y seguridad en servidores virtuales
{: #network-security-options}

Al implementar {{site.data.keyword.vsi_is_full}}, tiene acceso a las características más recientes de redes y seguridad.  
{:shortdesc}

## Utilización de las vNIC de instancia
{: #using-instance-vnics}

Una tarjeta de interfaz de red virtual (vNIC) se utiliza para conectar un servidor virtual a una red. Al crear una instancia de VSI, puede utilizar una vNIC para asignar varias direcciones IP. En la lista siguiente se puede ver cómo funcionan las vNICs con su instancia.

* Puede crear y asignar hasta 5 vNIC a cada instancia. A cada vNIC se le asignará una IP privada de la subred conectada y, Opcionalmente, puede conectar una IP flotante y grupos de seguridad.
* Puede conectar cada vNIC a una subred de una misma zona.
* Cada vNIC recibe una IP privada del rango de subred.
* Puede asociar y desasociar IP flotantes a y desde cada vNIC.
* Puede asignar grupos de seguridad a cada vNIC.
* Puede cambiar el nombre de cualquier vNIC existente.

El ancho de banda se asocia a la instancia propiamente dicha y no es un aspecto configurable de una vNIC individual. El ancho de banda predeterminado de una instancia es 100 Mbps, actualizable opcionalmente a 1 Gbps.

## Opciones de red
{: #networking-options}

Para obtener más información sobre las características generales de red en el entorno de {{site.data.keyword.vpc_short}}, consulte [Acerca de las redes para VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc).

## Opciones de seguridad
{: #security-options}

{{site.data.keyword.vsi_is_short}} incluye opciones de seguridad integradas:
* Las listas de control de accesos (ACL) pueden limitar el tráfico hacia y desde una subred.
* Los grupos de seguridad funcionan como un cortafuegos virtual para las instancias de servidor virtual.
* Las claves SSH en la instancia de servidor virtual autentican un canal seguro para la comunicación de red.

Para obtener más información sobre estas opciones de seguridad, consulte [Seguridad en la VPC de IBM Cloud](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) y [Gestión de claves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
