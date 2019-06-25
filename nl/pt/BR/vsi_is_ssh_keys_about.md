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
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Chaves SSH
{: #ssh-keys}
[comment]: # (tópico da ajuda vinculado)

Ao provisionar os {{site.data.keyword.vsi_is_full}}, deve-se selecionar uma chave SSH existente ou fazer upload de uma nova chave SSH para usar antes de poder criar a instância. As chaves SSH são usadas por servidores para identificar um usuário ou instância por meio da criptografia de chave pública. As chaves SSH são compostas de uma combinação alfanumérica e são exclusivas para a instância à qual são designadas. É possível incluir, editar ou excluir chaves SSH usando o console do {{site.data.keyword.cloud_notm}}.
{:shortdesc}

As chaves SSH permitem acesso a uma instância sem usar uma senha de clientes correspondentes para cada chave pública implementada na instância. Ao incluir uma chave SSH em uma instância, o que você pode fazer durante o provisionamento, a instância pode ser acessada com a chave correspondente em vez de uma senha. É possível incluir chaves SSH em uma instância apenas quando você criar inicialmente a instância. Depois que uma instância do Linux é criada, é possível editar chaves diretamente no diretório `~/.ssh/` da instância.

Efetuar login em sua instância com uma senha não é suportado. Se você tiver uma instância do Windows, a chave SSH será usada para decriptografar sua senha. Para obter mais informações, consulte [Conectando-se à sua instância do Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance).
{:note}

## Localizando ou gerando a sua chave SSH
{: #locating-or-generating-your-ssh-key}

Sua chave SSH deve estar disponível. Para localizar a chave SSH ou gerar uma chave SSH, conclua uma das etapas a seguir.

 * Localize uma chave SSH: procure um arquivo chamado `id_rsa.pub` sob um diretório `.ssh` em seu diretório inicial, por exemplo, `/Users/<USERNAME>/.ssh/id_rsa.pub`. O arquivo começa com `ssh-rsa` e termina com seu endereço de e-mail.

* Gere uma chave SSH: se você não tiver uma chave SSH pública ou se tiver esquecido a senha de uma existente, gere uma nova executando o comando `ssh-keygen` e seguindo os prompts. Por exemplo, é possível gerar uma chave SSH em seu servidor Linux executando o comando `ssh-keygen -t rsa -C "user_ID"`. Esse comando gera dois arquivos. A chave pública gerada está no arquivo `<your key>.pub`.

  Se você estiver usando o OpenSSH versão 7.8 ou mais recente e planejar usar a chave SSH para acessar uma instância do Windows, deverá usar o comando a seguir para gerar a chave no formato PEM. `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

Para obter mais informações sobre como criar, editar ou excluir chaves SSH, consulte [Gerenciando chaves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
