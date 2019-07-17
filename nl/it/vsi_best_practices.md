---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Pianificazione per le istanze
{: #planning-for-instances}
[comment]: # (argomento della guida collegato)


Quando stai pianificando di eseguire il provisioning di {{site.data.keyword.vsi_is_full}}, potresti trovare utile questo elenco di controllo di configurazione per ottenere il massimo dalla tua distribuzione del server virtuale.
{:shortdesc}

Prima di cominciare, assicurati di aver [creato un {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Pianificazione del provisioning delle istanze
{: #planning-for-provisioning-instances}

Dopo che hai ottenuto la disponibilità di un {{site.data.keyword.vpc_short}}, tieni presente quanto segue prima di eseguire il provisioning della tua istanza.

|        Considerazioni|
|-------------------|
|__ 1. Assicurati che il tuo account abbia le [autorizzazioni utente](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions) necessarie. Se hai l'autorizzazione da editor o amministratore per una risorsa {{site.data.keyword.vpc_short}}, allora erediti anche l'autorizzazione per creare, eliminare e modificare le istanze del server virtuale all'interno di tale cloud privato virtuale.|
|__ 2. Controlla i tuoi [limiti dell'account](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) per le istanze simultanee. |
|__ 3. Assicurati che la tua [chiave SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) sia disponibile.
|__ 4. Determina quale ubicazione dell'istanza selezionare.|
|__ 5. Considera le [opzioni di profilo](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) popolari di combinazioni di vCPU e RAM per il tuo carico di lavoro. I profili contengono delle istanze preconfigurate pronte per l'utilizzo in pochi minuti. È importante assicurarti che le tue istanze abbiano le risorse necessarie per mantenere i tuoi carichi di lavoro e il tuo ambiente attivi e in esecuzione.|
|__ 6. Determina quale immagine di sistema operativo selezionerai per la tua istanza. Puoi scegliere tra le [immagini](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images) predefinite correnti. |
|__ 7. Assicurati di avere un nome univoco per l'istanza. Se hai un metodo per denominare le istanze del server virtuale, è molto più facile filtrarle o ricercarle in un secondo momento. |

## Passi successivi
{: #next-create-instance}

Quando sei pronto ad iniziare, vedi le seguenti risorse per creare la tua istanza:
* [Creazione di un'istanza utilizzando la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Creazione di un'istanza utilizzando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
