---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Fehlerbehebung bei Virtual Servers for VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
Falls Sie im Zusammenhang mit Ihren {{site.data.keyword.vsi_is_full}}-Instanzen Probleme feststellen, können Sie sich in diesem Abschnitt über mögliche Ursachen informieren.

## Fehler: 409 Konflikt beim Erstellen einer Instanzenaktion

Bestimmte Instanzenaktionen können nicht erstellt werden, wenn der Status Ihrer Instanz mit einer anderen Aktion kollidiert. Falls Ihre Instanz beispielsweise den Status `stopped` (= gestoppt) aufweist und Sie versuchen, eine Aktion `reboot` zu erstellen, gibt das System den Fehler 409 zurück.

| Status      | Aktion     | Konflikt |
| ----------- | ---------- | -------- |
| Aktiv     | start      | Ja      |
| Gestoppt     | not start  | Ja      |
| Nicht aktiv | reboot     | Ja      |

## Instanzstatus verbleibt bei `deleting`

Wenn Sie beim Auflisten von Instanzen feststellen, dass eine Instanz im Status `deleting` (= wird gelöscht) verbleibt, aktualisieren Sie mithilfe der API zum Anzeigen von Instanzen (`/instances/{instanz-id}`) den Instanzstatus für die spezielle virtuelle Serverinstanz. Wenn zum Anzeigen aller Instanzen die API für das Auflisten (`/instances`) verwendet wird, werden möglicherweise nicht die aktuellsten Statuswerte angezeigt.
