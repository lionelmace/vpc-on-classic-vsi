---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# SSH 密钥
{: #ssh-keys}
[comment]: # (链接的帮助主题)

供应 {{site.data.keyword.vsi_is_full}} 时，必须选择现有 SSH 密钥或上传要使用的新 SSH 密钥，然后才能创建实例。服务器使用 SSH 密钥通过公用密钥加密系统来识别用户或实例。SSH 密钥由字母数字组合构成，并且对于将其分配到的实例唯一。可以使用 {{site.data.keyword.cloud_notm}} 控制台来添加、编辑或删除 SSH 密钥。
{:shortdesc}

通过 SSH 密钥，可从在实例上实施的每个公用密钥的对应客户机来访问该实例，而无需使用密码。通过将 SSH 密钥添加到实例（可以在供应期间执行此操作），可以使用对应的密钥而不是密码来访问该实例。仅当初始创建实例时，才能将 SSH 密钥添加到实例。创建 Linux 实例后，可以直接在实例的 `~/.ssh/` 目录中编辑密钥。

不支持使用密码登录到实例。如果您拥有的是 Windows 实例，那么可使用 SSH 密钥来解密密码。有关更多信息，请参阅[连接到 Windows 实例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance)。
{:note}

## 查找或生成 SSH 密钥
{: #locating-or-generating-your-ssh-key}

您必须有 SSH 密钥可用。要查找 SSH 密钥或生成 SSH 密钥，请完成下列其中一个步骤。

 * 查找 SSH 密钥：在主目录下的 `.ssh` 目录中查找名为 `id_rsa.pub` 的文件，例如 `/Users/<USERNAME>/.ssh/id_rsa.pub`。该文件以 `ssh-rsa` 开头，以您的电子邮件地址结尾。

* 生成 SSH 密钥：如果您没有公用 SSH 密钥，或者忘记了现有公用 SSH 密钥的密码，请通过运行 `ssh-keygen` 命令并遵循提示来生成新的 SSH 密钥。例如，可以在 Linux 服务器上，通过运行 `ssh-keygen -t rsa -C "user_ID"` 命令来生成 SSH 密钥。该命令会生成两个文件。生成的公用密钥位于 `<your key>.pub` 文件中。

  如果使用的是 OpenSSH V7.8 或更高版本，并且计划使用 SSH 密钥来访问 Windows 实例，那么必须使用以下命令生成 PEM 格式的密钥：`$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

有关创建、编辑或删除 SSH 密钥的更多信息，请参阅[管理 SSH 密钥](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)。
