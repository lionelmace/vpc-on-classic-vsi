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

# Planificación de instancias
{: #planning-for-instances}
[comment]: # (tema de ayuda enlazado)


Al planificar el suministro de {{site.data.keyword.vsi_is_full}}, esta lista de comprobación de configuración puede serle de ayuda para conseguir el máximo rendimiento de su despliegue de servidor virtual.
{:shortdesc}

Antes de empezar, asegúrese de haber [creado una {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Planificación del suministro de instancias
{: #planning-for-provisioning-instances}

Una vez que tenga una {{site.data.keyword.vpc_short}} disponible, tenga en cuenta lo siguiente antes de suministrar una instancia.

|        Consideraciones|
|-------------------|
|__ 1. Asegúrese de que su cuenta tiene los [permisos de usuario](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions) necesarios. Si tiene autorización como editor o administrador en un recurso {{site.data.keyword.vpc_short}}, también puede heredar la autorización para crear suprimir y modificar instancias de servidor virtual dentro de la nube privada virtual.|
|__ 2. Compruebe los [límites de su cuenta](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) de instancias simultáneas. |
|__ 3. Asegúrese de que su [clave SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) está disponible.
|__ 4. Determine la ubicación de instancia a seleccionar.|
|__ 5. Considere las [opciones de perfil](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) popular de combinaciones de vCPU y RAM de su carga de trabajo. Los perfiles contienen instancias preconfiguradas que están listas para utilizar en cuestión de minutos. Es importante asegurarse de que las instancias dispondrán de los recursos necesarios para mantener las cargas de trabajo y el entorno en funcionamiento.|
|__ 6. Determine la imagen del sistema operativo que seleccionará para su instancia. Puede elegir entre las [imágenes](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images) en stock actuales. |
|__ 7. Asegúrese tener un nombre exclusivo para la instancia. Si utiliza algún método para denominar las instancias de servidor virtual, después le resultará mucho más fácil aplicar filtros y hacer búsquedas en ellas. |

## Siguientes pasos
{: #next-create-instance}

Cuando esté preparado para empezar, consulte los recursos siguientes para crear la instancia:
* [Creación de una instancia utilizando la consola de {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Creación de una instancia utilizando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
