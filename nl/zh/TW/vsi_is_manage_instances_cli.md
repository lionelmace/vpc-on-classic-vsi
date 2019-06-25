---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 管理虛擬伺服器實例 (CLI)
{: #managing-virtual-servers-cli}

您可以使用指令行介面 (CLI) 來檢視及管理 {{site.data.keyword.vsi_is_full}} 實例。
{:shortdesc}

## 開始之前
{: #prereq-managing-instances}

1. 確定您已下載、安裝及起始設定下列 CLI 外掛程式：
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 外掛程式

   如需相關資訊，請參閱 [IBM Cloud CLI for VPC Reference](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)。
   
   第一次安裝 vpc-infrastructure 外掛程式時，您必須將目標世代設為 gen 1，`ibmcloud is target --gen 1`。
   {:important}
   
2. 確定您已經[建立了 {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。

## 檢視實例動作
{: #viewing-instance-actions}

若要檢視對實例執行的管理動作，請執行下列指令：

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

您將看到類似下列輸出的清單：

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## 管理實例
{: #managing-your-instances}

需要一點協助？請隨時執行 `ibmcloud is help` 指令來檢視指令。

### Reset  

```
ibmcloud is instance-reset
```
{:codeblock}

關閉實例電源，然後開啟電源。  

### Restart

```
ibmcloud is instance-reboot
```
{:codeblock}

重新啟動實例的作業系統。  

### Stop and start

```
ibmcloud is instance-stop 或 ibmcloud is instance-start
```
{:codeblock}

如果裝置已停止，裝置會保持在已停止狀態，必須手動啟動。如果實例已停止，您便無法與實例互動。如果裝置已啟動，正常的互動會繼續。 

### Update

```
ibmcloud is instance-update
```
{:codeblock}

重新命名裝置之後，會自動更新名稱。執行搜尋時，當嘗試尋找與其相關聯的內容時，請使用新的實例名稱。 

### Delete

```
ibmcloud is instance-delete
```
{:codeblock}

在確認 delete 動作之後，即會開始刪除實例及其相關聯 vNIC、開機磁區及資料的處理程序。delete 動作可能需要數分鐘，但是當處理程序完成時，實例不再出現在「虛擬伺服器實例」頁面上。與虛擬伺服器實例相關聯的浮動 IP 位址未相關聯，但仍留在您的帳戶中。

如果您偏好使用 {{site.data.keyword.cloud}} 主控台來管理實例，請參閱[管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)。
{: tip}
