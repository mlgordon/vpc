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


# Tarification de VPC
{: #pricing-for-vpc}

Le tableau récapitule la tarification des transferts de données Internet avec {{site.data.keyword.cloud}} Virtual Private Cloud. Sachez que le trafic entre les services VPC et classiques d'IBM Cloud n'est pas facturé. De plus, pour les services de paiement à la carte (PayGo), les niveaux de service sont liés à votre compte et non à une instance de VPC spécifique. Les montants sont affichés en dollars américains. 

Une tarification distincte s'applique pour les [instances de serveur virtuel](/docs/infrastructure/vpc?topic=vpc-pricing-for-virtual-servers-for-vpc) utilisées avec votre cloud privé virtuel IBM Cloud. 

## Franchises pour le transfert de données Internet 

| Transfert de données | Coût pour tous les clients IBM Cloud VPC |
|---------------|------------------|
| Dans la zone | Gratuit |
| Entre les zones d'une même région | Gratuit |
| Utilisation de la passerelle publique | Gratuit (seule l'adresse IP flottante utilisée par la passerelle publique est facturée) |

## Tarification des adresses IP flottantes 

Une adresse IP flottante est facturée 1 dollar (américain) par mois, à partir de sa réservation. Ces frais sont facturés même si l'adresse IP flottante n'est pas associée à une instance de serveur virtuel ou si elle n'est pas utilisée. Les frais mensuels d'1 dollar sont facturés même si l'adresse IP flottante n'est réservée que pendant quelques jours. 


## Tarification à la carte (PayGo) de base pour le transfert de données Internet 

| Transfert de données | Quantité de données | Tarification PayGo |
|-----------|-----------|------------------|
| Sortie vers Internet |  0 à 5 Go | Gratuit |
|  | 6 à 10000 Go | 0,087 $ par Go |
|  | 10001 à 50000 Go | 0,083 $ par Go |
|  | 50001 à 150000 Go | 0,07 $ par Go |
|  | 150001 Go et plus | 0,05 $ par Go |


Lorsque vous créez un cloud privé virtuel, il peut s'écouler jusqu'à une heure avant que les frais facturés initiaux n'apparaissent dans l'interface utilisateur de la console ou l'API.
{: tip}

Si vous disposez d'une passerelle publique ou d'une adresse IP flottante, vous pouvez constater des frais de sortie minimaux, même si vous n'avez pas envoyé de trafic sortant. Ces frais concernent le trafic ARP (protocole de résolution d'adresse), qui est nécessaire pour faire fonctionner votre compte.
{: important}


