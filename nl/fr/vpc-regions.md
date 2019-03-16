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

# Création d'un cloud privé virtuel dans une autre région 
{: #creating-a-vpc-in-a-different-region}

Une région est un emplacement géographique spécifique où vous pouvez déployer des applications, des services et d'autres ressources {{site.data.keyword.cloud}}. Les régions se composent d'une ou de plusieurs zones, lesquelles correspondent à des centres de données physiques qui hébergent les ressources de calcul, les ressources réseau et les ressources de stockage, ainsi que les systèmes de refroidissement et les appareils électriques hébergeant les services et les applications. Les zones sont isolées les unes des autres pour éviter le partage d'un point de défaillance unique. 

Virtual Private Cloud est en cours de déploiement dans toutes les régions IBM Cloud, en plusieurs phases. 

|   Emplacement     | Région | Noeud final d'API | Statut |
| ------- | :------: | :------: |:------: |
| Dallas | us-south | `us-south.iaas.cloud.ibm.com`| Disponible |
| Francfort | eu-de | `eu-de.iaas.cloud.ibm.com`| Disponible |
| Washington DC | us-east | `us-east.iaas.cloud.ibm.com`| Bientôt disponible |
| Tokyo | jp-tok | `jp-tok.iaas.cloud.ibm.com`| Bientôt disponible |
| Londres | eu-gb | `eu-gb.iaas.cloud.ibm.com`| Bientôt disponible |
| Sydney | au-syd | `au-syd.iaas.cloud.ibm.com`| Bientôt disponible |

Le noeud final d'API régionale (VPC) est défini automatiquement par l'interface de ligne de commande d'IBM Cloud lorsque vous vous connectez à une région spécifique.
{: note}

## Connexion à une région spécifique via l'interface de ligne de commande 

Lorsque vous vous connectez à IBM Cloud, vous pouvez spécifier une région ou la choisir ultérieurement. Par exemple, pour vous connecter au noeud final d'API global dans la région de Dallas (`us-south`) directement, exécutez les commandes suivantes, selon que vous disposez d'un compte fédéré (SSO) ou non : 

Pour un compte fédéré

```
ibmcloud login -a https://cloud.ibm.com -r us-south --sso
```
{: pre}

Pour un compte non fédéré

```
ibmcloud login -a https://cloud.ibm.com -r us-south
```
{: pre}

Pour choisir la région ultérieurement, ne spécifiez pas le paramètre `-r <region>`. Ainsi, l'interface de ligne de commande vous invitera à choisir une région. 

Exemple de sortie : 

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

## Changement de région via l'interface de ligne de commande 

Pour obtenir le statut le plus récent des régions de cloud privé virtuel disponibles, exécutez la commande suivante : 

```
ibmcloud is regions
```
{: pre}

Pour changer de région, exécutez la commande `ibmcloud target -r <region>`. Par exemple, pour passer à la région Francfort, exécutez la commande suivante : 

```
ibmcloud target -r eu-de
```
{: pre}

Pour déterminer l'emplacement actuel, exécutez la commande suivante : 

```
ibmcloud target
```
{: pre}

## Changement de région à l'aide de l'API   

Pour interagir avec l'API régionale via REST, dirigez la demande vers le noeud final d'API de la région dans laquelle créer les ressources. Le noeud final d'API de la région est affiché dans le tableau ci-dessus. De plus, vous pouvez rechercher le noeud final disponible pour les différentes régions en exécutant la commande suivante : 

```
ibmcloud is regions
```
{: pre}


Par exemple, pour obtenir la liste des clouds privés virtuels qui se trouvent dans la région `us-south`, exécutez la commande suivante : 

```
curl https://us-south.iaas.cloud.ibm.com/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Zones

Pour obtenir la liste des zones disponibles pour chaque région, exécutez la commande `ibmcloud is zones <region>`. Par exemple, pour obtenir la liste des zones qui se trouvent dans la région `us-south`, exécutez la commande suivante : 

```
ibmcloud is zones us-south
```
{: pre}
