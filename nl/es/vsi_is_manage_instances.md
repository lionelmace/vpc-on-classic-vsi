---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Gestión de instancias de servidor virtual
{: #managing-virtual-server-instances}
[comment]: # (tema de ayuda enlazado)

Puede ver y gestionar las instancias de {{site.data.keyword.vsi_is_full}} desde la página *Instancias de servidor virtual* en la consola de {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Para gestionar las instancias, complete los pasos siguientes.
1. En [la consola de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.cloud.ibm.com/vpc), vaya a **Icono de menú ![Icono de menú](../icons/icon_hamburger.svg) > Infraestructura de VPC > Cálculo > Instancias de servidor virtual**.
2. Desde aquí, puede gestionar las tareas de una instancia específica o pulsar en una instancia para ver y editar sus propiedades.

## Rearrancar

La acción Rearrancar apaga inmediatamente una instancia y, a continuación, la vuelve a activar.

## Detener e iniciar

La acción Detener e iniciar activa o desactiva de forma remota una instancia. Si la instancia está detenida, permanece en estado detenido y se debe iniciar manualmente. La facturación se [suspende](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing) para algunos recursos de cálculo mientras la instancia está detenida. No se puede interactuar con una instancia si está detenida. Si se inicia el dispositivo, continúa la interacción normal.

## Suprimir

La acción Suprimir elimina de forma permanente una instancia y su vNIC conectada, el volumen de arranque y los datos de la cuenta. Tras confirmar la acción Suprimir, comienza el proceso para suprimir la instancia y su vNIC asociada, el volumen de arranque y los datos. La acción Suprimir puede tardar hasta 30 minutos, pero cuando el proceso se haya completado, la instancia ya no aparecerá en la página Instancias de servidor virtual. La dirección IP flotante asociada a la instancia de servidor virtual está desasociada, pero permanece en la cuenta.

## Ver detalles de instancia
Puede interactuar con instancias visualizando el resumen de todas las instancias en la página *Instancias de servidor virtual*, o pulsando en una instancia individual para ver detalles y realizar cambios. En la página de detalles de instancia, también puede ver la interfaz de red asociada, acceder a su subred y reservar o suprimir una dirección IP flotante.

Si prefiere gestionar las instancias utilizando la CLI, consulte [Gestión de una instancia utilizando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
{: tip}
