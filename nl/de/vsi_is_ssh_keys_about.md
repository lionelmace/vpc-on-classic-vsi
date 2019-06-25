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
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# SSH-Schlüssel
{: #ssh-keys}
[comment]: # (Verlinktes Hilfethema)

Bei der Bereitstellung von {{site.data.keyword.vsi_is_full}} müssen Sie einen vorhandenen SSH-Schlüssel auswählen oder einen neuen zu verwendenden SSH-Schlüssel hochladen, bevor Sie die Instanz erstellen können. Mithilfe von SSH-Schlüsseln identifizieren Server einen Benutzer oder eine Instanz mittels Public-Key-Verschlüsselung (Verschlüsselung mit öffentlichem Schlüssel). SSH-Schlüssel bestehen aus einer alphanumerischen Zeichenkombination und sind für die Instanz, der sie zugeordnet sind, eindeutig. Mit der {{site.data.keyword.cloud_notm}}-Konsole können Sie SSH-Schlüssel hinzufügen, bearbeiten oder löschen.
{:shortdesc}

SSH-Schlüssel ermöglichen aus entsprechenden Clients für jeden öffentlichen Schlüssel, der in der Instanz implementiert ist, den Zugriff auf eine Instanz ohne die Verwendung eines Kennworts. Indem Sie einen SSH-Schlüssel zu einer Instanz hinzufügen, was Sie während der Bereitstellung vornehmen können, kann mit dem entsprechenden Schlüssel anstelle eines Kennworts auf die Instanz zugegriffen werden. SSH-Schlüssel können zu einer Instanz nur bei ihrer erstmaligen Erstellung hinzugefügt werden. Nachdem eine Linux-Instanz erstellt wurde, können Sie die Schlüssel direkt im Verzeichnis `~/.ssh/` der Instanz bearbeiten.

Das Anmelden bei Ihrer Instanz mit einem Kennwort wird nicht unterstützt. Falls Sie eine Windows-Instanz verwenden, wird Ihr Kennwort mithilfe des SSH-Schlüssels entschlüsselt. Weitere Informationen finden Sie unter [Verbindung zu Ihrer Windows-Instanz herstellen](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance).
{:note}

## Position des SSH-Schlüssels ermitteln oder SSH-Schlüssel generieren
{: #locating-or-generating-your-ssh-key}

Ihr SSH-Schlüssel muss verfügbar sein. Führen Sie einen der folgenden Schritte aus, um die Position des SSH-Schlüssels zu ermitteln oder einen SSH-Schlüssel zu generieren.

 * Position eines SSH-Schlüssels ermitteln: Suchen Sie unter einem Verzeichnis `.ssh` Ihres Ausgangsverzeichnisses nach einer Datei namens `id_rsa.pub` (z. B. `/Users/<USERNAME>/.ssh/id_rsa.pub`). Die Datei beginnt mit `ssh-rsa` und endet mit Ihrer E-Mail-Adresse.

* SSH-Schlüssel generieren: Wenn Sie keinen öffentlichen SSH-Schlüssel besitzen oder das Kennwort eines vorhandenen Schlüssels vergessen haben, generieren Sie einen neuen Schlüssel, indem Sie den Befehl `ssh-keygen` ausführen und die Eingabeaufforderungen befolgen. Sie können z. B. einen SSH-Schlüssel auf Ihrem Linux-Server generieren, indem Sie den Befehl `ssh-keygen -t rsa -C "benutzer-id"` ausführen. Dieser Befehl generiert zwei Dateien. Der generierte öffentliche Schlüssel befindet sich in der Datei `<your key>.pub`.

  Wenn Sie OpenSSH Version 7.8 oder höher verwenden und den SSH-Schlüssel für den Zugriff auf eine Windows-Instanz verwenden wollen, müssen Sie den Schlüssel mit dem folgenden Befehl im PEM-Format generieren: `$ssh-keygen -m PEM -t rsa -f "benutzer-id"`
  {:important}

Weitere Informationen zum Erstellen, Bearbeiten oder Löschen von SSH-Schlüsseln enthält der Abschnitt [SSH-Schlüssel verwalten](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
