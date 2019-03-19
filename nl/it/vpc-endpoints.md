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

# Endpoint di servizio disponibili per IBM Cloud VPC
{: #service-endpoints-available-for-ibm-cloud-vpc}

Quando sei pronto per eseguire carichi di lavoro, puoi raggiungere alcuni servizi dell'infrastruttura IBM Cloud da una VSI all'interno di {{site.data.keyword.cloud}} VPC utilizzando determinati endpoint ADN. Diversi tipi di servizi sono disponibili tramite endpoint privati, che sono raggiungibili dai clienti VPC. Utilizzando questi endpoint interni, puoi evitare i costi relativi alla larghezza di banda che potrebbero essere addebitati se raggiungi gli endpoint dall'Internet pubblica.

I servizi che puoi raggiungere includono:

* Resolver DNS
* Mirror
* Cloud Object Storage
* NTP

## Endpoint di esempio per IBM Cloud Object Storage

Ad esempio, per raggiungere un endpoint privato per un servizio di archiviazione oggetti sulla rete privata IBM Cloud, sostituisci la parte "dominio" dell'URL con `objectstorage.adn.networklayer.com`.

## Endpoint per DNS e mirror

DNS e mirror utilizzano ovunque lo stesso spazio 161.26/16. Questi endpoint IP specifici sono disponibili in ogni sito abilitato a VPC:

* `mirrors.adn.networklayer.com` (161.26.0.6)
* Server DNS (161.26.0.10 e 161.26.0.11)
