---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Connessione alla tua istanza Linux
{: #connecting-to-your-linux-instance}

Dopo aver creato la tua istanza Linux {{site.data.keyword.vsi_is_full}}, ti puoi connettere ad essa completando questa procedura.
{:shortdesc}

## Individuazione dell'indirizzo IP mobile
{: #locating-floating-ip-address}

Se devi individuare il tuo indirizzo IP mobile per l'istanza a cui vuoi connetterti, completa la seguente procedura. Se già conosci il tuo indirizzo IP mobile, puoi andare a [Effettuare la connessione](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected). 

1. Devi identificare il tuo ID IP mobile prima di poter individuare il tuo indirizzo IP mobile. Immetti il seguente comando per identificare il tuo ID IP mobile:

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output (utilizzando una x generica e i valori 123 solo per gli scopi dell'esempio):

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. Ora che hai il tuo ID IP mobile, puoi individuare il tuo indirizzo IP mobile immettendo il seguente comando.

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   Per questo esempio, vedrai una risposta simile al seguente output (utilizzando una x generica e i valori 123 solo per gli scopi dell'esempio):

   ```
   ID               12345x67-8901-234x-5678-9xx01xx23x4x   
   Address          123.45.678.90   
   Name             my-instance   
   Target           primary(1xx2x34x-.)   
   Target Type      intf   
   Target IP        12.345.6.78   
   Created          1 week ago   
   Status           available   
   Zone             us-south-1   
   Resource Group   -   
   Tags             -   
   ```
   {:screen}

Facoltativamente, puoi individuare l'indirizzo IP mobile associato all'istanza a cui vuoi connetterti tramite la console {{site.data.keyword.cloud_notm}}.
{:tip}

## Effettua connessione
{: #getting-connected}

I seguenti valori restituiti sono solo per scopi di esempio.

1. Per connetterti alla tua istanza, utilizza la tua chiave privata ed immetti il seguente comando:

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   Ricevi una risposta simile al seguente esempio. Quando ti viene richiesto di continuare con la connessione, immetti `yes`.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   Stai ora eseguendo l'accesso al tuo server.

2. Quando sei pronto ad interrompere la tua connessione, immetti il seguente comando:

   ```
   # exit
   ```
   {:codeblock}

## Passi successivi
{: #next-managing-instances}

Dopo esserti connesso alla tua istanza, puoi [gestire le tue istanze utilizzando la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) o [gestire le tue istanze utilizzando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
