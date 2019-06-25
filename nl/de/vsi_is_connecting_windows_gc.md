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

# Verbindung zu Ihrer Windows-Instanz herstellen
{: #connecting-to-your-windows-instance}

Nachdem Sie Ihre Windows-Instanz von {{site.data.keyword.vsi_is_full}} erstellt haben, können Sie mit den hier beschriebenen Schritten eine Verbindung zur Instanz herstellen.
{:shortdesc}

## Vorbereitende Schritte
{: #prereqs-connect-windows}

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie beginnen:

1. Bitten Sie Ihren Kontoadministrator, Ihnen Zugriff zu erteilen, damit Sie das Kennwort aus Ihrer virtuellen Serverinstanz abrufen können. Weitere Informationen finden Sie im Abschnitt [Benutzerberechtigungen](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources).
2. Erstellen Sie eine neue Sicherheitsgruppe oder fügen Sie der Standardsicherheitsgruppe eine Regel hinzu, um den eingehenden Zugriff für den Remote Desktop-Standardport 3389 zu aktivieren. Weitere Informationen hierzu finden Sie im Abschnitt [Sicherheitsgruppen verwenden](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups).
3. Stellen Sie sicher, dass eingehender Datenverkehr über den TCP/IP-Port 3389 gemäß der Standardzugriffssteuerungsliste (Standard-ACL) der virtuellen privaten Cloud (VPC) zulässig ist. Weitere Informationen hierzu finden Sie im Abschnitt [Netz-ACLs konfigurieren](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls).
4. Vergewissern Sie sich, dass OpenSSL installiert ist. Sie müssen OpenSSL und nicht LibreSSL ausführen, damit Sie Ihr Kennwort erfolgreich entschlüsseln können. Weitere Informationen finden Sie auf der Seite [OpenSSL Downloads. ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.openssl.org/source/){: new_window}

LibreSSL ist für die Entschlüsselung Ihres Kennworts nicht kompatibel. Zum Entschlüsseln Ihres Kennworts müssen Sie OpenSSL ausführen.
{:important}

## Verbindung herstellen
{: #getting-connected-windows}

Nachdem Sie die Windows-Instanz erstellt und die Voraussetzungen erfüllt haben, führen Sie die folgenden Schritte aus, um eine Verbindung zu Ihrer Windows-Instanz herzustellen.

1. Fragen Sie mit dem folgenden Befehl den Status Ihrer Instanz ab:
  ```
  $ ibmcloud is instance <instanz-id>
  ```
  {:codeblock}
  
  Wenn für die Instanz der Status `running` (= aktiv) angezeigt wird, können Sie die Initialisierungswerte für den Abruf Ihres Kennworts abrufen. 

2. Initialisieren Sie Ihre Instanz mit dem folgenden Befehl:

  ```
  $ ibmcloud is instance-initialization-values <instanz-id>
  ```
  {:codeblock}
  
  Mit diesem Befehl wird Ihr verschlüsseltes Kennwort angezeigt, das automatisch generiert wird, wenn Sie eine Instanz unter Verwendung eines Windows-Image erstellen.

3. Nun müssen Sie Ihr Kennwort in einem manuellen Entschlüsselungsprozess entschlüsseln. Führen Sie zum Entschlüsseln Ihres Kennworts den folgenden Befehl aus:

  ```
  # Verschlüsseltes Kennwort decodieren:
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decodiertes Kennwort mit RSA-Private-Key entschlüsseln:
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  Hierbei ist `~/examplepwd` die Datei, in der Sie Ihr verschlüsseltes Kennwort wie in Schritt 2 beschrieben gespeichert haben.  
  
  Das in MacOS enthaltene LibreSSL unterstützt SHA2-Hashalgorithmen nicht, die zum Entschlüsseln des Kennworts erforderlich sind, was zu Nachrichten über einen `Fehler bei der Operation für den öffentlichen Schlüssel` führt. Die OpenSSL-Standardbibliotheken können Sie mithilfe eines Paketmanagementtools abrufen oder manuell installieren. 
  {:note}

4. Nachdem Sie Ihr Kennwort entschlüsselt haben, können Sie Ihrer Windows-Instanz optional eine variable IP-Adresse zuordnen, damit Sie über eine Internetadresse eine Verbindung zu dieser IP-Adresse herstellen können. Führen Sie den folgenden Befehl aus, um Ihrer Instanz eine variable IP-Adresse zuzuordnen:

  ```
  ibmcloud is fipc --nic <instanz-nic-id>
  ```
  {:codeblock}

5. Alle Voraussetzungen für eine Verbindung zu Ihrer Windows-Instanz - also ein entschlüsseltes Kennwort und eine variable IP-Adresse - liegen jetzt vor. Verwenden Sie zum Herstellen der Verbindung zu Ihrer Instanz einen Remote Desktop-Client Ihrer Wahl. Geben Sie die variable IP-Adresse und das entschlüsselte Kennwort an, damit die Verbindung zu Ihrer Instanz hergestellt wird. Der Benutzername lautet standardmäßig `Administrator`.

## Nächste Schritte
{: #next-manage-instances}

Nachdem Sie eine Verbindung zu Ihrer Instanz hergestellt haben, können Sie [Ihre Instanzen über die {{site.data.keyword.cloud_notm}}-Konsole verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) oder [Ihre Instanzen über die CLI verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
