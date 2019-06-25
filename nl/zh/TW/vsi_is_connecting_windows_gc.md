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

# 連接至 Windows 實例
{: #connecting-to-your-windows-instance}

建立 {{site.data.keyword.vsi_is_full}} Windows 實例之後，您可以完成下列步驟來連接它。
{:shortdesc}

## 開始之前
{: #prereqs-connect-windows}

開始之前，請務必先完成下列必要條件：

1. 要求您的帳戶管理者授與您從虛擬伺服器實例擷取密碼的存取權。如需相關資訊，請檢閱[使用者許可權](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources)。
2. 建立新的安全群組，或將規則新增至預設安全群組，以啟用「遠端桌面」預設埠 3389 的入埠存取。如需相關資訊，請參閱[使用安全群組](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups)。
3. 確保在 VPC 的預設 ACL 上，允許透過 TCP/IP 埠 3389 的入埠資料流量。如需相關資訊，請參閱[設定網路 ACL](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls)。
4. 驗證您已安裝 OpenSSL。若要順利將密碼解密，您必須執行 OpenSSL 而非 LibreSSL。如需相關資訊，請參閱 [OpenSSL Downloads ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.openssl.org/source/){: new_window}。

LibreSSL 與您的密碼解密不相容。您必須執行 OpenSSL 來將密碼解密。
{:important}

## 取得連線
{: #getting-connected-windows}

建立 Windows 實例並完成必要條件之後，請完成下列步驟來連接至 Windows 實例。

1. 執行下列指令，查詢實例的狀態：
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  當實例顯示它是 `running` 時，您便可以擷取起始設定值來取得您的密碼。 

2. 執行下列指令來起始設定實例：

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  這個指令會顯示您的已加密密碼，這會在您使用 Windows 映像檔建立實例時自動產生。

3. 您現在需要透過手動解密程序來將密碼解密。若要將密碼解密，請執行下列指令：

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  其中 `~/examplepwd` 是您儲存已加密密碼的檔案，如步驟 2 中所提及。  
  
  macOS 所附的 LibreSSL 不支援將密碼解密所需的 SHA2 雜湊演算法，導致 `Public Key operation error` 錯誤。您可以使用套件管理工具或藉由手動安裝標準 OpenSSL 程式庫，而取得標準 OpenSSL 程式庫。
  {:note}

4. 將密碼解密之後，您可以選擇性地建立浮動 IP 位址與 Windows 實例的關聯，以便從網際網路位置連接至該實例。執行下列指令，以建立浮動 IP 位址與您實例的關聯：

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. 您現在具有要連接至 Windows 實例所需的項目：已解密的密碼及浮動 IP 位址。請使用偏好的「遠端桌面」用戶端連接至實例。若要連接至實例，請提供浮動 IP 位址及解密的密碼。依預設，使用者名稱是 `Administrator`。

## 後續步驟
{: #next-manage-instances}

在連接至實例之後，您可以[使用 {{site.data.keyword.cloud_notm}} 主控台管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)或[使用 CLI 管理實例](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)。 
