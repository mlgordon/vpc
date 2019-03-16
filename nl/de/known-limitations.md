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

# Bekannte Einschränkungen
{: #known-limitations}

Dieses Dokument enthält kurze Beschreibungen zu bekannten Programmfehlern im aktuellen Release, Beschreibungen der nicht unterstützten Funktionen und APIs sowie Hinweise dazu, welche Funktionen derzeitig ausschließlich als Betaservices unterstützt werden. Bekannte Einschränkungen können sich ändern, wenn Funktionalität zu {{site.data.keyword.cloud}} Virtual Private Cloud hinzugefügt wird. Es empfiehlt sich daher, dieses Dokument von Zeit zu Zeit zu überprüfen. 

## Bekannte Programmfehler

* Wenn Sie ein Teilnetz umbenennen, kann es aufgrund des Cache-Timings bis zu einer Stunde dauern, bis der neue Name Ihres Teilnetzes auf der Seite mit den Serverdetails angezeigt wird. (#758)

## Zusammenfassung der nicht unterstützten Funktionen

* Direct Link-Zugriff auf Virtual Private Cloud wird ausschließlich über den [**klassischen Zugriff**](/docs/infrastructure/vpc/classic-access.html) unterstützt.
* Eine Untergruppe der privaten Serviceendpunkte steht für Virtual Private Cloud zur Verfügung; es sind nicht alle Endpunkte verfügbar. 
* Das Speichern und Wiederherstellen von Images wird nicht unterstützt.

## Nicht unterstützte APIs

Informationen darüber, was unterstützt wird, finden Sie in der [API-Spezifikation](https://{DomainName}/apidocs/rias).

Die folgenden APIs werden in diesem Release nicht unterstützt.

| Komponente | Funktionen | Kommentare |
|------|------|--------|
| **Datenverarbeitung:** |   |   |
| Images | Erstellen/Löschen wird nicht unterstützt | Ubuntu 16.04, CentOS 7.X, Windows 08, Debian|
| Netzschnittstellen | Abrufen (kein Erstellen, Löschen, Aktualisieren) | |
| Datenträgerschnittstellen | Nicht unterstützt |   |
| Portgeschwindigkeit | | Nur 100 und 1000 |
| **Speicher:** |   |   |
| Datenträger | Nicht unterstützt |   |
| Momentaufnahmen | Nicht unterstützt |  |

## Noch nicht unterstützte Funktionen und Anwendungsfälle

In diesem Abschnitt finden Sie eine detaillierte Liste der nicht unterstützten Funktionen und Anwendungsfälle. 

* Eine VPC kann kein Peer anderer VPCs sein.
* Vorhandene IBM Cloud-VSIs oder Bare-Metal-Server können nicht zu einer VPC migriert werden.
* Angepasste Routen können nicht zu einer VPC hinzugefügt werden. Alle Teilnetze in einer VPC können standardmäßig miteinander kommunizieren.
* IBM Cloud VPC unterstützt keine Multicast- oder Broadcast-Domänen.
* IBM Cloud VPC bietet keine End-to-End-Verschlüsselung an. 
* Nachfolgend sind einige zentrale IBM Cloud-Services aufgeführt, die von der VPC-Instanz aus genutzt werden können. Auf andere Services kann nicht zugegriffen werden. 
  * NTP
  * Protokollierung
  * DNS-Resolver
* Ein Teilnetz kann sich nicht in mehreren Zonen befinden.
* Ein Teilnetz kann nicht von einer Zone in eine andere verschoben werden.
* Die Größe der Teilnetze kann nach ihrer Erstellung nicht geändert werden.
* Bare-Metal-Server können nicht in einer VPC bereitgestellt werden.
* Klassische IBM Cloud-Ressourcen können sich nicht in demselben Teilnetz in einer VPC befinden. Die Konnektivität zwischen klassischen Ressourcen und einer VPC in Ihrem Konto ist mit dem [**klassischen Zugriff**](/docs/infrastructure/vpc/classic-access.html) möglich.
* IPv6 wird nicht unterstützt.
* Sie können Ihre eigene öffentliche IP nicht als variable IP-Adresse verwenden. Der Pool der variablen IP-Adressen wird von IBM bereitgestellt.
* Eine variable IP-Adresse ist an eine Zone gebunden. Beispielsweise kann eine variable IP-Adresse, die aus einem Pool in Zone 1 reserviert ist, nicht einer VSI in Zone 2 in derselben VPC zugeordnet werden.
* Private IP-Adressen können nicht zwischen VSIs verschoben werden.
* Netzschnittstellen können nicht zwischen VSIs verschoben werden.
* Sie können die spezifische IP-Adresse der VSI nicht angeben. Sie können nur den IP-Bereich für das Teilnetz angeben. Sobald Sie eine VSI an ein Teilnetz angeschlossen haben, ordnet das System eine private IP aus diesem Teilnetz zu.
* IBM Cloud VPC verfügt über eigene Network as a Service-Tools wie LBaaS, ACLs und Sicherheitsgruppen. Sie können keine eigenen Netzgeräte (z. B. ein Vyatta Gateway oder eine andere Lastausgleichsfunktion) verwenden, um alle Ressourcen in der VPC zu steuern. In ähnlicher Form können Sie auch nicht Ihre eigenen Service für Lastausgleichsfunktionen oder Sicherheitsgruppen in der klassischen IBM Cloud-Infrastruktur verwenden, um Ressourcen in der IBM Cloud VPC-Instanz zu steuern.
* Das öffentliche Gateway lässt nicht zu, dass der Datenverkehr vom Internet zu einer VSI in IBM Cloud VPC initiiert wird. Zu diesem Zweck muss eine variable IP-Adresse verwendet werden.
* ACL ist statusunabhängig, sodass der zurückfließende Datenverkehr explizit in ACL-Regeln zugelassen werden muss.

## Als Betaservices verfügbare Komponenten oder Funktionen

* **VPN für IBM Cloud VPC** ist nur als Betaservice verfügbar.
* **LBaaS für IBM Cloud VPC** ist nur als Betaservice verfügbar.
