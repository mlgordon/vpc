---

copyright:
  years: 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Creazione di un VPC in una regione diversa
{: #creating-a-vpc-in-a-different-region}

Una regione è una specifica ubicazione geografica in cui puoi distribuire applicazioni, servizi e altre risorse {{site.data.keyword.cloud}}}. Le regioni sono costituite da una o più zone che sono data center fisici che ospitano le risorse di calcolo, rete e archiviazione, nonché il raffreddamento e l'alimentazione correlati, che ospitano i servizi e le applicazioni. Le zone sono isolate l'una dall'altra, il che garantisce che non ci sia alcun singolo punto di guasto condiviso.

Virtual Private Cloud viene distribuito in tutte le regioni IBM Cloud in fasi.

|   Ubicazione     | Regione | Endpoint API | Stato |
| ------- | :------: | :------: |:------: |
| Dallas | us-south | `us-south.iaas.cloud.ibm.com`| Disponibile |
| Francoforte | eu-de | `eu-de.iaas.cloud.ibm.com`| Disponibile |
| Washington DC | us-east | `us-east.iaas.cloud.ibm.com`| Presto disponibile |
| Tokyo | jp-tok | `jp-tok.iaas.cloud.ibm.com`| Presto disponibile |
| Londra | eu-gb | `eu-gb.iaas.cloud.ibm.com`| Presto disponibile |
| Sydney | au-syd | `au-syd.iaas.cloud.ibm.com`| Presto disponibile |

L'endpoint API regionale (VPC) viene impostato automaticamente dalla CLI IBM Cloud quando accedi a una regione specifica.
{: note}

## Accedi a una regione specifica utilizzando la CLI

Quando accedi a IBM Cloud, puoi specificare una regione o sceglierla in un secondo momento. Ad esempio, per accedere direttamente all'endpoint API globale nella regione di Dallas (`us-south`), immetti i seguenti comandi, a seconda che tu disponga o meno di un account federato (SSO).

Per un account federato,

```
ibmcloud login -a https://cloud.ibm.com -r us-south --sso
```
{: pre}

Per un account non federato,

```
ibmcloud login -a https://cloud.ibm.com -r us-south
```
{: pre}

Per scegliere la regione in un secondo momento, non specificare il parametro `-r <region>` e la CLI ti chiederà di scegliere una regione.

Output di esempio:

```
API endpoint: cloud.ibm.com

Get One Time Code from https://identity-2.eu-central.iam.cloud.ibm.com/identity/passcode to proceed.
Open the URL in the default browser? [Y/n]> y
One Time Code >
Authenticating...
OK

Select an account:
1. MyAccount (00a11aa1a11aa11a1111a1111aaa11aa) <-> 1234567
2. TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321
Enter a number> 2
Targeted account TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321


Targeted resource group Default

Select a region (or press enter to skip):
1. au-syd
2. jp-tok
3. eu-de
4. eu-gb
5. us-south
6. us-east
Enter a number> 5
Targeted region us-south


API endpoint:      https://cloud.ibm.com   
Region:            us-south   
User:              first.last@email.com   
Account:           TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321  
Resource group:    Default   
CF API endpoint:      
Org:                  
Space:                

...
```
{: screen}

## Cambia le regioni utilizzando la CLI

Per ottenere lo stato più recente delle regioni VPC disponibili, immetti il seguente comando:

```
ibmcloud is regions
```
{: pre}

Per passare a una regione diversa, esegui il comando `ibmcloud target -r <region>`. Ad esempio, per passare alla regione di Francoforte, immetti il seguente comando:

```
ibmcloud target -r eu-de
```
{: pre}

Per verificare in quale ubicazione ti trovi attualmente, immetti il seguente comando:

```
ibmcloud target
```
{: pre}

## Cambia le regioni utilizzando l'API  

Per interagire con l'API regionale tramite REST, indirizza la richiesta all'endpoint API della regione in cui vuoi creare le risorse. L'endpoint API della regione è mostrato nella precedente tabella. Inoltre, puoi trovare l'endpoint disponibile per le diverse regioni immettendo il seguente comando:

```
ibmcloud is regions
```
{: pre}


Ad esempio, per ottenere l'elenco dei VPC nella regione `us-south`, immetti il seguente comando:

```
curl https://us-south.iaas.cloud.ibm.com/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Zone

Per ottenere l'elenco delle zone disponibili per ogni regione, esegui il comando `ibmcloud is zones <region>`. Ad esempio, per ottenere l'elenco delle zone nella regione `us-south`, immetti il seguente comando:

```
ibmcloud is zones us-south
```
{: pre}
