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

# Connessione a IBM Cloud Object Storage da un VPC
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

Questo documento spiega come connettersi a IBM® Cloud Object Storage dal tuo Virtual Private Cloud.

## Che cos'è IBM Cloud Object Storage (COS)?

IBM Cloud Object Storage (COS) è una piattaforma su scala web che archivia i dati non strutturati. Fornisce affidabilità, sicurezza, disponibilità e ripristino di emergenza senza replica manuale.
Le informazioni archiviate in IBM Cloud Object Storage vengono crittografate e distribuite in più ubicazioni geografiche. Sono accessibili tramite un'implementazione dell'API S3. Questo servizio utilizza le tecnologie di archiviazione distribuita fornite dal servizio IBM Cloud Object Storage.

IBM COS è disponibile in tre configurazioni: **Cross Region**, **Regional** e **Single-Site**.
 * Il servizio **Cross Region** offre una maggiore durata e disponibilità rispetto all'utilizzo di una singola regione, ma al costo di una latenza leggermente superiore.
 * Il servizio **Regional** fornisce il contrario: distribuisce gli oggetti in più zone di disponibilità all'interno di una singola regione. Se una determinata regione o zona di disponibilità non è accessibile, l'archivio oggetti continua a funzionare correttamente. Tutte le modifiche mancanti vengono applicate quando il data center non accessibile torna online.
 * Il servizio **Single Site** offre accesso a Cloud Object Storage in un data center selezionato.
 
### Endpoint diretti COS da utilizzare con VPC

Gli endpoint sono URL che le applicazioni utilizzano per immettere i comandi COS e scambiare i dati con COS. Ogni endpoint utilizza la stessa API (Application Programming Interface) per interagire con COS.
I server forniti all'internodi IBM Cloud utilizzano
gli endpoint API per i servizi, incluso COS. Gli endpoint diretti forniscono ai server IBM Cloud dei clienti connessioni dirette ad alta velocità ai servizi senza costi aggiuntivi di larghezza di banda.
 
## Come connettersi a IBM Cloud Object Storage (COS) da un VPC
 1. Esegui il provisioning di COS dal [catalogo ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window}.
 2. Crea un bucket COS in una delle regioni elencate nella seguente sezione.
 3. Utilizza l'endpoint diretto per VPC per creare un'interfaccia con il tuo bucket COS.
 
## Endpoint su più regioni USA
 
| **Più regioni USA** | **Endpoint diretto per VPC** |
|------------|-------------------------------|
| Più regioni USA | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| Punto di accesso Dallas | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| Punto di accesso San Jose | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| Punto di accesso Washington, DC | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## Endpoint regionali USA
 
| **Regione** | **Endpoint diretto per VPC** |
|------------|-------------------------------|
| Stati Uniti Sud | `s3.direct.us-south.cloud-object-storage.appdomain.cloud`|
| Stati Uniti Est | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`|

 ## Endpoint su singolo data center
 
| **Regione** | **Endpoint diretto per VPC** |
|------------|-------------------------------|
| Toronto, Canada | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| Montreal, Canada | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
