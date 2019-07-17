---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Perfiles
{: #profiles}

Al suministrar {{site.data.keyword.vsi_is_full}}, puede seleccionar tres familias de perfiles: Equilibrado, Cálculo y Memoria. Un perfil es una combinación de vCPU y RAM que se puede instanciar rápidamente para iniciar una instancia de servidor virtual. En la consola de {{site.data.keyword.Bluemix_notm}}, puede elegir una de las configuraciones de perfil más populares o seleccionar en una lista los perfiles que mejor se adapten a sus necesidades.
{: shortdesc}

Hay las siguientes familias disponibles:

| Familias | Descripción |
| -------- | ----------- |
| [Equilibrado](#balanced) | Adecuado para cargas de trabajo comunes de la nube que requieren un equilibrio entre rendimiento y escalabilidad. Los perfiles equilibrados (con almacenamiento conectado a red) proporcionan un rendimiento más alto, ya que los recursos no se suscriben en exceso. |
| [Cálculo](#compute)  | Adecuado para cargas de trabajo con un tráfico web de moderado a alto. Los perfiles de cálculo son la mejor opción para las cargas de trabajo con demandas de CPU intensivas, como por ejemplo cargas de trabajo con un elevado tráfico web, procesamiento por lotes de producción y servidores web frontales. |
| [Memoria](#memory) | Adecuado para cargas de trabajo con colocación en memoria caché y análisis en tiempo real. Los perfiles de memoria son la mejor opción para cargas de trabajos intensivas en memoria, como por ejemplo cargas de trabajo de memoria caché grandes, aplicaciones de base de datos intensivas o cargas de trabajo analíticas en memoria. |
{: caption="Tabla 1. Selecciones de familias de servidores virtuales" caption-side="top"}

## Equilibrado
{: #balanced}

Los perfiles equilibrados proporcionan un rendimiento más alto, ya que los recursos no se suscriben en exceso. El rendimiento de red va desde estándar a premium.

Esta oferta está disponible en los perfiles siguientes:

| Perfil | vCPU | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="Tabla 2. Opciones para perfil de servidor virtual Equilibrado" caption-side="top"}

**Notas sobre el almacenamiento:**

* El volumen de arranque primario de SAN (100GB) se crea y se conecta automáticamente cuando se suministra una instancia.
* Opcionalmente, puede crear un volumen de datos secundario. Los perfiles de volumen están disponibles como tres niveles de IOPS predefinidos o como IOPS personalizados. Un [perfil de nivel de propósito general de 3 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) proporciona un rendimiento de IOPS/GB adecuado para un perfil de VSI Equilibrado.
* Los precios para los servidores virtuales públicos que utilizan almacenamiento SAN incluyen la CPU, la memoria y el volumen de arranque primario. Los volúmenes de datos secundarios tienen precios aparte.

Todos los sistemas operativos soportados (como, por ejemplo, CentOS, Debian, Ubuntu y Windows) están disponibles con esta oferta.

## Cálculo
{: #compute}

Los perfiles de cálculo son la mejor opción para las cargas de trabajo con demandas de CPU intensivas, como por ejemplo cargas de trabajo con un elevado tráfico web, procesamiento por lotes de producción y servidores web frontales.

Esta oferta está disponible en los perfiles siguientes:

| Perfil | vCPU | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="Tabla 3. Opciones para perfil de servidor virtual de Cálculo" caption-side="top"}

**Notas sobre el almacenamiento:** 

* El volumen de arranque primario de SAN (100GB) se crea y se conecta automáticamente cuando se suministra una instancia.
* Opcionalmente, puede crear un volumen de datos secundario. Los perfiles de volumen están disponibles como tres niveles de IOPS predefinidos o como IOPS personalizados. Un perfil [de nivel 5 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) proporciona un rendimiento de IOPS/GB adecuado para un perfil de VSI de Cálculo.
* Los precios para los servidores virtuales públicos que utilizan almacenamiento SAN incluyen la CPU, la memoria y el volumen de arranque primario. Los volúmenes de datos secundarios tienen precios aparte.

Todos los sistemas operativos soportados (como, por ejemplo, CentOS, Debian, Ubuntu y Windows) están disponibles con esta oferta. 

## Memoria 
{: #memory}

Los perfiles de memoria son la mejor opción para cargas de trabajos intensivas en memoria, como por ejemplo cargas de trabajo de memoria caché grandes, aplicaciones de base de datos intensivas o cargas de trabajo analíticas en memoria.

Esta oferta está disponible en los perfiles siguientes:

| Perfil | vCPU | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="Tabla 4. Opciones para perfil de servidor virtual de Memoria" caption-side="top"}

**Notas sobre el almacenamiento:** 

* El volumen de arranque primario de SAN (100GB) se crea y se conecta automáticamente cuando se suministra una instancia.
* Opcionalmente, puede crear un volumen de datos secundario. Los perfiles de volumen están disponibles como tres niveles de IOPS predefinidos o como IOPS personalizados. Un perfil [de nivel 10 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) proporciona un rendimiento de IOPS/GB adecuado para un perfil de VSI de Memoria.
* Los precios para los servidores virtuales públicos que utilizan almacenamiento SAN incluyen la CPU, la memoria y el volumen de arranque primario. Los volúmenes de datos secundarios tienen precios aparte.

Todos los sistemas operativos soportados (como, por ejemplo, CentOS, Debian, Ubuntu y Windows) están disponibles con esta oferta. 

## Visualización de las configuraciones de perfiles
{: #popularprofiles}

Puede ver las configuraciones de perfiles disponibles utilizando la consola de {{site.data.keyword.cloud_notm}} o la CLI. En la consola de {{site.data.keyword.cloud_notm}}, puede elegir una de las configuraciones de perfil más populares que admiten la mayoría de casos prácticos.

### Utilizando la consola de IBM Cloud
1. En la consola de {{site.data.keyword.cloud_notm}}, vaya al **Icono de menú ![Icono de menú ](../icons/icon_hamburger.svg) > Infraestructura de VPC > Cálculo > Instancias de servidor virtual**.
2. En esta página, pulse **Nueva instancia**.
3. Puede seleccionar una configuración de perfil de **Perfiles populares** o bien pulsar **Todos los perfiles** para ver otras configuraciones.

### Utilizando la CLI
Para ver la lista de perfiles disponibles utilizando la CLI, ejecute el mandato siguiente:
```
$ ibmcloud is instance-profiles
```
{:codeblock}

Cuando se utiliza la línea de mandatos, la información siguiente describe lo que representa la salida. Los tamaños de perfil tienen distintos coeficientes de CPU frente a memoria para distintas cargas de trabajo:

*  "b" es Equilibrado, que es un coeficiente de 1:2 o 1:4
*  "c" es Cálculo (superior en las CPU), que es un coeficiente de 1:1
*  “m” es Memoria (superior en la memoria), que es un coeficiente de 1:8
