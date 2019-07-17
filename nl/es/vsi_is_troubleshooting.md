---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Resolución de problemas de Virtual Servers for VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
Si tiene dificultades con las instancias de {{site.data.keyword.vsi_is_full}}, revise las siguientes causas posibles.

## Error: 409 Conflicto al crear una acción de instancia

No se pueden crear determinadas acciones de instancia si el estado de la instancia entra en conflicto con otra acción. Por ejemplo, si el estado de la instancia es `detenido` e intenta crear una acción de `rearranque`, el sistema devuelve un error 409.

| Estado      | Acción     | Conflicto |
| ----------- | ---------- | -------- |
| En ejecución     | iniciar      | sí      |
| Detenido     | no iniciar  | sí      |
| No se está ejecutando | rearrancar     | sí      |

## Estado de instancia atascado en el estado `suprimiendo`

Si, al listar las instancias, el estado de una de ellas está atascado en `suprimiendo`, utilice la api para mostrar instancias `/instances/{instance_id}` para actualizar el estado de la instancia de servidor virtual específica. Puede ser que no se muestre el estado más reciente al utilizar la api de lista `/instances` para ver todas las instancias.
