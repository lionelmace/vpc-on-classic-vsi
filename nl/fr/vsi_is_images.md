---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Images
{: #images}

Lorsque vous mettez à disposition {{site.data.keyword.vsi_is_full}}, vous pouvez effectuer votre sélection parmi les images stockées prises en charge. L'image que vous sélectionnez détermine le système d'exploitation mis à disposition pour votre instance. 
{:shortdesc}

## Images stockées
{: #stock-images}

Les systèmes d'exploitation suivants sont disponibles en tant qu'images stockées lorsque vous créez un serveur virtuel.
* CentOS 7.x
* Debian 8.x, 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04, 18.04
* Windows 2012, 2012 R2, 2016

Lorsque vous commandez une instance, les images sont activées par cloud-init pour optimiser les temps de mise à disposition. Avec une image activée par cloud-init, vous pouvez fournir des données utilisateur. Dans la zone **Données utilisateur** du formulaire de commande, vous pouvez saisir des données utilisateur cloud-init facultatives, pour le serveur. Pour plus d'informations sur les données utilisateur et l'automatisation, voir [Données utilisateur](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).

## Virtualisation
{: #virtualization}
Les instances nécessitent une image prenant en charge le mode de démarrage HVM (Hardware Virtualization Machine). Le type de virtualisation HVM permet à une image de s'exécuter directement sur un serveur virtuel, ce qui est requis pour la mise en réseau avancée et les fonctionnalités GPU.
