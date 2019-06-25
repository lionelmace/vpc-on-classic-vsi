---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Clés SSH
{: #ssh-keys}
[comment]: # (rubrique d'aide liée)

Lorsque vous mettez à disposition {{site.data.keyword.vsi_is_full}}, vous devez sélectionner une clé SSH existante ou télécharger une nouvelle clé SSH à utiliser avant de pouvoir créer l'instance. Les serveurs utilisent les clés SSH pour identifier un utilisateur ou une instance via une cryptographie à clé publique. Les clés SSH sont constituées d’une combinaison alphanumérique et sont spécifiques à l’instance à laquelle elles sont attribuées. Vous pouvez ajouter, modifier ou supprimer des clés SSH à l'aide de la console {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Les clés SSH permettent d'accéder à une instance sans utiliser de mot de passe des clients correspondants pour chaque clé publique implémentée sur l'instance. En ajoutant une clé SSH à une instance, ce que vous pouvez faire lors de la mise à disposition, vous pouvez accéder à l'instance avec la clé correspondante au lieu d'un mot de passe. Vous pouvez ajouter des clés SSH à une instance uniquement lors de la création initiale de celle-ci. Après la création d’une instance Linux, vous pouvez modifier les clés directement dans le répertoire `~/.ssh/` de l’instance.

La connexion à votre instance avec un mot de passe n'est pas prise en charge. Si vous disposez d'une instance Windows, la clé SSH est utilisée pour déchiffrer votre mot de passe. Pour plus d'informations, voir [Connexion à votre instance Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance).
{:note}

## Localisation ou génération de votre clé SSH
{: #locating-or-generating-your-ssh-key}

Votre clé SSH doit être disponible. Pour localiser votre clé SSH ou générer une clé SSH, effectuez l’une des étapes suivantes.

 * Localisez une clé SSH : recherchez un fichier appelé `id_rsa.pub` dans le répertoire `.ssh` de votre répertoire personnel, par exemple, `/Users/<USERNAME>/.ssh/id_rsa.pub`. Le fichier commence par `ssh-rsa` et se termine par votre adresse électronique.

* Générez une clé SSH : si vous ne possédez pas de clé SSH publique ou si vous avez oublié le mot de passe d'une clé existante, générez-en une nouvelle en exécutant la commande `ssh-keygen` et en répondant aux invites. Par exemple, vous pouvez générer une clé SSH sur votre serveur Linux en exécutant la commande `ssh-keygen -t rsa -C "user_ID"`. Cette commande génère deux fichiers. La clé publique générée se trouve dans le fichier `<your key>.pub`.

  Si vous utilisez OpenSSH version 7.8 ou ultérieure et prévoyez d'utiliser la clé SSH pour accéder à une instance Windows, vous devez utiliser la commande suivante pour générer la clé au format PEM. `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

Pour plus d'informations sur la création, la modification ou la suppression de clés SSH, voir [ Gestion des clés SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
