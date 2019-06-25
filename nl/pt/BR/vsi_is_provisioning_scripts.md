---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Dados do usuário
{: #user-data}
[comment]: # (tópico da ajuda vinculado)

Ao criar uma instância dos {{site.data.keyword.vsi_is_full}}, é possível incluir dados do usuário que executam automaticamente tarefas de configuração comuns ou executam scripts. No campo **Dados do usuário** no formulário de pedido, é possível inserir dados do usuário cloud-init opcionais para o servidor.
{:shortdesc}

## Exemplos de dados do usuário para Linux 
{: #user-data-examples-for-linux}

O exemplo a seguir mostra como um usuário do Linux pode incluir um novo usuário e fornecer ao usuário uma chave SSH autorizada. O campo **Nome** terá a chave pública incluída em `~/.ssh/authorized_keys`. 

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

Aqui está outro exemplo de um shell script que mostra como um usuário do Linux pode incluir uma chave SSH para o usuário atual.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

É possível colar um desses exemplos diretamente no campo **Dados do usuário**. Então, os dados do usuário estão disponíveis para a instância de servidor virtual durante o provisionamento. 

Para obter mais exemplos e informações de dados do usuário do Linux, consulte [Exemplos de configuração de nuvem ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}.

## Exemplo de dados do usuário para Windows
{: #user-data-example-for-windows}

O exemplo a seguir mostra como os dados do usuário podem ser passados para uma instância do Windows. É possível copiar e colar esse exemplo diretamente no campo **Dados do usuário**.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

Para obter mais informações e exemplos de dados do usuário do Windows, consulte a [documentação do Cloudbase-init 1.0 ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}.
