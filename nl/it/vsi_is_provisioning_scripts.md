---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Dati utente
{: #user-data}
[comment]: # (argomento della guida collegato)

Quando crei un'istanza {{site.data.keyword.vsi_is_full}}, puoi aggiungere dei dati utente che eseguono automaticamente le attività di configurazione comuni o eseguono gli script. Nel campo **User Data** sul modulo d'ordine, puoi immettere i dati utente cloud-init facoltativi per il server.
{:shortdesc}

## Esempi di dati utente per Linux 
{: #user-data-examples-for-linux}

Il seguente esempio mostra come un utente Linux può aggiungere un nuovo utente e fornirgli una chiave SSH autorizzata. Il campo **Name** avrà la chiave pubblica aggiunta a `~/.ssh/authorized_keys`. 

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

Questo è un altro esempio di uno script shell che mostra come un utente Linux può aggiungere una chiave SSH all'utente corrente.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

Puoi incollare uno di questi esempi direttamente nel campo **User Data**. I dati utente sono poi disponibili per l'istanza del server virtuale durante il provisioning. 

Per ulteriori informazioni ed esempi di dati utente Linux, vedi [Cloud config examples ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}.

## Esempio di dati utente per Windows
{: #user-data-example-for-windows}

Il seguente esempio mostra come i dati utente possono essere passati a un'istanza Windows. Puoi copiare e incollare questo esempio direttamente nel campo **User Data**.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

Per ulteriori informazioni ed esempi di dati utente Windows, vedi [Cloudbase-init 1.0 documentation ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}.
