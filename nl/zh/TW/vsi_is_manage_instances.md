---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 管理虛擬伺服器實例
{: #managing-virtual-server-instances}
[comment]: # (鏈結的說明主題)

您可以從 {{site.data.keyword.cloud_notm}} 主控台的*虛擬伺服器實例* 頁面中，檢視和管理 {{site.data.keyword.vsi_is_full}} 實例。
{:shortdesc}

若要管理實例，請完成下列步驟。
1. 在 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.cloud.ibm.com/vpc) 中，導覽至**功能表圖示 ![功能表圖示](../icons/icon_hamburger.svg) > VPC 基礎架構 > 運算 > 虛擬伺服器實例**。
2. 從這裡，您可以管理特定實例的作業，或按一下實例來檢視和編輯其內容。

## Reboot

reboot 動作會立即關閉實例電源，然後重新開啟電源。

## Stop and start

stop and start 動作會從遠端關閉或啟動實例。如果實例已停止，實例會保持在已停止狀態，必須手動啟動。實例已停止時，部分運算資源的計費會[暫停](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing)。如果實例已停止，您便無法與實例互動。如果裝置已啟動，正常的互動會繼續。

## Delete

delete 動作會永久地從您的帳戶移除實例及其已連接的 vNIC、開機磁區及資料。在確認 delete 動作之後，即會開始刪除實例及其相關聯 vNIC、開機磁區及資料的處理程序。delete 動作最多可能需要 30 分鐘，但是當處理程序完成時，實例不再出現在「虛擬伺服器實例」頁面上。與虛擬伺服器實例相關聯的浮動 IP 位址未相關聯，但仍留在您的帳戶中。

## 檢視實例詳細資料
您可以透過在*虛擬伺服器實例* 頁面上檢視所有實例的摘要，或按一下個別實例來檢視詳細資料並進行變更，而與實例互動。從實例詳細資料頁面中，您也可以檢視相關聯的網路介面、存取其子網路，以及保留或刪除浮動 IP 位址。

如果您偏好使用 CLI 來管理實例，請參閱[使用 CLI 管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)。
{: tip}
