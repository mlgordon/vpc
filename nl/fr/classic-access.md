---
copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# Configuration de l'accès à votre infrastructure classique depuis VPC 
{: #setting-up-access-to-your-classic-infrastructure-from-vpc}

Vous pouvez configurer l'accès à votre infrastructure classique d'{{site.data.keyword.cloud}}, notamment la connectivité Direct Link, depuis un cloud privé virtuel dans chaque région, pour n'importe quel compte. Ces "clouds privés virtuels à accès classique" spéciaux utilisent le même routeur implicite que votre infrastructure classique d'{{site.data.keyword.cloud}}. 

Une fois que vous avez configuré un cloud privé virtuel pour l'accès classique, chaque hôte de calcul (interface de serveur virtuel ou bare metal) sur votre compte classique peut envoyer et recevoir des paquets vers et depuis le cloud privé virtuel à accès classique. Toutefois, n'oubliez pas que les pare-feux, les passerelles, les listes de contrôle d'accès au réseau ou les groupes de sécurité peuvent filtrer ce trafic. Il est recommandé de n'autoriser que le trafic nécessaire au bon fonctionnement de vos applications. 

## Prérequis :
1. Votre compte classique doit être lié à votre compte IBM Cloud. Voir [Liaison des comptes IBMid](/docs/account/softlayerlink.html) pour des instructions sur cette opération. 
1. Votre compte classique doit être activé pour le service VRF (Routage et transfert virtuel). 
    * Si Direct Link est déjà disponible sur votre compte, vous êtes prêt.
    * Si votre compte n'est pas compatible avec le service VRF, ouvrez un ticket afin de demander la "migration VRF" pour votre compte. Voir [Comment lancer la conversion](/docs/infrastructure/direct-link?topic=direct-link-how-you-can-initiate-the-conversion) dans notre documentation Direct Link pour en savoir plus sur le processus de conversion. 

Des pare-feux, des passerelles, des listes de contrôle d'accès au réseau ou des groupes de sécurité peuvent exclure une partie ou l'intégralité du trafic réseau entre les ressources classiques et les ressources VPC.
{: important}

## Création d'un cloud privé virtuel à accès classique 
Vous pouvez créer un cloud privé virtuel avec une fonction d'accès classique depuis l'interface utilisateur, l'interface de ligne de commande ou l'interface de programmation (API). 

Un cloud privé virtuel doit être configuré pour l'accès classique lorsqu'il est créé : vous ne pourrez pas le mettre à jour ultérieurement pour ajouter ou retirer la fonction d'accès classique.
{: note}

### Création d'un cloud privé virtuel à accès classique depuis l'interface utilisateur 

Créez un cloud privé virtuel à accès classique depuis la page **Créer un VPC** en cliquant sur la case à cocher **Activer l'accès à une ressource classique**, sous le libellé **Accès classique**. 

![classic-access-ui](/images/classic-access-ui.png)

### Création d'un cloud privé virtuel à accès classique via l'interface de ligne de commande 

Utilisez l'indicateur `--classic-access` lorsque vous créez le cloud privé virtuel. Exemple : 

```
ibmcloud is vpc-create my-access-vpc --classic-access
```
{: pre}


### Création d'un cloud privé virtuel à accès classique à l'aide de l'API 

Transmettez le paramètre `classic_access` lorsque vous créez le cloud privé virtuel. Exemple : 

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "my-access-vpc",
        "classic_access": true
      }'
```
{: pre}


## Limitations

* Seuls vos réseaux privés (en arrière-plan) seront connectés au routeur implicite privé de votre compte. 
* Seuls les sous-réseaux alloués avec des API classiques sont connectés au côté classique de votre routeur implicite privé. Les sous-réseaux qui se trouvent sur des réseaux locaux virtuels classiques ne sont pas routés par le routeur implicite. 
* Un cloud privé virtuel et un seul par région et par compte peut être activé pour l'accès classique. 
