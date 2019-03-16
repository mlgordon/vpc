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

# Für IBM Cloud VPC verfügbare Serviceendpunkte
{: #service-endpoints-available-for-ibm-cloud-vpc}

Wenn Sie bereit sind, Workloads auszuführen, können Sie einige IBM Cloud-Infrastrukturservices von einer VSI in Ihrer {{site.data.keyword.cloud}} VPC-Instanz aus erreichen, indem Sie bestimmte ADN-Endpunkte verwenden. Verschiedene Servicetypen stehen über private Endpunkte zur Verfügung, die für VPC-Kunden erreichbar sind. Durch die Verwendung solcher internen Endpunkte können Sie die Bandbreitengebühren vermeiden, die anfallen, wenn Sie aus dem öffentlichen Internet auf die Endpunkte zugegriffen haben.

Zu diesen erreichbaren Services zählen unter anderem:

* DNS-Resolver
* Spiegel
* Cloudobjektspeicher (COS, Cloud Object Storage)
* NTP

## Beispielendpunkt für IBM Cloud Object Storage

Wenn Sie z. B. einen privaten Endpunkt für einen Objektspeicherservice im privaten IBM Cloud-Netz erreichen möchten, ersetzen Sie den Abschnitt "Domäne" der URL durch `objectstorage.adn.networklayer.com`.

## Endpunkte für DNS und Spiegel

DNS und Spiegel verwenden überall den gleichen 161.26/16-Bereich. Diese spezifischen IP-Endpunkte sind auf jeder VPC-fähigen Site verfügbar:

* `mirrors.adn.networklayer.com` (161.26.0.6)
* DNS-Server (161.26.0.10 und 161.26.0.11)
