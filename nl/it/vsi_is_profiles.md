---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Profili
{: #profiles}

Quando esegui il provisioning di {{site.data.keyword.vsi_is_full}}, puoi effettuare una selezione tra tre famiglie di profili: bilanciato, calcolo e memoria. Un profilo è una combinazione di vCPU e RAM che può essere istanziato velocemente per avviare un'istanza del server virtuale. Nella console {{site.data.keyword.Bluemix_notm}}, puoi scegliere tra le configurazioni del profilo popolari o da un elenco di profili che meglio si adattano ai tuoi bisogni.
{: shortdesc}

Sono disponibili le seguenti famiglie:

| Famiglie | Descrizione |
| -------- | ----------- |
| [Bilanciato](#balanced) | Migliore per i carichi di lavoro cloud comuni che richiedono un bilanciamento di prestazioni e scalabilità. I profili bilanciati (con l'archiviazione assegnata per rete) forniscono prestazioni più elevate, poiché le risorse non possono sottoscrivere più della disponibilità effettiva. |
| [Calcolo](#compute)  | Migliore per i carichi di lavoro con traffico web da moderato a elevato. I profili di calcolo sono migliori per i carichi di lavoro con richieste di CPU intensiva, come i carichi di lavoro di traffico web elevato, l'elaborazione batch di produzione e i server web di frontend. |
| [Memoria](#memory) | Migliore per la memorizzazione nella cache e i carichi di lavoro di analisi in tempo reale. I profili di memoria sono migliori per i carichi di lavoro con uso intensivo di memoria, come i grandi carichi di lavoro con memorizzazione in cache, le applicazioni database intensive o i carichi di lavoro di analisi nella memoria. |
{: caption="Tabella 1. Selezioni della famiglia del server virtuale" caption-side="top"}

## Bilanciato
{: #balanced}

I profili bilanciati forniscono prestazioni più elevate, poiché le risorse non possono sottoscrivere più della disponibilità effettiva. Le prestazioni di rete vanno da standard a premium.

L'offerta è disponibile nei seguenti profili:

| Profilo | vCPU | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="Tabella 2. Opzioni di profilo bilanciato del server virtuale" caption-side="top"}

**Note di archiviazione:**

* Il volume di avvio primario SAN (100GB) viene automaticamente creato e collegato quando esegui il provisioning di un'istanza.
* Facoltativamente, crea un volume di dati secondario. I profili del volume sono disponibile come tre livelli IOPS predefiniti o come un'IOPS personalizzato. Un [profilo di livello di utilizzo generico con 3 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornisce prestazioni IOPS/GB adatte a un profilo bilanciato VSI.
* I prezzi per i server virtuali pubblici che utilizzano l'archiviazione SAN includono CPU virtuale, memoria e volume di avvio primario. I volumi di dati secondari hanno dei prezzi separati.

Tutti i sistemi operativi supportati (ad esempio CentOS, Debian, Ubuntu e Windows) sono disponibili con questa offerta.

## Calcolo
{: #compute}

I profili di calcolo sono migliori per i carichi di lavoro con richieste di CPU intensiva, come i carichi di lavoro di traffico web elevato, l'elaborazione batch di produzione e i server web di frontend.

L'offerta è disponibile nei seguenti profili:

| Profilo | vCPU | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="Tabella 3. Opzioni di profilo di calcolo dell'istanza del server virtuale" caption-side="top"}

**Note di archiviazione:** 

* Il volume di avvio primario SAN (100GB) viene automaticamente creato e collegato quando esegui il provisioning di un'istanza.
* Facoltativamente, crea un volume di dati secondario. I profili del volume sono disponibile come tre livelli IOPS predefiniti o come un'IOPS personalizzato. Un profilo [al livello di 5 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornisce le prestazioni IOPS/GB adatte per un profilo di calcolo VSI.
* I prezzi per i server virtuali pubblici che utilizzano l'archiviazione SAN includono CPU virtuale, memoria e volume di avvio primario. I volumi di dati secondari hanno dei prezzi separati.

Tutti i sistemi operativi supportati (ad esempio CentOS, Debian, Ubuntu e Windows) sono disponibili con questa offerta. 

## Memoria 
{: #memory}

I profili di memoria sono migliori per i carichi di lavoro con uso intensivo di memoria, come i grandi carichi di lavoro con memorizzazione in cache, le applicazioni database intensive o i carichi di lavoro di analisi nella memoria.

L'offerta è disponibile nei seguenti profili:

| Profilo | vCPU | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="Tabella 4. Opzioni di profilo di memoria dell'istanza del server virtuale" caption-side="top"}

**Note di archiviazione:** 

* Il volume di avvio primario SAN (100GB) viene automaticamente creato e collegato quando esegui il provisioning di un'istanza.
* Facoltativamente, crea un volume di dati secondario. I profili del volume sono disponibile come tre livelli IOPS predefiniti o come un'IOPS personalizzato. Un profilo [al livello di 10 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornisce le prestazioni IOPS/GB adatte per un profilo di memoria VSI.
* I prezzi per i server virtuali pubblici che utilizzano l'archiviazione SAN includono CPU virtuale, memoria e volume di avvio primario. I volumi di dati secondari hanno dei prezzi separati.

Tutti i sistemi operativi supportati (ad esempio CentOS, Debian, Ubuntu e Windows) sono disponibili con questa offerta. 

## Visualizzazione delle configurazioni del profilo
{: #popularprofiles}

Puoi visualizzare le configurazioni del profilo disponibili utilizzando la console {{site.data.keyword.cloud_notm}} o la CLI. Nella console {{site.data.keyword.cloud_notm}}, puoi scegliere tra le configurazioni del profilo popolari che supportano i casi di utilizzo più comuni.

### Utilizzo della console IBM Cloud
1. Nella console {{site.data.keyword.cloud_notm}}, vai a **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. Da questa pagina, fai clic su **New instance**.
3. Puoi selezionare una configurazione del profilo da **Popular profiles** oppure fare clic su **All profiles** per visualizzare ulteriori configurazioni.

### Utilizzo della CLI
Per visualizzare l'elenco di profili disponibili utilizzando la CLI, immetti il seguente comando:
```
$ ibmcloud is instance-profiles
```
{:codeblock}

Quando utilizzi la riga di comando, le seguenti informazioni descrivono cosa rappresenta l'output. Le dimensioni del profilo hanno rapporti di CPU e memoria diversi, progettati per carichi di lavoro differenti:

*  "b" è bilanciato, con un rapporto 1:2 o 1:4
*  "c" è calcolo (con maggiori CPU), con un rapporto 1:1
*  “m” è memoria (con maggiore memoria), con un rapporto 1:8
