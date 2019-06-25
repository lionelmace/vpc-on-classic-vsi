---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Planejando instâncias
{: #planning-for-instances}
[comment]: # (tópico da ajuda vinculado)


Quando você estiver planejando o provisionamento dos {{site.data.keyword.vsi_is_full}}, poderá achar essa lista de verificação de configuração útil para obter o máximo de sua implementação do servidor virtual.
{:shortdesc}

Antes de iniciar, certifique-se de que você tenha [criado um {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Planejando o provisionamento de instâncias
{: #planning-for-provisioning-instances}

Depois de ter um {{site.data.keyword.vpc_short}} disponível, considere os seguintes itens antes de provisionar sua instância.

|        Considerações|
|-------------------|
|__ 1. Certifique-se de que sua conta tenha as [permissões de usuário](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions) necessárias. Se você tiver autorização como um editor ou um administrador em um recurso do {{site.data.keyword.vpc_short}}, você também herdará a autorização para criar, excluir e modificar instâncias de servidor virtual dentro dessa nuvem particular virtual.|
|__ 2. Verifique os seus [limites de conta](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) para instâncias simultâneas. |
|__ 3. Certifique-se de que sua [chave SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) esteja disponível.
|__ 4. Determine o local da instância a ser selecionado.|
|__ 5. Considere as [opções de perfil](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) populares de combinações de vCPU e RAM para a sua carga de trabalho. Os perfis contêm instâncias pré-configuradas que estão prontas para uso em uma questão de minutos. É importante assegurar que as instâncias tenham os recursos necessários para manter as suas cargas de trabalho e o seu ambiente funcionando.|
|__ 6. Determine qual imagem do sistema operacional você selecionará para a sua instância. É possível escolher entre os bancos de [imagens](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images) atuais. |
|__ 7. Certifique-se de que você tenha um nome exclusivo para a instância. Se você tiver um método para nomear as instâncias de servidor virtual, será muito mais fácil filtrá-las e pesquisá-las posteriormente. |

## Próximas Etapas
{: #next-create-instance}

Quando você estiver pronto para iniciar, consulte os recursos a seguir para criar a sua instância:
* [Criando uma instância usando o console do {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Criando uma instância usando a CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
