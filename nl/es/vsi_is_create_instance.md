---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

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

# Creación de instancias de servidor virtual
{: #creating-virtual-servers}
[comment]: # (tema de ayuda enlazado)

Puede crear {{site.data.keyword.vsi_is_full}} desde la página *Instancias de servidor virtual* en la consola de {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Antes de empezar, asegúrese de haber [creado una VPC de IBM Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

Para crear una instancia, seleccione los detalles de instancia siguientes.
1. En [la consola de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.cloud.ibm.com/vpc), vaya a **Icono de menú ![Icono de menú](../icons/icon_hamburger.svg) > Infraestructura de VPC > Cálculo > Instancias de servidor virtual**.
2. Pulse en **Nueva instancia** y especifique la información siguiente:

    <table>
    <CAPTION>Tabla 1. Selecciones para el suministro de instancias</CAPTION>
    <THEAD>
    <TR>
    <th>Campo</th>
    <th>Valor</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Nombre </td>
    <td>El obligatorio especificar un nombre para la instancia de servidor virtual.</td>
    </tr>
    <tr>
    <td>Nube privada virtual</td>
    <td>Especifique la VPC de IBM Cloud donde desea crear la instancia.</td>
    </tr>
    <tr>
    <td>Ubicación</td>
    <td>Las ubicaciones se componen de regiones (áreas geográficas específicas) y de zonas (centros de datos tolerantes a errores dentro de una región). Seleccione la ubicación donde desea que se cree la instancia de servidor virtual.</td>
    </tr>
    <tr>
    <td>Perfil</td>
    <td><p>
    Seleccione uno de los perfiles más populares o entre todas las combinaciones de vCPU y RAM. Se admiten las familias siguientes:
    <ul>
    <li>Equilibrado</li>
    <li>Cálculo</li>
    <li>Memoria</li>
    </ul>
    </p>
    <p>Cada núcleo físico del servidor tiene HyperThreading y se presenta como dos CPU virtuales (vCPU). La oferta de servidor virtual proporciona 2,0 GHz por vCPU con hasta 48 vCPU disponibles en un único servidor virtual.</p>

    <p>En el caso de la memoria, una instancia puede tener hasta 256 GB de RAM totalmente dedicada.</p>
    <p>< note>Nota: los valores máximos varían según la familia.</note></p>
    <p>Para obtener más información, consulte [Perfiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).</p>
    </td>
    </tr>
    <tr>
    <td>Imagen</td>
    <td><p>Todas las imágenes utilizan cloud-init, lo que le permite especificar los metadatos de usuario asociados con la instancia para los scripts posteriores al suministro.</p>
    <p>Para obtener más información, consulte [Imágenes](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images).</p>
    </td>
    </tr>
    <td>Clave SSH</td>
    <td>
    <p>Para poder crear la instancia, debe seleccionar una clave SSH existente o cargar una nueva clave SSH a utilizar. Las claves SSH se utilizan para conectarse de forma segura a la instancia una vez se está ejecutando. Puede añadir claves SSH a la instancia sólo en el momento de crearla.</p>
    <p>Nota: las combinaciones alfanuméricas tienen un límite de 100 caracteres.</p>
    <p>Para obtener más información, consulte [Claves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</p></td>
    </tr>
    <tr>
    <td>Datos de usuario</td>
    <td>
    <p>Puede añadir datos de usuario que realizan tareas de configuración comunes o ejecutan scripts automáticamente. <p>Para obtener más información, consulte [Datos de usuario](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).</p>
    </td>
    </tr>
    <tr>
    <td>Volumen de arranque</td>
    <td><p>El tamaño de volumen de arranque predeterminado para todos los perfiles es de 100 GB. De forma predeterminada, el volumen de arranque incluye cifrado gestionado por el proveedor. Si desea utilizar cifrado gestionado por el cliente, puede editar los detalles del volumen de arranque. Para obtener más información, consulte [Almacenamiento](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage).</p>
    </td>
    </tr>
    <tr>
    <td>Volumen de almacenamiento en bloques conectado</td>
    <td><p>Puede añadir uno o más volúmenes de datos secundarios que se incluirán cuando suministre la instancia. Para añadir volúmenes, pulse **Nuevo volumen de almacenamiento en bloques**. Para obtener más información, consulte [Creación de volúmenes de almacenamiento en bloques](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).</p>
    </td>
    </tr>
    <tr>
    <td>Interfaces de red</td>
    <td>Asigne opciones de red para conectarse a la VPC de IBM Cloud. Puede crear y asignar hasta 5 tarjetas de interfaz de red a cada instancia. Para obtener más información, consulte [Varias direcciones IP](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options).</td>
    </tr>
    </TBODY>
    </table>

    El *Resumen de costes* se muestra en el lado derecho de la página *Nueva instancia de servidor virtual*.

3. Pulse en **Crear instancia de servidor virtual** cuando esté preparado para suministrar. Se envía una serie de correos electrónicos al administrador: el acuse de recibo del pedido de instancia de servidor virtual, la aprobación y el proceso del pedido y un mensaje que indica que se ha creado la instancia.

¿Prefiere crear una instancia utilizando la CLI? Para obtener más información, consulte [Creación de una instancia utilizando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli).
{: tip}

## Reserva de una dirección IP flotante
{: #reserving-a-floating-ip-address}

Puede reservar y asociar una dirección IP flotante a la instancia para poder conectarse a la misma desde una ubicación de Internet.

La instancia debe estar en ejecución para poder asociar una dirección IP flotante. La instancia puede tardar unos minutos en estar activa y en ejecución.
{: note} 

Para reservar y asociar una dirección IP flotante, siga los pasos siguientes.
1. En la página **Instancias de servidor virtual**, pulse en la instancia para ver su información detallada.
2. En la sección **Interfaces de red**, pulse en **Reservar +** para asociar una dirección IP flotante a la instancia.

## Siguientes pasos
{: #next-connecting-to-instance}

Ahora ya está preparado para conectar con la instancia. Para obtener más información, consulte [Conexión con la instancia de Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) o [Conexión con la instancia de Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).
