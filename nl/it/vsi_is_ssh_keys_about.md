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

# Chiavi SSH
{: #ssh-keys}
[comment]: # (argomento della guida collegato)

Quando esegui il provisioning di {{site.data.keyword.vsi_is_full}}, devi selezionare una chiave SSH esistente o caricarne una nuova da utilizzare prima di poter creare l'istanza. Le chiavi SSH vengono utilizzate dai server per identificare un utente o un'istanza tramite la crittografia della chiave pubblica. Le chiavi SSH sono formate da una combinazione alfanumerica e sono univoche per l'istanza a cui sono assegnate. Puoi aggiungere, modificare o eliminare le chiavi SSH utilizzando la console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Le chiavi SSH consentono l'accesso a un'istanza senza utilizzare una password dai client corrispondenti per ogni chiave pubblica implementata sull'istanza. Aggiungendo una chiave SSH a un'istanza, cosa che puoi fare durante il provisioning, è possibile accedere all'istanza con la chiave corrispondente invece di una password. Puoi aggiungere le chiavi SSH a un'istanza solo quando la crei inizialmente. Dopo aver creato un'istanza Linux, puoi modificare le chiavi direttamente nella directory `~/.ssh/` dell'istanza.

L'accesso alla tua istanza con una password non è supportato. Se hai un'istanza Windows, la chiave SSH viene utilizzata per decrittografare la tua password. Per ulteriori informazioni, vedi [Connessione alla tua istanza Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance).
{:note}

## Individuazione o generazione della tua chiave SSH
{: #locating-or-generating-your-ssh-key}

La tua chiave SSH deve essere disponibile. Per individuare la tua chiave SSH o generarne una, completa una delle seguenti procedure.

 * Individua una chiave SSH: cerca un file denominato `id_rsa.pub` in una directory `.ssh` nella directory home, ad esempio, `/Users/<USERNAME>/.ssh/id_rsa.pub`. Il file inizia con `ssh-rsa` e termina con il tuo indirizzo email.

* Genera una chiave SSH: se non hai una chiave SSH pubblica o se hai dimenticato la password di una chiave esistente, generane una nuova immettendo il comando `ssh-keygen` e seguendo le istruzioni. Ad esempio, puoi generare una chiave SSH sul tuo server Linux eseguendo il comando `ssh-keygen -t rsa -C "user_ID"`. Tale comando genera due file. La chiave pubblica generata si trova nel file `<your key>.pub`.

  Se stai utilizzando OpenSSH versione 7.8 o superiore e pianifichi di utilizzare la chiave SSH per accedere a un'istanza Windows, devi utilizzare il seguente comando per generare la chiave nel formato PEM. `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

Per ulteriori informazioni sulla creazione, modifica o eliminazione delle chiavi SSH, vedi [Gestione delle chiavi SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
