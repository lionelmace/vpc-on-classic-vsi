---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Gerenciando instâncias de servidor virtual (CLI)
{: #managing-virtual-servers-cli}

É possível visualizar e gerenciar suas instâncias dos {{site.data.keyword.vsi_is_full}} usando a interface da linha de comandos (CLI).
{:shortdesc}

## Antes de iniciar
{: #prereq-managing-instances}

1. Certifique-se de fazer download dos seguintes plug-ins da CLI, de instalá-los e de inicializá-los:
    * CLI do {{site.data.keyword.cloud_notm}}
    * O plug-in infrastructure-service

   Para obter mais informações, consulte [Referência da CLI do IBM Cloud para o VPC](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference).
   
   Ao instalar o plug-in vpc-infrastructure pela primeira vez, deve-se configurar a geração de destino como gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Certifique-se de que já tenha [criado um {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Visualizando ações da instância
{: #viewing-instance-actions}

Para visualizar as ações de gerenciamento que são executadas em sua instância, execute o comando a seguir:

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

Você verá uma lista semelhante à saída a seguir:

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## Gerenciando suas instâncias
{: #managing-your-instances}

Precisa de uma ajudinha? Execute o comando `ibmcloud is help` para visualizar comandos a qualquer momento.

### Reconfigurar  

```
ibmcloud is instance-reset
```
{:codeblock}

A instância é desligada e, em seguida, ligada.  

### Reiniciar

```
ibmcloud is instance-reboot
```
{:codeblock}

O sistema operacional da instância é reiniciado.  

### Parar e iniciar

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

Se o dispositivo tiver sido interrompido, ele permanecerá no estado pausado e deverá ser iniciado manualmente. Não será possível interagir com uma instância se ela estiver parada. Se o dispositivo tiver sido iniciado, a interação normal continuará. 

### Atualizar

```
ibmcloud is instance-update
```
{:codeblock}

Depois de renomear o dispositivo, o nome é atualizado automaticamente. Ao executar uma procura, use o novo nome da instância ao tentar localizar o conteúdo associado a ele. 

### Excluir

```
ibmcloud is instance-delete
```
{:codeblock}

Depois de confirmar a ação de exclusão, o processo para excluir a instância e sua vNIC, volume de inicialização e dados associados é iniciado. A ação de exclusão pode levar vários minutos, mas, quando o processo é concluído, a instância não aparece mais na página Instâncias de servidor virtual. O endereço IP flutuante associado à instância de servidor virtual está desassociado, mas permanece em sua conta.

Se você preferir gerenciar instâncias usando o console do {{site.data.keyword.cloud}}, consulte [Gerenciando uma instância](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).
{: tip}
