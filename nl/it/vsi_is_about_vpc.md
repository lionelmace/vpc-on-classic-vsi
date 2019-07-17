---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# Informazioni su Virtual Servers for VPC
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}} ti fornisce l'accesso a tutti i vantaggi di {{site.data.keyword.vpc_short}}, inclusi l'isolamento della rete, la sicurezza e la flessibilità. 
{:shortdesc}

## Che cos'è {{site.data.keyword.vpc_short}}?
Un {{site.data.keyword.vpc_short}} è una rete virtuale collegata al tuo account cliente. Ti offre un punto di ingresso conveniente che fornisce la sicurezza cloud e la possibilità di eseguire il ridimensionamento in modo dinamico man mano che ne hai bisogno. Ti fornisce un controllo dettagliato sulla tua infrastruttura virtuale e sulla tua segmentazione del traffico di rete.
{: shortdesc}

Per ulteriori informazioni su {{site.data.keyword.vpc_short}}, vedi [Informazioni su IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about).

## Che cos'è {{site.data.keyword.vsi_is_short}}?
Con {{site.data.keyword.vsi_is_short}}, puoi creare un'istanza composta dalle tue risorse di calcolo virtuali e la capacità risultante all'interno di un {{site.data.keyword.vpc_short}}. Quando esegui il provisioning di un'istanza, selezioni un profilo dell'istanza che corrisponde alla quantità di potenza di memoria e calcolo di cui hai bisogno per l'applicazione o il software su cui pianifichi di eseguire l'istanza. Dopo aver eseguito il provisioning di un'istanza, controlli e gestisci tali risorse dell'infrastruttura. Ogni account ha un limite sul numero di istanze in esecuzione tra i server. Per ulteriori informazioni su questo limite, vedi [FAQ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). 

## In quale modo le istanze del server virtuale per {{site.data.keyword.vpc_short}} sono diverse dalle altre offerte di server virtuale di IBM?

Nell'offerta IBM Cloud Virtual Server odierna, le istanze utilizzano la sottorete nativa e la rete VLAN per comunicare tra loro all'interno di un data center (e un singolo pod). L'utilizzo della sottorete e della rete VLAN in un pod funziona bene finché devi effettuare un ridimensionamento incrementale o disporre di grandi richieste di risorse virtuali che richiedono la creazione di risorse tra i pod. (Aggiungere dei dispositivi per lo spanning della VLAN può essere caro e complicato.) 

{{site.data.keyword.vpc_short}} aggiunge un livello di orchestrazione della rete che elimina il limite dei pod, creando una capacità infinita per il ridimensionamento delle istanze. Il livello di orchestrazione della rete gestisce tutta la rete per tutte le istanze del server virtuale presenti all'interno di un {{site.data.keyword.vpc_short}} tra le regioni e le zone. Con le funzionalità di rete definite dal software fornite da {{site.data.keyword.vpc_short}}, hai più opzioni per [VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc), istanze con più vNIC e dimensioni di [sottorete](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets) più grandi. Per ulteriori informazioni, vedi [Informazioni sulla rete per VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc). 

{{site.data.keyword.vsi_is_short}} dispone inoltre delle seguenti funzioni che forniscono un'esperienza utente più semplice e dei risparmi sui costi:
* Nuova console {{site.data.keyword.cloud_notm}}
* Nuove API e CLI Virtual Private Cloud
* Nuovo modello di fatturazione con livelli di sconto sull'utilizzo prolungato, come descritto in [Prezzi](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)

{{site.data.keyword.vsi_is_short}} non sono compatibili con le offerte del server virtuale classico. Se sei interessato in una delle offerte {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} sull'infrastruttura classica, vedi [Server virtuali IBM Cloud](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial).
{:note}




