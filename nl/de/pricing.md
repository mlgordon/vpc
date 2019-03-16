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


# Preisstruktur für VPC
{: #pricing-for-vpc}

In der Tabelle sind die Preise für die Übertragung von Internetdaten mit {{site.data.keyword.cloud}} Virtual Private Cloud zusammengefasst. Beachten Sie, dass es keine Gebühren für den Datenverkehr zwischen VPC- und klassischen IBM Cloud-Services gibt. Auch für PayGo-Services sind die Serviceebenen an Ihr Konto und nicht an eine bestimmte VPC-Instanz gebunden. Die Beträge werden in US-Dollar angezeigt.

Für [virtuelle Serverinstanzen](/docs/infrastructure/vpc?topic=vpc-pricing-for-virtual-servers-for-vpc), die in Ihrer IBM Cloud VPC-Instanz verwendet werden, gilt eine separate Preisstruktur.

## Freibeträge für die Datenübertragung über das Internet

| Datenübertragung |  Kosten für alle IBM Cloud-VPC-Kunden |
|---------------|------------------|
| Innerhalb der Zone | Kostenlos |
| Zwischen Zonen in derselben Region | Kostenlos |
| Verwendung des öffentlichen Gateways | Kostenlos (Gebühren nur für die vom PWG verwendete variable IP-Adresse) |

## Preisstruktur für variable IP-Adressen

Eine variable IP-Adresse wird mit einem Gebührensatz von 1 USD pro Monat ab dem Zeitpunkt der Reservierung berechnet. Die Gebühr wird auch dann erhoben, wenn die variable IP-Adresse nicht einer VSI zugeordnet ist oder nicht verwendet wird. Die monatliche Gebühr von 1 USD wird auch dann berechnet, wenn die variable IP-Adresse für nur ein paar Tage reserviert ist.


## Grundlegende Preisstruktur für PayGo für die Datenübertragung über das Internet

| Datenübertragung | Datenvolumen | PayGo-Preisstruktur |
|-----------|-----------|------------------|
| Ausgehend zum Internet |  0 bis 5 GB | Kostenlos |
|  | 6 bis 10.000 GB | 0,087 USD pro GB |
|  | 10.001 bis 50.000 GB | 0,083 USD pro GB |
|  | 50.001 bis 150.000 GB | 0,07 USD pro GB |
|  | 150.001 GB und mehr | 0,05 USD pro GB |


Wenn Sie eine neue VPC erstellen, kann es bis zu einer Stunde dauern, bis die Gebühren für die Anfangsabrechnung in der Konsolenbenutzerschnittstelle oder in der API angezeigt werden.
{: tip}

Wenn Sie ein öffentliches Gateway oder eine variable IP-Adresse verwenden, können einige geringe Gebühren für den abgehenden Datenverkehr ins Internet angezeigt werden, auch wenn Sie keinen abgehenden Datenverkehr zu diesem Zeitpunkt gesendet haben. Diese Gebühren fallen für den ARP-Datenverkehr an, der für das Betreiben Ihres Kontos notwendig ist.
{: important}


