---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

keywords: Windows instance, encrypt password, decrypt password, retrieve password

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Connessione alla tua istanza Windows
{: #connecting-to-your-windows-instance}

Dopo aver creato la tua istanza Windows {{site.data.keyword.vsi_is_full}}, ti puoi connettere ad essa completando questa procedura.
{:shortdesc}

## Prima di cominciare
{: #prereqs-connect-windows}

Assicurati di completare i seguenti prerequisiti prima di cominciare:

1. Chiedi al tuo amministratore dell'account di concederti l'accesso per richiamare la password dalla tua istanza del server virtuale. Per ulteriori informazioni, rivedi le [autorizzazioni utente](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources).
2. Crea un nuovo gruppo di sicurezza o aggiungi una regola a quello predefinito per abilitare l'accesso in entrata per la porta predefinita del desktop remoto, 3389. Per ulteriori informazioni, vedi [Utilizzo dei gruppi di sicurezza](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups).
3. Assicurati che il traffico in entrata tramite la porta TCP/IP 3389 sia consentito sull'ACL predefinito del VPC. Per ulteriori informazioni, vedi [Configurazione degli ACL di rete](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls).
4. Verifica che OpenSSL sia installato. Per decrittografare correttamente la tua password, devi eseguire OpenSSL e non LibreSSL. Per ulteriori informazioni, vedi [OpenSSL Downloads ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.openssl.org/source/){: new_window}.

LibreSSL non è compatibile per la decrittografia della tua password. Devi eseguire OpenSSL per decrittografare la tua password.
{:important}

## Effettua connessione
{: #getting-connected-windows}

Dopo aver creato la tua istanza Windows e completato i prerequisiti, completa la seguente procedura per connetterti alla tua stanza Windows.

1. Esegui la query dello stato della tua istanza immettendo il seguente comando:
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  Quando l'istanza mostra che è in esecuzione (`running`), sei pronto per richiamare i valori di inizializzazione per ottenere la tua password. 

2. Immetti il seguente comando per inizializzare la tua istanza:

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  Questo comando visualizza la tua password crittografata, che viene automaticamente generata quando crei un'istanza utilizzando un'immagine Windows.

3. Ora devi decrittografare la tua password tramite un processo di decrittografia manuale. Per decrittografare la tua password, immetti il seguente comando:

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  dove `~/examplepwd` è il file in cui hai salvato la tua password crittografata come indicato nel passo 2.  
  
  LibreSSL, incluso con macOS, non supporta gli algoritmi di hash SHA2 necessari per decrittografare la password, creando degli errori `Public Key operation error`. Puoi ottenere le librerie OpenSSL standard utilizzando uno strumento di gestione dei pacchetti o installandole manualmente. 
  {:note}

4. Dopo aver decrittografato la tua password, puoi facoltativamente associare un indirizzo IP mobile alla tua istanza Windows in modo da poterti connettere ad essa da un'ubicazione internet. Immetti il seguente comando per associare un indirizzo IP mobile alla tua istanza:

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. Ora hai quello che ti serve per connetterti alla tua istanza Windows: la password decrittografata e l'indirizzo IP mobile. Utilizza il tuo client desktop remoto preferito per connetterti alla tua istanza. Per connetterti alla tua istanza, fornisci l'indirizzo IP mobile e la password decrittografata. Per impostazione predefinita il nome utente è `Administrator`.

## Passi successivi
{: #next-manage-instances}

Dopo esserti connesso alla tua istanza, puoi [gestire le tue istanze utilizzando la console {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) o [gestire le tue istanze utilizzando la CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
