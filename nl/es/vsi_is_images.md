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


# Imágenes
{: #images}

Al suministrar {{site.data.keyword.vsi_is_full}}, puede seleccionar una de las imágenes en stock soportadas. La imagen que seleccione determina el sistema operativo que se suministrará para la instancia. 
{:shortdesc}

## Imágenes en stock
{: #stock-images}

Hay los siguientes sistemas operativos disponibles como imágenes en stock al crear un servidor virtual.
* CentOS 7.x
* Debian 8.x, 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04, 18.04
* Windows 2012, 2012 R2, 2016

Cuando se hace un pedido de una instancia, las imágenes están habilitadas para cloud-init para optimizar los tiempos de suministro. Con una imagen habilitada para cloud-init, se pueden proporcionar datos de usuario. En el campo **Datos de usuario** del formulario de pedido, puede especificar datos de usuario de cloud-init opcionales para el servidor. Para obtener más información sobre datos de usuario y automatización, consulte [Datos de usuario](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).

## Virtualización
{: #virtualization}
Las instancias requieren una imagen que admita a la modalidad de arranque HVM (Hardware Virtualization Machine). El tipo de virtualización HVM permite que una imagen se ejecute directamente en un servidor virtual, lo cual es necesario para las funciones avanzadas de red y GPU.
