---

copyright:
  years: 2019
lastupdated: "2019-06-05"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Criando instâncias de servidor virtual com criptografia gerenciada pelo cliente
{: #creating-instances-byok}

Será possível criar os {{site.data.keyword.vsi_is_full}} que usam criptografia gerenciada pelo cliente para volumes de armazenamento de bloco quando você tiver um serviço de gerenciamento de chave provisionado que inclua sua própria chave de criptografia de dados. Por padrão, as instâncias são provisionadas com um volume de inicialização que inclui criptografia gerenciada pelo provedor. É possível provisionar instâncias que usam criptografia gerenciada pelo cliente para os volumes de armazenamento de bloco por meio do console do {{site.data.keyword.cloud_notm}} ou usando a interface da linha de comandos (CLI).
{:shortdesc}

## Serviços de gerenciamento de chave suportados para criptografia gerenciada pelo cliente
{: #kms-for-byok}

É possível usar o serviço de gerenciamento de chave que funciona melhor para suas necessidades. O {{site.data.keyword.keymanagementserviceshort}} e o {{site.data.keyword.hscrypto}} (disponíveis em determinadas [regiões](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)) usam uma API de provedor de chave comum para fornecer uma abordagem consistente para gerenciar chaves de criptografia.  Nos bastidores, os data centers do {{site.data.keyword.cloud_notm}} fornecem um módulo de segurança de hardware dedicado (HSM) para proteger as suas chaves.  Os serviços de gerenciamento de chave a seguir são suportados com a criptografia gerenciada pelo cliente para volumes de armazenamento de bloco: 

| Serviço de gerenciamento de chave | Certificação de criptografia HSM |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Conformidade FIPS 140-2 *Nível 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Conformidade FIPS 140-2 *Nível 4* |
{: caption="Tabela 1. Opções de serviço de gerenciamento de chave disponíveis" caption-side="top"}

## Pré-requisito
{: #byok-vsi-prereqs}

Para criar uma instância de servidor virtual que usa a criptografia gerenciada pelo cliente para os volumes de armazenamento de bloco, deve-se ter um serviço de gerenciamento de chave provisionado e uma chave raiz do cliente incluída. Deve-se também autorizar o acesso entre o Cloud Block Storage e o serviço de gerenciamento de chave. Quando você tiver concluído esses pré-requisitos, será possível começar a criar instâncias que usam criptografia gerenciada pelo cliente para os volumes de armazenamento de bloco. 

As etapas de exemplo a seguir são específicas para o {{site.data.keyword.keymanagementserviceshort}}, mas o fluxo geral também se aplica ao {{site.data.keyword.hscrypto}}. Se você estiver usando o {{site.data.keyword.hscrypto}}, consulte as [informações do {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) para obter as instruções correspondentes.
{:note}

1. Forneça o serviço [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision). 
   
   O provisionamento de uma nova instância de serviço do {{site.data.keyword.keymanagementserviceshort}} assegura que ele inclua as atualizações mais recentes que são necessárias para a criptografia gerenciada pelo cliente de volumes de armazenamento de bloco. 
   {: tip}
   
2. [Crie](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) ou
[importe](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) uma chave raiz (CRK) no
{{site.data.keyword.keymanagementservicelong_notm}}.
3. Por meio do IBM {{site.data.keyword.iamshort}} (IAM), [autorize o acesso](/docs/iam?topic=iam-serviceauth#serviceauth) entre o **Cloud
Block Storage** (serviço de origem) e o **{{site.data.keyword.keymanagementserviceshort}}** (serviço de destino).

## Provisionando instâncias de servidor virtual com volumes que usam criptografia gerenciada pelo cliente
{: #provision-byok-ui}

Ao provisionar uma instância de servidor virtual, é possível especificar a criptografia gerenciada pelo cliente para seu volume de inicialização e qualquer volume de dados que você deseja incluir no tempo de provisionamento. Se desejar, será possível usar uma combinação de criptografia gerenciada por provedor e criptografia gerenciada por cliente para os volumes que estão associados à sua instância.

1. No [console do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.cloud.ibm.com/vpc), navegue para **Ícone de menu ![Ícone de menu](../icons/icon_hamburger.svg) > Infraestrutura do VPC > Calcular > Instâncias de servidor virtual**. Clique em **Nova instância** e preencha os campos obrigatórios. (Para obter mais informações sobre a criação de instâncias, consulte [Criando instâncias de servidor virtual](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).) 
2. Na seção **Volume de inicialização**, o modo padrão de criptografia é a criptografia _Provedor gerenciado_ Para especificar a criptografia gerenciada pelo cliente, clique no ícone de lápis na linha do volume de inicialização. Na página **Editar volume de inicialização**, atualize os campos na seção **Criptografia**. Veja a tabela a seguir para obter mais informações. Quando suas mudanças estiverem concluídas, clique em **Aplicar**.
3. Na seção **Volume de armazenamento de bloco anexado**, é possível clicar em **Novo volume de armazenamento de bloco** para incluir um volume de dados e especificar a criptografia gerenciada pelo cliente, caso você queira. Na página **Novo volume de armazenamento de bloco**, atualize os campos na seção **Criptografia**. Veja a tabela a seguir para obter mais informações. Quando suas mudanças estiverem concluídas, clique em **Anexar**.

| Campos | Valor |
| ----- | ----- |
| Encryption | _Provedor gerenciado_ é o modo de criptografia padrão. Para usar a criptografia gerenciada pelo cliente, selecione um serviço de gerenciamento de chave na lista suspensa. A instância de serviço de gerenciamento de chave deve incluir a chave raiz do cliente que você deseja usar para criptografia gerenciada pelo cliente. |
| Instância de serviço de criptografia | Se você tiver múltiplas instâncias de serviço de gerenciamento de chave provisionadas em sua conta, selecione aquela que inclui a chave raiz do cliente que você deseja usar para criptografia gerenciada pelo cliente. |
| Nome principal | Selecione a chave de criptografia de dados na instância de serviço de gerenciamento de chave que você deseja usar para criptografar o volume. | 
| ID da chave | Exibe o ID da chave que está associado à chave de criptografia de dados que você selecionou. | 
{: caption="Tabela 1. Valores para especificar criptografia de volumes gerenciada pelo cliente" caption-side="top"}

## Usando a CLI para provisionar instâncias e volumes com criptografia gerenciada pelo cliente
{: #provision-byok-cli}

Para usar a CLI para criar uma instância de servidor virtual com volumes que usam criptografia gerenciada pelo cliente, é possível usar o comando `ibmcloud is instance-create` e referenciar um JSON para anexar volumes que usam criptografia gerenciada pelo cliente. 

1. Obtenha o CRN da chave raiz em sua instância de serviço de gerenciamento de chave desejada. O exemplo a seguir é específico para o {{site.data.keyword.keymanagementserviceshort}}. 
    
    1. Se você ainda não tiver o plug-in da CLI do {{site.data.keyword.keymanagementserviceshort}} instalado, instale-o executando o comando a seguir: 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. Liste as instâncias de serviço do {{site.data.keyword.keymanagementserviceshort}} para sua conta executando o comando a seguir:
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. Recupere o ID da instância para a instância de serviço do {{site.data.keyword.keymanagementserviceshort}} em que as chaves raiz do cliente são armazenadas executando o comando a seguir.  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       em que _Key Protect-17_ é a instância de serviço do {{site.data.keyword.keymanagementserviceshort}} desejada.
    
       Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       em que o ID da instância é a sequência após o `::` final no CRN, `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`. 
    
    4. Liste as chaves disponíveis e seus CRNs associados dentro da instância de serviço do {{site.data.keyword.keymanagementserviceshort}} desejada, executando o comando a seguir:
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       em que _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ é o ID da instância de sua instância de serviço do {{site.data.keyword.keymanagementserviceshort}} desejada.
       
       Para esse exemplo, você veria uma resposta semelhante à saída a seguir:
       ```
       Retrieving keys...
              
       SUCCESS
               
       Key ID                                 Key Name               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. Use o comando [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) e anexe os arquivos JSON necessários que especificam a criptografia gerenciada pelo cliente para o volume de inicialização e qualquer volume de dados secundários que você deseja incluir. O parâmetro `encryption_key` deve incluir um CRN válido para a chave raiz no serviço de proteção de chave. Consulte os [exemplos de arquivo JSON](#vsi-vol-attachment-json) a seguir de um volume de inicialização JSON e de volume secundário JSON. (Para obter mais informações sobre como criar instâncias, consulte [Criando instâncias de servidor virtual (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli).)

## Criando um anexo de volume no formato JSON
{: #vsi-vol-attachment-json}

Ao criar um volume de inicialização ou um volume de dados durante o provisionamento da VSI, deve-se especificar um arquivo JSON para definir os parâmetros de volume. Consulte os exemplos de arquivo JSON a seguir.

### Arquivo JSON de volume de inicialização de exemplo
{: #boot-volume-byok-json}

O exemplo a seguir define um volume de inicialização de propósito geral e especifica o parâmetro `encryption key` para criptografia gerenciada pelo cliente.

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      }, "encryption_key":{ "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### Arquivo JSON de volume secundário de exemplo
{: #secondary-volume-byok-json}

O exemplo a seguir define um volume secundário de propósito geral (dados) e especifica o parâmetro `encryption key` para criptografia gerenciada pelo cliente.

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         }, "encryption_key":{ "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}
