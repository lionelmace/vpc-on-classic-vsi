---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Gerenciando chaves SSH
{: #managing-ssh-keys}

## Antes de iniciar
{: #prereq-ssh-key-available}

Para acessar as instâncias dos {{site.data.keyword.vsi_is_full}}, deve-se ter uma chave SSH disponível para uso. É possível gerenciar as chaves SSH no console do {{site.data.keyword.cloud_notm}} e usando a CLI. 

Gerenciar as chaves usando o console ou a CLI do {{site.data.keyword.cloud_notm}} não tem efeito em chaves em instâncias que já foram criadas. (Para uma instância existente do Linux, é possível editar as chaves diretamente no diretório `~/.ssh/` da instância.)

Para obter mais informações sobre como localizar ou gerar uma chave SSH, consulte [Chaves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).
{: tip}

## Gerenciando chaves SSH com o console do IBM Cloud
{: #managing-ssh-keys-with-ibm-cloud-console}

Ao provisionar um servidor virtual, é possível selecionar entre as chaves SSH disponíveis ou fazer upload de uma nova. Não é possível gerar chaves SSH no console do {{site.data.keyword.cloud_notm}}.
{:shortdesc}

É possível gerenciar e excluir chaves SSH usando o console do {{site.data.keyword.cloud_notm}}.
1. No [console do {{site.data.keyword.cloud_notm}}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.cloud.ibm.com/vpc), navegue para o **ícone de Menu ![Ícone de menu](../icons/icon_hamburger.svg) > Infraestrutura de VPC > Cálculo > Chaves SSH**.
2. Aqui, é possível incluir ou excluir uma chave SSH.

## Gerenciando chaves SSH usando a CLI
{: #managing-ssh-keys-by-using-the-cli}

Também é possível gerenciar suas chaves SSH usando a CLI.

| Ação           | Comando:                     | O que acontece depois |
| ---------------- | --------------------------- | ----------------- |
| Criar chave SSH   | `ibmcloud is key-create`    | Depois de criar uma chave SSH, ela é incluída na lista de chaves. |
| Visualizar detalhes da chave | `ibmcloud is key`           | É possível visualizar o nome da chave e o ID da chave. |
| Listar chaves        | `ibmcloud is keys`          | É possível visualizar todas as suas chaves SSH existentes. |
| Chave de atualização       | `ibmcloud is key-update`    | Depois de atualizar uma chave existente, ela é renomeada imediatamente. |
| Tecla Delete       | `ibmcloud is key-delete`    | Depois de remover uma chave SSH, ela não poderá mais ser usada quando você provisionar uma nova instância ou quando executar um recarregamento de S.O. em uma instância existente. No entanto, a chave ainda estará disponível em qualquer instância que você tenha provisionado com ela e será possível usá-la para efetuar login. |
{: caption="Tabela 1. Ações de chave SSH" caption-side="top"}
