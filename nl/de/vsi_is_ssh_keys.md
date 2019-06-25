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

# SSH-Schlüssel verwalten
{: #managing-ssh-keys}

## Vorbereitende Schritte
{: #prereq-ssh-key-available}

Damit Sie auf {{site.data.keyword.vsi_is_full}}-Instanzen zugreifen können, muss Ihnen ein verwendungsbereiter SSH-Schlüssel zur Verfügung stehen. Zur Verwaltung von SSH-Schlüsseln können Sie die {{site.data.keyword.cloud_notm}}-Konsole und die CLI verwenden. 

Die Verwaltung von Schlüsseln mithilfe der {{site.data.keyword.cloud_notm}}-Konsole oder der CLI hat keinen Einfluss auf Schlüssel in bereits erstellten Instanzen. (Die Schlüssel für eine vorhandene Linux-Instanz können Sie direkt im Verzeichnis `~/.ssh/` der Instanz bearbeiten.)

Weitere Informationen zum Ermitteln oder Generieren eines SSH-Schlüssels finden Sie unter [SSH-Schlüssel](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).
{: tip}

## SSH-Schlüssel über die IBM Cloud-Konsole verwalten
{: #managing-ssh-keys-with-ibm-cloud-console}

Bei der Bereitstellung eines virtuellen Servers können Sie eine Auswahl unter vorhandenen SSH-Schlüsseln treffen oder einen neuen Schlüssel hochladen. Die Generierung von SSH-Schlüsseln in der {{site.data.keyword.cloud_notm}}-Konsole ist nicht möglich.
{:shortdesc}

In der {{site.data.keyword.cloud_notm}}-Konsole können Sie SSH-Schlüssel verwalten und löschen.
1. Navigieren Sie in der [{{site.data.keyword.cloud_notm}}-Konsole ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.cloud.ibm.com/vpc) zum **Menü ![Menüsymbol](../icons/icon_hamburger.svg) > VPC-Infrastruktur > Datenverarbeitung > SSH-Schlüssel**.
2. Von dieser Seite aus können Sie einen SSH-Schlüssel hinzufügen oder löschen.

## SSH-Schlüssel über die CLI verwalten
{: #managing-ssh-keys-by-using-the-cli}

Zur Verwaltung Ihrer SSH-Schlüssel können Sie auch die CLI verwenden.

| Aktion           | Befehl                     | Folge |
| ---------------- | --------------------------- | ----------------- |
| SSH-Schlüssel erstellen   | `ibmcloud is key-create`    | Nachdem Sie einen SSH-Schlüssel erstellt haben, wird er zur Liste der Schlüssel hinzugefügt. |
| Schlüsseldetails anzeigen | `ibmcloud is key`           | Sie können den Namen des Schlüssels und die ID des Schlüssels anzeigen. |
| Schlüssel auflisten        | `ibmcloud is keys`          | Sie können alle vorhandenen SSH-Schlüssel anzeigen. |
| Schlüssel aktualisieren       | `ibmcloud is key-update`    | Nachdem Sie einen vorhandenen Schlüssel aktualisiert haben, wird der Schlüssel sofort umbenannt. |
| Schlüssel löschen       | `ibmcloud is key-delete`    | Nachdem Sie einen SSH-Schlüssel entfernt haben, kann er nicht mehr verwendet werden, wenn Sie eine neue Instanz bereitstellen oder wenn Sie ein erneutes Laden des Betriebssystems in einer vorhandenen Instanz ausführen. Der Schlüssel steht jedoch immer noch für alle Instanzen zur Verfügung, die Sie mit ihm bereitgestellt haben, und Sie können ihn verwenden, um sich anzumelden. |
{: caption="Tabelle 1. Aktionen für SSH-Schlüssel" caption-side="top"}
