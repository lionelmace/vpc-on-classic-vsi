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

# 创建虚拟服务器实例
{: #creating-virtual-servers}
[comment]: # (链接的帮助主题)

您可以在 {{site.data.keyword.cloud_notm}} 控制台的*虚拟服务器实例*页面中创建 {{site.data.keyword.vsi_is_full}}。
{:shortdesc}

开始之前，请确保您已[创建 IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

要创建实例，请选择以下实例详细信息。
1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.cloud.ibm.com/vpc) 中，导航至**“菜单”图标 ![“菜单”图标](../icons/icon_hamburger.svg) > VPC 基础架构 > 计算 > 虚拟服务器实例**。
2. 单击**新建实例**，然后输入以下信息：

    <table>
    <CAPTION>表 1. 实例供应选择</CAPTION>
    <THEAD>
    <TR>
    <th>字段</th>
    <th>值</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>名称</td>
    <td>虚拟服务器实例的名称是必需的。</td>
    </tr>
    <tr>
    <td>虚拟私有云</td>
    <td>指定要在其中创建实例的 IBM Cloud VPC。</td>
    </tr>
    <tr>
    <td>位置</td>
    <td>位置由区域（特定地理区域）和专区（区域内的容错数据中心）组成。选择要在其中创建虚拟服务器实例的位置。</td>
    </tr>
    <tr>
    <td>概要文件</td>
    <td><p>
    从常用概要文件或所有可用的 vCPU 和 RAM 组合中进行选择。支持以下系列：
    <ul>
    <li>均衡</li>
    <li>计算</li>
    <li>内存</li>
    </ul>
    </p>
    <p>服务器上的每个物理核心都是超线程的，作为两个虚拟 CPU (vCPU) 提供。虚拟服务器产品为每个 vCPU 提供 2.0 GHz 或更高频率，在单个虚拟服务器上最多提供 48 个 vCPU。</p>

    <p>对于内存，一个实例最多可以有 256 GB 的完全专用 RAM。</p>
    <p><note>注：最大值因系列而有所不同。</note></p>
    <p>有关更多信息，请参阅[概要文件](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)。</p>
    </td>
    </tr>
    <tr>
    <td>映像</td>
    <td><p>所有映像都使用 cloud-init，这允许您输入与实例关联的用户元数据以用于供应后脚本。</p>
    <p>有关更多信息，请参阅[映像](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)。</p>
    </td>
    </tr>
    <td>SSH 密钥</td>
    <td>
    <p>必须选择现有 SSH 密钥或上传要使用的新 SSH 密钥，然后才能创建实例。在实例处于运行状态后，SSH 密钥用于安全地连接到实例。仅当初始创建实例时，才能将 SSH 密钥添加到实例。</p>
    <p>注：字母数字组合限制为 100 个字符。</p>
    <p>有关更多信息，请参阅 [SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)。</p></td>
    </tr>
    <tr>
    <td>用户数据</td>
    <td>
    <p>可以添加用于自动执行常见配置任务或运行脚本的用户数据。<p>有关更多信息，请参阅[用户数据](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)。</p>
    </td>
    </tr>
    <tr>
    <td>引导卷</td>
    <td><p>所有概要文件的缺省引导卷大小均为 100 GB。缺省情况下，引导卷包含提供者管理的加密。如果要使用客户管理的加密，可以编辑引导卷的详细信息。有关更多信息，请参阅[存储器](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage)。</p>
    </td>
    </tr>
    <tr>
    <td>连接的块存储卷</td>
    <td><p>供应实例时，可以添加要包含的一个或多个辅助数据卷。要添加卷，请单击**新建块存储卷**。有关更多信息，请参阅[创建块存储卷](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)。</p>
    </td>
    </tr>
    <tr>
    <td>网络接口</td>
    <td>分配用于连接到 IBM Cloud VPC 的联网选项。可以为每个实例最多创建并分配 5 个网络接口卡。有关更多信息，请参阅[多个 IP 地址](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options)。</td>
    </tr>
    </TBODY>
    </table>

    *成本摘要*显示在*新建虚拟服务器实例*页面的右侧。

3. 准备好供应时，单击**创建虚拟服务器实例**。这将向管理员发送一系列电子邮件：虚拟服务器实例订单确认，订单核准和处理，以及指示实例已创建的消息。

您更倾向于使用 CLI 创建实例吗？有关更多信息，请参阅[使用 CLI 创建实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)。
{: tip}

## 保留浮动 IP 地址
{: #reserving-a-floating-ip-address}

可以保留浮动 IP 地址并将其与实例相关联，以便可以从因特网位置连接到该实例。

实例必须正在运行，然后才能关联浮动 IP 地址。实例启动并运行可能需要几分钟时间。
{: note} 

要保留并关联浮动 IP 地址，请完成以下步骤。
1. 在**虚拟服务器实例**页面上，单击实例以查看其详细信息。
2. 在**网络接口**部分中，单击**保留+** 以将浮动 IP 地址与实例相关联。

## 后续步骤
{: #next-connecting-to-instance}

现在，您已准备好连接到实例。有关更多信息，请参阅[连接到 Linux 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)或[连接到 Windows 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)。
