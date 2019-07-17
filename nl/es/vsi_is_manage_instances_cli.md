---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Gestión de instancias de servidor virtual (CLI)
{: #managing-virtual-servers-cli}

Puede ver y gestionar las instancias de {{site.data.keyword.vsi_is_full}} utilizando la interfaz de línea de mandatos (CLI).
{:shortdesc}

## Antes de empezar
{: #prereq-managing-instances}

1. Asegúrese de haber descargado, instalado e inicializado los siguientes plug-ins de CLI:
    * CLI de {{site.data.keyword.cloud_notm}}
    * El plugin infrastructure-service

   Para obtener más información, consulte [Consulta de la CLI de IBM Cloud para VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Cuando instala el plug-in vpc-infrastructure por primera vez, debe establecer la generación de destino en gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Asegúrese de haber [creado un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Ver las acciones de instancia
{: #viewing-instance-actions}

Para ver las acciones de gestión que se realizan en la instancia, ejecute el mandato siguiente:

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

Verá una lista similar a la salida siguiente:

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## Gestión de las instancias
{: #managing-your-instances}

¿Necesita ayuda? Ejecute el mandato `ibmcloud is help` para ver los mandatos en cualquier momento.

### Restablecer  

```
ibmcloud is instance-reset
```
{:codeblock}

La instancia se apaga y después se enciende.  

### Reiniciar

```
ibmcloud is instance-reboot
```
{:codeblock}

Se reinicia el sistema operativo de la instancia.  

### Detener e iniciar

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

Si el dispositivo se ha detenido, el dispositivo permanece en el estado detenido y se debe iniciar manualmente. No se puede interactuar con una instancia si está detenida. Si se inicia el dispositivo, continúa la interacción normal. 

### Actualizar

```
ibmcloud is instance-update
```
{:codeblock}

Tras renombrar el dispositivo, el nombre se actualiza automáticamente. Al realizar una búsqueda, utilice el nuevo nombre de instancia al intentar localizar contenidos asociados a la misma. 

### Suprimir

```
ibmcloud is instance-delete
```
{:codeblock}

Tras confirmar la acción Suprimir, comienza el proceso para suprimir la instancia y su vNIC asociada, el volumen de arranque y los datos. La acción Suprimir puede tardar varios minutos, pero cuando el proceso se haya completado, la instancia ya no aparecerá en la página Instancias de servidor virtual. La dirección IP flotante asociada a la instancia de servidor virtual está desasociada, pero permanece en la cuenta.

Si prefiere gestionar las instancias utilizando la consola de {{site.data.keyword.cloud}}, consulte [Gestión de una instancia](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).
{: tip}
