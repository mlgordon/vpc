---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Glossaire de VPC 
{: #vpc-glossary}

La terminologie ci-après est communément utilisée et est propre à {{site.data.keyword.cloud}} Virtual Private Cloud. Voir [Termes du glossaire d'IBM Cloud](/docs/overview/glossary/glossary.html) pour la signification de termes supplémentaires employés plus généralement. 

## clé SSH 
Données d'identification d'accès cryptographiques générées automatiquement qui contrôlent l'accès aux instances de serveur virtuel dans un cloud privé virtuel. 

## cloud privé virtuel 
Réseau virtuel lié à un compte. Il permet un contrôle à granularité fine de l'infrastructure virtuelle et de la segmentation du trafic réseau, tout en assurant la sécurité et la mise à l'échelle dynamique. 

## conversion NAT
La conversion d'adresses réseau (NAT) est une méthode d'adressage décrite dans la spécification [Internet RFC 1631 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://tools.ietf.org/html/rfc1631){: new_window}, qui permet d'utiliser une adresse IP pour communiquer avec plusieurs autres adresses IP, comme celles d'un sous-réseau privé, principalement à l'aide d'une table de correspondance. Il existe deux types principaux de conversion NAT : la conversion NAT 1 à 1 et la [conversion NAT plusieurs à 1 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://en.wikipedia.org/wiki/Network_address_translation){: new_window}. A l'origine, la conversion NAT a été conçue pour étendre la vie utile des adresses IP IPv4 ; à présent, elle est fréquemment utilisée dans les environnements de cloud pour permettre la communication avec les sous-réseaux privés. 

## équilibreur de charge en tant que service (LBaaS)
Un équilibreur de charge en tant que service (LBaaS) permet de répartir le trafic de façon équilibrée entre les instances d'un cloud privé virtuel. 

## géographie
Dans un cloud privé virtuel, la désignation de la géographique fournit des informations sur la région et la zone dans lesquelles le cloud privé virtuel et ses ressources associées sont déployés. 

## groupe de sécurité
Un groupe de sécurité fait office de pare-feu virtuel qui contrôle le trafic entrant et sortant pour un ou plusieurs serveurs (instances de serveur virtuel). Il s'agit d'une collection de règles qui spécifient si le trafic doit être autorisé pour une instance de serveur virtuel associée. Lorsqu'un client lance une instance de serveur virtuel, il peut lui associer un ou plusieurs groupes de sécurité. S'il dispose des droits appropriés, il peut modifier les règles des groupes de sécurité. 

## image
Informations requises pour lancer une instance de serveur virtuel, ou _instance_. En général, il s'agit d'une image instantanée d'un système d'exploitation disponible sur le marché, utilisée pour l'amorçage. 

## instance
Nom abrégé désignant un serveur virtuel ou une instance de serveur virtuel, qui s'exécute dans un cloud privé virtuel. 

## IP flottante 
La méthode IP flottante autorise l'accès entrant et sortant à Internet pour les ressources de cloud privé virtuel, telles que des instances, un équilibreur de charge ou un tunnel VPN, à l'aide d'_adresses IP flottantes_ affectées depuis un pool. 

Les adresses IP flottantes sont des adresses IP publiques fournies par le système depuis le pool existant. Vous ne pouvez pas indiquer vos propres adresses IP publiques. Les adresses IP flottantes sont accessibles depuis Internet et peuvent être associées à une instance (par exemple, une instance de serveur virtuel, un équilibreur de charge ou une passerelle VPN) à l'aide d'une carte d'interface réseau virtuel. 

Vous pouvez réserver une adresse IP flottante depuis le pool des adresses IP flottantes disponibles fournies par IBM, et vous pouvez l'associer à toute instance se trouvant dans le même cloud privé virtuel, ou la dissocier. La méthode IP flottante utilise la [conversion NAT](#nat) 1 à 1 pour permettre à un serveur de communiquer avec l'Internet public ainsi qu'avec un sous-réseau privé dans votre environnement de cloud. 

## liste de contrôle d'accès
Une liste de contrôle d'accès impose des contrôles de sécurité pour le trafic entrant et sortant pour un [sous-réseau](#subnet). Une liste de contrôle d'accès est sans état. Chaque liste de contrôle d'accès se compose de règles, reposant sur une _adresse IP source_, un _port source_, une _adresse IP de destination_, un _port de destination_ et un _protocole_.

Dans IBM Cloud VPC, chaque sous-réseau est créé avec une liste de contrôle d'accès par défaut, qui autorise le trafic entrant et sortant ; cependant, les clients peuvent créer des listes de contrôle d'accès personnalisées. Une liste de contrôle d'accès est associée à un sous-réseau spécifique à tout moment, mais peut également être associée à plusieurs sous-réseaux.

Parfois aussi appelée _liste de contrôle d'accès au réseau_. 

## partages 
Moyen de fournir un stockage de fichiers dans un cloud privé virtuel. 

## passerelle publique
Une passerelle publique permet l'accès sortant uniquement pour un sous-réseau (avec toutes les instances de serveur virtuel associées au sous-réseau) en vue de la connexion à Internet. Notez que les sous-réseaux sont privés par défaut. Toutefois, si vous le souhaitez, vous pouvez créer une passerelle publique et lui associer un sous-réseau. Une fois qu'un sous-réseau est connecté à la passerelle publique, toutes les instances de serveur virtuel de ce sous-réseau peuvent se connecter à Internet.

Une passerelle publique utilise la conversion NAT plusieurs à 1, ce qui signifie que des milliers d'instances de serveur virtuel possédant des adresses privées utilisent une adresse IP publique pour communiquer avec l'Internet public. La passerelle publique ne permet pas à Internet d'établir une connexion à ces instances.

## profil 
Un profil est une combinaison courante d'unités centrales virtuelles et de mémoire RAM qui peut être instanciée rapidement pour démarrer une instance de serveur virtuel. Trois familles de profil sont prises en charge : les profils équilibrés, les profils de calcul et les profils de mémoire. 

## région 
Zone géographique dans laquelle un cloud privé virtuel est déployé. Chaque région contient plusieurs zones, qui représentent des domaines d'erreur indépendants. IBM Cloud VPC s'étend sur plusieurs zones dans la région qui lui est affectée. 

## réseau privé virtuel 
Un réseau privé virtuel (VPN) permet d'établir une connexion privé entre deux noeuds finaux, même lorsque les données sont transférées sur un réseau public. Les clients peuvent partager des données comme s'ils étaient connectés à un réseau privé. En général, un réseau privé virtuel est utilisé en conjonction avec des méthodes de sécurité telles que l'authentification et le chiffrement afin d'assurer une sécurité et une confidentialité des données maximales. 

## réseau privé virtuel en tant que service (VPNaaS) 
Connexion privée entre deux noeuds finaux, qui reste privée et peut être chiffrée, même lorsque les données sont transférées sur un réseau public. 

## ressource
Type d'actif appartenant à un déploiement de cloud privé virtuel et pouvant être facturé, par exemple une instance de serveur virtuel, une adresse IP flottante ou le cloud privé virtuel lui-même. Les ressources peuvent être combinées dans des _groupes de ressources_ pour faciliter la comptabilité lorsque certaines ressources sont systématiquement utilisées ensemble dans un cloud privé virtuel. 

## sous-réseau
Un sous-réseau est une plage d'adresses IP, liée à une zone unique, qui ne peut pas s'étendre sur plusieurs zones ou régions. Un sous-réseau peut couvrir l'intégralité d'une zone dans un cloud privé virtuel IBM Cloud. 

Pour IBM Cloud VPC, la caractéristique essentielle d'un sous-réseau est qu'il peut être isolé d'un autre sous-réseau, mais aussi connecté de façon classique. Un sous-réseau peut être isolé à l'aide de listes de contrôle d'accès au réseau qui font office de pare-feux pour contrôler le flux de paquets de données sur les sous-réseaux. De même, des groupes de sécurité font office de pare-feux virtuels pour contrôler le flux de paquets de donnée depuis et vers des instances de serveur virtuel. 

C'est l'isolement des sous-réseaux qui vous permet de créer un espace privé dans le cloud public. 

## volumes
Stockage de données à hautes performances monté par l'hyperviseur pour les instances de serveur virtuel dans un cloud privé virtuel. 

## zone
Domaine d'erreur indépendant. Une zone est une abstraction qui propose une assistance en apportant une tolérance aux pannes améliorée et un temps d'attente réduit. Une zone garantit les propriétés suivantes : 

 * Etant donné que chaque zone constitue un domaine d'erreur indépendant, il est fort peu probable que deux zones d'une région tombent en panne simultanément. 
 * Le trafic entre les zones d'une région connaît un temps d'attente inférieur à deux millisecondes. 
