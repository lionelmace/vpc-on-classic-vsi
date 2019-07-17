---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Datos de usuario
{: #user-data}
[comment]: # (tema de ayuda enlazado)

Al crear una instancia de {{site.data.keyword.vsi_is_full}}, puede añadir datos de usuario que realicen automáticamente tareas de configuración comunes o que ejecuten scripts. En el campo **Datos de usuario** del formulario de pedido, puede especificar datos de usuario de cloud-init opcionales para el servidor.
{:shortdesc}

## Ejemplos de datos de usuario para Linux 
{: #user-data-examples-for-linux}

En el ejemplo siguiente se muestra cómo un usuario de Linux puede añadir un nuevo usuario y proporcionar al usuario una clave SSH autorizada. El campo **Nombre** tendrá la clave pública añadida en `~/.ssh/authorized_keys`. 

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

A continuación se muestra otro ejemplo de un script de shell que muestra cómo un usuario de Linux puede añadir una clave SSH para el usuario actual.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

Puede pegar uno de estos ejemplos directamente en el campo **Datos de usuario**. De esta forma, los datos de usuario están disponibles para la instancia de servidor virtual durante el suministro. 

Para obtener más información y ejemplos de datos de usuario de Linux, consulte el apartado [Ejemplos de configuración de nube ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}.

## Ejemplo de datos de usuario para Windows
{: #user-data-example-for-windows}

El ejemplo siguiente muestra cómo se pueden pasar datos de usuario a una instancia de Windows. Puede copiar y pegar este ejemplo directamente en el campo **Datos de usuario**.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

Para obtener más información y ejemplos de datos de usuario de Windows, consulte el apartado [Documentación de Cloudbase-init 1.0 ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}.
