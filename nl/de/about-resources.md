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
{:DomainName: data-hd-keyref="DomainName"}

# Informationen zu VPC-Infrastrukturressourcen
{: #about-vpc-infrastructure-resources}

Der Begriff _Ressourcen_ bezieht sich auf die einzelnen Komponenten einer {{site.data.keyword.cloud}} Virtual Private Cloud-Bereitstellung. Jede VPC-Instanz kann Ressourcen der folgenden Typen enthalten, die nach Bedarf gruppiert werden können:

* **VPC**
* **Instanz**
* **Schlüssel**
* **Image**
* **Teilnetz**
* **Datenträger**
* **ACL**
* **Sicherheitsgruppe**
* **Variable IP-Adresse**
* **vNIC**
* **Gateway**
* **Lastausgleichsfunktion**
* **VPN**

Sie können sich die meisten dieser Typen von Ressourcen als "untergeordnete Elemente" ihrer jeweiligen VPC-Instanz vorstellen, da sie viele ihrer Berechtigungsrichtlinien, die ihre Verwendung steuern, von ihrer "übergeordneten" VPC-Instanz übernehmen (wie in der Übersichtstabelle im nächsten Abschnitt dargestellt).

Als Ausnahme verwaltet die Ressourcentypen `Lastausgleichsfunktion` und `VPN` ihre eigenen Berechtigungsrichtlinien. Weitere Informationen zur Ressourcenberechtigung für Lastausgleichs- und VPN-Ressourcen finden Sie weiter unten in diesem Dokument.
{: note}

## Ressourcenrichtlinien

Im Allgemeinen wird der Zugriff auf Ressourcen in einer VPC-Instanz durch _Richtlinien_ gesteuert. Wenn Sie den Zugriff auf Ressourcen für die VPC-Instanz anpassen möchten, können Sie angepasste Richtlinien erstellen. Eine Ressourcenrichtlinie kann ausgerichtet sein auf:

* alle Ressourcen
* alle Ressourcen eines Typs
* alle Ressourcen in einer Gruppe
* eine einzelne Ressource

## Ressourcen und Ressourcengruppen
Eine _Ressourcengruppe_ ist eine Gruppe von Ressourcen, z. B. eine ganze VPC oder ein einzelnes Teilnetz und die zugehörige Zugriffssteuerungsliste (ACL, Access Control List), die für Verwendungs- und Berechtigungszwecke entsprechend zugeordnet werden. Eine Ressourcengruppe kann als eine Zusammenstellung von Infrastrukturen angesehen werden, die von einem Projekt, einer Abteilung oder einem Team verwendet werden können.

Große Unternehmen können eine VPC in Ressourcengruppen aufteilen. Für kleinere Unternehmen wäre dies möglicherweise nicht nötig, da alle Teams die gesamte VPC nutzen würden. Wenn Sie mit _OpenStack_ vertraut sind, ist eine Ressourcengruppe vom Konzept her ähnlich wie ein _Projekt_ in _OpenStack Keystone_.

Die Zuordnung einer Ressource zu einer Ressourcengruppe kann NUR beim Erstellen der VPC erfolgen. Ressourcen können keine Ressourcengruppen ändern, sobald sie erstellt wurden.
{: .note}

Ressourcengruppen sind in erster Linie für große Organisationen konzipiert. Bei den meisten Unternehmen und Teams befindet sich der Ressourcen-Breakout an einer VPC-Grenze. Diese allgemeine Faustregel kann sich ändern, wenn es möglich ist, einzelne VSI-Instanzen (Instanzen) einer Ressourcengruppe und einzelne Benutzer einer VSI-Ressource (Instanz) zuzuordnen.

Wenn Sie die IBM Cloud VPC-Instanz einrichten und Ressourcengruppen verwenden möchten, ist es sinnvoll, vorab einen Plan für die Zuordnung der Ressourcen und der Benutzer in Ihrem Unternehmen zu jeder Ressourcengruppe zu haben.
{: tip}

## Spezifikationen für VPC

Derzeit ordnet VPC Rollen und Zugriff nur an der VPC-Grenze für eine oder alle Ressourcen in dieser bestimmten VPC zu. Beispielsweise können Sie keinen Zugriff für einzelne Teilnetze in dieser VPC zuordnen. Stattdessen werden die Berechtigungen für alle Typen von Ressourcen für diese VPC (Teilnetze, Instanzen, variable IP-Adressen, Sicherheitsgruppen, ACLs usw.) vom übergeordneten Element der VPC dieser Ressource übernommen. Bestimmte Ressourcen, wie z. B. **Lastausgleichsfunktionen** und **VPN**, verwalten Berechtigungen separat von der VPC, der sie zugeordnet sind.

### VPC-Ressourcenberechtigung nach Ressourcentyp

In der Tabelle ist aufgeführt, wie VPC-Ressourcen standardmäßig ihre Berechtigungen erhalten.

| Ressourcentyp | Erhalt der Standardberechtigung |
|-----------|------------|
| VPC | Berechtigungsprüfung beim Erstellen |
| Lastausgleichsfunktion | Berechtigungsprüfung beim Erstellen |
| VPN | Berechtigungsprüfung beim Erstellen |
| Teilnetz | Übergeordnete VPC |
| Öffentliches Gateway | Übergeordnete VPC |
| Instanz | Übergeordnete VPC |
| Sicherheitsgruppe | Übergeordnete VPC |
| Schlüssel | Konto |
| Image | Konto |
| Variable IP-Adresse | Konto |
| ACL | Konto |
| Datenträger | n.z. |

Variable IP-Adressen und ACLs können mit Scoping auf Kontenebene erstellt werden, wenn sie nicht zugeordnet sind. Sobald jedoch eine variable IP-Adresse einer Instanz oder eine ACL einem Teilnetz zugeordnet wird, unterliegen diese Ressourcen dem Berechtigungsbereich der VPC.
{: note}

### VPC-Abdeckung von Rollen und berechtigten Aktionen für Ressourcen

In einem Szenario mit 2 VPCs sind hier einige Beispiele dafür, was passiert, wenn ein Benutzer mit bestimmten Rollen versucht, bestimmte Aktionen auszuführen:

* Benutzer des Typs _Administrator_ mit **Administrator**-Berechtigungen für alle Ressourcen
  * Erstellt `vpc1`: OK

* Benutzer des Typs _Editor_ mit **Editor**-Berechtigungen für alle Ressourcen
  * Erstellt `vpc2`: OK
  * Aktualisiert `vpc2`: OK
  * Löscht `vpc2`: OK

* Benutzer des Typs _Operator_ mit **Operator**-Berechtigungen für alle Ressourcen
  * Erstellt `vpc`: verweigert
  * Aktualisiert `vpc1`: verweigert
  * Löscht `vpc1`: verweigert

* Benutzer des Typs _Anzeigeberechtigter_ mit **Anzeigeberechtiger**-Berechtigungen für alle Ressourcen
  * Listet VPCs auf: sieht [vpc1]
  * Liest `vpc1`: OK

* Benutzer des Typs _keine Rolle_ ohne Richtlinien
  * Listet VPCs auf: sieht []
  * Liest `vpc1`: verweigert

### Übersichtstabelle für VPC-Abdeckung

Für jede Richtlinie, die den Zugriff nach Rolle (Administrator, Editor, Operator, Anzeigeberechtigter) erteilt, werden die folgenden Aktionen ausgeführt (X=verweigert, o=OK):

 Rolle:      | keine | Anzeigeberechtigter | Operator | Editor | Administrator
-----------:|------|--------|-------|--------|-------
Erstellen   | X    | X      | X     | o      | o
Auflisten   | X    | o      | X     | o      | o
Lesen       | X    | o      | X     | o      | o
Aktual.     | X    | X      | X     | o      | o
Löschen     | X    | X      | X     | o      | o


## Ressourcenberechtigung 'VPN für VPC'

Die Ressourcenberechtigung **VPN für VPC** wird zwar getrennt von anderen Typen der VPC-Ressourcenautorisierung eingerichtet, jedoch in ähnlicher Weise.

Richtlinien in VPN für VPC steuern den Zugriff auf VPN-Ressourcen, insbesondere VPN-Gateways. Wenn Sie Zugriff auf ein VPN-Gateway haben, bedeutet dies **nicht** automatisch, dass Sie auch Zugriff auf untergeordnete Ressourcen, wie VPN-Verbindungen oder lokale oder gleichgeordnete CIDRs, haben. IKE- und IPSec-Richtlinien sind unabhängig vom VPN-Gateway und werden nicht durch die Richtlinie des Gateways reguliert. Eine Ressourcenrichtlinie in VPN kann ausgerichtet sein auf:

* alle VPN-Gateways
* ein einzelnes VPN-Gateway

Ein VPN-Gateway kann auch Teil einer Ressourcengruppe sein. Wenn Sie Zugriff auf eine bestimmte Ressourcengruppe haben, haben Sie Zugriff auf die VPN-Gateways, die in dieser Gruppe enthalten sind.

Die VPN-Nutzung wird auch separat in Rechnung gestellt.
{: note}

### 'VPN für VPC'-Abdeckung von Rollen und berechtigten Aktionen für Ressourcen

Es werden dieselben Benutzerrollen wie bei der VPC-Ressourcenberechtigung unterstützt, jedoch sind für die einzelnen Rolle andere Aktionen aktiviert.

Im Folgenden finden Sie einige Beispiele dafür, was passiert, wenn Benutzer mit bestimmten Rollen versuchen, bestimmte VPN-bezogene Aktionen auszuführen:

* Benutzer des Typs _Administrator_ mit **Administrator**-Berechtigungen für alle Ressourcen
  * Erstellt, aktualisiert, löscht, liest, listet VPN-Gateways auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet VPN-Verbindungen auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet VPN-Verbindungen & lokale CIDRs auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet IKE-Richtlinien auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet IPSec-Richtlinien auf: OK

* Benutzer des Typs _Editor_ mit **Editor**-Berechtigungen für alle Ressourcen
  * Identisch mit denen des Administrators

* Benutzer des Typs _Operator_, mit **Operator**-Berechtigungen für alle Ressourcen
  * Erstellt, aktualisiert und löscht VPN-Gateways: verweigert
  * Erstellt, aktualisiert und löscht VPN-Verbindungen: verweigert
  * Erstellt, aktualisiert und löscht VPN-Verbindungspeer & lokale CIDRs: verweigert
  * Erstellt, aktualisiert und löscht IKE-Richtlinien: verweigert
  * Erstellt, aktualisiert und löscht IPSec-Richtlinien: verweigert
  * Liest, listet VPN-Gateways auf: OK - sieht tatsächliche Daten
  * Liest, listet VPN-Verbindungen auf: OK - sieht tatsächliche Daten
  * Liest, listet VPN-Verbindungspeer & lokale CIDRs auf: OK - sieht tatsächliche Daten
  * Liest, listet IKE-Richtlinien auf: OK - sieht tatsächliche Daten
  * Liest, listet IPSec-Richtlinien auf: OK - sieht tatsächliche Daten

* Benutzer des Typs _Anzeigeberechtigter_ mit **Anzeigeberechtiger**-Berechtigungen für alle Ressourcen
  * Identisch mit denen des Operators

* Benutzer des Typs _keine Rolle_ ohne Richtlinien
  * Liest, listet VPN-Gateways auf: verweigert - sieht leere Daten
  * Liest, listet VPN-Verbindungen auf: verweigert - sieht leere Daten
  * Liest, listet VPN-Verbindungspeer & lokale CIDRs auf: verweigert - sieht leere Daten
  * Liest, listet IKE-Richtlinien auf: verweigert - sieht leere Daten
  * Liest, listet IPSec-Richtlinien auf: verweigert - sieht leere Daten

### Übersichtstabelle für 'VPN für VPC'-Abdeckung

Die Aktionsrollenzuordnung in 'VPN für VPC' kann durch die folgende Tabelle dargestellt werden (X=verweigert, o=OK):

 Rolle:     | keine | Anzeigeberechtigter | Operator | Editor | Administrator
-----------:|------|--------|-------|--------|-------
Erstellen   | X    | X      | X     | o      | o
Auflisten   | X    | o      | o     | o      | o
Lesen       | X    | o      | o     | o      | o
Aktual.     | X    | X      | X     | o      | o
Löschen     | X    | X      | X     | o      | o

## Ressourcenberechtigung 'Lastausgleichsfunktion für VPC'

Die Ressourcenberechtigung **Lastausgleichsfunktion für VPC** wird separat von der anderen Ressourcenberechtigung in Ihrer VPC eingerichtet, jedoch in ähnlicher Weise.

Die Nutzung der Lastausgleichsfunktion wird auch separat in Rechnung gestellt.
{: note}

### Abdeckung im Rahmen der Lastausgleichsfunktion von Rollen und berechtigten Aktionen für Ressourcen

Im Folgenden finden Sie einige Beispiele dafür, was passiert, wenn Benutzer mit bestimmten Rollen versuchen, bestimmte Aktionen auszuführen, die sich auf die VPC-Lastausgleichsfunktion beziehen:

* Benutzer des Typs _Administrator_ mit **Administrator**-Berechtigungen für alle Ressourcen
  * Erstellt, aktualisiert, löscht, liest, listet Lastausgleichsfunktionen auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet Listener auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet Pools auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet Mitglieder auf: OK
  * Erstellt, aktualisiert, löscht, liest, listet Statistiken für die Lastausgleichsfunktion auf: OK

* Benutzer des Typs _Editor_ mit **Editor**-Berechtigungen für alle Ressourcen
  * Identisch mit denen des Administrators

* Benutzer des Typs _Operator_ mit **Operator**-Berechtigungen für alle Ressourcen
  * Erstellt, aktualisiert, löscht, liest, listet Lastausgleichsfunktionen auf: verweigert
  * Erstellt, aktualisiert, löscht, liest, listet Listener auf: verweigert
  * Erstellt, aktualisiert, löscht, liest, listet Pools auf: verweigert
  * Erstellt, aktualisiert, löscht, liest, listet Mitglieder auf: verweigert
  * Erstellt, aktualisiert, löscht, liest, listet Statistiken für die Lastausgleichsfunktion auf: verweigert

* Benutzer des Typs _Anzeigeberechtigter_ mit **Anzeigeberechtiger**-Berechtigungen für alle Ressourcen
  * Liest, listet Lastausgleichsfunktionen auf: OK
  * Liest, listet Listener auf: OK
  * Liest, listet Pools auf: OK
  * Liest, listet Mitglieder auf: OK
  * Liest Statistiken für die Lastausgleichsfunktion: OK

* Benutzer des Typs _keine Rolle_ ohne Richtlinien
  * Liest, listet Lastausgleichsfunktionen auf: verweigert - Liste zeigt leere Daten an
  * Liest, listet Listener auf: verweigert
  * Liest, listet Pools auf: verweigert
  * Liest, listet Mitglieder auf: verweigert
  * Liest Statistiken für die Lastausgleichsfunktion: verweigert

### Übersichtstabelle für die Abdeckung der Lastausgleichsfunktion

Die Aktionsrollenzuordnung in 'Lastausgleichsfunktion für VPC' kann durch die folgende Tabelle dargestellt werden (X=verweigert, o=OK):

Rolle:     | keine | Anzeigeberechtigter | Operator | Editor | Administrator
-----------:|------|--------|-------|--------|-------
Erstellen   | X    | X      | X     | o      | o
Auflisten   | X    | o      | X     | o      | o
Lesen       | X    | o      | X     | o      | o
Aktual.     | X    | X      | X     | o      | o
Löschen     | X    | X      | X     | o      | o
