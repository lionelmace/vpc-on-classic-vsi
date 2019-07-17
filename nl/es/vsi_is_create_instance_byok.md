---

copyright:
  years: 2019
lastupdated: "2019-06-05"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Creación de instancias de servidor virtual con cifrado gestionado por el cliente
{: #creating-instances-byok}

Puede crear {{site.data.keyword.vsi_is_full}} que utilicen cifrado gestionado por el cliente para volúmenes de almacenamiento de bloques cuando tenga un servicio de gestión de claves suministrado que incluya su propia clave de cifrado de datos. De forma predeterminada, las instancias se suministran con un volumen de arranque que incluye cifrado gestionado por el proveedor. Puede suministrar instancias que utilicen cifrado gestionado por el cliente para los volúmenes de almacenamiento de bloques desde la consola de {{site.data.keyword.cloud_notm}} o utilizando la interfaz de línea de mandatos (CLI).
{:shortdesc}

## Servicios de gestión de claves soportados para el cifrado gestionado por el cliente
{: #kms-for-byok}

Puede utilizar el servicio de gestión de claves que vaya mejor para sus necesidades. {{site.data.keyword.keymanagementserviceshort}} y {{site.data.keyword.hscrypto}} (disponible en ciertas regiones de [](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)) utilizan una API de proveedor de claves común para ofrecer un método para la gestión de claves de cifrado.  De manera oculta, los centros de datos de {{site.data.keyword.cloud_notm}} proporcionan un módulo de seguridad de hardware (HSM) para proteger las claves.  Se da soporte a los siguientes servicios de gestión de claves con cifrado gestionado por el cliente para los volúmenes de almacenamiento en bloques: 

| Servicio de gestión de claves | Certificación de cifrado HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 conformidad *Nivel 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 conformidad *Nivel 4* |
{: caption="Tabla 1. Opciones de servicio de gestión de claves disponibles" caption-side="top"}

## Requisitos previos
{: #byok-vsi-prereqs}

Para crear una instancia de servidor virtual que utilice cifrado gestionado por el cliente para los volúmenes de almacenamiento en bloques, debe haber suministrado un servicio de gestión de claves y también debe haber añadido una raíz de cliente. Además, debe autorizar el acceso entre Cloud Block Storage y el servicio de gestión de claves. Cuando haya completado estos requisitos previos, puede empezar a crear instancias que utilicen el cifrado gestionado por el cliente para los volúmenes de almacenamiento en bloques. 

Los pasos de ejemplo siguientes son específicos de {{site.data.keyword.keymanagementserviceshort}}, pero el flujo general también se aplica a {{site.data.keyword.hscrypto}}. Si utiliza {{site.data.keyword.hscrypto}}, consulte la [información de {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) para obtener las instrucciones correspondientes.
{:note}

1. Suministre el servicio [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision). 
   
   Al suministrar una nueva instancia de servicio de {{site.data.keyword.keymanagementserviceshort}}, se asegura de que incluye las actualizaciones más recientes necesarias para el cifrado gestionado por el cliente de los volúmenes de almacenamiento en bloques. 
   {: tip}
   
2. [Cree](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) o
[importe](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) una clave raíz (CRK) en
{{site.data.keyword.keymanagementservicelong_notm}}.
3. Desde IBM {{site.data.keyword.iamshort}} (IAM), [autorice el acceso](/docs/iam?topic=iam-serviceauth#serviceauth) entre **Cloud
Block Storage** (servicio de origen) y **{{site.data.keyword.keymanagementserviceshort}}** (servicio de destino).

## Suministro de instancias de servidor virtual con volúmenes que utilizan cifrado gestionado por el cliente
{: #provision-byok-ui}

Al suministrar una instancia de servidor virtual, puede especificar cifrado gestionado por el cliente para el volumen de arranque y para cualquier volumen de datos que desee añadir en el momento del suministro. Si lo desea, puede utilizar una combinación de cifrado gestionado por el proveedor y cifrado gestionado por el cliente para los volúmenes que están asociados a la instancia.

1. En [la consola de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.cloud.ibm.com/vpc), vaya a **Icono de menú ![Icono de menú](../icons/icon_hamburger.svg) > Infraestructura de VPC > Cálculo > Instancias de servidor virtual**. Pulse en **Nueva instancia** y complete los campos obligatorios. (Para obtener más información sobre la creación de instancias, consulte [Creación de instancias de servidor virtual](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).) 
2. En la sección **Volumen de arranque**, la modalidad predeterminada de cifrado es el cifrado _Gestionado por el proveedor_. Para especificar el cifrado gestionado por el cliente, pulse en el icono de lápiz en la fila del volumen de arranque. En la página **Editar volumen de arranque**, actualice los campos de la sección **Cifrado**. Consulte la tabla siguiente para obtener más información. Cuando haya completado los cambios, pulse **Aplicar**.
3. En la sección **Volumen de almacenamiento en bloques conectado**, puede pulsar **Nuevo volumen de almacenamiento de bloques** para añadir un volumen de datos y especificar el cifrado gestionado por el cliente si lo desea. En la página **Nuevo volumen de almacenamiento en bloques**, actualice los campos de la sección **Cifrado**. Consulte la tabla siguiente para obtener más información. Cuando haya completado los cambios, pulse **Conectar**.

| Campo | Valor |
| ----- | ----- |
| Cifrado | _Gestionado por el proveedor_ es la modalidad de cifrado predeterminada. Para utilizar el cifrado gestionado por el cliente, seleccione un servicio de gestión de claves en la lista desplegable. La instancia de servicio de gestión de claves debe incluir la clave raíz del cliente que desea utilizar para el cifrado gestionado por el cliente. |
| Instancia de servicio de cifrado | Si tiene varias instancias de servicio de gestión de claves suministradas en la cuenta, seleccione la que incluya la clave raíz de cliente que desee utilizar para el cifrado gestionado por el cliente. |
| Nombre de clave | Seleccione la clave de cifrado de datos dentro de la instancia de servicio de gestión de claves que desee utilizar para cifrar el volumen. | 
| ID de clave | Muestra el ID de clave que asociado a la clave de cifrado de datos que ha seleccionado. | 
{: caption="Tabla 1. Valores para especificar el cifrado gestionado por el cliente de los volúmenes" caption-side="top"}

## Utilización de la CLI para suministrar instancias y volúmenes con cifrado gestionado por el cliente
{: #provision-byok-cli}

Para utilizar la CLI para crear una instancia de servidor virtual con volúmenes que utilicen cifrado gestionado por el cliente, puede utilizar el mandato `ibmcloud is instance-create` y hacer referencia a un JSON para conectar volúmenes que utilicen cifrado gestionado por el cliente. 

1. Obtenga el CRN de la clave raíz en la instancia de servicio de gestión de claves deseada. El ejemplo siguiente es específico de {{site.data.keyword.keymanagementserviceshort}}. 
    
    1. Si todavía no tiene instalado el plug-in de CLI de {{site.data.keyword.keymanagementserviceshort}}, instálelo ejecutando el mandato siguiente: 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. Obtenga una lista de las instancias de servicio de {{site.data.keyword.keymanagementserviceshort}} de su cuenta ejecutando el mandato siguiente:
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. Recupere el ID de instancia de la instancia de servicio de {{site.data.keyword.keymanagementserviceshort}} donde se almacenan las claves raíz del cliente ejecutando el mandato siguiente.  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       donde _Key Protect-17_ es la instancia de servicio de {{site.data.keyword.keymanagementserviceshort}} deseada.
    
       Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       donde el ID de instancia es la serie que sigue a los caracteres finales `::` del CRN, `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`. 
    
    4. Obtenga una lista de las claves disponibles y sus CRN asociados con la instancia de servicio de {{site.data.keyword.keymanagementserviceshort}} deseada ejecutando el mandato siguiente:
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       donde _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ es el ID de instancia de la instancia de servicio de {{site.data.keyword.keymanagementserviceshort}} deseada.
       
       Para este ejemplo, obtendría una respuesta similar a la salida siguiente:
       ```
       Retrieving keys...
              
       SUCCESS
               
       Key ID                                 Key Name               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. Utilice el mandato [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) y adjunte los archivos JSON necesarios que especifiquen el cifrado gestionado por el cliente para el volumen de arranque y para cualquier volumen de datos secundario que desee incluir. El parámetro `encryption_key` debe incluir un CRN válido para la clave raíz en el servicio Key Protect. Consulte los siguientes [ejemplos de archivo JSON](#vsi-vol-attachment-json) de un JSON de volumen de arranque y un JSON de volumen secundario. (Para obtener más información sobre la creación de instancias, consulte [Creación de instancias de servidor virtual (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli).)

## Creación de un archivo adjunto de volumen en formato JSON
{: #vsi-vol-attachment-json}

Al crear un volumen de arranque o un volumen de datos durante el suministro de VSI, debe especificar un archivo JSON para definir los parámetros de volumen. Consulte los siguientes ejemplos de archivos JSON.

### Ejemplo de archivo JSON de volumen de arranque
{: #boot-volume-byok-json}

En el ejemplo siguiente se define un volumen de arranque de propósito general y se especifica el parámetro `encryption key` para el cifrado gestionado por el cliente.

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      },
      "encryption_key":{  
         "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### Ejemplo de archivo JSON de volumen secundario
{: #secondary-volume-byok-json}

El ejemplo siguiente define un volumen secundario de propósito general (datos) y especifica el parámetro `encryption key` para el cifrado gestionado por el cliente.

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         },
         "encryption_key":{  
            "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}
