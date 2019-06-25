---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-24"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Armazenamento
{: #storage}

Ao provisionar uma instância dos {{site.data.keyword.vsi_is_full}}, um volume de armazenamento de bloco IOPS (3 IOPS/GB) de 100 GB de propósito geral é criado automaticamente como um volume de inicialização primário e conectado à instância. Também é possível criar volumes de dados secundários que são anexados automaticamente à instância.
{:shortdesc}

- Para obter mais informações sobre volumes de armazenamento de bloco para o VPC, consulte [Sobre o Block Storage for VPC](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about).  
- Para começar a criar volumes independentemente do provisionamento da instância de servidor virtual, consulte [Introdução ao {{site.data.keyword.block_storage_is_short}}](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started).

Por padrão, os volumes de inicialização e de dados são criptografados com a criptografia gerenciada pela IBM. Também é possível criptografar seus volumes usando suas próprias chaves de criptografia durante o provisionamento da instância ou [criando um volume independente](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption).  

Os volumes de inicialização são excluídos quando você exclui a instância de servidor virtual. Por padrão, os volumes de dados persistem quando são removidos da instância. É possível anexar o volume a uma nova instância posteriormente. Como alternativa, é possível especificar que os volumes de dados sejam excluídos automaticamente quando você exclui a instância.  

## Criptografia gerenciada pelo cliente para armazenamento de bloco  
{: #customer-managed-encryption-keys}

É possível criar os {{site.data.keyword.vsi_is_full}} com criptografia de armazenamento de bloco e suas próprias chaves de criptografia de dados que você gerencia. Você precisa somente do serviço do {{site.data.keyword.keymanagementservicelong_notm}} e de sua própria chave de criptografia de dados para começar. Para obter mais informações, consulte [Criando instâncias de servidor virtual com criptografia gerenciada pelo cliente](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok).
{:shortdesc}

