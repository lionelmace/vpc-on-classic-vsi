---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Gestione delle istanze del server virtuale (CLI)
{: #managing-virtual-servers-cli}

Puoi visualizzare e gestire le istanze di {{site.data.keyword.vsi_is_full}} utilizzando l'interfaccia di riga comando (CLI).
{:shortdesc}

## Prima di cominciare
{: #prereq-managing-instances}

1. Assicurati di aver scaricato, installato e inizializzato i seguenti plugin CLI:
    * CLI {{site.data.keyword.cloud_notm}}
    * Il plugin infrastructure-service

   Per ulteriori informazioni, vedi [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Quando installi il plugin vpc-infrastructure per la prima volta, devi configurare la generazione di destinazione su gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Assicurati di aver già [creato un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Visualizzazione delle azioni dell'istanza
{: #viewing-instance-actions}

Per visualizzare le azioni di gestione effettuate sulla tua istanza, immetti il seguente comando:

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

Visualizzerai un elenco simile al seguente output:

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## Gestione delle tue istanze
{: #managing-your-instances}

Hai bisogno di un po' d'aiuto? Esegui il comando `ibmcloud is help` per visualizzare i comandi in qualsiasi momento.

### Ripristina  

```
ibmcloud is instance-reset
```
{:codeblock}

L'istanza viene spenta e poi accesa.  

### Riavvia

```
ibmcloud is instance-reboot
```
{:codeblock}

Il sistema operativo dell'istanza viene riavviato.  

### Arresta e avvia

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

Se il dispositivo è stato arrestato, rimane in tale stato e deve essere avviato manualmente. Non puoi interagire con un'istanza se è arrestata. Se il dispositivo viene avviato, continua una normale interazione. 

### Aggiorna

```
ibmcloud is instance-update
```
{:codeblock}

Dopo la ridenominazione del dispositivo, il nome viene automaticamente aggiornato. Quando esegui una ricerca, utilizza il nuovo nome dell'istanza quando tenti di individuare il contenuto associato ad essa. 

### Elimina

```
ibmcloud is instance-delete
```
{:codeblock}

Dopo aver confermato l'azione elimina, viene avviato il processo di eliminazione dell'istanza e dei rispettivi vNIC, volume di avvio e dati associati. L'azione elimina può richiedere diversi minuti, ma una volta che il processo è stato completato, l'istanza non viene più visualizzata sulla pagina delle istanze del server virtuale. L'associazione dell'indirizzo IP mobile all'istanza del server virtuale viene annullata, ma rimane sul tuo account.

Se preferisci gestire le istanze utilizzando la console {{site.data.keyword.cloud}}, vedi [Gestione di un'istanza](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).
{: tip}
