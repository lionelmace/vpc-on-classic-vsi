---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

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

# 建立虛擬伺服器實例
{: #creating-virtual-servers}
[comment]: # (鏈結的說明主題)

您可以從 {{site.data.keyword.cloud_notm}} 主控台的*虛擬伺服器實例* 頁面中，建立 {{site.data.keyword.vsi_is_full}}。
{:shortdesc}

開始之前，請確定您已[建立 IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)。
{:important}

若要建立實例，請選取下列實例詳細資料。
1. 在 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.cloud.ibm.com/vpc) 中，導覽至**功能表圖示 ![功能表圖示](../icons/icon_hamburger.svg) > VPC 基礎架構 > 運算 > 虛擬伺服器實例**。
2. 按一下**新建實例**，並輸入下列資訊：

    <table>
    <CAPTION>表 1. 實例佈建選項</CAPTION>
    <THEAD>
    <TR>
    <th>欄位</th>
    <th>值</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>名稱 </td>
    <td>虛擬伺服器實例需要名稱。</td>
    </tr>
    <tr>
    <td>Virtual Private Cloud</td>
    <td>指定要在其中建立實例的 IBM Cloud VPC。</td>
    </tr>
    <tr>
    <td>位置</td>
    <td>位置是由地區（特定地理區域）及區域（地區內的容錯資料中心）所組成。選取要建立虛擬伺服器實例的位置。</td>
    </tr>
    <tr>
    <td>設定檔</td>
    <td><p>
    從熱門設定檔或所有可用的 vCPU 及 RAM 組合中選取。支援下列系列：
    <ul>
    <li>平衡</li>
    <li>運算</li>
    <li>記憶體</li>
    </ul>
    </p>
    <p>伺服器上的每一個實體核心都是超執行緒，且呈現為兩個虛擬 CPU (vCPU)。虛擬伺服器供應項目的每個 vCPU 會提供 2.0 GHz 或更佳的處理能力，並且在單一虛擬伺服器上有最多 48 個 vCPU 可用。</p>

    <p>針對記憶體，實例可以有最多 256 GB 的完全專用 RAM。</p>
    <p><note>附註：最大值可能會依系列而變。</note></p>
    <p>如需相關資訊，請參閱[設定檔](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)。</p>
    </td>
    </tr>
    <tr>
    <td>映像檔</td>
    <td><p>所有映像檔都使用 cloud-init，這可讓您輸入與實例相關聯的使用者 meta 資料，用於佈建後的 Script。</p>
    <p>如需相關資訊，請參閱[映像檔](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)。</p>
    </td>
    </tr>
    <td>SSH 金鑰</td>
    <td>
    <p>您必須先選取現有的 SSH 金鑰或上傳新的 SSH 金鑰以便使用，才能建立實例。SSH 金鑰用來在實例執行之後安全地連接至實例。只有在您最初建立實例時，才可以將 SSH 金鑰新增至實例。</p>
    <p>附註：英數數字組合限制為 100 個字元。</p>
    <p>如需相關資訊，請參閱 [SSH 金鑰](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)。</p></td>
    </tr>
    <tr>
    <td>使用者資料</td>
    <td>
    <p>您可以新增使用者資料，以自動執行一般配置作業或執行 Script。<p>如需相關資訊，請參閱[使用者資料](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)。</p>
    </td>
    </tr>
    <tr>
    <td>開機磁區</td>
    <td><p>所有設定檔的預設開機磁區大小都是 100 GB。依預設，開機磁區包括提供者管理的加密。如果您要使用客戶管理的加密，可以編輯開機磁區的詳細資料。如需相關資訊，請參閱[儲存空間](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage)。</p>
    </td>
    </tr>
    <tr>
    <td>連接的區塊儲存空間磁區</td>
    <td><p>您可以在佈建實例時，新增一個以上要包含的次要資料磁區。若要新增磁區，請按一下**新建區塊儲存空間磁區**。如需相關資訊，請參閱[建立區塊儲存空間磁區](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)。</p>
    </td>
    </tr>
    <tr>
    <td>網路介面</td>
    <td>指派網路功能選項以連接至 IBM Cloud VPC。您可以建立最多 5 片網路介面卡至每一個實例。如需相關資訊，請參閱[多個 IP 位址](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options)。</td>
    </tr>
    </TBODY>
    </table>

    *成本摘要* 會顯示在*新建虛擬伺服器實例* 頁面的右側。

3. 當您準備好佈建時，請按一下**建立虛擬伺服器實例**。一系列的電子郵件會傳送給您的管理者：確認虛擬伺服器實例訂單、訂單核准和處理，以及指出已建立實例的訊息。

您偏好使用 CLI 來建立實例嗎？如需相關資訊，請參閱[使用 CLI 建立實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)。
{: tip}

## 保留浮動 IP 位址
{: #reserving-a-floating-ip-address}

您可以保留浮動 IP 位址，並使它與您的實例相關聯，這樣您就可以從網際網路位置連接它。

您的實例必須先執行，您才能關聯浮動 IP 位址。可能需要一些時間，實例才能開始執行。
{: note} 

若要保留及關聯浮動 IP 位址，請完成下列步驟。
1. 在**虛擬伺服器實例**頁面上，按一下實例來檢視其詳細資料。
2. 在**網路介面**區段中，按一下**保留 +**，使浮動 IP 位址與您的實例相關聯。

## 後續步驟
{: #next-connecting-to-instance}

現在，您已準備好連接到您的實例。如需相關資訊，請參閱[連接至 Linux 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)或[連接至 Windows 實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)。
