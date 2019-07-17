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

# Creazione delle istanze del server virtuale
{: #creating-virtual-servers}
[comment]: # (argomento della guida collegato)

Puoi creare {{site.data.keyword.vsi_is_full}} dalla pagina *Virtual server instances* nella console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Prima di cominciare, assicurati di aver [creato un IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

Per creare un'istanza, seleziona i seguenti dettagli dell'istanza.
1. Nella console [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.cloud.ibm.com/vpc), vai a **Menu icon ![Icona menu](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. Fai clic su **New instance** e immetti le seguenti informazioni:

    <table>
    <CAPTION>Tabella 1. Selezioni per il provisioning dell'istanza</CAPTION>
    <THEAD>
    <TR>
    <th>Campo</th>
    <th>Valore</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Nome </td>
    <td>È obbligatorio un nome per la tua istanza del server virtuale.</td>
    </tr>
    <tr>
    <td>VPC (Virtual Private Cloud)</td>
    <td>Specifica l'IBM Cloud VPC in cui vuoi creare la tua istanza.</td>
    </tr>
    <tr>
    <td>Ubicazione</td>
    <td>Le ubicazioni sono formate da regioni (aree geografiche specifiche) e zone (data center a tolleranza di errore all'interno di una regione). Seleziona l'ubicazione in cui vuoi venga creata la tua istanza del server virtuale.</td>
    </tr>
    <tr>
    <td>Profilo</td>
    <td><p>
    Effettua la seleziona dai profili popolari o da tutte le combinazioni di vCPU e RAM disponibili. Sono supportate le seguenti famiglie:
    <ul>
    <li>Bilanciato</li>
    <li>Calcolo</li>
    <li>Memoria</li>
    </ul>
    </p>
    <p>Ogni core fisico sul server è con hyperthreading e presentato come due CPU virtuali (vCPU). L'offerta di server virtuale fornisce 2.0 GHz o più per vCPU con fino a 48 vCPU disponibili su un solo server virtuale.</p>

    <p>Per quanto riguarda la memoria, un'istanza può avere fino a 256 GB di RAM completamente dedicata.</p>
    <p><note>Nota: i valori massimi variano in base alla famiglia.</note></p>
    <p>Per ulteriori informazioni, vedi [Profili](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).</p>
    </td>
    </tr>
    <tr>
    <td>Immagine</td>
    <td><p>Tutte le immagini utilizzano cloud-init, che ti permette di immettere i metadati utente associati all'istanza per gli script di post-provisioning.</p>
    <p>Per ulteriori informazioni, vedi [Immagini](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images).</p>
    </td>
    </tr>
    <td>Chiave SSH</td>
    <td>
    <p>Devi selezionare una chiave SSH esistente o caricarne una nuova da utilizzare prima di poter creare l'istanza. Le chiavi SSH sono utilizzate per la connessione sicura all'istanza dopo che è in esecuzione. Puoi aggiungere le chiavi SSH alla tua istanza solo quando la crei inizialmente.</p>
    <p>Nota: le combinazioni alfanumeriche sono limitate a 100 caratteri.</p>
    <p>Per ulteriori informazioni, vedi [Chiavi SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</p></td>
    </tr>
    <tr>
    <td>Dati utente</td>
    <td>
    <p>Puoi aggiungere dei dati utente che eseguono automaticamente le attività di configurazione comuni o eseguono gli script. <p>Per ulteriori informazioni, vedi [Dati utente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).</p>
    </td>
    </tr>
    <tr>
    <td>Volume di avvio</td>
    <td><p>La dimensione del volume di avvio predefinita per tutti i profili è 100 GB. Per impostazione predefinita il volume di avvio include la crittografia gestita dal provider. Se vuoi utilizzare la crittografia gestita dal cliente, puoi modificare i dettagli del volume di avvio. Per ulteriori informazioni, vedi [Archiviazione](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage).</p>
    </td>
    </tr>
    <tr>
    <td>Volume di archiviazione blocchi collegato</td>
    <td><p>Puoi aggiungere uno o più volumi di dati secondari che devono essere inclusi quando esegui il provisioning dell'istanza. Per aggiungere i volumi, fai clic su **New block storage volume**. Per ulteriori informazioni, vedi [Creazione dei volumi di archiviazione blocchi](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).</p>
    </td>
    </tr>
    <tr>
    <td>Interfacce di rete</td>
    <td>Assegna le opzioni di rete per la connessione all'IBM Cloud VPC. Puoi creare ed assegnare fino a 5 schede di interfaccia di rete ad ogni istanza. Per ulteriori informazioni, vedi [Indirizzi IP multipli](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options).</td>
    </tr>
    </TBODY>
    </table>

    Il tuo riepilogo dei costi (*Cost summary*) viene visualizzato sul lato destro della pagina *New virtual server instance*.

3. Fai clic su **Create virtual server instance** quando sei pronto ad eseguire il provisioning. Viene inviata una serie di email al tuo amministratore: il riconoscimento dell'ordine dell'istanza del server virtuale, l'elaborazione e l'approvazione dell'ordine e un messaggio che indica che l'istanza è stata creata.

Preferisci creare un'istanza utilizzando la CLI? Per ulteriori informazioni, vedi [Creazione di un'istanza utilizzando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli).
{: tip}

## Riservare un indirizzo IP mobile
{: #reserving-a-floating-ip-address}

Puoi riservare e associare un indirizzo IP mobile alla tua istanza in modo da poterti connettere ad essa da un'ubicazione internet.

La tua istanza deve essere in esecuzione prima di poter associare un indirizzo IP mobile. Servono alcuni minuti perché l'istanza diventi attiva e in esecuzione.
{: note} 

Per riservare e associare un indirizzo IP mobile, completa la seguente procedura.
1. Sulla pagina **Virtual server instances**, fai clic sulla tua istanza per visualizzarne i dettagli.
2. Nella sezione **Network interfaces**, fai clic su **Reserve +** per associare un indirizzo IP mobile alla tua istanza.

## Passi successivi
{: #next-connecting-to-instance}

Sei ora pronto per connetterti alla tua istanza. Per ulteriori informazioni, vedi [Connessione alla tua istanza Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) o [Connessione alla tua istanza Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).
