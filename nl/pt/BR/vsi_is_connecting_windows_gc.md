---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

keywords: Windows instance, encrypt password, decrypt password, retrieve password

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Conectando-se à sua instância do Windows
{: #connecting-to-your-windows-instance}

Depois de ter criado a sua instância do Windows dos {{site.data.keyword.vsi_is_full}}, é possível se conectar a ela concluindo estas etapas.
{:shortdesc}

## Antes de iniciar
{: #prereqs-connect-windows}

Certifique-se de concluir os pré-requisitos a seguir antes de começar:

1. Peça ao administrador da conta para conceder a você acesso para recuperar a senha de sua instância de servidor virtual. Para obter mais informações, revise as [permissões de usuário](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources).
2. Crie um novo grupo de segurança ou inclua uma regra no grupo de segurança padrão para ativar o acesso de entrada para a porta padrão da área de trabalho remota 3389. Para obter mais informações, consulte [Usando grupos de segurança](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups).
3. Assegure-se de que o tráfego de entrada sobre a porta TCP/IP 3389 seja permitido na ACL padrão do VPC. Para obter mais informações, consulte [Configurando ACLs de rede](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls).
4. Verifique se você tem o OpenSSL instalado. Para decriptografar com sucesso a senha, deve-se executar o OpenSSL e não o LibreSSL. Para obter mais informações, consulte [Downloads do OpenSSL ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.openssl.org/source/){: new_window}.

O LibreSSL não é compatível para a decriptografia de senha. Deve-se executar o OpenSSL para decriptografar a senha.
{:important}

## Sendo conectado
{: #getting-connected-windows}

Depois de criar a sua instância do Windows e concluir os pré-requisitos, conclua as etapas a seguir para se conectar à sua instância do Windows.

1. Consulte o status de sua instância executando o comando a seguir:
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  Quando a instância mostrar que está `running`, você estará pronto para recuperar os valores de inicialização para obter a sua senha. 

2. Execute o comando a seguir para inicializar a sua instância:

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  Esse comando exibe sua senha criptografada, que é gerada automaticamente quando você cria uma instância usando uma imagem do Windows.

3. Agora é necessário decriptografar sua senha por meio de um processo de decriptografia manual. Para decriptografar sua senha, execute o comando a seguir:

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  em que `~/examplepwd` é o arquivo no qual você salvou sua senha criptografada conforme referenciado na etapa 2.  
  
  O LibreSSL, incluído com o macOS, não suporta algoritmos hash SHA2 que são necessários para decriptografar a senha, resultando em erros `Public Key operation error`. É possível obter bibliotecas OpenSSL padrão usando uma ferramenta de gerenciamento de pacote ou instalando-as manualmente. 
  {:note}

4. Opcionalmente, depois de decriptografar a sua senha, é possível associar um endereço IP flutuante à sua instância do Windows para que seja possível se conectar a ela por meio de um local de Internet. Execute o comando a seguir para associar um endereço IP flutuante à sua instância:

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. Agora você tem o que precisa para se conectar à sua instância do Windows: senha decriptografada e endereço IP flutuante. Use seu cliente do desktop remoto preferencial para se conectar à sua instância. Para se conectar à sua instância, forneça o endereço IP flutuante e a senha decriptografada. O nome do usuário é `Administrator` por padrão.

## Próximas Etapas
{: #next-manage-instances}

Depois que você estiver conectado à sua instância, será possível [gerenciar suas instâncias usando o console do {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) ou [gerenciar suas instâncias usando a CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
