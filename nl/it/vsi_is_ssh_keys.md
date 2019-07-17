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

# Gestione delle chiavi SSH
{: #managing-ssh-keys}

## Prima di cominciare
{: #prereq-ssh-key-available}

Per accedere alle istanze {{site.data.keyword.vsi_is_full}}, devi avere una chiave SSH disponibile per l'utilizzo. Puoi gestire le chiavi SSH nella console {{site.data.keyword.cloud_notm}} e utilizzando la CLI. 

La gestione delle chiavi utilizzando la console {{site.data.keyword.cloud_notm}} o la CLI non ha effetto sulle chiavi nelle istanze che sono state già create. (Per un'istanza Linux esistente, puoi modificare le chiavi direttamente nella directory `~/.ssh/` dell'istanza.)

Per ulteriori informazioni sull'individuazione o la generazione di una chiave SSH, vedi [Chiavi SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).
{: tip}

## Gestione delle chiavi SSH con la console IBM Cloud
{: #managing-ssh-keys-with-ibm-cloud-console}

Quando esegui il provisioning di un server virtuale, puoi selezionare le chiavi SSH disponibili o caricarne una nuova. Non puoi generare le chiavi SSH nella console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Puoi gestire ed eliminare le chiavi SSH utilizzando la console {{site.data.keyword.cloud_notm}}.
1. Nella [console {{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.cloud.ibm.com/vpc), vai a **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > SSH keys**.
2. Da qui, puoi aggiungere o eliminare una chiave SSH.

## Gestione delle chiavi SSH utilizzando la CLI
{: #managing-ssh-keys-by-using-the-cli}

Puoi anche gestire le tue chiavi SSH utilizzando la CLI.

| Azione           | Comando                     | Cosa succede poi |
| ---------------- | --------------------------- | ----------------- |
| Crea la chiave SSH   | `ibmcloud is key-create`    | Dopo che hai creato una chiave SSH, viene aggiunta all'elenco di chiavi. |
| Visualizza i dettagli della chiave | `ibmcloud is key`           | Puoi visualizzare il nome e l'ID della chiave. |
| Elenca le chiavi        | `ibmcloud is keys`          | Puoi visualizzare tutte le tue chiavi SSH esistenti. |
| Aggiorna la chiave       | `ibmcloud is key-update`    | Dopo aver aggiornato una chiave esistente, la chiave viene ridenominata immediatamente. |
| Elimina la chiave       | `ibmcloud is key-delete`    | Dopo aver rimosso una chiave SSH, non può più essere utilizzata quando esegui il provisioning di una nuova istanza o quando effettui un ricaricamento SO su un'istanza esistente. Tuttavia, la chiave è ancora disponibile su tutte le istanze di cui hai eseguito il provisioning con essa e puoi utilizzarla per accedere. |
{: caption="Tabella 1. Azioni della chiave SSH" caption-side="top"}
