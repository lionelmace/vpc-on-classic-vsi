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

# SSH 金鑰
{: #ssh-keys}
[comment]: # (鏈結的說明主題)

當您佈建 {{site.data.keyword.vsi_is_full}} 時，必須選取現有 SSH 金鑰，或上傳要使用的新 SSH 金鑰，然後才能建立實例。透過公開金鑰加密法，伺服器使用 SSH 金鑰來識別使用者或實例。SSH 金鑰由英數組合所構成，且對於其獲指派的實例而言是唯一的。您可以使用 {{site.data.keyword.cloud_notm}} 主控台來新增、編輯或刪除 SSH 金鑰。
{:shortdesc}

SSH 金鑰容許您存取實例，而不使用實例上實作之每個公開金鑰的對應用戶端的密碼。藉由將 SSH 金鑰新增至實例（您可以在佈建期間執行），可以使用對應金鑰而非密碼來存取實例。只有在您最初建立實例時，才能將 SSH 金鑰新增至實例。建立 Linux 實例之後，您可以直接在實例的 `~/.ssh/` 目錄中編輯金鑰。

不支援使用密碼登入您的實例。如果您有 Windows 實例，則會使用 SSH 金鑰來將您的密碼解密。如需相關資訊，請參閱[連接至 Windows 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance)。
{:note}

## 尋找或產生 SSH 金鑰
{: #locating-or-generating-your-ssh-key}

您必須具有可用的 SSH 金鑰。若要尋找 SSH 金鑰或產生 SSH 金鑰，請完成下列其中一個步驟。

 * 尋找 SSH 金鑰：在起始目錄下的 `.ssh` 目錄下尋找一個稱為 `id_rsa.pub` 的檔案，例如 `/Users/<USERNAME>/.ssh/id_rsa.pub`。該檔案的開頭為 `ssh-rsa`，結尾為電子郵件位址。

* 產生 SSH 金鑰：如果您沒有公開 SSH 金鑰，或者您忘記現有 SSH 金鑰的密碼，請藉由執行 `ssh-keygen` 指令並遵循提示來產生新的 SSH 金鑰。例如，您可以藉由執行指令 `ssh-keygen -t rsa -C "user_ID"` 在 Linux 伺服器上產生 SSH 金鑰。該指令產生兩個檔案。產生的公開金鑰位於 `<your key>.pub` 檔案中。

  如果您使用 OpenSSH 7.8 版或更新版本，並計劃使用 SSH 金鑰來存取 Windows 實例，則必須使用下列指令，以 PEM 格式產生金鑰。`$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

如需建立、編輯或刪除 SSH 金鑰的相關資訊，請參閱[管理 SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)。
