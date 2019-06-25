---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Traitement des incidents liés à Virtual Servers for VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
Si vous rencontrez des difficultés avec vos instances {{site.data.keyword.vsi_is_full}}, examinez les causes possibles suivantes.

## Erreur 409 : conflit lors de la création d'une action d'instance

Vous ne pouvez pas créer certaines actions d'instance si le statut de votre instance est en conflit avec une autre action. Par exemple, si votre statut d'instance est `arrêté`, et que vous tentez de créer une action `redémarrage`, le système renvoie une erreur 409.

| Statut      | Action     | Conflit |
| ----------- | ---------- | -------- |
| En cours d'exécution     | démarrage      | oui      |
| Arrêté     | pas de démarrage  | oui      |
| Hors exécution | réamorçage     | oui      |

## Le statut de l'instance est bloqué sur `en cours de suppression`

Lorsque vous répertoriez des instances et recherchez le statut d'une instance bloquée sur `en cours de suppression`, utilisez l'API d'affichage d'instances `/instances/{instance_id}` pour mettre à jour le statut de votre instance de serveur virtuel spécifique. Le dernier statut peut ne pas s'afficher lors de l'utilisation de l'API de liste `/instances` pour afficher toutes les instances.
