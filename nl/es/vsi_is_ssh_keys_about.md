---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Claves SSH
{: #ssh-keys}
[comment]: # (tema de ayuda enlazado)

Al suministrar {{site.data.keyword.vsi_is_full}}, para poder crear la instancia debe seleccionar una clave SSH existente o cargar una nueva clave SSH a utilizar. Los servidores utilizan las claves SSH para identificar un usuario o una instancia mediante la criptografía de clave pública. Las claves SSH están formadas por una combinación alfanumérica y son exclusivas de la instancia a la que están asignadas. Puede añadir, editar o suprimir claves SSH utilizando la consola de {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Las claves SSH permiten el acceso a una instancia sin utilizar una contraseña desde los clientes correspondientes para cada clave pública que está implementada en la instancia. Añadiendo una clave SSH a una instancia, lo que puede hacer durante el suministro, se puede acceder a la instancia con la clave correspondiente en lugar con de una contraseña. Puede añadir claves SSH a una instancia sólo en el momento de crearla. Cuando una instancia de Linux ya está creada, puede editar las claves directamente en el directorio `~/.ssh/` de la instancia.

No se da soporte a iniciar sesión en la instancia con una contraseña. Si tiene una instancia de Windows, la clave SSH se utiliza para descifrar la contraseña. Para obtener más información, consulte [Conexión con la instancia de Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance).
{:note}

## Localización o generación de la clave SSH
{: #locating-or-generating-your-ssh-key}

Debe tener la clave SSH disponible. Para localizar la clave SSH o generar una clave SSH, complete uno de los pasos siguientes.

 * Localizar una clave SSH: Busque un archivo denominado `id_rsa.pub` en un directorio `.ssh` bajo el directorio de inicio, por ejemplo, `/Users/<USERNAME>/.ssh/id_rsa.pub`. El archivo empieza por `ssh-rsa` y termina con su dirección de correo electrónico.

* Generar una clave SSH: Si no tiene una clave SSH pública o si olvidó la contraseña de una existente, genere una nueva ejecutando el mandato `ssh-keygen` y siguiendo las indicaciones. Por ejemplo, puede generar una clave SSH en el servidor Linux ejecutando el mandato `ssh-keygen -t rsa -C "user_ID"`. Este mandato genera dos archivos. La clave pública generada se encuentra en el archivo `<your key>.pub`.

  Si utiliza OpenSSH versión 7.8 o superior y tiene la intención de utilizar la clave SSH para acceder a una instancia de Windows, debe utilizar el mandato siguiente para generar la clave en formato PEM. `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

Para obtener más información sobre cómo crear, editar o suprimir claves SSH, consulte [Gestión de claves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
