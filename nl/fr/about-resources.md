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
{:DomainName: data-hd-keyref="DomainName"}

# A propos des ressources d'infrastructure du cloud privé virtuel 
{: #about-vpc-infrastructure-resources}

Le terme _ressources_ désigne les composants d'un déploiement de cloud privé virtuel {{site.data.keyword.cloud}}. Chaque cloud privé virtuel peut contenir des ressources des types suivants, qui peuvent être regroupées en fonction des besoins : 

* **cloud privé virtuel**
* **instance**
* **clé**
* **image**
* **sous-réseau**
* **volume **
* **liste de contrôle d'accès**
* **groupe de sécurité**
* **adresse IP flottante**
* **carte d'interface réseau virtuel**
* **passerelle**
* **équilibreur de charge**
* **réseau privé virtuel**

Considérez la plupart de ces types de ressource comme des "enfants" de leur cloud privé virtuel car ils acquièrent la majorité de leurs règles d'autorisation, qui régissent leur utilisation, de leur cloud privé virtuel "parent" (comme indiqué dans le tableau récapitulatif présenté dans la section suivante). 

Toutefois, il existe une exception : les types de ressource `équilibreur de charge` et `réseau privé virtuel` conservent leurs propres règles d'autorisation. Vous trouverez davantage de détails sur l'autorisation de ressource pour les ressources de réseau privé virtuel et d'équilibreur de charge ultérieurement dans ce document.
{: note}

## Règles de ressource 

En général, l'accès aux ressources dans un cloud privé virtuel est contrôlé par des _règles_. Si vous voulez personnaliser l'accès aux ressources pour votre cloud privé virtuel, vous pouvez créer des règles personnalisées. Une règle de ressource peut cibler : 

* toutes les ressources
* toutes les ressources d'un même type 
* toutes les ressources dans un groupe 
* une ressource individuelle 

## Ressources et groupes de ressources
Un _groupe de ressources_ est une collection de ressources, par exemple un cloud privé virtuel entier, ou un sous-réseau unique et sa liste de contrôle d'accès, qui sont associées en vue de l'établissement d'une autorisation et d'une utilisation. Considérez un groupe de ressources comme une collection d'infrastructure pouvant être utilisée par un projet, un service ou une équipe. 

Les entreprises de grande taille peuvent décider de diviser un cloud privé virtuel en groupes de ressources. Les entreprises de petite taille n'ont généralement pas besoin de diviser leur cloud privé virtuel en groupes de ressources car habituellement, tous les membres de leur équipe utilisent le cloud privé virtuel entier. Si vous connaissez _OpenStack_, un groupe de ressources est similaire au concept de _projet_ dans _OpenStack Keystone_.

Une ressource peut être affectée à un groupe de ressources UNIQUEMENT lorsque vous créez votre cloud privé virtuel. L'affectation d'une ressource à un groupe de ressources ne peut pas être changée une fois créée.
{: .note}

Les groupes de ressources ont été conçus essentiellement pour les organisations de grande taille. Pour la plupart des entreprises et des équipes, la répartition des ressources se trouve dans les limites du cloud privé virtuel. Cette règle empirique générale peut changer lorsqu'il est possible d'affecter des instances de serveur virtuel (VSI) à un groupe de ressources et des utilisateurs individuels à une ressource d'instance de serveur virtuel. 

Lorsque vous configurez votre cloud privé virtuel IBM Cloud, si vous voulez utiliser des groupes de ressources, il est judicieux d'élaborer à l'avance un plan d'affectation des ressources et des utilisateurs de votre organisation à chaque groupe de ressources.
{: tip}

## Spécificités du cloud privé virtuel 

Actuellement, le cloud privé virtuel affecte des rôles et l'accès dans les limites du cloud privé virtuel seulement, pour une ressource individuelle ou pour toutes les ressources qu'il contient. Par exemple, vous ne pouvez pas affecter l'accès à des sous-réseaux individuels dans ce cloud privé virtuel. A la place, les autorisations pour tous les types de ressource du cloud privé virtuel (sous-réseaux, instances, adresses IP flottante, groupes de sécurité, listes de contrôle d'accès, etc.) sont héritées du cloud privé virtuel "parent" de cette ressource. Pour certaines ressources, comme les **équilibreurs de charge** et les **réseaux privés virtuels**, l'autorisation est conservée séparément du cloud privé virtuel auquel elles sont associées. 

### Autorisation de ressource VPC par type de ressource 

Le tableau récapitule la façon dont les ressources de cloud privé virtuel sont autorisées par défaut. 

| Type de ressource | Provenance de son autorisation par défaut |
|-----------|------------|
| Cloud privé virtuel | Vérification d'autorisation lors de sa création |
| Equilibreur de charge | Vérification d'autorisation lors de sa création |
| Réseau privé virtuel | Vérification d'autorisation lors de sa création |
| Sous-réseau | Cloud privé virtuel parent |
| Passerelle publique | Cloud privé virtuel parent |
| Instance | Cloud privé virtuel parent |
| Groupe de sécurité | Cloud privé virtuel parent |
| Clé | Compte |
| Image | Compte |
| Adresse IP flottante | Compte |
| Liste de contrôle d'accès | Compte |
| Volume | Non disponible |

Les adresses IP flottantes et les listes de contrôle d'accès peuvent être créées au niveau du compte, si aucune n'est affectée. Toutefois, dès qu'une adresse IP flottante est affectée à une instance ou qu'une liste de contrôle d'accès est affectée à un sous-réseau, ces ressources sont soumises à la portée de l'autorisation du cloud privé virtuel.
{: note}

### Couverture VPC des rôles et des actions autorisées sur les ressources 

Voici quelques exemples de ce qui se passe lorsqu'un utilisateur disposant de certains rôles tente d'effectuer certaines actions, dans le cas où il existe deux clouds privés virtuels : 

* Utilisateur _admin_, avec les droits d'accès **Administrateur** sur toutes les ressources 
  * Création de `vpc1` : OK 

* Utilisateur _editor_, avec les droits d'accès **Editeur** sur toutes les ressources 
  * Création de `vpc2` : OK 
  * Mise à jour de `vpc2` : OK 
  * Suppression de `vpc2` : OK 

* Utilisateur _operator_, avec les droits d'accès **Opérateur** sur toutes les ressources 
  * Création de `vpc` : refusée 
  * Mise à jour de `vpc1` : refusée 
  * Suppression de `vpc1` : refusée 

* Utilisateur _viewer_, avec les droits d'accès **Afficheur** sur toutes les ressources 
  * Liste des clouds privés virtuels : affichage de [vpc1]
  * Lecture de `vpc1` : OK 

* Utilisateur _noRole_, sans règle 
  * Liste des clouds privés virtuels : affichage de []
  * Lecture de `vpc1` : refusée 

### Tableau récapitulatif de la couverture VPC 

Pour toute règle accordant l'accès par rôle (Administrateur, Editeur, Opérateur, Afficheur), les actions suivantes sont autorisées (X=refusée, o=OK) : 

 rôle :     | aucun | Afficheur | Opérateur | Editeur | Administrateur
-----------:|------|--------|-------|--------|-------
Création    | X    | X      | X     | o      | o
Liste        | X    | o      | X     | o      | o
Lecture | X    | o      | X     | o      | o
Mise à jour | X    | X      | X     | o      | o
Suppression | X    | X      | X     | o      | o


## Autorisation de ressource VPN pour VPC 

L'autorisation de ressource **VPN pour VPC** est configurée séparément des autres types d'autorisation de ressource dans votre cloud privé virtuel, mais de la même manière. 

Les règles dans VPN pour VPC contrôlent l'accès aux ressources de réseau privé virtuel, spécifiquement aux passerelles VPN. Le fait d'avoir accès à une passerelle VPN ne signifie **pas** que vous disposez également de l'accès à ses ressources enfant telles que les connexions VPN ou les blocs CIDR homologues et locaux. Les stratégies IKE et IPSec ne dépendent pas de la passerelle VPN et ne sont pas gérées par la règle de la passerelle. Une règle de ressource dans un réseau privé virtuel peut cibler : 

* toutes les passerelles VPN 
* une passerelle VPN individuelle 

Une passerelle VPN peut également faire partie d'un groupe de ressources. Si vous avez accès à un groupe de ressources particulier, vous avez également accès aux passerelles VPN qui se trouvent dans ce groupe.

L'utilisation du réseau privé virtuel est facturée séparément.
{: note}

### Couverture VPN pour VPC des rôles et des actions autorisées sur les ressources

Les rôles utilisateur qui sont pris en charge sont les mêmes que ceux pris en charge dans l'autorisation de ressource VPC, mais des actions différentes sont activées pour chaque rôle. 

Voici quelques exemples de ce qui se passe lorsque des utilisateurs affectés à certains rôles tentent d'effectuer certaines actions liées au réseau privé virtuel : 

* Utilisateur _admin_, avec les droits d'accès **Administrateur** sur toutes les ressources 
  * Création, mise à jour, suppression, lecture, liste des passerelles VPN : OK 
  * Création, mise à jour, suppression, lecture, liste des connexions VPN : OK 
  * Création, mise à jour, suppression, lecture, liste des blocs CIDR homologues et locaux des connexions VPN : OK 
  * Création, mise à jour, suppression, lecture, liste des stratégies IKE : OK 
  * Création, mise à jour, suppression, lecture, liste des stratégies IPSec : OK 

* Utilisateur _editor_, avec les droits d'accès **Editeur** sur toutes les ressources 
  * Similaire à Administrateur 

* Utilisateur _operator_, avec les droits d'accès **Opérateur** sur toutes les ressources 
  * Création, mise à jour, suppression des passerelles VPN : refusées 
  * Création, mise à jour, suppression des connexions VPN : refusées 
  * Création, mise à jour, suppression des blocs CIDR homologues et locaux des connexions VPN : refusées 
  * Création, mise à jour, suppression des stratégies IKE : refusées 
  * Création, mise à jour, suppression des stratégies IPSec : refusées 
  * Lecture, liste des passerelles VPN : OK - affichage des données réelles 
  * Lecture, liste des connexions VPN : OK - affichage des données réelles 
  * Lecture, liste des blocs CIDR homologues et locaux des connexions VPN : OK - affichage des données réelles 
  * Lecture, liste des stratégies IKE : OK - affichage des données réelles 
  * Lecture, liste des stratégies IPSec : OK - affichage des données réelles 

* Utilisateur _viewer_, avec les droits d'accès **Afficheur** sur toutes les ressources 
  * Similaire à Opérateur 

* Utilisateur _noRole_, sans règle 
  * Lecture, liste des passerelles VPN : refusées - affichage de données vides 
  * Lecture, liste des connexions VPN : refusées - affichage de données vides 
  * Lecture, liste des blocs CIDR homologues et locaux des connexions VPN : refusées - affichage de données vides 
  * Lecture, liste des stratégies IKE : refusées - affichage de données vides 
  * Lecture, liste des stratégies IPSec : refusées - affichage de données vides 

### Tableau récapitulatif de la couverture VPN pour VPC 

Le mappage des rôles et des actions dans VPN pour VPC est présenté dans le tableau suivant (X=refusée, o=OK) : 

rôle :     | aucun | Afficheur | Opérateur | Editeur | Administrateur
-----------:|------|--------|-------|--------|-------
Création    | X    | X      | X     | o      | o
Liste        | X    | o      | o     | o      | o
Lecture | X    | o      | o     | o      | o
Mise à jour | X    | X      | X     | o      | o
Suppression | X    | X      | X     | o      | o

## Autorisation de ressource Equilibreur de charge pour VPC 

L'utilisation de l'autorisation de ressource **Equilibreur de charge pour VPC** est configurée séparément des autres autorisations de ressource dans votre cloud virtuel privé, mais de la même manière. 

L'utilisation de l'équilibreur de charge est facturée séparément.
{: note}

### Couverture de l'équilibreur de charge des rôles et des actions autorisées sur les ressources 

Voici quelques exemples de ce qui se passe lorsque des utilisateurs affectés à certains rôles tentent d'effectuer certaines actions liées à l'équilibreur de charge du cloud privé virtuel : 

* Utilisateur _admin_, avec les droits d'accès **Administrateur** sur toutes les ressources 
  * Création, mise à jour, suppression, lecture, liste des équilibreurs de charge : OK 
  * Création, mise à jour, suppression, lecture, liste des écouteurs : OK 
  * Création, mise à jour, suppression, lecture, liste des pools : OK 
  * Création, mise à jour, suppression, lecture, liste des membres : OK 
  * Création, mise à jour, suppression, lecture, liste des statistiques d'équilibreur de charge : OK 

* Utilisateur _editor_, avec les droits d'accès **Editeur** sur toutes les ressources 
  * Similaire à Administrateur 

* Utilisateur _operator_, avec les droits d'accès **Opérateur** sur toutes les ressources 
  * Création, mise à jour, suppression, lecture, liste des équilibreurs de charge : refusées 
  * Création, mise à jour, suppression, lecture, liste des écouteurs : refusées 
  * Création, mise à jour, suppression, lecture, liste des pools : refusées 
  * Création, mise à jour, suppression, lecture, liste des membres : refusées 
  * Création, mise à jour, suppression, lecture, liste des statistiques d'équilibreur de charge : refusées 

* Utilisateur _viewer_, avec les droits d'accès **Afficheur** sur toutes les ressources 
  * Lecture, liste des équilibreurs de charge : OK 
  * Lecture, liste des écouteurs : OK 
  * Lecture, liste des pools : OK 
  * Lecture, liste des membres : OK 
  * Lecture des statistiques d'équilibreur de charge : OK 

* Utilisateur _noRole_, sans règle 
  * Lecture, liste des équilibreurs de charge : refusées - la liste contient des données vides 
  * Lecture, liste des écouteurs : refusées 
  * Lecture, liste des pools : refusées 
  * Lecture, liste des membres : refusées 
  * Lecture des statistiques d'équilibreur de charge : refusée 

### Tableau récapitulatif de la couverture de l'équilibreur de charge 

Le mappage des rôles et des actions dans Equilibreur de charge pour VPC est présenté dans le tableau suivant (X=refusée, o=OK) : 

rôle :       | aucun | Afficheur | Opérateur | Editeur | Administrateur
-----------:|------|--------|-------|--------|-------
Création      | X    | X      | X     | o      | o
Liste        | X    | o      | X     | o      | o
Lecture     | X    | o      | X     | o      | o
Mise à jour      | X    | X      | X     | o      | o
Suppression  | X    | X      | X     | o      | o
