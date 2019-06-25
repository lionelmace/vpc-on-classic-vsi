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

# Données utilisateur
{: #user-data}
[comment]: # (rubrique d'aide liée)

Lorsque vous créez une instance {{site.data.keyword.vsi_is_full}}, vous pouvez ajouter des données utilisateur qui effectuent automatiquement des tâches de configuration courantes ou exécutent des scripts. Dans la zone **Données utilisateur** du formulaire de commande, vous pouvez saisir des données utilisateur cloud-init facultatives, pour le serveur.
{:shortdesc}

## Exemple de données utilisateur pour Linux 
{: #user-data-examples-for-linux}

L'exemple suivant montre comment un utilisateur Linux peut ajouter un nouvel utilisateur et lui fournir une clé SSH autorisée. La clé publique sera ajoutée à `~/.ssh/authorized_keys` dans la zone **Nom**. 

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

Voici un autre exemple de script shell montrant comment un utilisateur Linux peut ajouter une clé SSH à l'utilisateur en cours.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

Vous pouvez coller l'un de ces exemples directement dans la zone **Données utilisateur**. Les données utilisateur sont ensuite disponibles pour l'instance de serveur virtuel lors de la mise à disposition. 

Pour plus d'informations et d'exemples de données utilisateur Linux, voir [Exemples de configuration dans le cloud ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}.

## Exemple de données utilisateur pour Windows
{: #user-data-example-for-windows}

L'exemple suivant montre comment les données utilisateur peuvent être transmises à une instance Windows. Vous pouvez copier et coller cet exemple directement dans la zone **Données utilisateur**.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

Pour plus d'informations et d'exemples de données utilisateur Windows, voir la [documentation Cloudbase-init 1.0 ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}.
