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

# Benutzerdaten
{: #user-data}
[comment]: # (Verlinktes Hilfethema)

Beim Erstellen einer {{site.data.keyword.vsi_is_full}}-Instanz können Sie Benutzerdaten hinzufügen, die automatisch allgemeine Konfigurationstasks oder Scripts ausführen. Im Feld **Benutzerdaten** des Bestellformulars können Sie optionale Cloud-init-Benutzerdaten für den Server eingeben.
{:shortdesc}

## Beispiele von Benutzerdaten für Linux 
{: #user-data-examples-for-linux}

Das folgende Beispiel zeigt, wie ein Linux-Benutzer einen neuen Benutzer hinzufügen und dem Benutzer einen autorisierten SSH-Schlüssel zur Verfügung stellen kann. Im Feld **Name** wird der öffentliche Schlüssel zu `~/.ssh/authorized_keys` hinzugefügt. 

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
        - <öffentlicher_ssh-schlüssel>
```
{:codeblock}

Das nächste Beispiel für ein Shell-Script zeigt, wie ein Linux-Benutzer einen SSH-Schlüssel für den aktuellen Benutzer hinzufügen kann.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

Sie können eines dieser Beispiele direkt im Feld **Benutzerdaten** einfügen. Die Benutzerdaten sind dann während der Bereitstellung für die virtuelle Serverinstanz verfügbar. 

Weitere Benutzerdatenbeispiele für Linux und Informationen finden Sie auf der Seite [Cloud config examples. ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}

## Beispiel von Benutzerdaten für Windows
{: #user-data-example-for-windows}

Das folgende Beispiel zeigt, wie Benutzerdaten an eine Windows-Instanz übergeben werden können. Sie können dieses Beispiel kopieren und direkt im Feld **Benutzerdaten** einfügen.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

Weitere Benutzerdatenbeispiele für Windows und Informationen finden Sie auf der Seite [Cloudbase-init 1.0 documentation. ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}
