---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Gestione delle istanze del server virtuale
{: #managing-virtual-server-instances}
[comment]: # (argomento della guida collegato)

Puoi visualizzare e gestire le tue istanze {{site.data.keyword.vsi_is_full}} dalla pagina *Virtual server instances* nella console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Per gestire le tue istanze, completa la seguente procedura.
1. Nella console [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.cloud.ibm.com/vpc), vai a **Menu icon ![Icona menu](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. Da qui, puoi gestire le attività per un'istanza specifica oppure fare clic su un'istanza per visualizzarne e modificarne le proprietà.

## Riavvio

L'azione di riavvio spegne immediatamente un'istanza e poi la riavvia.

## Arresta e avvia

L'azione di arresto e avvio arresta o avvia un'istanza in remoto. Se l'istanza viene arrestata, rimane in tale stato e deve essere avviata manualmente. La fatturazione è [sospesa](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing) per alcune risorse di calcolo mentre l'istanza è arrestata. Non puoi interagire con un'istanza se è arrestata. Se il dispositivo viene avviato, continua una normale interazione.

## Elimina

L'azione elimina rimuove in modo permanente un'istanza e i rispettivi vNIC, volume di avvio e dati connessi dal tuo account. Dopo aver confermato l'azione elimina, viene avviato il processo di eliminazione dell'istanza e dei rispettivi vNIC, volume di avvio e dati associati. L'azione elimina può richiedere fino a 30 minuti, ma una volta che il processo è stato completato, l'istanza non viene più visualizzata sulla pagina delle istanze del server virtuale. L'associazione dell'indirizzo IP mobile all'istanza del server virtuale viene annullata, ma rimane sul tuo account.

## Visualizzazione dei dettagli dell'istanza
Puoi interagire con le istanze visualizzando il riepilogo di tutte le istanze nella pagina *Virtual server instances* o facendo clic su una singola istanza per visualizzare i dettagli e apportare delle modifiche. Dalla pagina dei dettagli dell'istanza, puoi anche visualizzare l'interfaccia di rete associata, accedere alla sua sottorete e riservare o eliminare un indirizzo IP mobile.

Se preferisci gestire le tue istanze utilizzando la CLI, vedi [Gestione di un'istanza utilizzando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
{: tip}
