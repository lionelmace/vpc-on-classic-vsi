---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

keywords: Windows instance, encrypt password, decrypt password, retrieve password

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Conexión con la instancia de Windows
{: #connecting-to-your-windows-instance}

Una vez que haya creado la instancia de Windows de {{site.data.keyword.vsi_is_full}}, puede conectarse a ella siguiendo estos pasos.
{:shortdesc}

## Antes de empezar
{: #prereqs-connect-windows}

Asegúrese de completar los siguientes requisitos previos antes de empezar:

1. Pida al administrador de la cuenta que le dé acceso para recuperar la contraseña de la instancia de servidor virtual. Para obtener más información, revise el apartado [Permisos de usuario](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources).
2. Cree un nuevo grupo de seguridad o añada una regla al grupo de seguridad predeterminado para habilitar el acceso de entrada al puerto predeterminado de Escritorio remoto, 3389. Para obtener más información, consulte [Utilización de grupos de seguridad](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups).
3. Asegúrese que se permite el tráfico de entrada sobre el puerto TCP/IP 3389 en la lista de control de accesos predeterminada de la VPC. Para obtener más información, consulte [Configuración de las ACL de red](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls).
4. Verifique que tiene OpenSSL instalado. Para descifrar correctamente la contraseña, debe ejecutar OpenSSL y no LibreSSL. Para obtener más información, consulte [Descargas de OpenSSL ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.openssl.org/source/){: new_window}.

LibreSSL no es compatible para descifrar la contraseña. Debe ejecutar OpenSSL para descifrar la contraseña.
{:important}

## Establecer conexión
{: #getting-connected-windows}

Después de crear la instancia de Windows y completar los requisitos previos, complete los pasos siguientes para conectarse a la instancia de Windows.

1. Consulte el estado de la instancia ejecutando el mandato siguiente:
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  Cuando la instancia muestra que está `running` (en ejecución), ya está listo para recuperar los valores de inicialización para obtener la contraseña. 

2. Ejecute el mandato siguiente para inicializar la instancia:

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  Este mandato muestra la contraseña cifrada, que se genera automáticamente cuando se crea una instancia utilizando una imagen de Windows.

3. Ahora tiene que descifrar la contraseña a través de un proceso de descifrado manual. Para descifrar la contraseña, ejecute el mandato siguiente:

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  donde `~/examplepwd` es el archivo donde ha guardado la contraseña cifrada como se ha explicado en el paso 2.  
  
  LibreSSL, que se incluye con macOS, no admite algoritmos de hash SHA2, necesarios para descifrar la contraseña, y produce errores de tipo `Public Key operation error`. Puede obtener bibliotecas de OpenSSL estándar utilizando una herramienta de gestión de paquetes o instalándolas manualmente. 
  {:note}

4. Después de descifrar la contraseña, opcionalmente, puede asociar una dirección IP flotante a la instancia de Windows para poder conectarse a la misma desde una ubicación de Internet. Ejecute el mandato siguiente para asociar una dirección IP flotante a la instancia:

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. Ahora ya tiene lo que necesita para conectarse a su instancia de Windows: la contraseña descifrada y la dirección IP flotante. Utilice el cliente de escritorio remoto que prefiera para conectarse a la instancia. Para conectarse a la instancia, indique la dirección IP flotante y la contraseña descifrada. De forma predeterminada, el nombre de usuario es `Administrator`.

## Siguientes pasos
{: #next-manage-instances}

Una vez que se haya conectado a la instancia, puede [gestionar sus instancias utilizando la consola de {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) o [gestionar sus instancias utilizando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
