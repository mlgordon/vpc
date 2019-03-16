---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Einführung in die Infrastruktur von IBM Cloud Virtual Private Cloud
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

IBM akzeptiert eine begrenzte Anzahl von Kunden, die ab Anfang April 2019 an einem Early Access-Programm für VPC teilnehmen können, wobei die erweiterte Nutzung in den folgenden Monaten freigegeben wird. Wenn Ihre Organisation Zugriff auf IBM Virtual Private Cloud erhalten möchte, füllen Sie bitte dieses [Nominierungsformular](https://cloud.ibm.com/vpc){: new_window} aus. Ein IBM Ansprechpartner wird sich dann bezüglich der nächsten Schritte mit Ihnen in Verbindung setzen.
{: important}

Führen Sie als Einführung in die Infrastruktur von {{site.data.keyword.cloud}} Virtual Private Cloud die folgenden Schritte aus:

1. Erstellen Sie eine Virtual Private Cloud-Instanz (VPC).
2. Erstellen Sie ein oder mehrere Teilnetze in der Virtual Private Cloud-Instanz in einer oder mehreren Zonen.
3. Erstellen Sie ein öffentliches Gateway (PGW) in einem Teilnetz, wenn Ressourcen in Ihrem Teilnetz Zugriff auf das Internet haben sollen (oder umgekehrt).
4. Wählen Sie die Profile der virtuellen Serverinstanzen (VSIs) aus, die Sie ausführen möchten, und instanziieren Sie sie.
5. Reservieren Sie eine variable IP-Adresse und ordnen Sie sie einer virtuellen Serverinstanz zu, wenn Sie sie aus dem Internet erreichen möchten.
5. Stellen Sie Ihren Service oder Ihre Anwendungen auf den virtuellen Serverinstanzen bereit.

## Vorbedingungen

 * **Benutzerberechtigungen**: Stellen Sie sicher, dass Ihr Benutzer über ausreichende Berechtigungen zum Erstellen und Verwalten von Ressourcen in Ihrer VPC verfügt. Eine Liste der erforderlichen Berechtigungen finden Sie im Abschnitt zum [Erteilen der erforderlichen Berechtigungen für VPC-Benutzer](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).

 * **SSH-Schlüssel bereithalten**: Sie verwenden einen SSH-Schlüssel, um eine Verbindung zu den virtuellen Serverinstanzen herzustellen.

   * Suchen Sie nach einer Datei mit dem Namen `id_rsa.pub` in einem `.ssh`-Verzeichnis unter Ihrem Ausgangsverzeichnis, z. B. `/Users/<USERNAME>/.ssh/id_rsa.pub`. Die Datei beginnt mit `ssh-rsa` und endet mit Ihrer E-Mail-Adresse.

   * Oder: SSH-Schlüssel generieren: Wenn Sie keinen öffentlichen SSH-Schlüssel oder das Kennwort eines vorhandenen Schlüssels vergessen haben, generieren Sie einen neuen, indem Sie den Befehl `ssh-keygen` ausführen und die Eingabeaufforderungen befolgen. Sie können z. B. einen SSH-Schlüssel auf Ihrem Linux-Server generieren, indem Sie den Befehl `ssh-keygen -t rsa -C "benutzer-id"` ausführen. Dieser Befehl generiert zwei Dateien. Der generierte öffentliche Schlüssel befindet sich in der Datei `<your key>.pub`.
   
## Benutzerschnittstelle, CLI oder REST-API verwenden

Sie können alle Ihre VPC-Ressourcen über die Benutzerschnittstelle, CLI oder REST-API bereitstellen und verwalten.

Wenn Sie neu bei IBM Cloud Virtual Private Cloud sind, wählen Sie einen der unten aufgeführten Links aus, die Sie von Anfang bis Ende durch den Prozess der Erstellung Ihrer IBM Cloud VPC-Instanz und der entsprechenden Ressourcen führen. Dabei können Sie auswählen, ob Sie von der Benutzerschnittstelle der Konsole, der Befehlszeilenschnittstelle (CLI) oder der RIAS-API (RIAS, Regional Infrastructure API Services) aus starten möchten.

* Für den Zugriff über die Benutzerschnittstelle melden Sie sich an der [IBM Cloud-Konsole ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")]( https://{DomainName}/vpc){: new_window} an. Befolgen Sie die Anweisungen im [UI-Leitfaden](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console), falls Sie Hilfe benötigen sollten.
* Um die Befehlszeilenschnittstelle zu nutzen, verwenden Sie das Plug-in [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) der [IBM Cloud-CLI](https://console.bluemix.net/docs/cli/index.html#overview) und folgen Sie dem [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli)-Beispiel.
* Fortgeschrittene Benutzer können direkt die [REST-APIs](https://{DomainName}/apidocs/rias) aufrufen. Folgen Sie dem Lernprogramm zum [Beispielcode](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis), um die REST-APIs zu nutzen.

## Nächste Schritte
Wenn Sie bereit sind, wechseln Sie direkt zu den ausführlichen Dokumentationen zum **VPC-Netzbetrieb** und zu **VSIs für VPC**:

* [**Netzbetrieb für IBM Virtual Private Cloud**](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**Virtuelle IBM Server für Virtual Private Cloud**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

