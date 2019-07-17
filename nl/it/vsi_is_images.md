---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Immagini
{: #images}

Quando esegui il provisioning di {{site.data.keyword.vsi_is_full}}, puoi anche selezionare dalle immagini predefinite supportate. L'immagine che selezioni determina il sistema operativo di cui è stato eseguito il provisioning per la tua istanza. 
{:shortdesc}

## Immagini predefinite
{: #stock-images}

I seguenti sistemi operativi sono disponibili come immagini predefinite quando crei un server virtuale.
* CentOS 7.x
* Debian 8.x, 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04, 18.04
* Windows 2012, 2012 R2, 2016

Quando ordini un'istanza, le immagini sono abilitate cloud-init per ottimizzare i tempi di provisioning. Con un'immagine abilitata cloud-init, puoi fornire i dati utente. Nel campo **User Data** sul modulo d'ordine, puoi immettere i dati utente cloud-init facoltativi per il server. Per ulteriori informazioni sui dati utente e l'automazione, vedi [Dati utente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).

## Virtualizzazione
{: #virtualization}
Le istanze richiedono un'immagine che supporta la modalità di avvio HVM (Hardware Virtualization Machine). Il tipo di virtualizzazione HVM consente l'esecuzione di un'immagine direttamente su un server virtuale, il che è obbligatorio per le funzionalità GPU e di rete avanzate.
