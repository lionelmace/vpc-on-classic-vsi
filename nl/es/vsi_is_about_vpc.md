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

# Acerca de Virtual Servers for VPC
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}} le da acceso a todas las ventajas de {{site.data.keyword.vpc_short}}, incluyendo aislamiento, seguridad y flexibilidad de red. 
{:shortdesc}

## ¿Qué es {{site.data.keyword.vpc_short}}?
Una {{site.data.keyword.vpc_short}} es una red virtual que está vinculada a su cuenta de cliente. Le ofrece un punto de entrada rentable que proporciona seguridad de nube y la capacidad de escalar dinámicamente a medida que se crece. Le proporciona un control preciso sobre la infraestructura virtual y la segmentación de tráfico de red.
{: shortdesc}

Para obtener más información sobre {{site.data.keyword.vpc_short}}, consulte [Acerca de VPC de IBM Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about).

## ¿Qué son los {{site.data.keyword.vsi_is_short}}?
Con {{site.data.keyword.vsi_is_short}}, puede crear una instancia que consista de sus recursos de cálculo virtuales y la capacidad resultante dentro de una {{site.data.keyword.vpc_short}}. Al suministrar una instancia, se selecciona un perfil de instancia que coincide con la cantidad de memoria y la potencia de cálculo que necesita para la aplicación o el software que tiene previsto ejecutar en la instancia. Después de suministrar una instancia, puede controlar y gestionar esos recursos de infraestructura. Cada cuenta tiene un límite en cuanto al número de instancias en ejecución entre servidores. Para obtener más información sobre este límite, consulte [Preguntas frecuentes](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). 

## ¿En qué se diferencian las instancias de servidor virtual de {{site.data.keyword.vpc_short}} de otras ofertas de servidor virtual de IBM?

En la oferta de IBM Cloud Virtual Server actual, las instancias utilizan una subred nativa y una red VLAN para comunicarse entre sí dentro de un centro de datos (y un solo pod). La utilización de subredes y de redes VLAN en un pod funciona bien hasta que necesita escalar o tiene grandes demandas de recursos virtuales que requieren crear recursos entre los pods. (Añadir dispositivos para expandir la VLAN puede ser costoso y complicado). 

{{site.data.keyword.vpc_short}} añade una capa de orquestación de red que elimina el límite del pod, creando una capacidad infinita para escalar instancias. La capa de orquestación de red maneja todas las redes de todas las instancias de servidor virtual que están dentro de una {{site.data.keyword.vpc_short}} entre regiones y zonas. Con las prestaciones de red definidas por software que {{site.data.keyword.vpc_short}} proporciona, dispone de más opciones para [VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc), instancias de varias vNIC, y tamaños de [subredes](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets) más grandes. Para obtener más información, consulte [Acerca de las redes para VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc). 

{{site.data.keyword.vsi_is_short}} también tiene las siguientes características que proporcionan una experiencia de usuario más sencilla y un ahorro de costes:
* Una nueva consola de {{site.data.keyword.cloud_notm}}
* Una nueva API y CLI de Virtual Private Cloud
* Un nuevo modelo de facturación con niveles de descuento por uso continuado, tal como se describe en [Precios](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)

{{site.data.keyword.vsi_is_short}} no son compatibles con las ofertas clásicas del servidor virtual. Si está interesado en alguna de las ofertas de {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} de la infraestructura clásica, consulte [Servidores virtuales de IBM Cloud](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial).
{:note}




