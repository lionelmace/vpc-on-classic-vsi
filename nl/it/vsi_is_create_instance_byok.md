---

copyright:
  years: 2019
lastupdated: "2019-06-05"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Creazione delle istanze del server virtuale con la crittografia gestita dal cliente
{: #creating-instances-byok}

Puoi creare {{site.data.keyword.vsi_is_full}} che utilizzano la crittografia gestita dal cliente per i volumi di archiviazione blocchi quando hai eseguito il provisioning di un servizio di gestione delle chiavi che include la tua chiave di crittografia dei dati. Per impostazione predefinita, viene eseguito il provisioning delle istanze con un volume di avvio che include la crittografia gestita dal provider. Puoi eseguire il provisioning di istanze che utilizzano la crittografia gestita dal cliente per i volumi di archiviazione blocchi dalla console {{site.data.keyword.cloud_notm}} o utilizzando l'interfaccia di riga comando (CLI).
{:shortdesc}

## Servizi di gestione delle chiavi supportati per la crittografia gestita dal cliente
{: #kms-for-byok}

Puoi utilizzare il servizio di gestione delle chiavi che meglio si adatta ai tuoi bisogni. {{site.data.keyword.keymanagementserviceshort}} e {{site.data.keyword.hscrypto}} (disponibili in alcune [regioni](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)) utilizzano un'API del provider di chiavi comune per fornire un approccio coerente per la gestione delle chiavi di crittografia.  Dietro le quinte, i data center {{site.data.keyword.cloud_notm}} forniscono un HSM (hardware security module) dedicato per proteggere le tue chiavi.  I seguenti servizi di gestione delle chiavi sono supportati con la crittografia gestita dal cliente per i volumi di archiviazione blocchi: 

| Servizio di gestione delle chiavi | Certificazione di crittografia HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conformità FIPS 140-2 *Level 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conformità FIPS 140-2 *Level 4* |
{: caption="Tabella 1. Opzioni di servizi di gestione delle chiavi disponibili" caption-side="top"}

## Prerequisiti
{: #byok-vsi-prereqs}

Per creare un'istanza del server virtuale che utilizza la crittografia gestita dal cliente per i volumi di archiviazione blocchi, devi aver eseguito il provisioning di un servizio di gestione delle chiavi e aver aggiunto una chiave root cliente. Devi anche autorizzare l'accesso tra Cloud Block Storage e il servizio di gestione delle chiavi. Dopo aver completato questi prerequisiti, puoi iniziare a creare delle istanze che utilizzano la crittografia gestita dal cliente per i volumi di archiviazione blocchi. 

La seguente procedura di esempio è specifica per {{site.data.keyword.keymanagementserviceshort}}, ma il flusso generale si applica anche a {{site.data.keyword.hscrypto}}. Se stai utilizzando {{site.data.keyword.hscrypto}}, vedi le [informazioni su {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) per delle istruzioni corrispondenti.
{:note}

1. Esegui il provisioning del servizio [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision). 
   
   Il provisioning di una nuova istanza del servizio {{site.data.keyword.keymanagementserviceshort}} garantisce che siano inclusi gli aggiornamenti più recenti necessari per la crittografia gestita dal cliente dei volumi di archiviazione blocchi. 
   {: tip}
   
2. [Crea](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) o
[importa](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) una chiave root (CRK) in
{{site.data.keyword.keymanagementservicelong_notm}}.
3. Da IBM {{site.data.keyword.iamshort}} (IAM), [autorizza l'accesso](/docs/iam?topic=iam-serviceauth#serviceauth) tra **Cloud
Block Storage** (servizio di origine) e **{{site.data.keyword.keymanagementserviceshort}}** (servizio di destinazione).

## Provisioning delle istanze del server virtuale con volumi che utilizzano la crittografia gestita dal cliente
{: #provision-byok-ui}

Quando esegui il provisioning di un'istanza del server virtuale, puoi specificare la crittografia gestita dal cliente per il tuo volume di avvio e per tutti i volumi di dati che vuoi aggiungere al momento del provisioning. Se vuoi, puoi utilizzare una combinazione di crittografia gestita dal provider e dal cliente per i volumi associati alla tua istanza.

1. Nella console [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.cloud.ibm.com/vpc), vai a **Menu icon ![Icona menu](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**. Fai clic su **New instance** e completa i campi obbligatori. (Per ulteriori informazioni sulla creazione delle istanze, vedi [Creazione delle istanze del server virtuale](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).) 
2. Nella sezione **Boot volume**, la modalità di crittografia predefinita è _Provider managed_. Per specificare la crittografia gestita dal cliente, fai clic sull'icona matita nella riga del volume di avvio. Nella pagina **Edit boot volume**, aggiorna i campi nella sezione **Encryption**. Per ulteriori informazioni, consulta la seguente tabella. Quando hai terminato le tue modifiche, fai clic su **Apply**.
3. Nella sezione **Attached block storage volume**, puoi fare clic su **New block storage volume** per aggiungere un volume di dati e specificare la crittografia gestita dal cliente se scegli questa opzione. Nella pagina **New block storage volume**, aggiorna i campi nella sezione **Encryption**. Per ulteriori informazioni, consulta la seguente tabella. Quando hai terminato le tue modifiche, fai clic su **Attach**.

| Campo | Valore |
| ----- | ----- |
| Crittografia | _Provider managed_ è la modalità di crittografia predefinita. Per utilizzare la crittografia gestita dal cliente, seleziona un servizio di gestione delle chiavi dall'elenco a discesa. L'istanza del servizio di gestione delle chiavi dovrebbe includere la chiave root del cliente che vuoi utilizzare per la crittografia gestita dal cliente. |
| Istanza del servizio di crittografia | Se hai eseguito il provisioning di più istanze del servizio di gestione delle chiavi nel tuo account, seleziona quella che include la chiave root del cliente che vuoi utilizzare per la crittografia gestita dal cliente. |
| Nome chiave | Seleziona la chiave di crittografia dei dati all'interno dell'istanza del servizio di gestione delle chiavi che vuoi utilizzare per crittografare il volume. | 
| ID chiave | Visualizza l'ID chiave associato alla chiave di crittografia dei dati che hai selezionato. | 
{: caption="Tabella 1. Valori per specificare la crittografia gestita dal cliente dei volumi." caption-side="top"}

## Utilizzo della CLI per eseguire il provisioning di istanze e volumi con la crittografia gestita dal cliente
{: #provision-byok-cli}

Per utilizzare la CLI per creare un'istanza del server virtuale con dei volumi che utilizzano la crittografia gestita dal cliente, puoi utilizzare il comando `ibmcloud is instance-create` e fare riferimento a un JSON per collegare i volumi che utilizzano la crittografia gestita dal cliente. 

1. Ottieni il CRN della chiave root nella tua istanza del servizio di gestione delle chiavi desiderata. Il seguente esempio è specifico per {{site.data.keyword.keymanagementserviceshort}}. 
    
    1. Se ancora non hai installato il plugin CLI {{site.data.keyword.keymanagementserviceshort}}, installalo immettendo il seguente comando: 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. Elenca le istanze del servizio {{site.data.keyword.keymanagementserviceshort}} per il tuo account immettendo il seguente comando:
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       Per questo esempio, vedrai una risposta simile al seguente output:
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. Richiama l'ID istanza per l'istanza del servizio {{site.data.keyword.keymanagementserviceshort}} in cui sono archiviate le chiavi root del cliente immettendo il seguente comando.  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       dove _Key Protect-17_ è la tua istanza del servizio {{site.data.keyword.keymanagementserviceshort}} desiderata.
    
       Per questo esempio, vedrai una risposta simile al seguente output:
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       dove l'ID istanza è la stringa che segue il simbolo `::` finale nel CRN, `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`. 
    
    4. Elenca le chiavi disponibili e i rispetti CRN associati alla tua istanza del servizio {{site.data.keyword.keymanagementserviceshort}} desiderata immettendo il seguente comando:
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       dove _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ è l'ID istanza della tua istanza del servizio {{site.data.keyword.keymanagementserviceshort}} desiderata.
       
       Per questo esempio, vedrai una risposta simile al seguente output:
       ```
       Retrieving keys...
              
       SUCCESS
               
       Key ID                                 Key Name               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. Utilizza il comando [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) e collega i file JSON necessari che specificano la crittografia gestita dal cliente per il volume di avvio e per tutti i volumi di dati secondari che vuoi includere. Il parametro `encryption_key` deve includere un CRN valido per la chiave root nel servizio Key Protect. Vedi i seguenti [esempi di file JSON](#vsi-vol-attachment-json) di un JSON del volume di avvio e un JSON del volume secondario. (Per ulteriori informazioni sulla creazione delle istanze, vedi [Creazione delle istanze del server virtuale (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli).)

## Creazione di un allegato del volume nel formato JSON
{: #vsi-vol-attachment-json}

Quando crei un volume di avvio o di dati durante il provisioning della VSI, devi specificare un file JSON per definire i parametri del volume. Vedi i seguenti esempi di file JSON.

### File JSON del volume di avvio di esempio
{: #boot-volume-byok-json}

Il seguente esempio definisce un volume di avvio per un utilizzo generico e specifica il parametro `encryption key` per la crittografia gestita dal cliente.

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      },
      "encryption_key":{  
         "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### File JSON del volume secondario di esempio
{: #secondary-volume-byok-json}

Il seguente esempio definisce un volume secondario (dati) per un utilizzo generico e specifica il parametro `encryption key` per la crittografia gestita dal cliente.

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         },
         "encryption_key":{  
            "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}
