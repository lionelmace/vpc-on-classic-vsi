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

# Risoluzione dei problemi dei tuoi server virtuali per VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
Se stai riscontrando delle difficoltà con le tue istanze {{site.data.keyword.vsi_is_full}}, controlla le seguenti possibili cause.

## Errore: 409 Conflitto durante la creazione di un'azione dell'istanza

Non puoi creare alcune azioni dell'istanza se lo stato della tua istanza è in conflitto con un'altra azione. Ad esempio, se lo stato della tua istanza è `stopped` e tenti di creare un'azione `reboot`, il sistema restituisce un errore 409.

| Stato      | Azione     | Conflitto |
| ----------- | ---------- | -------- |
| Running     | avvia      | sì      |
| Stopped     | non avvia  | sì      |
| Not running | riavvia     | sì      |

## Blocco dello stato dell'istanza su `deleting`

Quando elenchi le istanze e trovi lo stato di un'istanza bloccato su `deleting`, utilizza l'API show instance `/instances/{instance_id}` per aggiornare lo stato della tua istanza del server virtuale specifica. Lo stato più recente potrebbe non essere visualizzato quando utilizzi l'API list `/instances` per visualizzare tutte le istanze.
