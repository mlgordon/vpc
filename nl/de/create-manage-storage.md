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
{:note: .note}
{:download: .download}

# Speicher in VPC erstellen und verwalten
{: #creating-and-managing-storage-in-vpc}

Derzeit ermöglicht die {{site.data.keyword.cloud}} Virtual Private Cloud nur Boot-Speicherdatenträger.

Wenn Sie eine virtuelle Serverinstanz bereitstellen, wird ein 100 GB-Blockspeicherdatenträger als primärer Bootdatenträger erstellt und der Instanz automatisch zugeordnet. Der Bootdatenträger bietet eine 3 IOPS/GB-Leistung und ist nur während der Lebensdauer der VSI vorhanden. 

Wenn Sie die Instanz löschen, wird der Bootdatenträger gelöscht.

## Bewährte Verfahren zum Erstellen und Benennen von VPC-Speicherdatenträgern:

* Stellen Sie sicher, dass Sie ALLE Ihre Datenträger während der Bereitstellung benennen, einschließlich den Bootdatenträger.
* Stellen Sie sicher, dass Sie ALLE Ihrer Datenträgeranhänge zur Anhangszeit benennen.
* Jeder Datenträger muss einen eindeutigen Namen innerhalb einer Region innerhalb eines Kontos haben. 

Sie können den Namen eines Datenträgers erneut verwenden, nachdem dieser Datenträger gelöscht wurde. Es ist jedoch zu beachten, dass die Wiederverwendung eines Datenträgernamens zu Verwechslungen bei der Abrechnung führen kann.{:note}
