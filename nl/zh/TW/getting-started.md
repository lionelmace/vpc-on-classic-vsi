---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# 入門指導教學
{: #getting-started}

請使用 {{site.data.keyword.vsi_is_full}} (VPC) 在 IBM Cloud 中佈建可擴充的運算資源。
{:shortdesc}

您可以建立所需數量的虛擬伺服器、配置網路及安全，以及管理儲存空間。在改良的 IBM Cloud 主控台中，這一切都可做到。主控台的建置是為了讓您快速且輕鬆地存取，以因應不斷變化的工作負載需求來調整您的環境。相信您也很急著開始使用了，讓我們直接進入正題。

開始之前，請確定您已[建立 IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

{{site.data.keyword.vsi_is_short}} 與標準虛擬伺服器供應項目不相容。如果您對標準基礎架構上的任何 {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} 供應項目有興趣，請參閱 [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial)。
{:note}

<p>請使用下列資訊來快速開始建立及連接至您的實例。
<table>
   <CAPTION>表 1. 快速入門步驟</CAPTION>
   <THEAD>
   <TR>
   <th>作業</th>
   <th>詳細資料</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. 檢閱有助於您實作的內容</td>
   <td>剛接觸 IBM Cloud 及虛擬伺服器嗎？下列網站提供有用的資訊來協助您規劃環境。
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">何謂 IBM Cloud</a></li>
      <li><a href="https://ibm.com/cloud/get-started">開始使用 IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. 註冊 IBM Cloud</td>
   <td>如需如何設定 IBM Cloud 帳戶的相關資訊，請參閱<a href="/docs/account?topic=account-signup#signup">註冊 IBM Cloud</a>。</td>
 <tr>
   <td>3. 決定工作負載規格</td>
   <td>在建立實例之前，請決定其使用方式及您順利作業所需要的實例大小。例如，您是要用它來進行開發及測試，還是用於正式作業？您要測試使用者體驗、處理冗長的演算法、備份及還原資料，還是提高延遲速度？</td>  
 <tr>
   <td>4. 調整實例的大小及價格</td>
   <td>當建立您的實例時，您有三個系列選項：平衡、運算、記憶體。系列包含預先配置的實例（稱為「設定檔」），這些實例符合大部分客戶的需求，而且可以在短短五分鐘內準備好配置。  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">平衡</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">運算</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">記憶體</a></li>
     </ul>
  <p>請使用[定價](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)資訊，來協助您調整實例的大小及價格。</p></td>
 <tr>
   <td>5. 登入 IBM Cloud 帳戶</td>
   <td>從 <a href="https://console.bluemix.net/catalog/">IBM Cloud 型錄</a>存取 {{site.data.keyword.vsi_is_short}} 訂單表格。您將需要 <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBM ID 及密碼</a>。
   </td>
 <tr>
   <td>6. 要求存取 {{site.data.keyword.vpc_short}} 體驗</td>
   <td>如果您尚未要求存取，請要求存取 {{site.data.keyword.vpc_short}}。</td>
<tr>
<td>7. 產生 SSH 金鑰</td>
<td> 如需相關指示，請參閱 [SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)。</td>
<tr>
<td>8. 規劃實例</td>
<td> 如需協助您順利規劃、佈建及配置資源的相關資訊，請參閱[規劃實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances)。</td>
<tr>
<td>9. 建立實例</td>
<td>
<p>
若要開始建立實例，請參閱[建立實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)。
</td>  
<tr>
<td>10. 連接至實例</td>
<td>您的實例現在已備妥！請參閱*連接* 下的下列主題，以驗證是否已順利建立實例。
   <ul>
   <li>[連接至 Linux 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[連接至 Windows 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. 清除實例</td>
<td>當您不再需要您的實例時，可以刪除它。</td>
</tr>
</TBODY>
</table>
</p>

## 後續步驟
佈建實例之後，請探索您的選項。
* [管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [{{site.data.keyword.vsi_is_short}} 許可權](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [IBM Cloud VPC 的安全](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about) 的相關資訊
