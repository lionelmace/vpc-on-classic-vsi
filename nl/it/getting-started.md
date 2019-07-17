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

# Esercitazione introduttiva
{: #getting-started}

Utilizza {{site.data.keyword.vsi_is_full}} (VPC) per eseguire il provisioning di risorse di calcolo scalabili in IBM Cloud.
{:shortdesc}

Puoi creare tutti i server virtuali di cui hai bisogno, configurare la rete e la sicurezza e gestire l'archiviazione. Tutto questo è disponibile in una console IBM Cloud migliorata. La console è creata per fornirti un accesso veloce e semplice per modificare il tuo ambiente quando cambiano le tue richieste di carico di lavoro. Scommettiamo che sei ansioso di iniziare, quindi iniziamo subito con il business.

Prima di cominciare, assicurati di aver [creato un IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

{{site.data.keyword.vsi_is_short}} non sono compatibili con le offerte del server virtuale classico. Se sei interessato in una delle offerte {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} sull'infrastruttura classica, vedi [Server virtuali IBM Cloud](/docs/vsi?topic=virtual-servers-getting-started-tutorial).
{:note}

<p>Utilizza le seguenti informazioni per iniziare a creare e connetterti alle tue istanze velocemente.
<table>
   <CAPTION>Tabella 1. Procedura d'avvio rapida</CAPTION>
   <THEAD>
   <TR>
   <th>Attività</th>
   <th>Dettagli</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Controlla il contenuto che può aiutarti con la tua implementazione.</td>
   <td>Non hai esperienza con IBM Cloud e i server virtuali? I seguenti siti forniscono informazioni utili per pianificare il tuo ambiente.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">What is IBM Cloud</a></li>
      <li><a href="https://ibm.com/cloud/get-started">Getting started with IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. Registrati per IBM Cloud</td>
   <td>Per informazioni su come configurare il tuo account IBM Cloud, vedi <a href="/docs/account?topic=account-signup#signup">Registrazione a IBM Cloud</a>.</td>
 <tr>
   <td>3. Determina le tue specifiche del carico di lavoro</td>
   <td>Prima di creare la tua istanza, determina come sarà utilizzata e la dimensione dell'istanza necessaria per la sua realizzazione. Ad esempio, intendi utilizzarla per lo sviluppo, il test o la produzione? Stai testando un'esperienza utente, elaborando lunghi algoritmi, eseguendo il backup e il ripristino di dati o aumentando la velocità di latenza?</td>  
 <tr>
   <td>4. Dimensione e prezzo della tua istanza</td>
   <td>Hai tre opzioni di famiglia quando si tratta di creare le tue istanze: Bilanciato, Calcolo e Memoria. Le famiglie contengono delle istanze preconfigurate, denominate profili, che soddisfano i bisogni della maggior parte dei clienti e possono essere pronte per la configurazione in poco più di 5 minuti.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Bilanciato</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Calcolo</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Memoria</a></li>
     </ul>
  <p>Utilizza le informazioni sui [Prezzi](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) per la dimensione e i prezzi della tua istanza.</p></td>
 <tr>
   <td>5. Accedi al tuo account IBM Cloud</td>
   <td>Accesso al modulo d'ordine di {{site.data.keyword.vsi_is_short}} dal <a href="https://console.bluemix.net/catalog/">Catalogo IBM Cloud</a>. Avrai bisogno di <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">un ID IBM e una password</a>.
   </td>
 <tr>
   <td>6. Richiedi l'accesso all'esperienza {{site.data.keyword.vpc_short}}</td>
   <td>Se non hai ancora richiesto l'accesso, richiedilo a {{site.data.keyword.vpc_short}}.</td>
<tr>
<td>7. Genera una chiave SSH</td>
<td> Per istruzioni, vedi [Chiavi SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</td>
<tr>
<td>8. Pianificazione per la tua istanza</td>
<td> Per ulteriori informazioni per pianificare, eseguire il provisioning e configurare le tue risorse correttamente, vedi [Pianificazione per le istanze](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances).</td>
<tr>
<td>9. Creazione della tua istanza</td>
<td>
<p>
Per iniziare a creare un'istanza, vedi [Creazione di un'istanza](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
</td>  
<tr>
<td>10. Connessione alla tua istanza</td>
<td>La tua istanza è ora pronta. Vedi i seguenti argomenti in *Connessione* per verificare se l'istanza è stata creata correttamente.
   <ul>
   <li>[Connessione alla tua istanza Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Connessione alla tua istanza Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. Ripulitura della tua istanza</td>
<td>Quando non hai più bisogno della tua istanza, puoi eliminarla. </td>
</tr>
</TBODY>
</table>
</p>

## Passi successivi
Dopo aver eseguito il provisioning della tua istanza, esplora le tue opzioni.
* [Gestione della tua istanza](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [Autorizzazioni {{site.data.keyword.vsi_is_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Sicurezza nel tuo IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* Ulteriori informazioni su [VPC (Virtual Private Cloud) IBM Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
