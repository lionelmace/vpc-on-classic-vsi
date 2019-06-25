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

# Tutoriel d'initiation
{: #getting-started}

Utilisez {{site.data.keyword.vsi_is_full}} (VPC) pour fournir des ressources de calcul évolutives dans IBM Cloud.
{:shortdesc}

Vous pouvez créer autant de serveurs virtuels que nécessaire, configurer le réseau et la sécurité et gérer le stockage. Toutes ces ressources sont disponibles dans une console IBM Cloud améliorée. Cette console est conçue pour vous fournir un accès rapide et facile permettant d'adapter votre environnement à l'évolution de votre charge de travail. Vous avez certainement hâte de commencer, alors entrons dans le vif du sujet.

Avant de commencer, veillez à [créer un VPC IBM Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

{{site.data.keyword.vsi_is_short}} n'est pas compatible avec les offres de serveur virtuel classiques. Si vous êtes intéressé par l'une des offres {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} sur l'infrastructure classique, voir [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial).
{:note}

<p>Utilisez les informations suivantes pour créer et vous connecter rapidement à vos instances.
<table>
   <CAPTION>Tableau 1. Etapes de démarrage rapide</CAPTION>
   <THEAD>
   <TR>
   <th>Tâche</th>
   <th>Détails</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Examinez le contenu pouvant vous aider pour votre implémentation.</td>
   <td>IBM Cloud et les serveurs virtuels sont nouveaux pour vous ? Les sites suivants fournissent des informations utiles pour planifier votre environnement.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">Qu'est-ce qu'IBM Cloud ?</a></li>
      <li><a href="https://ibm.com/cloud/get-started">Initiation à IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. Inscrivez-vous à IBM Cloud</td>
   <td>Pour plus d'informations sur la configuration de votre compte IBM Cloud, voir <a href="/docs/account?topic=account-signup#signup">Inscription à IBM Cloud</a>.</td>
 <tr>
   <td>3. Déterminez vos spécifications de charge de travail</td>
   <td>Avant de créer votre instance, déterminez son utilisation et la taille de l'instance nécessaire pour aboutir. Prévoyez-vous, par exemple, de l'utiliser à des fins de développement et test ou de production ? Procédez-vous à un test des acquis utilisateur, traitez-vous des algorithmes assez longs, procédez-vous à la restauration et à la sauvegarde de données ou augmentez-vous la vitesse des temps d'attente ?</td>  
 <tr>
   <td>4. Dimensionnez et chiffrez votre instance</td>
   <td>Vous disposez de trois options de famille pour créer vos instances : Balanced, Compute et Memory. Ces familles contiennent des instances préconfigurées, appelées Profils, qui répondent aux besoins de la plupart des clients et peuvent être prêtes à être configurées en quelque 5 minutes.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Balanced</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Compute</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Memory</a></li>
     </ul>
  <p>Utilisez les informations de [Tarification](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) pour vous aider à dimensionner et chiffrer votre instance.</p></td>
 <tr>
   <td>5. Connectez-vous à votre compte IBM Cloud</td>
   <td>Accédez au formulaire de commande {{site.data.keyword.vsi_is_short}} à partir du <a href="https://console.bluemix.net/catalog/">catalogue IBM Cloud</a>. Vous aurez besoin d'un <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBMid et d'un mot de passe</a>.
   </td>
 <tr>
   <td>6. Demandez l'accès à l'expérience {{site.data.keyword.vpc_short}}</td>
   <td>Si vous n'avez pas encore demandé l'accès, demandez l'accès à {{site.data.keyword.vpc_short}}.</td>
<tr>
<td>7. Générez une clé SSH</td>
<td> Pour obtenir des instructions, voir [Clés SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</td>
<tr>
<td>8. Planifiez votre instance</td>
<td> Pour plus d'informations sur la planification, la mise à disposition et la configuration de vos ressources, voir [Planification d'instances](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances).</td>
<tr>
<td>9. Créez votre instance</td>
<td>
<p>
Pour commencer à créer une instance, reportez-vous à [Création d'une instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
</td>  
<tr>
<td>10. Connectez-vous à votre instance</td>
<td>Votre instance est maintenant prête ! Voir les rubriques suivantes sous *Connexion* pour vérifier que l'instance a été créée.
   <ul>
   <li>[Connexion à votre instance Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Connexion à votre instance Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. Nettoyez votre instance</td>
<td>Lorsque vous n'avez plus besoin de votre instance, vous pouvez la supprimer. </td>
</tr>
</TBODY>
</table>
</p>

## Etapes suivantes
Une fois votre instance mise à disposition, explorez vos options.
* [Gestion de votre instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [Droits {{site.data.keyword.vsi_is_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Sécurité de votre instance IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* En savoir plus sur [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
