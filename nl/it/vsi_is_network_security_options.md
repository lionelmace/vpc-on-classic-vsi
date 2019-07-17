---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Rete e sicurezza sui server virtuali
{: #network-security-options}

Quando implementi {{site.data.keyword.vsi_is_full}}, hai accesso alle ultime funzioni di rete e sicurezza.  
{:shortdesc}

## Utilizzo delle vNIC dell'istanza
{: #using-instance-vnics}

Viene utilizzata una vNIC (virtual network interface card) per connettere un server virtuale a una rete. Quando crei un'istanza VSI, puoi utilizzare una vNIC per assegnare più indirizzi IP. Il seguente elenco illustra come le vNIC funzionano con la tua istanza.

* Puoi creare ed assegnare fino a 5 vNIC ad ogni istanza. Ad ogni vNIC sarà assegnato un IP privato dalla sottorete connessa e puoi facoltativamente collegare un IP mobile o dei gruppi di sicurezza.
* Puoi collegare ogni vNIC a una sottorete nella stessa zona.
* Ogni vNIC riceve un IP privato dall'intervallo di sottoreti.
* Puoi associare e annullare l'associazione degli IP mobili a/da ogni vNIC.
* Puoi assegnare i gruppi di sicurezza ad ogni vNIC.
* Puoi modificare il nome di tutte le vNIC esistenti.

La larghezza di banda è associata all'istanza stessa e non è un aspetto configurabile di una singola vNIC. La larghezza di banda predefinita per un'istanza è 100 Mbps, con un'opzione per l'upgrade a 1 Gbps.

## Opzioni si rete
{: #networking-options}

Per ulteriori informazioni sulle funzioni generali di rete nell'ambiente {{site.data.keyword.vpc_short}}, vedi [Informazioni sulla rete per VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc).

## Opzioni di sicurezza
{: #security-options}

{{site.data.keyword.vsi_is_short}} include delle opzioni di sicurezza integrate:
* Gli ACL (Access Control List) possono limitare il traffico in entrata e uscita da una sottorete.
* I gruppi di sicurezza funzionano come un firewall virtuale per le istanze del server virtuale.
* Le chiavi SSH sull'istanza del server virtuale autenticano un canale sicuro per la comunicazione di rete.

Per ulteriori informazioni su queste opzioni di sicurezza, vedi [Sicurezza nel tuo IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) e [Gestione delle chiavi SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
