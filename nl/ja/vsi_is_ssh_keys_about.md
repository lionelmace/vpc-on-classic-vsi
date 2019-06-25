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

# SSH 鍵
{: #ssh-keys}
[comment]: # (リンクされているヘルプ・トピック)

{{site.data.keyword.vsi_is_full}} をプロビジョンするときは、インスタンスを作成する前に、使用する SSH 鍵として、既存の SSH 鍵を選択するか、新規 SSH 鍵をアップロードする必要があります。 SSH 鍵は、公開鍵暗号方式を使用してユーザーまたはインスタンスを識別するためにサーバーによって使用されます。 SSH 鍵は、英数字の組み合わせで構成されており、それらが割り当てられているインスタンスに固有です。 {{site.data.keyword.cloud_notm}} コンソールを使用して、SSH 鍵を追加、編集、または削除できます。
{:shortdesc}

SSH 鍵があれば、インスタンスで実装されている各公開鍵に対する該当クライアントのパスワードを使用せずにインスタンスへアクセスすることができます。 インスタンスに SSH 鍵を追加すると (これはプロビジョニング中に実行できます)、パスワードではなく対応する鍵を使用してインスタンスにアクセスできます。 インスタンスに SSH 鍵を追加できるのは、インスタンスの初回作成時のみです。 Linux インスタンスの作成後は、インスタンスの `~/.ssh/` ディレクトリーで鍵を直接編集できます。

パスワードによるインスタンスへのログインはサポートされていません。 Windows インスタンスの場合は、パスワードの暗号化解除に SSH 鍵が使用されます。 詳しくは、[Windows インスタンスへの接続](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance)を参照してください。
{:note}

## SSH 鍵の検索または生成
{: #locating-or-generating-your-ssh-key}

使用可能な SSH 鍵が必要です。 SSH 鍵を見つけるか、SSH 鍵を生成するには、以下のいずれかの手順を実行します。

 * SSH 鍵の検索: ホーム・ディレクトリーの `.ssh` ディレクトリー内で `id_rsa.pub` というファイル (例: `/Users/<USERNAME>/.ssh/id_rsa.pub`) を探します。 このファイルは `ssh-rsa` で始まり、E メール・アドレスで終わります。

* SSH 鍵の生成: 公開 SSH 鍵がない場合、または既存の SSH 鍵のパスワードを忘れた場合は、`ssh-keygen` コマンドを実行し、プロンプトの指示に従って新しい鍵を生成します。 例えば、Linux サーバーで SSH 鍵を生成するには、コマンド `ssh-keygen -t rsa -C"user_ID "` を実行します。 このコマンドにより 2 つのファイルが生成されます。 生成された公開鍵は `<your key>.pub` ファイルに含まれています。

  OpenSSH バージョン 7.8 以降を使用しており、SSH 鍵を使用して Windows インスタンスにアクセスする予定の場合は、以下のコマンドを使用して PEM 形式で鍵を生成する必要があります。 `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

SSH 鍵の作成、編集、または削除について詳しくは、[SSH 鍵の管理](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)を参照してください。
