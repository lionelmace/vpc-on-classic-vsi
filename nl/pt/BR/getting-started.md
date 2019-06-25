---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# Tutorial de introdução
{: #getting-started}

Use os {{site.data.keyword.vsi_is_full}} (VPC) para provisionar recursos de cálculo escaláveis no IBM Cloud.
{:shortdesc}

É possível criar quantos servidores virtuais você precisar, configurar a rede e a segurança e gerenciar o armazenamento. Tudo isso está disponível em um console aprimorado do IBM Cloud. O console é construído para fornecer a você acesso rápido e fácil para ajustar seu ambiente com suas demandas de carga de trabalho em mudança. Aposto que você está ansioso para começar a usar, então vamos logo ao que interessa.

Antes de começar, certifique-se de que você tenha [criado um IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

{{site.data.keyword.vsi_is_short}} não são compatíveis com as ofertas de servidor virtual clássico. Se você estiver interessado em qualquer uma das ofertas do {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} na infraestrutura clássica, consulte [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial).
{:note}

<p>Use as informações a seguir para começar a criar suas instâncias e conectar-se a elas rapidamente.
<table>
   <CAPTION>Tabela 1. Etapas de iniciação rápida</CAPTION>
   <THEAD>
   <TR>
   <th>Tarefa</th>
   <th>Detalhes</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Revise o conteúdo que pode ajudar a implementação</td>
   <td>Sem experiência com o IBM Cloud e com servidores virtuais? Os sites a seguir fornecem informações úteis para ajudá-lo a planejar o
ambiente.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">O que é IBM Cloud?</a></li>
      <li><a href="https://ibm.com/cloud/get-started">Introdução ao IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. Inscrever-se para o IBM Cloud</td>
   <td>Para obter informações sobre como configurar sua conta do IBM Cloud, consulte <a href="/docs/account?topic=account-signup#signup">Inscrevendo-se para o IBM Cloud</a>.</td>
 <tr>
   <td>3. Determine suas especificações de carga de trabalho</td>
   <td>Antes de criar sua instância, determine como ela será usada e o tamanho da instância que você precisa para ser bem-sucedido. Por exemplo, você
pretende utilizá-lo para desenvolvimento e teste ou produção? Você está testando uma experiência do usuário, processando algoritmos longos, fazendo backup e restaurando dados ou aumentando a velocidade de latência?</td>  
 <tr>
   <td>4. Tamanho e preço de sua instância</td>
   <td>Você tem três opções de família quando se trata de criar suas instâncias: Balanceado, Cálculo e Memória. As famílias contêm instâncias pré-configuradas, chamadas de Perfis, que atendem às necessidades da maioria dos clientes e podem estar prontas para serem configuradas em apenas cinco minutos.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Balanceado</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Computação</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Memória</a></li>
     </ul>
  <p>Use as informações de [Precificação](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) para ajudar a dimensionar e a precificar a sua instância.</p></td>
 <tr>
   <td>5. Efetue login na conta do IBM Cloud</td>
   <td>Acesse o Formulário de pedido dos {{site.data.keyword.vsi_is_short}} no <a href="https://console.bluemix.net/catalog/">catálogo do IBM Cloud</a>. Você precisará de <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">um IBMid e uma senha</a>.
   </td>
 <tr>
   <td>6. Solicitar acesso à experiência do {{site.data.keyword.vpc_short}}</td>
   <td>Se você ainda não tiver solicitado acesso, solicite-o ao {{site.data.keyword.vpc_short}}.</td>
<tr>
<td>7. Gerar uma chave SSH</td>
<td> Para obter instruções, consulte [Chaves SSH](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</td>
<tr>
<td>8. Planejando sua instância</td>
<td> Para obter mais informações para planejar, provisionar e configurar seus recursos com sucesso, consulte [Planejando instâncias](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances).</td>
<tr>
<td>9. Criando sua instância</td>
<td>
<p>
Para iniciar a criação de uma instância, consulte [Criando uma instância](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
</td>  
<tr>
<td>10. Conectando-se à sua instância</td>
<td>Sua instância agora está pronta! Consulte os tópicos a seguir em *Conectando-se* para verificar se a instância foi criada com sucesso.
   <ul>
   <li>[Conectando-se à sua instância do Linux](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Conectando-se à sua instância do Windows](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. Limpando sua instância</td>
<td>Quando você não precisar mais de sua instância, poderá excluí-la. </td>
</tr>
</TBODY>
</table>
</p>

## Próximas Etapas
Após a sua instância ser provisionada, explore suas opções.
* [Gerenciando sua instância](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [Permissões dos {{site.data.keyword.vsi_is_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Segurança em seu IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* Mais sobre o [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
