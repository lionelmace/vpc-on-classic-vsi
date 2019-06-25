---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# Sobre os Virtual Servers for VPC
{: #virtual-private-cloud}

Os {{site.data.keyword.vsi_is_full}} fornecem acesso a todos os benefícios do {{site.data.keyword.vpc_short}}, incluindo o isolamento de rede, a segurança e a flexibilidade. 
{:shortdesc}

## O que é o {{site.data.keyword.vpc_short}}?
Um {{site.data.keyword.vpc_short}} é uma rede virtual que está vinculada à sua conta do cliente. Ele oferece a você um ponto de entrada com custo reduzido que fornece a segurança na nuvem e a capacidade de escalar dinamicamente com o crescimento. Ele fornece controle de baixa granularidade sobre a sua infraestrutura virtual e a sua segmentação de tráfego de rede.
{: shortdesc}

Para obter mais informações sobre o {{site.data.keyword.vpc_short}}, consulte [Sobre o IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about).

## O que são os {{site.data.keyword.vsi_is_short}}?
Com os {{site.data.keyword.vsi_is_short}}, é possível criar uma instância que consiste em seus recursos de cálculo virtual e na capacidade resultante em um {{site.data.keyword.vpc_short}}. Ao provisionar uma instância, você seleciona um perfil de instância que corresponde à quantia de memória e à potência de cálculo necessárias para o aplicativo ou para o software que você planeja executar na instância. Depois de provisionar uma instância, você controla e gerencia esses recursos de infraestrutura. Cada conta tem um limite para o número de instâncias em execução nos servidores. Para obter mais informações sobre esse limite, consulte as [Perguntas mais frequentes](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). 

## Como as instâncias de servidor virtual para o {{site.data.keyword.vpc_short}} são diferentes de outras ofertas de servidor virtual da IBM?

Na oferta atual do IBM Cloud Virtual Server, as instâncias usam a sub-rede nativa e a rede VLAN para se comunicarem entre si dentro de um data center (e de um pod único). O uso de uma sub-rede e de uma rede VLAN em um pod funciona bem até que você precise aumentar a capacidade ou tenha grandes demandas de recurso virtual que requeiram que os recursos sejam criados entre os pods. (A inclusão de dispositivos para a ampliação de VLAN pode ser dispendiosa e complicada.) 

O {{site.data.keyword.vpc_short}} inclui uma camada de orquestração de rede que elimina o limite de pod, criando capacidade infinita para escalar instâncias. A camada de orquestração de rede manipula toda a rede para todas as instâncias de servidor virtual que estão dentro de um {{site.data.keyword.vpc_short}} entre regiões e zonas. Com os recursos de rede definidos pelo software que o {{site.data.keyword.vpc_short}} fornece, há mais opções para [VPNs](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc), instâncias com múltiplas vNICs e tamanhos de [sub-rede](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets) maiores. Para obter mais informações, consulte [Sobre a rede para o VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc). 

Os {{site.data.keyword.vsi_is_short}} também têm os recursos a seguir, que fornecem uma experiência de usuário mais simples e economia de custo:
* Novo console do {{site.data.keyword.cloud_notm}}
* Nova API e CLI do Virtual Private Cloud
* Novo modelo de faturamento com camadas de desconto de uso sustentadas, conforme descrito em [Precificação](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)

{{site.data.keyword.vsi_is_short}} não são compatíveis com as ofertas de servidor virtual clássico. Se você estiver interessado em qualquer uma das ofertas do {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} na infraestrutura clássica, consulte [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial).
{:note}




