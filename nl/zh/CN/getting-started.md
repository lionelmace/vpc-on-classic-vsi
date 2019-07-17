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

# 入门教程
{: #getting-started}

使用 {{site.data.keyword.vsi_is_full}} (VPC) 可在 IBM Cloud 中供应可缩放计算资源。
{:shortdesc}

您可以根据需要创建任意数量的虚拟服务器，配置网络和安全性以及管理存储器。所有这些操作都可在经过改进的 IBM Cloud 控制台中执行。通过构建的控制台，可以快速轻松地访问您的环境，以根据不断变化的工作负载需求调整环境。您一定等不及开始使用了吧，下面我们将直接进入主题。

开始之前，请确保您已[创建 IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

{{site.data.keyword.vsi_is_short}} 与经典虚拟服务器产品不兼容。如果您对经典基础架构上的任何 {{site.data.keyword.cloud_notm}}{{site.data.keyword.BluVirtServers_short}} 产品感兴趣，请参阅 [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial)。
{:note}

<p>使用以下信息可快速开始创建和连接实例。
<table>
   <CAPTION>表 1. 快速入门步骤</CAPTION>
   <THEAD>
   <TR>
   <th>任务</th>
   <th>详细信息</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. 查看可帮助您实施的内容</td>
   <td>不熟悉 IBM Cloud 和虚拟服务器？以下站点提供了有助于您规划环境的有用信息。
       <ul>
      <li><a href="https://ibm.com/cloud-computing/">什么是 IBM Cloud</a></li>
      <li><a href="https://ibm.com/cloud/get-started">IBM Cloud 入门</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. 注册 IBM Cloud</td>
   <td>有关如何设置 IBM Cloud 帐户的信息，请参阅<a href="/docs/account?topic=account-signup#signup">注册 IBM Cloud</a>。</td>
 <tr>
   <td>3. 确定工作负载规范</td>
   <td>创建实例之前，请确定实例的用途以及需要的实例大小，以便成功创建实例。例如，是打算将其用于开发和测试环境还是生产环境？是要测试用户体验，处理冗长的算法，备份和复原数据，还是缩短等待时间以提高速度？</td>  
 <tr>
   <td>4. 确定实例的大小和价格</td>
   <td>创建实例时，有三个系列选项：均衡、计算和内存。这些系列包含预配置的实例（称为“概要文件”），可满足大多数客户的需求，并且可以在短短 5 分钟内就准备就绪以供配置。  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">均衡</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">计算</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">内存</a></li>
     </ul>
  <p>使用[定价](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)信息可帮助您确定实例的大小和价格。</p></td>
 <tr>
   <td>5. 登录到 IBM Cloud 帐户</td>
   <td>通过 <a href="https://console.bluemix.net/catalog/">IBM Cloud 目录</a>访问 {{site.data.keyword.vsi_is_short}} 订购表单。您将需要 <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBM 标识和密码</a>。
   </td>
 <tr>
   <td>6. 请求对 {{site.data.keyword.vpc_short}} 的访问权以进行体验</td>
   <td>如果您尚未请求过访问权，那么请求对 {{site.data.keyword.vpc_short}} 的访问权。</td>
<tr>
<td>7. 生成 SSH 密钥</td>
<td> 有关指示信息，请参阅 [SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)。</td>
<tr>
<td>8. 规划实例</td>
<td> 有关可帮助您成功规划、供应和配置资源的更多信息，请参阅[规划实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances)。</td>
<tr>
<td>9. 创建实例</td>
<td>
<p>
要开始创建实例，请参阅[创建实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)。
</td>  
<tr>
<td>10. 连接到实例</td>
<td>您的实例现在已准备就绪！请参阅*连接*下的以下主题以验证实例是否已成功创建。
   <ul>
   <li>[连接到 Linux 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[连接到 Windows 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. 清除实例</td>
<td>不再需要实例时，可以将其删除。</td>
</tr>
</TBODY>
</table>
</p>

## 后续步骤
供应实例后，请浏览您的选项。
* [管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [{{site.data.keyword.vsi_is_short}}许可权](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [IBM Cloud VPC 中的安全性](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* 有关 [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about) 的更多信息
