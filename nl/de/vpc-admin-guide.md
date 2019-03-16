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
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Rollenbasierten Zugriff auf VPC-Ressourcen zuordnen
{: #assigning-role-based-access-to-vpc-resources}

Kontoadministratoren können _Berechtigungsrichtlinien_ verwenden, die basierend auf der _Rolle_ eines Benutzers den Zugriff auf _Ressourcen_ steuern. Richtlinien können auch angewendet werden für:

(1) die Autorisierung einer Gruppe von Benutzern, die als _Zugriffsgruppe_ bezeichnet wird,

(2) die zugeordneten Merkmale einer einzelnen _Ressource_ oder

(3) eine Gruppe von Ressourcen, die als _Ressourcengruppe_ bezeichnet wird.

Die Berechtigungen für Ressourcen und die Berechtigungen für Benutzer können unabhängig voneinander zugeordnet werden.

Weitere Informationen zum Erstellen von Benutzern, Benutzerzugriffsgruppen, Ressourcengruppen und Richtlinien finden Sie unter [Informationen zu Ressourcen](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources).

## IAM-basierte Zugriffssteuerung

Im Allgemeinen sind die Verfahren für Berechtigungen und das Ressourcenmanagement für {{site.data.keyword.cloud}} Virtual Private Cloud auf die IBM Cloud-IAM-Services (IAM, Identity and Access Management) abgestimmt. Weitere Informationen zu IAM, Ressourcengruppen und Zugriffsgruppen im Allgemeinen finden Sie in den folgenden IBM Cloud-Dokumenten:

* [IBM Cloud-IAM](https://{DomainName}/docs/iam/quickstart.html#getstarted)
* [Ressourcengruppen](https://{DomainName}/docs/overview/resource-groups.html#whatis)
* [Zugriffsgruppen](https://{DomainName}/docs/overview/manageaccess.html#cloudaccess)

Bestimmte Funktionen des IBM Cloud-IAM-Service wurden für die Verwendung in IBM Cloud VPC angepasst. Im Abschnitt [Informationen zu Ressourcen](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources) werden die IAM-Berechtigungsrichtlinien und ihre Anwendungsweise in VPC erläutert.

Sie können also IAM-basierte Berechtigungen zuordnen basierend auf:

* einzelnen Benutzern
* Zugriffsgruppen (Gruppen von Benutzern)
* bestimmten Typen von Ressourcen
* Ressourcengruppen

## Benutzerberechtigungen zuordnen

Für Benutzer wird der Zugriff gesteuert, indem systemdefinierte IAM-Rollen zugeordnet werden:

* Administrator
* Editor
* Operator
* Anzeigeberechtigter

Nachfolgend finden Sie eine Tabelle, die die Analogie zwischen den einzelnen Benutzerrollen und der Art der entsprechenden Kontrolle für VPCs zeigt:

| Rollename | Zulässige Art des Zugriffs |
|-----------|-------------------------|
| Anzeigeberechtigter | VPC anzeigen, VPCs auflisten  |
| Editor | VPC anzeigen, VPCs auflisten, VPCs erstellen, VPCs löschen, VPCs aktualisieren |
| Operator | VPC anzeigen, VPCs auflisten  |
| Administrator |VPC anzeigen, VPCs auflisten, VPCs erstellen, VPCs löschen, VPCs aktualisieren, Richtlinien anderen Benutzern zuordnen |


## Nächste Schritte

Im Abschnitt [Benutzerberechtigungen für VPC-Ressourcen verwalten](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) finden Sie schrittweise Anweisungen zum Erteilen rollenbasierter Berechtigungen für Benutzer für bestimmte Tasks.
