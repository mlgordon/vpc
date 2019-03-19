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

# Creazione e gestione dell'archiviazione in VPC
{: #creating-and-managing-storage-in-vpc}

Attualmente, il tuo {{site.data.keyword.cloud}} Virtual Private Cloud consente solo i volumi di archiviazione di boot.

Quando esegui il provisioning di un'istanza del server virtuale (VSI), un volume di archiviazione a blocchi da 100 GB viene creato automaticamente come volume di boot primario che viene collegato all'istanza. Il volume di boot fornisce prestazioni di 3 IOPS/GB ed esiste per tutto il ciclo di vita della VSI. 

Quando elimini l'istanza, viene eliminato anche il volume di boot.

## Procedure ottimali per la creazione e la denominazione dei volumi di archiviazione del VPC:

* Assicurati di dare un nome a TUTTI i tuoi volumi al momento del provisioning, incluso il volume di boot.
* Assicurati di dare un nome a TUTTI i collegamenti del volume al momento del collegamento
* Ogni volume deve avere un nome distinto all'interno di una regione all'interno di un account. 

Puoi riutilizzare il nome di un volume dopo che il volume è stato eliminato. Tuttavia, tieni presente che riutilizzare un nome di volume potrebbe causare confusione a fini di fatturazione.
{:note}
