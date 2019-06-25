---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Verbindung zu Ihrer Linux-Instanz herstellen
{: #connecting-to-your-linux-instance}

Nachdem Sie Ihre Linux-Instanz von {{site.data.keyword.vsi_is_full}} erstellt haben, können Sie mit den hier beschriebenen Schritten eine Verbindung zur Instanz herstellen.
{:shortdesc}

## Variable IP-Adresse ermitteln
{: #locating-floating-ip-address}

Falls Sie die variable IP-Adresse für die Instanz ermitteln müssen, zu der Sie eine Verbindung herstellen wollen, führen Sie die folgenden Schritte aus. Wenn Sie die variable IP-Adresse bereits kennen, können Sie direkt mit dem Schritt [Verbindung herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected) fortfahren. 

1. Sie müssen Ihre ID für die variable IP-Adresse ermitteln, bevor Sie Ihre variable IP-Adresse ermitteln können. Führen Sie zum Ermitteln Ihrer ID für die variable IP-Adresse den folgenden Befehl aus:

   ```
   $ ibmcloud is instance-network-interfaces <INSTANZ-ID> --json
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat (mit Verwendung der generischen Werte x und 123 ausschließlich zu Beispielzwecken):

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. Nachdem Sie Ihre ID für die variable IP-Adresse kennen, können Sie nun Ihre variable IP-Adresse ermitteln, indem Sie den folgenden Befehl ausführen:

   ```
   $ ibmcloud is ip <ID_FÜR_VARIABLE_IP-ADRESSE>
   ```
   {:codeblock}

   Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat (mit Verwendung der generischen Werte x und 123 ausschließlich zu Beispielzwecken):

   ```
   ID               12345x67-8901-234x-5678-9xx01xx23x4x
   Address          123.45.678.90
   Name             my-instance
   Target           primary(1xx2x34x-.)   
   Target Type      intf
   Target IP        12.345.6.78
   Created          1 week ago
   Status           available
   Zone             us-south-1
   Resource Group   -
   Tags             -   
   ```
   {:screen}

Optional können Sie die variable IP-Adresse, die der Instanz zugeordnet ist, zu der Sie eine Verbindung herstellen wollen, auch in der {{site.data.keyword.cloud_notm}}-Konsole ermitteln.
{:tip}

## Verbindung herstellen
{: #getting-connected}

Die nachfolgend zurückgegebenen Werte dienen lediglich der Veranschaulichung.

1. Verwenden Sie zum Herstellen einer Verbindung zu Ihrer Instanz Ihren privaten Schlüssel und führen Sie den folgenden Befehl aus:

   ```
   $ ssh -i <pfad_zur_datei_mit_ihrem_privaten_schlüssel> root@<variable_ip-adresse>
   ```
   {:codeblock}

   Sie erhalten eine ähnliche Antwort wie im folgenden Beispiel. Wenn Sie aufgefordert werden, den Verbindungsaufbau fortzusetzen, geben Sie `yes` ein.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   Sie greifen jetzt auf Ihren Server zu.

2. Wenn Sie die Verbindung beenden möchten, führen Sie den folgenden Befehl aus:

   ```
   # exit
   ```
   {:codeblock}

## Nächste Schritte
{: #next-managing-instances}

Nachdem Sie eine Verbindung zu Ihrer Instanz hergestellt haben, können Sie [Ihre Instanzen über die {{site.data.keyword.cloud_notm}}-Konsole verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) oder [Ihre Instanzen über die CLI verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
