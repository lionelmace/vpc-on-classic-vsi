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


# Imagens
{: #images}

Ao provisionar os {{site.data.keyword.vsi_is_full}}, é possível selecionar uma imagem nos bancos de imagens suportados. A imagem que você seleciona determina o sistema operacional que é provisionado para sua instância. 
{:shortdesc}

## Bancos de imagens
{: #stock-images}

Os sistemas operacionais a seguir estão disponíveis como bancos de imagens quando você cria um servidor virtual.
* CentOS 7.x
* Debian 8.x, 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04, 18.04
* Windows 2012, 2012 R2, 2016

Ao pedir uma instância, as imagens são ativadas para cloud-init para otimizar os tempos de provisionamento. Com uma imagem ativada para cloud-init, é possível fornecer dados do usuário. No campo **Dados do usuário** no formulário de pedido, é possível inserir dados do usuário cloud-init opcionais para o servidor. Para obter mais informações sobre dados do usuário e automação, consulte [Dados do usuário](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).

## Virtualização
{: #virtualization}
As instâncias requerem uma imagem que suporta o modo de inicialização do Hardware Virtualization Machine (HVM). O tipo de virtualização do HVM permite que uma imagem seja executada diretamente em um servidor virtual, o que é necessário para redes avançadas e recursos de GPU.
