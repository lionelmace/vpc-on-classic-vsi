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
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Gestión de claves SSH
{: #managing-ssh-keys}

## Antes de empezar
{: #prereq-ssh-key-available}

Para acceder a las instancias de {{site.data.keyword.vsi_is_full}}, debe tener una clave SSH disponible para utilizar. Puede gestionar las claves SSH en la consola de {{site.data.keyword.cloud_notm}} o bien utilizando la CLI. 

Gestionar las claves utilizando la consola de {{site.data.keyword.cloud_notm}} o la CLI no tiene ningún efecto sobre las claves de las instancias que ya se han creado. (Para una instancia de Linux existente, puede editar las claves directamente en el directorio `~/.ssh/` de la instancia).

Para obtener más información sobre cómo localizar o generar una clave SSH, consulte [Claves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).
{: tip}

## Gestión de claves SSH con la consola de IBM Cloud
{: #managing-ssh-keys-with-ibm-cloud-console}

Cuando suministra un servidor virtual, puede seleccionar entre las claves SSH disponibles o cargar una nueva. No puede generar claves SSH en la consola de {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Puede gestionar y suprimir claves SSH utilizando la consola de {{site.data.keyword.cloud_notm}}.
1. En [la consola de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.cloud.ibm.com/vpc), vaya a **Icono de menú ![Icono de menú](../icons/icon_hamburger.svg) > Infraestructura de VPC > Cálculo > Claves SSH**.
2. Desde aquí, puede añadir o suprimir una clave SSH.

## Gestión de claves SSH utilizando la CLI
{: #managing-ssh-keys-by-using-the-cli}

También puede gestionar las claves SSH utilizando la CLI.

| Acción           | Mandato                     | Qué sucede a continuación |
| ---------------- | --------------------------- | ----------------- |
| Crear una clave SSH   | `ibmcloud is key-create`    | Después de crear una clave SSH, se añade a la lista de claves. |
| Ver detalles de clave | `ibmcloud is key`           | Puede ver el nombre de la clave y el ID de la clave. |
| Listar claves        | `ibmcloud is keys`          | Puede ver todas las claves SSH existentes. |
| Actualizar clave       | `ibmcloud is key-update`    | Después de actualizar una clave existente, la clave se renombra de forma inmediata. |
| Suprimir clave       | `ibmcloud is key-delete`    | Después de eliminar una clave SSH, ya no se puede utilizar al suministrar una instancia nueva o al realizar una recarga de sistema operativo en una instancia existente. Sin embargo, la clave sigue estando disponible en cualquier instancia que haya suministrado con la misma, y puede utilizarla para iniciar sesión. |
{: caption="Tabla 1. Acciones de claves SSH" caption-side="top"}
