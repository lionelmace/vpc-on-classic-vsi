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

# Solucionando problemas dos seus Virtual Servers for VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
Se você tiver dificuldades com suas instâncias do {{site.data.keyword.vsi_is_full}}, revise as possíveis causas a seguir.

## Erro: 409 Conflito ao criar uma ação de instância

Não será possível criar determinadas ações de instância se o status de sua instância estiver em conflito com outra ação. Por exemplo, se o status da instância for `stopped` e você tentar criar uma ação `reboot`, o sistema retornará um erro 409.

| Barra de Status      | Ação     | Conflito |
| ----------- | ---------- | -------- |
| Em execução     | start      | sim      |
| Interrompido     | não iniciar  | sim      |
| Não em execução | reiniciar     | sim      |

## O status da instância travou no status `deleting`

Ao listar instâncias e localizar o status de uma instância travada no status `deleting`, use a API de exibição de instância `/instances/{instance_id}` para atualizar o status da instância para a sua instância de servidor virtual específica. O status mais recente pode não ser exibido ao usar a API de lista `/instances` para exibir todas as instâncias.
