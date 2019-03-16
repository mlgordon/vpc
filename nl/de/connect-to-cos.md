---
copyright:
  years: 2018-2019
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

# Verbindung zu IBM Cloud Object Storage von einer VPC herstellen
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

In diesem Dokument erfahren Sie, wie Sie eine Verbindung zu IBM® Cloud Object Storage von Ihrer VPC herstellen.

## Was ist IBM Cloud Object Storage (COS)?

IBM Cloud Object Storage (COS) ist eine webbasierte Plattform zum Speichern unstrukturierter Daten. Diese Plattform bietet Zuverlässigkeit, Sicherheit, Verfügbarkeit und Disaster-Recovery ohne manuelle Replikation.
In IBM Cloud Object Storage gespeicherte Daten werden verschlüsselt und auf mehrere geografische Standorte verteilt. Die Daten sind über eine Implementierung der S3-API zugänglich. Dieser Service nutzt Technologien für die verteilte Speicherung, die vom IBM Cloud Object Storage-Service bereitgestellt werden.

IBM COS ist in drei Konfigurationen verfügbar: **Überregional**, **Regional** und **Single-Site** (einzelner Standort).
 * Der **überregionale** Service bietet größere Dauerhaftigkeit und höhere Verfügbarkeit als die Verwendung einer einzigen Region, jedoch auf Kosten einer etwas höheren Latenz.
 * Der **regionale** Service bietet die umgekehrte Funktionalität, d. h. Objekte werden auf mehrere Verfügbarkeitszonen innerhalb einer Region verteilt. Wenn eine Region oder Verfügbarkeitszone nicht zugänglich ist, kann der Objektspeicher reibungslos weiter genutzt werden. Alle fehlenden Änderungen werden angewendet, sobald das nicht zugängliche Rechenzentrum wieder online ist.
 * Der Service für einen **einzelnen Standort** bietet kosteneffizienten Zugriff auf Cloud Object Storage in einem ausgewählten Rechenzentrum.
 
### Direkte COS-Endpunkte für die Verwendung mit VPC

Endpunkte sind URLs, die von Anwendungen verwendet werden, um COS-Befehle abzusetzen und Daten mit COS auszutauschen. Jeder Endpunkt verwendet die gleiche Anwendungsprogrammierschnittstelle (API) für die Interaktion mit COS. Server, die in IBM Cloud bereitgestellt werden, verwenden API-Endpunkte für Services (einschließlich COS). Direkte Endpunkte stellen IBM Cloud-Servern von Kunden sehr schnelle Direktverbindungen zu Services ohne Zusatzkosten für die Bandbreite bereit.
 
## Vorgehensweise zum Herstellen einer Verbindung zu IBM Cloud Object Storage (COS) über eine VPC
 1. Stellen Sie COS über den [Katalog ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window} bereit.
 2. Erstellen Sie ein COS-Bucket in einer der Regionen, die im folgenden Abschnitt aufgelistet sind.
 3. Verwenden Sie den direkten Endpunkt für VPC zum Erstellen einer Schnittstelle mit dem COS-Bucket.
 
## Regionsübergreifende Endpunkte in den USA
 
| **Regionsübergreifend USA** | **Direkter Endpunkt für VPC** |
|------------|-------------------------------|
| Regionsübergreifend USA | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| Zugriffspunkt Dallas | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| Zugriffspunkt San Jose | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| Zugriffspunkt Washington, DC | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## Regionale Endpunkte in den USA
 
| **Region** | **Direkter Endpunkt für VPC** |
|------------|-------------------------------|
| USA (Süden) | `s3.direct.us-south.cloud-object-storage.appdomain.cloud`|
| USA (Osten) | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`|

 ## Endpunkte in einzelnen Rechenzentren
 
| **Region** | **Direkter Endpunkt für VPC** |
|------------|-------------------------------|
| Toronto, Kanada | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| Montreal, Kanada | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
