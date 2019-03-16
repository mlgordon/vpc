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

# Limitations connues
{: #known-limitations}

Ce document contient de brèves descriptions des bogues connus dans l'édition en cours ainsi que la description des fonctions et des API qui ne sont pas prises en charge, et indique les fonctions désormais disponibles sous forme de services bêta uniquement. Les limitations connues peuvent changer au fur et à mesure que nous ajoutons des fonctions à {{site.data.keyword.cloud}} Virtual Private Cloud ; par conséquent, n'hésitez pas à consulter ce document régulièrement.  

## Bogues connus

* Si vous renommez un sous-réseau, il peut s'écouler jusqu'à une heure avant que le nouveau nom de votre sous-réseau ne soit affiché dans la page des détails du serveur, en raison de la temporisation du cache (n° 758). 

## Récapitulatif des fonctions non prises en charge 

* L'accès Direct Link au cloud privé virtuel est pris en charge via l'[**accès classique**](/docs/infrastructure/vpc/classic-access.html) uniquement. 
* Un sous-ensemble de noeuds finaux de services privés uniquement est disponible dans le cloud virtuel privé ; les noeuds finaux ne sont pas tous disponibles.  
* La sauvegarde et la restauration des images ne sont pas prises en charge. 

## API non prises en charge 

Pour des détails sur les API prises en charge, voir la [spécification sur les API](https://{DomainName}/apidocs/rias).

Les API ci-dessous ne sont pas prises en charge dans cette édition. 

| Composant | Fonctions | Commentaires |
|------|------|--------|
| **Calcul :** |   |   |
| Images | Création/Suppression non prises en charge | Ubuntu 16.04, CentOS 7.X, Windows 08, Debian|
| Network_Interfaces | GET (pas de création, suppression, mise à jour) | |
| Volume_Interfaces | Non prises en charge |   |
| Port_Speed | | 100 et 1000 seulement |
| **Stockage :** |   |   |
| Volumes | Non prises en charge |   |
| Snapshots | Non prises en charge |  |

## Fonctions et cas d'utilisation pas encore pris en charge 

Cette section répertorie en détail les fonctions et les cas d'utilisation qui ne sont pas pris en charge.  

* Un cloud privé virtuel ne peut pas être apparié à d'autres clouds privés virtuels. 
* Des instances de serveur virtuel IBM Cloud ou des serveurs bare metal existants ne peuvent pas être migrés dans un cloud privé virtuel. 
* Des routes personnalisées ne peuvent pas être ajoutées à un cloud privé virtuel. Tous les sous-réseaux d'un cloud privé virtuel peuvent communiquer les uns avec les autres par défaut.
* IBM Cloud VPC ne prend pas en charge les domaines de diffusion ou de multidiffusion. 
* IBM Cloud VPC ne fournit pas de chiffrement de bout en bout.  
* Les services IBM Cloud de base ci-dessous sont ceux que vous pouvez utiliser depuis le cloud privé virtuel. Les autres services ne sont pas accessibles.  
  * Protocole de synchronisation NTP 
  * Journalisation
  * Programmes de résolution DNS 
* Un sous-réseau ne peut pas se trouver dans plusieurs zones. 
* Un sous-réseau ne peut pas être déplacé d'une zone à une autre. 
* Les sous-réseaux ne peuvent pas être redimensionnés après leur création. 
* Des serveurs bare metal ne peuvent pas être mis à disposition dans un cloud privé virtuel. 
* Les ressources classiques d'IBM Cloud ne peuvent pas se trouver sur le même sous-réseau dans un cloud privé virtuel. La connectivité entre les ressources classiques et un cloud privé virtuel sur votre compte est possible via l'[**accès classique**](/docs/infrastructure/vpc/classic-access.html).
* Le protocole IPv6 n'est pas pris en charge. 
* Vous ne pouvez pas utiliser votre propre adresse IP publique comme adresse IP flottante. Le pool d'adresses IP flottantes est fourni par IBM. 
* Une adresse IP flottante est liée à une zone. Par exemple, une adresse IP flottante réservée depuis un pool dans la zone 1 ne peut pas être affectée à une instance de serveur virtuel dans la zone 2 dans un même cloud privé virtuel. 
* Les adresses IP privées ne peuvent pas être déplacées d'une instance de serveur virtuel à une autre. 
* Les interfaces réseau ne peuvent pas être déplacées d'une instance de serveur virtuel à une autre. 
* Vous ne pouvez pas désigner l'adresse IP spécifique de l'instance de serveur virtuel. Vous pouvez uniquement spécifier la plage d'adresses IP pour le sous-réseau. Une fois que vous avez associé une instance de serveur virtuel à un sous-réseau, le système affecte une adresse IP privée depuis ce sous-réseau. 
* IBM Cloud VPC est livré avec ses propres outils NaaS (réseau en tant que service), tels qu'un équilibreur de charge en tant que service (LBaaS), des listes de contrôle d'accès et des groupes de sécurité. Vous ne pouvez pas utiliser vos propres dispositifs réseau (comme une passerelle Vyatta ou un autre équilibreur de charge) pour contrôler une ressource dans le cloud privé virtuel. De même, vous ne pouvez pas utiliser votre propre service d'équilibreur de charge ou de groupes de sécurité de l'infrastructure classique d'IBM Cloud pour contrôler des ressources dans IBM Cloud VPC. 
* La passerelle publique n'autorise pas le trafic initié depuis Internet vers une instance de serveur virtuel dans IBM Cloud VPC. A ces fins, une adresse IP flottante doit être utilisée. 
* Une liste de contrôle d'accès est sans état ; par conséquent, le trafic en retour doit être autorisé explicitement dans les règles de liste de contrôle d'accès. 

## Composants ou fonctions disponibles en tant que services bêta 

* **VPN for IBM Cloud VPC** est disponible uniquement en tant que service bêta. 
* **LBaaS for IBM Cloud VPC** est disponible uniquement en tant que service bêta. 
