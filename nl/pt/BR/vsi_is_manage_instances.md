---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Gerenciando instâncias de servidor virtual
{: #managing-virtual-server-instances}
[comment]: # (tópico da ajuda vinculado)

É possível visualizar e gerenciar suas instâncias dos {{site.data.keyword.vsi_is_full}} na página *Instâncias de servidor virtual* no console do {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Para gerenciar suas instâncias, conclua as etapas a seguir.
1. No [console do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.cloud.ibm.com/vpc), navegue para **Ícone de menu ![Ícone de menu](../icons/icon_hamburger.svg) > Infraestrutura do VPC > Calcular > Instâncias de servidor virtual**.
2. Aqui, é possível gerenciar tarefas para uma instância específica ou clicar em uma instância para visualizar e editar suas propriedades.

## Reinicializar

A ação de reinicialização imediatamente desliga uma instância e, em seguida, liga-a novamente.

## Parar e iniciar

A ação parar e iniciar liga ou desliga uma instância remotamente. Se a instância for interrompida, ela permanecerá no estado pausado e deverá ser iniciada manualmente. O faturamento é [suspenso](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing) para alguns recursos de cálculo enquanto a instância está pausada. Não será possível interagir com uma instância se ela estiver parada. Se o dispositivo tiver sido iniciado, a interação normal continuará.

## Excluir

A ação de exclusão remove permanentemente uma instância e sua vNIC, volume de inicialização e dados conectados de sua conta. Depois de confirmar a ação de exclusão, o processo para excluir a instância e sua vNIC, volume de inicialização e dados associados é iniciado. A ação de exclusão pode levar até 30 minutos, mas, quando o processo é concluído, a instância não aparece mais na página Instâncias de servidor virtual. O endereço IP flutuante associado à instância de servidor virtual está desassociado, mas permanece em sua conta.

## Visualizando detalhes da instância
É possível interagir com as instâncias visualizando o resumo de todas as instâncias na página *Instâncias de servidor virtual* ou clicando em uma instância individual para visualizar os detalhes e fazer mudanças. Na página de detalhes da instância, também é possível visualizar a interface de rede associada, acessar sua sub-rede e reservar ou excluir um endereço IP flutuante.

Se você preferir gerenciar suas instâncias usando a CLI, consulte [Gerenciando uma instância usando a CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
{: tip}
