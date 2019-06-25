---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

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

# Criando instâncias de servidor virtual
{: #creating-virtual-servers}
[comment]: # (tópico da ajuda vinculado)

É possível criar os {{site.data.keyword.vsi_is_full}} por meio da página *Instâncias de servidor virtual* no console do {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Antes de iniciar, certifique-se de que você tenha [criado um IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

Para criar uma instância, selecione os detalhes da instância a seguir.
1. No [console do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.cloud.ibm.com/vpc), navegue para **Ícone de menu ![Ícone de menu](../icons/icon_hamburger.svg) > Infraestrutura do VPC > Calcular > Instâncias de servidor virtual**.
2. Clique em **Nova instância** e insira as informações a seguir:

    <table>
    <CAPTION>Tabela 1. Seleções de provisionamento de instância</CAPTION>
    <THEAD>
    <TR>
    <th>Campo</th>
    <th>Valor</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Nome </td>
    <td>Um nome é necessário para a instância de servidor virtual.</td>
    </tr>
    <tr>
    <td>Nuvem virtual privada</td>
    <td>Especifique o IBM Cloud VPC no qual você deseja criar a sua instância.</td>
    </tr>
    <tr>
    <td>Localização</td>
    <td>Os locais são compostos de regiões (áreas geográficas específicas) e zonas (data centers tolerantes a falhas em uma região). Selecione o local em que deseja que sua instância de servidor virtual seja criada.</td>
    </tr>
    <tr>
    <td>Perfil</td>
    <td><p>
    Selecione entre os perfis populares ou todas as combinações de vCPU e RAM disponíveis. As famílias a seguir são suportadas:
    <ul>
    <li>Balanceado</li>
    <li>Computação</li>
    <li>Memória</li>
    </ul>
    </p>
    <p>Cada núcleo físico no servidor é hiperencadeado e apresentado como duas CPUs virtuais (vCPUs). A oferta de servidor virtual fornece 2.0 GHz ou mais por vCPU com até 48 vCPUs disponíveis em um único servidor virtual.</p>

    <p>Para a memória, uma instância pode ter até 256 GB de RAM totalmente dedicada.</p>
    <p><note>Nota: os valores máximos variam por família.</note></p>
    <p>Para obter mais informações, consulte [Perfis](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).</p>
    </td>
    </tr>
    <tr>
    <td>Imagem</td>
    <td><p>Todas as imagens usam cloud-init, que permite inserir metadados do usuário associados à instância para scripts de pós-provisionamento.</p>
    <p>Para obter mais informações, consulte [Imagens](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images).</p>
    </td>
    </tr>
    <td>Chave SSH</td>
    <td>
    <p>Deve-se selecionar uma chave SSH existente ou fazer upload de uma nova chave SSH para usar antes de poder criar a instância. As chaves SSH são usadas para se conectar com segurança à instância após ela estar em execução. É possível incluir chaves SSH em sua instância somente ao criar inicialmente a instância.</p>
    <p>Nota: as combinações alfanuméricas são limitadas a 100 caracteres.</p>
    <p>Para obter mais informações, consulte [Chaves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</p></td>
    </tr>
    <tr>
    <td>Dados do usuário</td>
    <td>
    <p>É possível incluir dados do usuário que executam automaticamente tarefas de configuração comuns ou executam scripts. <p>Para obter mais informações, consulte [Dados do usuário](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).</p>
    </td>
    </tr>
    <tr>
    <td>Volume de inicialização</td>
    <td><p>O tamanho do volume de inicialização padrão para todos os perfis é 100 GB. Por padrão, o volume de inicialização inclui criptografia gerenciada pelo provedor. Se você desejar usar a criptografia gerenciada pelo cliente, será possível editar os detalhes do volume de inicialização. Para obter mais informações, consulte [Armazenamento](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage).</p>
    </td>
    </tr>
    <tr>
    <td>Volume de armazenamento de bloco anexado</td>
    <td><p>É possível adicionar um ou mais volumes de dados secundários a serem incluídos ao provisionar a instância. Para incluir volumes, clique em **Novo volume de armazenamento de bloco**. Para obter mais informações, consulte [Criando volumes de armazenamento de bloco](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).</p>
    </td>
    </tr>
    <tr>
    <td>Interfaces de Rede</td>
    <td>Designar opções de rede para se conectar ao IBM Cloud VPC. É possível criar e designar até 5 placas da interface de rede para cada instância. Para obter mais informações, consulte [Múltiplos endereços IP](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options).</td>
    </tr>
    </TBODY>
    </table>

    Seu *Resumo de custo* é exibido no lado direito da página *Nova instância de servidor virtual*.

3. Clique em **Criar instância de servidor virtual** quando estiver pronto para provisionar. Uma série de e-mails é enviada para o seu administrador: confirmação do pedido de instância de servidor virtual, aprovação do pedido e processamento, e uma mensagem informando que a instância foi criada.

Você prefere criar uma instância usando a CLI? Para obter mais informações, consulte [Criando uma instância usando a CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli).
{: tip}

## Reservando um endereço IP flutuante
{: #reserving-a-floating-ip-address}

É possível reservar e associar um endereço IP flutuante à sua instância para que seja possível conectar-se a ela por meio de um local da Internet.

Sua instância deve estar em execução antes que seja possível associar um endereço IP flutuante. Pode levar alguns minutos para que a instância esteja funcionando.
{: note} 

Para reservar e associar um endereço IP flutuante, conclua as etapas a seguir.
1. Na página **Instâncias de servidor virtual**, clique em sua instância para visualizar seus detalhes.
2. Na seção **Interfaces de rede**, clique em **Reservar +** para associar um endereço IP flutuante à sua instância.

## Próximas Etapas
{: #next-connecting-to-instance}

Agora você está pronto para se conectar à sua instância. Para obter mais informações, consulte [Conectando-se à sua instância do Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) ou [Conectando-se à sua instância do Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).
