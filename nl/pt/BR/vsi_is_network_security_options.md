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

# Rede e segurança em servidores virtuais
{: #network-security-options}

Ao implementar os {{site.data.keyword.vsi_is_full}}, você tem acesso aos recursos mais recentes para rede e segurança.  
{:shortdesc}

## Usando vNICs de instância
{: #using-instance-vnics}

Uma placa da interface de rede virtual (vNIC) é usada para conectar um servidor virtual a uma rede. Ao criar uma instância de VSI, é possível usar uma vNIC para designar múltiplos endereços IP. A lista a seguir destaca como as vNICs funcionam com sua instância.

* É possível criar e designar até cinco vNICs para cada instância. Cada vNIC será designada a um IP privado por meio da sub-rede conectada e, opcionalmente, é possível anexar um IP flutuante e grupos de segurança.
* É possível anexar cada vNIC a uma sub-rede na mesma zona.
* Cada vNIC recebe um IP privado por meio do intervalo de sub-redes.
* É possível associar IPs flutuantes a cada vNIC e desassociá-los dela.
* É possível designar grupos de segurança a cada vNIC.
* É possível mudar o nome de qualquer vNIC existente.

A largura da banda está associada à própria instância e não é um aspecto configurável de uma vNIC individual. A largura da banda padrão para uma instância é 100 Mbps, com uma opção para fazer upgrade para 1 Gbps.

## Opções de rede
{: #networking-options}

Para obter mais informações sobre os recursos gerais de rede no ambiente do {{site.data.keyword.vpc_short}}, consulte [Sobre a rede para VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc).

## Opções de segurança
{: #security-options}

Os {{site.data.keyword.vsi_is_short}} incluem opções de segurança integradas:
* As listas de controle de acesso (ACLs) podem limitar o tráfego para e de uma sub-rede.
* Os grupos de segurança funcionam como um firewall virtual para instâncias de servidor virtual.
* As chaves SSH em sua instância de servidor virtual autenticam um canal seguro para comunicação de rede.

Para obter mais informações sobre essas opções de segurança, consulte [Segurança em seu IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) e [Gerenciando chaves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
