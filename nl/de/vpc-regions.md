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

# VPC in einer anderen Region erstellen
{: #creating-a-vpc-in-a-different-region}

Eine Region ist eine bestimmte geografische Position, in der Sie Apps, Services und andere {{site.data.keyword.cloud}}}-Ressourcen implementieren können. Regionen bestehen aus einer oder mehreren Zonen, bei denen es sich um physische Rechenzentren handelt, an denen die für Services und Apps verwendeten Ressourcen für Strom, Kühlung, Datenverarbeitung, Vernetzung und Speicher gehostet werden. Zonen werden voneinander isoliert, wodurch kein gemeinsamer Single Point of Failure gewährleistet ist.

Virtual Private Cloud wird phasenweise in allen IBM Cloud-Regionen implementiert.

|   Standort   | Region | API-Endpunkt | Status |
| ------- | :------: | :------: |:------: |
| Dallas | us-south | `us-south.iaas.cloud.ibm.com`| Verfügbar |
| Frankfurt | eu-de | `eu-de.iaas.cloud.ibm.com`| Verfügbar |
| Washington DC | us-east | `us-east.iaas.cloud.ibm.com`| Demnächst verfügbar |
| Tokio | jp-tok | `jp-tok.iaas.cloud.ibm.com`| Demnächst verfügbar |
| London | eu-gb | `eu-gb.iaas.cloud.ibm.com`| Demnächst verfügbar |
| Sydney | au-syd | `au-syd.iaas.cloud.ibm.com`| Demnächst verfügbar |

Der Endpunkt der regionalen API (VPC) wird automatisch von der IBM Cloud-CLI festgelegt, wenn Sie sich an einer bestimmten Region anmelden.
{: note}

## Bei einer bestimmten Region über die Befehlszeilenschnittstelle anmelden

Wenn Sie sich bei IBM Cloud anmelden, können Sie eine Region angeben oder sie später auswählen. Wenn Sie z. B. in der Region Dallas (`us-south`) direkt am globalen API-Endpunkt anmelden möchten, führen Sie die folgenden Befehle aus, je nachdem, ob Sie über ein föderiertes Konto (SSO) verfügen oder nicht.

Führen Sie für ein föderiertes Konto den folgenden Befehl aus:

```
ibmcloud login -a https://cloud.ibm.com -r us-south --sso
```
{: pre}

Führen Sie für ein nicht föderiertes Konto den folgenden Befehl aus:

```
ibmcloud login -a https://cloud.ibm.com -r us-south
```
{: pre}

Um eine Region zu einem späteren Zeitpunkt auszuwählen, geben Sie den Parameter `-r <region>` nicht an. Die CLI fordert Sie dann zur Auswahl einer Region auf.

Beispielausgabe:

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

## Über die Befehlszeilenschnittstelle zwischen Regionen wechseln

Führen Sie den folgenden Befehl aus, um den aktuellen Status der verfügbaren VPC-Regionen abzurufen:

```
ibmcloud is regions
```
{: pre}

Um zu einer anderen Region zu wechseln, führen Sie den Befehl `ibmcloud target -r <region>` aus. Um beispielsweise zur Region "Frankfurt" zu wechseln, führen Sie den folgenden Befehl aus:

```
ibmcloud target -r eu-de
```
{: pre}

Führen Sie den folgenden Befehl aus, um zu überprüfen, an welchem Standort Sie sich gerade befinden:

```
ibmcloud target
```
{: pre}

## Über die API zwischen Regionen wechseln  

Wenn Sie mit der regionalen API über REST interagieren möchten, leiten Sie die Anforderung direkt an den API-Endpunkt der Region, in der Sie Ressourcen erstellen möchten. Der API-Endpunkt der Region wird in der Tabelle oben angezeigt. Darüber hinaus können Sie den verfügbaren Endpunkt für die verschiedenen Regionen finden, indem Sie den folgenden Befehl ausführen:

```
ibmcloud is regions
```
{: pre}


Wenn Sie beispielsweise die Liste der VPCs in der Region `us-south` abrufen möchten, führen Sie den folgenden Befehl aus:

```
curl https://us-south.iaas.cloud.ibm.com/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Zonen

Um die Liste der Zonen abzurufen, die für jede Region verfügbar sind, führen Sie den Befehl `ibmcloud is zones <region>` aus. Wenn Sie beispielsweise die Liste der Zonen in der Region `us-south` abrufen möchten, führen Sie den folgenden Befehl aus:

```
ibmcloud is zones us-south
```
{: pre}
