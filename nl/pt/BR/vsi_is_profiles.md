---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Perfis
{: #profiles}

Ao provisionar os {{site.data.keyword.vsi_is_full}}, é possível selecionar entre três famílias de perfis: Balanceado, Cálculo e Memória. Um perfil é uma combinação de vCPU e RAM que pode ser instanciado rapidamente para iniciar uma instância de servidor virtual. No console do {{site.data.keyword.Bluemix_notm}}, é possível escolher entre configurações de perfil populares ou selecionar em uma lista de perfis que melhor se ajustam às suas necessidades.
{: shortdesc}

As famílias a seguir estão disponíveis:

| Famílias | Descrição |
| -------- | ----------- |
| [Balanceado](#balanced) | Melhor para cargas de trabalho de nuvem comuns que requerem um balanceamento de desempenho e escalabilidade. Os perfis balanceados (com o armazenamento conectado à rede) fornecem maior desempenho, pois os recursos não são alocados excessivamente. |
| [Cálculo](#compute)  | Melhor para cargas de trabalho de trafego da web moderado a alto. Os perfis de cálculo são melhores para cargas de trabalho com demandas de CPU intensivas, como cargas de trabalho de tráfego da web alto, processamento em lote de produção e servidores da web de front-end. |
| [Memória](#memory) | Melhor para cargas de trabalho de armazenamento em cache de memória e de analítica em tempo real. Os perfis de memória são melhores para cargas de trabalho de memória intensiva, como cargas de trabalho de armazenamento em cache grandes, aplicativos de banco de dados intensivos ou cargas de trabalho analíticas na memória. |
{: caption="Tabela 1. Seleções de família de servidor virtual" caption-side="top"}

## Balanceado
{: #balanced}

Os perfis balanceados fornecem desempenho mais alto, uma vez que os recursos não são sobrescritos. O desempenho da rede varia de padrão a premium.

A oferta está disponível nos perfis a seguir:

| Perfil | vCPU | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="Tabela 2. Opções de perfil balanceado de servidor virtual" caption-side="top"}

**Notas de armazenamento:**

* O volume de inicialização primário da SAN (100 GB) é criado e anexado automaticamente quando uma instância é provisionada.
* Opcionalmente, crie um volume de dados secundário. Os perfis de volume estão disponíveis como três camadas IOPS predefinidas ou como IOPS customizado. Um [perfil de camada de propósito geral de 3 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornece desempenho de IOPS/GB adequado para um perfil balanceado da VSI.
* A precificação de servidores virtuais públicos que usam armazenamento SAN inclui CPU virtual, memória e volume de inicialização primário. Os volumes de dados secundários são precificados separadamente.

Todos os sistemas operacionais suportados (como CentOS, Debian, Ubuntu e Windows) estão disponíveis com essa oferta.

## Computação
{: #compute}

Os perfis de cálculo são melhores para cargas de trabalho com demandas de CPU intensivas, como cargas de trabalho de tráfego da web alto, processamento em lote de produção e servidores da web de front-end.

A oferta está disponível nos perfis a seguir:

| Perfil | vCPU | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="Tabela 3. Opções de perfil de cálculo de instância de servidor virtual" caption-side="top"}

**Notas de armazenamento:** 

* O volume de inicialização primário da SAN (100 GB) é criado e anexado automaticamente quando uma instância é provisionada.
* Opcionalmente, crie um volume de dados secundário. Os perfis de volume estão disponíveis como três camadas IOPS predefinidas ou como IOPS customizado. Um perfil de [camada de 5 IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornece desempenho de IOPS/GB adequado para um perfil de cálculo da VSI.
* A precificação de servidores virtuais públicos que usam armazenamento SAN inclui CPU virtual, memória e volume de inicialização primário. Os volumes de dados secundários são precificados separadamente.

Todos os sistemas operacionais suportados (como CentOS, Debian, Ubuntu e Windows) estão disponíveis com essa oferta. 

## Memória 
{: #memory}

Os perfis de memória são melhores para cargas de trabalho de memória intensiva, como cargas de trabalho de armazenamento em cache grandes, aplicativos de banco de dados intensivos ou cargas de trabalho analíticas na memória.

A oferta está disponível nos perfis a seguir:

| Perfil | vCPU | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="Tabela 4. Opções de perfil de memória de instância de servidor virtual" caption-side="top"}

**Notas de armazenamento:** 

* O volume de inicialização primário da SAN (100 GB) é criado e anexado automaticamente quando uma instância é provisionada.
* Opcionalmente, crie um volume de dados secundário. Os perfis de volume estão disponíveis como três camadas IOPS predefinidas ou como IOPS customizado. Um perfil de [camada 10-IOPS](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) fornece o desempenho de IOPS/GB adequado para um perfil de memória da VSI.
* A precificação de servidores virtuais públicos que usam armazenamento SAN inclui CPU virtual, memória e volume de inicialização primário. Os volumes de dados secundários são precificados separadamente.

Todos os sistemas operacionais suportados (como CentOS, Debian, Ubuntu e Windows) estão disponíveis com essa oferta. 

## Visualizando configurações de perfil
{: #popularprofiles}

É possível visualizar as configurações de perfil disponíveis usando o console do {{site.data.keyword.cloud_notm}} ou a CLI. No console do {{site.data.keyword.cloud_notm}}, é possível selecionar entre as configurações de perfil populares que suportam casos de uso mais comuns.

### Usando o console do IBM Cloud
1. No console do {{site.data.keyword.cloud_notm}}, navegue para o **ícone de Menu ![Ícone de menu](../icons/icon_hamburger.svg) > Infraestrutura de VPC > Cálculo > Instâncias de servidor virtual**.
2. Nessa página, clique em **Nova instância**.
3. É possível selecionar uma configuração de perfil por meio dos **Perfis populares** ou clicar em **Todos os perfis** para visualizar configurações adicionais.

### Usando a CLI
Para visualizar a lista de perfis disponíveis usando a CLI, execute o comando a seguir:
```
$ ibmcloud is instance-profiles
```
{:codeblock}

Ao usar a linha de comandos, as informações a seguir descrevem o que a saída representa. Os tamanhos de perfil têm proporções diferentes de CPU para a memória, projetadas para cargas de trabalho diferentes:

*  "b" é balanceado, que é uma proporção 1:2 ou 1:4
*  "c" é cálculo (mais alta nas CPUs), que é uma proporção 1:1
*  "m" é memória (mais alta na memória), que é uma proporção 1:8
