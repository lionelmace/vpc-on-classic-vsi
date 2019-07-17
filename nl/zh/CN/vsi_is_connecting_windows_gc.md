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

# 连接到 Windows 实例
{: #connecting-to-your-windows-instance}

创建 {{site.data.keyword.vsi_is_full}} Windows 实例后，可以通过完成以下步骤来连接到该实例。
{:shortdesc}

## 开始之前
{: #prereqs-connect-windows}

开始之前，请确保完成以下先决条件：

1. 请求帐户管理员授予您从虚拟服务器实例检索密码的访问权。有关更多信息，请查看[用户许可权](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources)。
2. 创建新的安全组或将规则添加到缺省安全组，以启用对远程桌面缺省端口 3389 的入站访问。有关更多信息，请参阅[使用安全组](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups)。
3. 确保在 VPC 的缺省 ACL 中允许 TCP/IP 端口 3389 上的入站流量。有关更多信息，请参阅[设置网络 ACL](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls)。
4. 验证是否已安装 OpenSSL。要成功解密密码，必须运行 OpenSSL，而不是 LibreSSL。有关更多信息，请参阅 [OpenSSL 下载 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.openssl.org/source/){: new_window}。

LibreSSL 不支持对密码解密。必须运行 OpenSSL 来解密密码。
{:important}

## 连接
{: #getting-connected-windows}

创建 Windows 实例并完成先决条件后，请完成以下步骤连接到 Windows 实例。

1. 通过运行以下命令，查询实例的状态：
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  实例显示的状态为 `running` 时，说明您已准备好检索初始化值来获取密码。 

2. 运行以下命令来初始化实例：

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  此命令会显示加密密码，这是使用 Windows 映像创建实例时自动生成的密码。

3. 现在，需要通过手动解密过程来解密密码。要解密密码，请运行以下命令：

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  其中，`~/examplepwd` 是您将步骤 2 中所引用的加密密码保存到的文件。  
  
  macOS 随附的 LibreSSL 不支持解密密码所需的 SHA2 哈希算法，因此会生成`公用密钥操作错误`的错误。可以使用软件包管理工具或通过手动安装标准 OpenSSL 库来获取这些库。
  {:note}

4. 解密密码后，可以选择将浮动 IP 地址与 Windows 实例相关联，以便可以从因特网位置连接到该实例。运行以下命令将浮动 IP 地址与实例相关联：

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. 现在，您已经有了连接到 Windows 实例所需的信息：解密密码和浮动 IP 地址。请使用首选的远程桌面客户机连接到实例。要连接到实例，请提供浮动 IP 地址和解密密码。缺省情况下，用户名为 `Administrator`。

## 后续步骤
{: #next-manage-instances}

连接到实例后，可以[使用 {{site.data.keyword.cloud_notm}} 控制台管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)或[使用 CLI 管理实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)。 
