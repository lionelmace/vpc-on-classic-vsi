---

copyright:
  years: 2019
lastupdated: "2019-06-05"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# Virtuelle Serverinstanzen mit kundenverwalteter Verschlüsselung erstellen
{: #creating-instances-byok}

Sie können {{site.data.keyword.vsi_is_full}} mit Verwendung einer kundenverwalteten Verschlüsselung für Blockspeicherdatenträger erstellen, wenn Ihnen ein Schlüsselmanagementservice zur Verfügung steht, der Ihren eigenen Schlüssel zur Datenverschlüsselung beinhaltet. Standardmäßig werden Instanzen mit einem Bootdatenträger bereitgestellt, der eine providerverwaltete Verschlüsselung enthält. Sie können Instanzen, die eine kundenverwaltete Verschlüsselung für Blockspeicherdatenträger verwenden, über die {{site.data.keyword.cloud_notm}}-Konsole oder mithilfe der Befehlszeilenschnittstelle (CLI) bereitstellen.
{:shortdesc}

## Unterstützte Schlüsselmanagementservices für kundenverwaltete Verschlüsselung
{: #kms-for-byok}

Sie können den Schlüsselmanagementservice verwenden, der für Ihren Bedarf am besten geeignet ist. {{site.data.keyword.keymanagementserviceshort}} und {{site.data.keyword.hscrypto}} (verfügbar in bestimmten [Regionen](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)) nutzen eine allgemeine API für Schlüsselprovider, damit eine konsistente Methode für die Verwaltung von Verschlüsselungsschlüsseln bereitsteht.  {{site.data.keyword.cloud_notm}}-Rechenzentren bieten im Hintergrund ein dediziertes Hardwaresicherheitsmodul (HSM) für den Schutz Ihrer Schlüssel.  Die folgenden Schlüsselmanagementservices werden bei der kundenverwalteten Verschlüsselung für Blockspeicherdatenträger unterstützt: 

| Schlüsselmanagementservice | HSM-Verschlüsselungszertifizierung |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | Konformität mit FIPS 140-2 *Stufe 2* |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | Konformität mit FIPS 140-2 *Stufe 4* |
{: caption="Tabelle 1. Verfügbare Optionen für Schlüsselmanagementservice" caption-side="top"}

## Voraussetzungen
{: #byok-vsi-prereqs}

Damit Sie eine virtuelle Serverinstanz erstellen können, die eine kundenverwaltete Verschlüsselung für Blockspeicherdatenträger verwendet, müssen Sie einen Schlüsselmanagementservice bereitgestellt und einen Kundenrootschlüssel hinzugefügt haben. Außerdem müssen Sie den Zugriff zwischen Cloud Block Storage und dem Schlüsselmanagementservice berechtigen. Nachdem Sie diese Voraussetzungen geschaffen haben, können Sie mit der Erstellung von Instanzen beginnen, die eine kundenverwaltete Verschlüsselung für die Blockspeicherdatenträger verwenden. 

Die folgenden Schritte sind zwar für {{site.data.keyword.keymanagementserviceshort}} spezifisch, aber der allgemeine Ablauf gilt auch für {{site.data.keyword.hscrypto}}. Lesen Sie bei Verwendung von {{site.data.keyword.hscrypto}} die [Informationen zu {{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started), die entsprechende Anweisungen enthalten.
{:note}

1. Stellen Sie den [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision)-Service bereit. 
   
   Die Bereitstellung einer neuen Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service stellt sicher, dass sie die neuesten Aktualisierungen enthält, die für eine kundenverwaltete Verschlüsselung von Blockspeicherdatenträgern erforderlich sind. 
   {: tip}
   
2. [Erstellen](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) oder [importieren](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) Sie einen Rootschlüssel (CRK) in {{site.data.keyword.keymanagementservicelong_notm}}.
3. Richten Sie ausgehend von {{site.data.keyword.iamshort}} (IAM) die [Zugriffsberechtigung](/docs/iam?topic=iam-serviceauth#serviceauth) zwischen**Cloud Block Storage** (Quellenservice) und **{{site.data.keyword.keymanagementserviceshort}}** (Zielservice) ein.

## Virtuelle Serverinstanzen mit Datenträgern bereitstellen, die eine kundenverwaltete Verschlüsselung verwenden
{: #provision-byok-ui}

Beim Bereitstellen einer virtuellen Serverinstanz können Sie eine kundenverwaltete Verschlüsselung für Ihren Bootdatenträger und alle Datendatenträger angeben, die Sie zum Zeitpunkt der Bereitstellung hinzufügen wollen. Auf Wunsch können Sie eine Kombination aus providerverwalteter Verschlüsselung und kundenverwalteter Verschlüsselung für die Datenträger  verwenden, die Ihrer Instanz zugeordnet sind.

1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.cloud.ibm.com/vpc) zum **Menü ![Menüsymbol](../icons/icon_hamburger.svg) > VPC-Infrastruktur > Datenverarbeitung > Virtuelle Serverinstanzen**. Klicken Sie auf **Neue Instanz** und füllen Sie die erforderlichen Felder aus. (Weitere Informationen zum Erstellen von Instanzen finden Sie unter [Virtuelle Serverinstanzen erstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).) 
2. Im Abschnitt **Bootdatenträger** ist die _providerverwaltete_ Verschlüsselung der Standardverschlüsselungsmodus. Um die kundenverwaltete Verschlüsselung anzugeben, klicken Sie in der Zeile für den Bootdatenträger auf das Stiftsymbol. Aktualisieren SIe auf der Seite **Bootdatenträger bearbeiten** die Felder im Abschnitt **Verschlüsselung**. Weitere Informationen können Sie der folgenden Tabelle entnehmen. Nachdem Sie alle gewünschten Änderungen vorgenommen haben, klicken Sie auf **Anwenden**.
3. Im Abschnitt **Zugeordneter Blockspeicherdatenträger** können Sie auf **Neuer Blockspeicherdatenträger** klicken, um einen Datendatenträger hinzuzufügen und auf Wunsch die kundenverwaltete Verschlüsselung anzugeben. Aktualisieren SIe auf der Seite **Neuer Blockspeicherdatenträger** die Felder im Abschnitt **Verschlüsselung**. Weitere Informationen können Sie der folgenden Tabelle entnehmen. Nachdem Sie alle gewünschten Änderungen vorgenommen haben, klicken Sie auf **Anhängen**.

| Feld | Wert |
| ----- | ----- |
| Verschlüsselung | _Providerverwaltet_ ist der Standardverschlüsselungsmodus. Zur Verwendung der kundenverwalteten Verschlüsselung wählen Sie in der Dropdown-Liste einen Schlüsselmanagementservice aus. Die Instanz des Schlüsselmanagementservice sollte den Kundenrootschlüssel enthalten, den Sie für die kundenverwaltete Verschlüsselung verwenden wollen. |
| Instanz des Verschlüsselungsservice | Falls Sie in Ihrem Konto mehrere Instanzen des Schlüsselmanagementservice bereitgestellt haben, wählen Sie diejenige Instanz aus, die den Kundenrootschlüssel enthält, den Sie für die kundenverwaltete Verschlüsselung verwenden wollen. |
| Schlüsselname | Wählen Sie den Schlüssel zur Datenverschlüsselung in der Instanz des Schlüsselmanagementservice aus, den Sie zum Verschlüsseln des Datenträgers verwenden wollen. | 
| Schlüssel-ID | Zeigt die Schlüssel-ID an, die dem von Ihnen ausgewählten Schlüssel zur Datenverschlüsselung zugeordnet ist. | 
{: caption="Tabelle 1. Werte zur Angabe der kundenverwalteten Verschlüsselung von Datenträgern" caption-side="top"}

## Instanzen und Datenträger mit kundenverwalteter Verschlüsselung über die CLI bereitstellen
{: #provision-byok-cli}

Um eine virtuelle Serverinstanz mit Datenträgern, die die kundenverwaltete Verschlüsselung verwenden, über die CLI zu erstellen, können Sie den Befehl `ibmcloud is instance-create` verwenden und eine JSON-Datei zur Zuordnung von Datenträgern referenzieren, die die kundenverwaltete Verschlüsselung nutzen. 

1. Rufen Sie den CRN des Rootschlüssels in Ihrer gewünschten Instanz des Schlüsselmanagementservice ab. Das folgende Beispiel gilt speziell für {{site.data.keyword.keymanagementserviceshort}}. 
    
    1. Wenn Sie das Plug-in für die CLI von {{site.data.keyword.keymanagementserviceshort}} noch nicht installiert haben, installieren Sie es mit dem folgenden Befehl: 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. Listen Sie mit dem folgenden Befehl die Instanzen des {{site.data.keyword.keymanagementserviceshort}}-Service für Ihr Konto auf:
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. Rufen Sie mit dem folgenden Befehl die Instanz-ID für die Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service ab, in der Ihre Kundenrootschlüssel gespeichert sind:  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       Hierbei steht _Key Protect-17_ für Ihre gewünschte Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service.
    
       Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       Hierbei ist die Instanz-ID die Zeichenfolge, die auf die letzte Zeichengruppe `::` im CRN folgt, also `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`. 
    
    4. Listen Sie mit dem folgenden Befehl die verfügbaren Schlüssel sowie ihre zugehörigen CRNs in der gewünschten Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service auf:
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       Hierbei ist _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ die Instanz-ID Ihrer gewünschten Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service.
       
       Bei diesem Beispiel sehen Sie eine Antwort, die Ähnlichkeit mit der folgenden Ausgabe hat:
       ```
       Retrieving keys...
              
       SUCCESS
               
       Key ID                                 Key Name               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. Führen Sie den Befehl [ibmcloud is instance-create](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference#instance-create) aus und ordnen Sie die erforderlichen JSON-Dateien zu, die die kundenverwaltete Verschlüsselung für den Bootdatenträger und alle sekundären Datendatenträger angeben, die Sie einbeziehen wollen. Der Parameter `encryption_key` muss einen gültigen CRN für den Rootschlüssel im Key Protect-Service enthalten. Die folgenden [Beispiele für JSON-Dateien](#vsi-vol-attachment-json) zeigen eine JSON-Datei für einen Bootdatenträger und eine JSON-Datei für einen sekundären Datenträger. (Weitere Informationen zum Erstellen von Instanzen enthält der Abschnitt [Virtuelle Serverinstanzen erstellen (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli).)

## Datenträgerzuordnung im JSON-Format erstellen
{: #vsi-vol-attachment-json}

Wenn Sie während der VSI-Bereitstellung entweder einen Bootdatenträger oder einen Datendatenträger erstellen, müssen Sie eine JSON-Datei angeben, um die Datenträgerparameter zu definieren. Weitere Informationen können Sie den folgenden Beispielen für JSON-Dateien entnehmen.

### Beispiel einer JSON-Datei für Bootdatenträger
{: #boot-volume-byok-json}

Die Datei im folgenden Beispiel definiert einen vielseitig einsetzbaren Bootdatenträger und gibt den Parameter `encryption key` für die kundenverwaltete Verschlüsselung an.

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      },
      "encryption_key":{  
         "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### Beispiel einer JSON-Datei für sekundären Datenträger
{: #secondary-volume-byok-json}

Die Datei im folgenden Beispiel definiert einen vielseitig einsetzbaren sekundären Datenträger (für Daten) und gibt den Parameter `encryption key` für die kundenverwaltete Verschlüsselung an.

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         },
         "encryption_key":{  
            "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}
