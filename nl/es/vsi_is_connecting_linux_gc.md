---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Conexión con la instancia de Linux
{: #connecting-to-your-linux-instance}

Una vez que haya creado la instancia de Linux de {{site.data.keyword.vsi_is_full}}, puede conectarse a ella siguiendo estos pasos.
{:shortdesc}

## Localización de la dirección IP flotante
{: #locating-floating-ip-address}

Si necesita localizar la dirección IP flotante para la instancia a la que desea conectarse, complete los pasos siguientes. Si ya conoce la dirección IP flotante, puede saltar a [Establecer conexión](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected). 

1. Tiene que identificar el ID de IP flotante para poder localizar la dirección IP flotante. Ejecute el mandato siguiente para identificar el ID de IP flotante:

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente (utilizando valores genéricos x y 123, sólo a modo de ejemplo):

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. Ahora que ya tiene su ID de IP flotante, puede localizar la dirección IP flotante ejecutando el mandato siguiente.

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   Para este ejemplo, obtendría una respuesta similar a la salida siguiente (utilizando valores genéricos x y 123, sólo a modo de ejemplo):

   ```
   ID               12345x67-8901-234x-5678-9xx01xx23x4x   
   Address          123.45.678.90   
   Name             my-instance   
   Target           primary(1xx2x34x-.)   
   Target Type      intf   
   Target IP        12.345.6.78   
   Created          1 week ago   
   Status           available   
   Zone             us-south-1   
   Resource Group   -   
   Tags             -   
   ```
   {:screen}

Opcionalmente, puede localizar la dirección IP flotante asociada a la instancia a la que desea conectarse a través de la consola de {{site.data.keyword.cloud_notm}}.
{:tip}

## Establecer conexión
{: #getting-connected}

Los valores devueltos a continuación son solo a modo de ejemplo.

1. Para conectarse a la instancia, utilice la clave privada y ejecute el mandato siguiente:

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   Recibirá una respuesta similar a la del ejemplo siguiente. Cuando se le solicite si desea continuar la conexión, escriba `yes`.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   Ahora está accediendo al servidor.

2. Cuando esté listo para finalizar la conexión, ejecute el mandato siguiente:

   ```
   # exit
   ```
   {:codeblock}

## Siguientes pasos
{: #next-managing-instances}

Una vez que se haya conectado a la instancia, puede [gestionar sus instancias utilizando la consola de {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) o [gestionar sus instancias utilizando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
