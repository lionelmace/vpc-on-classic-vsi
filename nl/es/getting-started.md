---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# Guía de aprendizaje de iniciación
{: #getting-started}

Utilice {{site.data.keyword.vsi_is_full}} (VPC) para suministrar recursos de cálculo escalables en IBM Cloud.
{:shortdesc}

Puede crear tantos servidores virtuales como necesite, configurar la red y la seguridad y gestionar el almacenamiento. Todo esto está disponible en una consola de IBM Cloud mejorada. La consola está diseñada para proporcionarle un acceso rápido y fácil para ajustar su entorno a las demandas cambiantes de carga de trabajo. Seguro que está impaciente por empezar, así que entremos directamente en el tema.

Antes de empezar, asegúrese de haber [creado una VPC de IBM Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

{{site.data.keyword.vsi_is_short}} no son compatibles con las ofertas clásicas del servidor virtual. Si está interesado en alguna de las ofertas de {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} de la infraestructura clásica, consulte [Servidores virtuales de IBM Cloud](/docs/vsi?topic=virtual-servers-getting-started-tutorial).
{:note}

<p>Utilice la siguiente información para empezar a crear y conectarse a sus instancias rápidamente.
<table>
   <CAPTION>Tabla 1. Pasos de inicio rápido</CAPTION>
   <THEAD>
   <TR>
   <th>Tarea</th>
   <th>Detalles</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Revise el contenido que pueda ayudarle con la implementación</td>
   <td>¿Nuevo en IBM Cloud y en los servidores virtuales? Los sitios siguientes proporcionan información útil para ayudarle a planificar el entorno.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">Qué es IBM Cloud</a></li>
      <li><a href="https://ibm.com/cloud/get-started">Iniciación a IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. Regístrese en IBM Cloud</td>
   <td>Para obtener información sobre cómo configurar su cuenta de IBM Cloud, consulte <a href="/docs/account?topic=account-signup#signup">Registrarse en IBM Cloud</a>.</td>
 <tr>
   <td>3. Determine las especificaciones de carga de trabajo</td>
   <td>Antes de crear la instancia, determine cómo se utilizará y el tamaño de instancia que necesita para que todo funcione correctamente. Por ejemplo, ¿tiene la intención de utilizarla para desarrollo y para pruebas, o para producción? ¿Va a probar una experiencia de usuario, procesar algoritmos extensos, realizar copias de seguridad y restauraciones de datos o aumentar la velocidad de latencia?</td>  
 <tr>
   <td>4. Tamaño y precio de la instancia</td>
   <td>Tiene tres opciones de familia al crear las instancias: Equilibrado, Cálculo y Memoria. Las familias contienen instancias preconfiguradas, denominadas Perfiles, que satisfacen las necesidades de la mayoría de los clientes y que pueden estar listas para configurar en tan solo 5 minutos.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Equilibrado</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Cálculo</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Memoria</a></li>
     </ul>
  <p>Utilice la información de [Precios](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) para ayudarle a dimensionar y saber el precio de la instancia.</p></td>
 <tr>
   <td>5. Inicie sesión en su cuenta de IBM Cloud</td>
   <td>Acceda al Formulario de pedido de {{site.data.keyword.vsi_is_short}} desde el <a href="https://console.bluemix.net/catalog/">Catálogo de IBM Cloud</a>. Necesitará un <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBMid y una contraseña</a>.
   </td>
 <tr>
   <td>6. Solicite acceso a la experiencia de {{site.data.keyword.vpc_short}}</td>
   <td>Si todavía no lo ha solicitado, solicite acceso a {{site.data.keyword.vpc_short}}.</td>
<tr>
<td>7. Genere una clave SSH</td>
<td> Para obtener instrucciones, consulte [Claves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</td>
<tr>
<td>8. Planificación de la instancia</td>
<td> Para obtener más información para planificar, suministrar y configurar los recursos satisfactoriamente, consulte [Planificación de instancias](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances).</td>
<tr>
<td>9. Creación de la instancia</td>
<td>
<p>
Para empezar a crear una instancia, consulte [Creación de una instancia](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
</td>  
<tr>
<td>10. Conexión con la instancia</td>
<td>¡Su instancia ya está lista! Consulte los temas siguientes en *Conexión* para verificar que la instancia se ha creado correctamente.
   <ul>
   <li>[Conexión con la instancia de Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Conexión con la instancia de Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. Borrado de la instancia</td>
<td>Cuando ya no necesite la instancia, puede suprimirla. </td>
</tr>
</TBODY>
</table>
</p>

## Siguientes pasos
Una vez que se haya suministrado la instancia, explore las opciones posibles.
* [Gestión de la instancia](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [Permisos de {{site.data.keyword.vsi_is_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Seguridad en la VPC de IBM Cloud](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* Más información acerca de [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
