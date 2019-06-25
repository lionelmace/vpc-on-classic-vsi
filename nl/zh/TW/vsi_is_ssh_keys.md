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
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 管理 SSH 金鑰
{: #managing-ssh-keys}

## 開始之前
{: #prereq-ssh-key-available}

若要存取 {{site.data.keyword.vsi_is_full}} 實例，您必須具有可供使用的 SSH 金鑰。您可以在 {{site.data.keyword.cloud_notm}} 主控台及使用 CLI 來管理 SSH 金鑰。 

使用 {{site.data.keyword.cloud_notm}} 主控台或 CLI 來管理金鑰，不會影響已建立之實例中的金鑰。（對於現有 Linux 實例，您可以直接在實例的 `~/.ssh/` 目錄中編輯金鑰。）

如需尋找或產生 SSH 金鑰的相關資訊，請參閱 [SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)。
{: tip}

## 使用 IBM Cloud 主控台管理 SSH 金鑰
{: #managing-ssh-keys-with-ibm-cloud-console}

佈建虛擬伺服器時，您可以從可用的 SSH 金鑰中進行選取，或上傳新的 SSH 金鑰。您無法在 {{site.data.keyword.cloud_notm}} 主控台中產生 SSH 金鑰。
{:shortdesc}

您可以使用 {{site.data.keyword.cloud_notm}} 主控台來管理及刪除 SSH 金鑰。
1. 在 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.cloud.ibm.com/vpc) 中，導覽至**功能表圖示 ![「功能表」圖示](../icons/icon_hamburger.svg) > VPC 基礎架構 > 運算 > SSH 金鑰**。
2. 從這裡，您可以新增或刪除 SSH 金鑰。

## 使用 CLI 管理 SSH 金鑰
{: #managing-ssh-keys-by-using-the-cli}

您也可以使用 CLI 來管理 SSH 金鑰。

| 動作           | 指令                     | 接下來會發生什麼情況 |
| ---------------- | --------------------------- | ----------------- |
| 建立 SSH 金鑰   | `ibmcloud is key-create`    | 建立 SSH 金鑰之後，會將它新增至金鑰清單。 |
| 檢視金鑰詳細資料 | `ibmcloud is key`           | 您可以檢視金鑰的名稱和金鑰的 ID。 |
| 列出金鑰       | `ibmcloud is keys`          | 您可以檢視所有現有 SSH 金鑰。|
| 更新金鑰       | `ibmcloud is key-update`    | 更新現有金鑰之後，會立即重新命名金鑰。 |
| 刪除金鑰       | `ibmcloud is key-delete`    | 移除 SSH 金鑰之後，當您佈建新的實例時，或在現有實例上執行 OS 重新載入時，就無法再使用該金鑰。不過，金鑰仍可在您佈建它的任何實例上使用，您可以用它來進行登入。|
{: caption="表 1. SSH 金鑰動作" caption-side="top"}
