---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# 規劃實例
{: #planning-for-instances}
[comment]: # (鏈結的說明主題)


當您規劃佈建 {{site.data.keyword.vsi_is_full}} 時，可能會發現這項配置核對清單有助於充分利用虛擬伺服器部署。
{:shortdesc}

開始之前，請確定您已[建立 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

## 規劃佈建實例
{: #planning-for-provisioning-instances}

在您有可用的 {{site.data.keyword.vpc_short}} 之後，請先考量下列項目，再佈建您的實例。

|考量|
|-------------------|
|__ 1. 確定您的帳戶有必要的[使用者許可權](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)。如果您具有對 {{site.data.keyword.vpc_short}} 資源的編輯者或管理者授權，則您也會繼承權限，可以在該虛擬專用雲端內建立、刪除及修改虛擬伺服器實例。|
|__ 2. 檢查並行實例的[帳戶限制](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)。|
|__ 3. 確定 [SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)可供使用。
|__ 4. 決定要選取哪個實例位置。|
|__ 5. 考量工作負載 vCPU 和 RAM 組合的熱門[設定檔選項](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)。設定檔包含預先配置的實例，這些實例在幾分鐘內便可以使用。請務必確保實例將具有必要的資源，可保持工作負載及環境啟動並執行。|
|__ 6. 決定要為實例選取哪個作業系統映像檔。您可以從現行庫存[映像檔](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)當中進行選擇。|
|__ 7. 確定實例具有唯一名稱。如果您有一個命名虛擬伺服器實例的方法，則之後要進行過濾及搜尋會容易許多。|

## 後續步驟
{: #next-create-instance}

當您準備好開始使用時，請參閱下列資源來建立您的實例：
* [使用 {{site.data.keyword.cloud_notm}} 主控台建立實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [使用 CLI 建立實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
