---
copyright:
  years: 2017, 2019
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

# A propos de l'infrastructure IBM Cloud Virtual Private Cloud (VPC) 
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

{{site.data.keyword.cloud}} VPC appartient à la nouvelle génération de plateforme IBM One Cloud, qui redéfinit les normes de l'industrie traditionnelles en matière de performances, d'évolution des services, de souplesse et de liberté de déploiement. 

Un cloud privé virtuel (VPC) constitue un point d'entrée abordable pour la sécurité du cloud et la possibilité de mise à l'échelle dans un cloud public. Il permet un contrôle à granularité fine de votre infrastructure virtuelle et de la segmentation de votre trafic réseau. 

## Espace privé dans un cloud public 
IBM Cloud VPC propose un environnement isolé et sécurisé dans le cloud public. Il allie la sécurité d'un cloud privé à la souplesse d'un cloud public. 

 * Vous pouvez gérer les services de réseau essentiels et lancer des serveurs virtuels, en fonction des besoins pour la prise en charge de vos applications indispensables à la mission, compatibles avec le cloud et natives pour le cloud. 
 * Vous pouvez définir vos propres stratégies de mise en réseau, conçues pour assurer la sécurité et un accès pratique. 
 * Vous pouvez mettre à disposition vos ressources et les connecter les unes aux autres, ou les isoler. 

### Isolement logique 
IBM Cloud Virtual Private Cloud (VPC) vous permet d'isoler logiquement vos applications des autres réseaux dans toutes les régions, tout en assurant leur évolutivité et leur sécurité. 

Pour que cet isolement logique soit possible, le cloud privé virtuel est divisé en sous-réseaux à l'aide d'une plage d'adresses IP privées. Cependant, par défaut, toutes les ressources (comme les instances de serveur virtuel) dans un même cloud privé virtuel peuvent communiquer les unes avec les autres, quel que soit le réseau sur lequel elles se trouvent. Les sous-réseaux se trouvent dans une seule zone et ne peuvent pas couvrir plusieurs zones, ce qui contribue à la sécurité, tout en assurant un temps d'attente réduit et la reprise après incident. 

### Mise à disposition d'instance rapide et sécurité 

Créez des instances de serveur virtuel rapidement, à l'aide de profils prédéfinis optimisés pour vos charges de travail spécifiques. Protégez vos instances avec des groupes de sécurité. 

### Fonctions de mise en réseau 
IBM Cloud VPC propose des fonctions de mise en réseau complètes, notamment la sélection d'une plage d'adresses IP, des pare-feux virtuels (groupes de sécurité et listes de contrôle d'accès au réseau), des réseaux privés virtuels de site à site, et un équilibrage de charge (LBaaS) avec élasticité. 

 * Vous pouvez configurer votre topologie virtuelle automatiquement à l'aide des plages de préfixes suggérées et des règles de réseau préconfigurées. 
 * Vous pouvez personnaliser votre cloud privé virtuel IBM Cloud et l'adapter à vos exigences en constante évolution, en toute transparence. 
 * Vous pouvez ajouter votre propre plage d'adresses IP. 
 * Vous pouvez affecter une adresse IP flottante depuis un pool existant. 
 * L'équilibrage de charge et le réseau privé virtuel présentent plusieurs plans de contrôle multi-régions, ce qui signifie que chaque région dans laquelle le plan de contrôle est déployé peut prendre en charge toutes les régions pour les instances de serveur virtuel d'un client. En cas d'incident dans une région, le service n'est pas affecté dans les autres régions. 

### Connectivité globale 
Vous pouvez définir la portée de vos applications et des ressources disponibles de sorte qu'elles s'étendent sur plusieurs régions. A l'aide d'un réseau privé virtuel, vous pouvez créer des connexions privées à d'autres projets et à d'autres parties de vos déploiements de cloud hybride. 

### Sécurité des réseaux 
La sécurité est intégrée à IBM Cloud VPC, avec des groupes de sécurité qui font office de pare-feux virtuels pour une protection au niveau de l'instance, et avec des listes de contrôle d'accès au réseau pour une protection au niveau du sous-réseau. 

### Equilibrage de charge
Dans IBM Cloud VPC, utilisez l'équilibrage de charge pour répartir votre trafic réseau dans un ensemble de cibles afin d'améliorer les performances et la haute disponibilité. Les équilibreurs de charge surveillent également la santé de vos applications et de vos services. Vous pouvez configurer un équilibreur de charge pour répartir le trafic d'application entrant dans les instances d'une zone unique ou dans plusieurs zones d'une région. 

### Accès Internet
Deux options sont disponibles pour permettre la communication depuis vos instances de serveur virtuel avec l'Internet public : 
* Utilisez une passerelle publique afin de permettre la communication pour toutes les instances de serveur virtuel sur le sous-réseau associé. L'utilisation d'une passerelle publique n'est pas facturée, à l'inverse de l'utilisation de la bande passante. 
* Utilisez une adresse IP flottante afin de permettre la communication depuis une instance de serveur virtuel unique. 

![IBM Cloud VPC](images/vpc-experience.png)
**Figure : exemple de configuration d'IBM Cloud VPC**

## Prise en charge des charges de travail natives pour le cloud 

Un cloud privé virtuel est idéal pour les charges de travail natives pour le cloud et pour la liaison de votre infrastructure existante dans IBM Cloud. Vous pouvez créer le meilleur cloud pour toutes vos charges de travail importantes, comme les calculs cognitifs, d'intelligence artificielle et d'apprentissage automatique. Pendant ce temps, vous pouvez continuer d'utiliser la version classique d'IBM Cloud pour les charges de travail traditionnelles, si vous le souhaitez. 

VPC peut prendre en charge vos charges de travail hybrides, compatibles avec le cloud et natives pour le cloud à l'aide des fonctions suivantes : 

 * Création et gestion d'environnements d'application isolés via une API 
 * Conception de topologies de réseau avec l'ajout de votre propre plage d'adresses IP (BYOIP, Bring Your Own IP) 
 * Utilisation de groupes de sécurité et de listes de contrôle d'accès au réseau pour permettre des topologies souples gérées par API 
 * Des zones de disponibilité permettent des connexions à haute vitesse et à faible temps d'attente entre les régions, tout en assurant la haute disponibilité 
 * Mise à l'échelle automatique 
   * Mise à l'échelle supérieure ou inférieure par milliers de serveurs par jour 
   * Utilisation d'un équilibrage de charge évolutif et fiable avec gestion de certificats 
   * Etablissement d'une surveillance évolutive et fiable 
   * Illusion d'une capacité infinie pour vos clients 
 * Utilisation d'unités de stockage et de mise en réseau à haute vitesse 
 * Autorisation systématique pour les services (plan de contrôle) 
 * Couverture de plusieurs régions pour la reprise après incident et la résilience 
 * Mise à disposition et utilisation de services de base : gestion des adresses IP, réseau privé virtuel, pare-feux, SSH, DNS et équilibrage de charge L4 
 * Configuration d'autres services : mise à l'échelle automatique, réseaux de distribution de contenu, virtualisation des fonctions réseau de tiers 
 * Mise à disposition rapide d'instance de serveur virtuel, avec affinité et anti-affinité 
 * Gestion des images souple avec images préstockées 
 * Prise en charge des processeurs graphiques 

## Récapitulatif des avantages 

 * Initiation rapide à l'aide de configurations prédéfinies pour vos instances, appelées profils 
 * Portée géographique souple avec zones et régions disponibles globalement 
 * Sécurisation intégrale, avec listes de contrôle d'accès et groupes de sécurité 
 * Un réseau et des ressources de cloud privé virtuel, qui peuvent évoluer et être partagés rapidement, peuvent s'étendre depuis votre installation sur site jusque dans votre cloud 
 * Surveillance de vos charges de travail pour des performances et une efficience optimales 

## Récapitulatif des fonctions 

  * Création de sous-réseaux et ajout de votre propre plage d'adresses IP 
  * Création et gestion d'instances de serveur virtuel à l'aide d'Ubuntu 16.04, CentOS 7.x, Windows ou Debian
  * Réservation et association d'une adresse IP flottante IPv4 
  * Obtention d'un accès Internet aux sous-réseaux en créant une passerelle publique (une par zone) 
  * Création et affectation de groupes de sécurité à vos instances de serveur virtuel 
  * Utilisation de listes de contrôle d'accès au réseau pour assurer la sécurité de vos sous-réseaux 
  * Instances de serveur virtuel sur un seul réseau, avec une carte d'interface réseau virtuel 
  * Instances de serveur virtuel sur plusieurs réseaux, avec plusieurs cartes d'interface réseau virtuel 
  * Déploiement de zone, dans la région US-South ou FRA 
  * Accès Internet via un réseau privé virtuel 
  * Equilibrage de charge natif dans le cloud privé virtuel 

## Mises en garde relatives à l'ajout de votre propre plage d'adresses IP (BYOIP) 

Vous pouvez ajouter votre propre plage d'adresses IPv4 publiques à votre compte IBM Cloud VPC. Si vous ajoutez votre propre plage d'adresses IP, IBM Cloud doit configurer ces adresses IPv4 sur des ressources IBM Cloud, qui enverront des paquets vers et depuis les adresses que vous avez spécifiées. Par conséquent, suite à l'utilisation de votre plage d'adresses IPv4 fournie dans IBM Cloud, ces adresses IP peuvent être exposées au personnel d'assistance IBM et à des tiers dans le cadre de votre utilisation de ce service.
{: important}

Vous devez utiliser l'API ou l'interface de ligne de commande pour pouvoir ajouter votre propre plage d'adresses IP. Cette fonction avancée n'est pas disponible depuis l'interface utilisateur de la console IBM Cloud.
{: note}

Pour la liste complète des limitations connues et des fonctions qui ne sont pas prises en charge actuellement, voir le document [Limitations connues](/docs/infrastructure/vpc?topic=vpc-known-limitations). 

## En savoir plus 

* [**Terminologie IBM relative aux clouds privés virtuels**](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**Sécurité des clouds privés virtuels IBM**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**Régions et sous-réseaux disponibles pour les clouds privés virtuels IBM**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**Création et gestion des ressources de réseau dans le cloud privé virtuel**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [**Création et gestion des instances de serveur virtuel**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
