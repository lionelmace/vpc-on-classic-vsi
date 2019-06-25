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

# Windows インスタンスへの接続
{: #connecting-to-your-windows-instance}

{{site.data.keyword.vsi_is_full}} Windows インスタンスを作成した後、以下のステップを実行してそのインスタンスに接続できます。
{:shortdesc}

## 始める前に
{: #prereqs-connect-windows}

開始する前に、以下の前提条件を満たしていることを確認してください。

1. アカウント管理者に、仮想サーバー・インスタンスからパスワードを取得するための権限を付与するよう依頼してください。 詳しくは、[ユーザー権限](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources)を確認してください。
2. 新規セキュリティー・グループを作成するか、デフォルトのセキュリティー・グループにルールを追加して、リモート・デスクトップのデフォルト・ポート 3389 のインバウンド・アクセスを有効にします。 詳しくは、[セキュリティー・グループの使用](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups)を参照してください。
3. TCP/IP ポート 3389 を介したインバウンド・トラフィックが VPC のデフォルト ACL で許可されていることを確認します。 詳しくは、[ネットワーク ACL のセットアップ](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls)を参照してください。
4. OpenSSL が正常にインストールされたことを確認します。 パスワードを正常に暗号化解除するには、LibreSSL ではなく OpenSSL を実行する必要があります。 詳しくは、[OpenSSL のダウンロード![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.openssl.org/source/){: new_window}を参照してください。

LibreSSL には、パスワードの暗号化解除のための互換性がありません。 パスワードを暗号化解除するには、OpenSSL を実行する必要があります。
{:important}

## 接続
{: #getting-connected-windows}

Windows インスタンスを作成して前提条件を満たした後、以下のステップを実行して Windows インスタンスに接続します。

1. 以下のコマンドを実行して、インスタンスの状況を照会します。
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  インスタンスが`実行中`になっている場合、初期化値を取得してパスワードを取得することができます。 

2. 以下のコマンドを実行して、インスタンスを初期化します。

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  このコマンドは、Windows イメージを使用してインスタンスを作成するときに自動的に生成される暗号化パスワードを表示します。

3. 次に、手動暗号化解除プロセスでパスワードを暗号化解除する必要があります。 パスワードを暗号化解除するには、以下のコマンドを実行します。

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  ここで、`~/examplepwd` は、ステップ 2 で参照した暗号化パスワードが保存されているファイルです。  
  
  macOS に組み込まれている LibreSSL は、パスワードの暗号化解除に必要な SHA2 ハッシュ・アルゴリズムをサポートしていないため、`「パブリック鍵の操作エラー (Public Key operation error)」`エラーが発生します。 標準 OpenSSL ライブラリーは、パッケージ管理ツールを使用するか、手動でインストールすることによって取得できます。 
  {:note}

4. パスワードを暗号化解除した後、オプションで浮動 IP アドレスを Windows インスタンスに関連付けて、インターネット・ロケーションから接続できるようにすることができます。 以下のコマンドを実行して、浮動 IP アドレスをインスタンスに関連付けます。

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. これで、Windows インスタンスに接続するために必要な情報 (暗号化解除されたパスワードと浮動 IP アドレス) を取得できました。 任意のリモート・デスクトップ・クライアントを使用してインスタンスに接続します。 インスタンスに接続するには、浮動 IP アドレスと暗号化解除されたパスワードを指定します。 デフォルトでは、ユーザー名は `Administrator` です。

## 次のステップ
{: #next-manage-instances}

インスタンスに接続した後は、[{{site.data.keyword.cloud_notm}} コンソールを使用してインスタンスを管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)したり、[CLI を使用してインスタンスを管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)したりできます。 
