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

# Profils
{: #profiles}

Lorsque vous mettez à disposition {{site.data.keyword.vsi_is_full}}, vous pouvez choisir parmi trois familles de profils : Balanced, Compute et Memory. Un profil est une combinaison d'UC virtuelle et de RAM pouvant être instanciée rapidement pour démarrer une instance de serveur virtuel. Dans la console {{site.data.keyword.Bluemix_notm}}, vous pouvez choisir parmi les configurations de profil les plus courantes ou sélectionner dans une liste de profils la mieux adaptée à vos besoins.
{: shortdesc}

Les familles suivantes sont disponibles :

| Familles | Description |
| -------- | ----------- |
| [Balanced](#balanced) | Choix optimal pour les charges de travail de cloud communes nécessitant un équilibre entre les performances et l'évolutivité. Les profils Balanced (avec stockage en réseau) offrent de meilleures performances car les ressources ne sont pas trop sollicitées. |
| [Compute](#compute)  | Idéal pour les charges de travail avec un trafic Web de modéré à élevé. Les profils Compute sont recommandés pour les charges de travail avec des demandes d'unité centrale importantes, comme les fortes charges de travail de trafic Web, le traitement de lots de production et les serveurs Web frontaux. |
| [Memory](#memory) | Choix recommandé pour les charges de travail d'analyse en temps réel et de mise en cache de mémoire. Les profils Memory sont recommandés pour les charges de travail intensives de mémoire (mise en cache importantes ou analyse en mémoire, par exemple). |
{: caption="Tableau 1. Sélections de familles de serveurs virtuels" caption-side="top"}

## Balanced
{: #balanced}

Les profils Balanced offrent de meilleures performances car les ressources ne sont pas trop sollicitées. Les performances réseau vont de standard à premium.

L'offre est disponible dans les profils suivants :

| Profil | UC virtuelle | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="Tableau 2. Options du profil Balanced du serveur virtuel" caption-side="top"}

**Remarques sur le stockage :**

* Le volume d'amorçage principal SAN (100 Go) est automatiquement créé et connecté lorsque vous mettez une instance à disposition.
* Créez éventuellement un volume de données secondaire. Les profils de volume sont disponibles sous forme de trois niveaux d'E-S/s prédéfinis ou sous forme d'E-S/s personnalisées. Un [profil à 3 niveaux à usage général d'E-S/s](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) offre des performances d'E-S/s/Go adaptées à un profil Balanced d'instance VSI.
* La tarification des serveurs virtuels publics utilisant le stockage SAN comprend le processeur virtuel, la mémoire et le volume d'amorçage principal. Les volumes de données secondaires sont facturés séparément.

Tous les systèmes d'exploitation pris en charge (tels que CentOS, Debian, Ubuntu et Windows) sont disponibles avec cette offre.

## Compute
{: #compute}

Les profils Compute sont recommandés pour les charges de travail avec des demandes d'unité centrale importantes, comme les fortes charges de travail de trafic Web, le traitement de lots de production et les serveurs Web frontaux.

L'offre est disponible dans les profils suivants :

| Profil | UC virtuelle | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="Tableau 3. Options du profil Compute d'instance de serveur virtuel" caption-side="top"}

**Remarques sur le stockage :** 

* Le volume d'amorçage principal SAN (100 Go) est automatiquement créé et connecté lorsque vous mettez une instance à disposition.
* Créez éventuellement un volume de données secondaire. Les profils de volume sont disponibles sous forme de trois niveaux d'E-S/s prédéfinis ou sous forme d'E-S/s personnalisées. Un profil à [5 niveaux d'E-S/s](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) offre des performances d'E-S/s/Go adaptées à un profil Compute d'instance VSI.
* La tarification des serveurs virtuels publics utilisant le stockage SAN comprend le processeur virtuel, la mémoire et le volume d'amorçage principal. Les volumes de données secondaires sont facturés séparément.

Tous les systèmes d'exploitation pris en charge (tels que CentOS, Debian, Ubuntu et Windows) sont disponibles avec cette offre. 

## Memory 
{: #memory}

Les profils Memory sont recommandés pour les charges de travail intensives de mémoire (mise en cache importantes ou analyse en mémoire, par exemple).

L'offre est disponible dans les profils suivants :

| Profil | UC virtuelle | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="Tableau 4. Options du profil Memory d'instance de serveur virtuel" caption-side="top"}

**Remarques sur le stockage :** 

* Le volume d'amorçage principal SAN (100 Go) est automatiquement créé et connecté lorsque vous mettez une instance à disposition.
* Créez éventuellement un volume de données secondaire. Les profils de volume sont disponibles sous forme de trois niveaux d'E-S/s prédéfinis ou sous forme d'E-S/s personnalisées. Un profil à [10 niveaux d'E-S/s](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) offre des performances d'E-S/s/Go adaptées à un profil Memory d'instance VSI.
* La tarification des serveurs virtuels publics utilisant le stockage SAN comprend le processeur virtuel, la mémoire et le volume d'amorçage principal. Les volumes de données secondaires sont facturés séparément.

Tous les systèmes d'exploitation pris en charge (tels que CentOS, Debian, Ubuntu et Windows) sont disponibles avec cette offre. 

## Affichage des configurations de profil
{: #popularprofiles}

Vous pouvez afficher les configurations de profil disponibles à l'aide de la console {{site.data.keyword.cloud_notm}} ou de l'interface de ligne de commande. Dans la console {{site.data.keyword.cloud_notm}}, vous pouvez choisir parmi les configurations de profil courantes qui prennent en charge les cas d'utilisation les plus courants.

### Utilisation de la console IBM Cloud
1. Dans la console {{site.data.keyword.cloud_notm}}, accédez à **l'icône Menu ![Icône Menu](../icons/icon_hamburger.svg) > Infrastructure VPC > Compute > Instances de serveur virtuel**.
2. Sur cette page, cliquez sur **Nouvelle instance**.
3. Vous pouvez sélectionner une configuration de profil dans **Profils courants** ou cliquez sur **Tous les profils** pour afficher des configurations supplémentaires.

### Utilisation de l'interface de ligne de commande
Pour afficher la liste des profils disponibles à l'aide de la CLI, exécutez la commande suivante :
```
$ ibmcloud is instance-profiles
```
{:codeblock}

Lorsque vous utilisez la ligne de commande, les informations suivantes décrivent ce que la sortie représente. Les tailles de profil ont différents rapports processeur/mémoire, conçus pour différentes charges de travail :

*  "b" est Balanced, soit un rapport de 1:2 ou 1:4
*  "c" est Compute (plus élevé sur les processeurs), soit un rapport 1:1
*  "m" est Memory (plus élevé sur la mémoire), soit un rapport de 1:8
