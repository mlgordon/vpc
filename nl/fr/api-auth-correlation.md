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
{:DomainName: data-hd-keyref="DomainName"}

# Autorisations de ressource requises pour les appels API et d'interface de ligne de commande 
{: #resource-authorizations-required-for-api-and-cli-calls}

Le tableau ci-dessous répertorie les autorisations requises pour l'interaction avec les objets de l'infrastructure {{site.data.keyword.cloud}} Virtual Private Cloud. Ces informations sont particulièrement utiles pour savoir quand effectuer des appels API. A savoir pour utiliser ce tableau :

Les termes _associé_ et _dissocié_ signifient que la ressource est associée à un ou plusieurs clouds privés virtuels (directement ou indirectement par le biais de ses sous-réseaux), ou dissociée. Une adresse IP flottante ou une liste de contrôle d'accès au réseau dissociée ne possède pas de sous-réseau ; par conséquent, elle n'est associée à aucun cloud privé virtuel et l'autorisation par VPC n'est pas applicable. 

* Les actions **Afficher** et **Répertorier** correspondent au rôle **Afficheur** ou **Opérateur**. 
* L'action **Mettre à jour** et les actions connexes correspondent au rôle **Editeur** ou **Administrateur**. 
* Les ressources sont protégées par une autorisation, mais pas les objets de référence de ressource (ID, nom de ressource de cloud, etc.). 


| Ressource | Opération | Autorisation requise |
|--------|--------|---------|
| Cloud privé virtuel | Créer | Autorisation d'affichage pour le groupe de ressources pour ce cloud privé virtuel et autorisation de mise à jour pour les ressources de cloud privé virtuel |
| Cloud privé virtuel | Mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel |
| Cloud privé virtuel | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel |
| Liste de contrôle par défaut du cloud privé virtuel, groupe de sécurité par défaut | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel |
| Préfixes d'adresse de cloud privé virtuel | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel |
| Préfixes d'adresse de cloud privé virtuel | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel |
|—————|——————|———————|
| Adresse IP flottante (dissociée) | Créer, mettre à jour, supprimer | Tout utilisateur de compte et autorisation d'affichage pour tous les services de gestion des comptes, si la ressource est créée dans le groupe de ressources par défaut. Cliquez [ici](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources#setting-up-viewer-access) pour des instructions sur la configuration de l'accès Afficheur. **Remarque : l'association et la dissociation sont effectuées dans le cadre de l'opération de mise à jour de l'adresse IP flottante**|
| Adresse IP flottante (dissociée) | Afficher, répertorier | Utilisateur de compte |
| Adresse IP flottante (associée) | Mettre à jour | Autorisation de mise à jour pour le sous-réseau associé et son cloud privé virtuel (vous ne pouvez pas créer ni supprimer une adresse IP flottante une fois que celle-ci a été associée) |
| Adresse IP flottante (associée) | Afficher, répertorier | Autorisation d'affichage pour le sous-réseau de l'adresse IP flottante | 
|——————|———————|————————|
| Liste de contrôle d'accès au réseau (dissociée), règles de liste de contrôle d'accès | Créer, mettre à jour, supprimer |Tout utilisateur de compte |
| Liste de contrôle d'accès au réseau (dissociée), règles de liste de contrôle d'accès | Afficher, répertorier |Tout utilisateur de compte |
| Liste de contrôle d'accès au réseau (associée), règles de liste de contrôle d'accès | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour tous les sous-réseaux associés et le cloud privé virtuel |
| Liste de contrôle d'accès au réseau (associée), règles de liste de contrôle d'accès | Afficher, répertorier | Autorisation d'affichage pour au moins l'un des sous-réseaux associés et le cloud privé virtuel |
|——————|———————|————————|
| Passerelle publique | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel de la passerelle publique |
| Passerelle publique | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel de la passerelle publique |
|—————————|————————|———————————|
| Géographie | Afficher, répertorier | Pour les régions et les zones, tout utilisateur de compte |
|———————|————————|—————————|
| Clé SSH | Créer, mettre à jour, supprimer |Tout utilisateur de compte |
| Clé SSH | Afficher, répertorier |Tout utilisateur de compte |
|————————|—————————|————————|
| Sous-réseau | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel du sous-réseau |
| Sous-réseau | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel du sous-réseau |
| Liste de contrôle d'accès au sous-réseau ou passerelle publique | Associer, dissocier | Autorisation de mise à jour pour le cloud privé virtuel du sous-réseau |
| Liste de contrôle d'accès au sous-réseau ou passerelle publique | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel du sous-réseau |
|——————|—————————|————————|
| Groupe de sécurité, règles de groupe de sécurité | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel du groupe de sécurité |
| Groupe de sécurité, règles de groupe de sécurité | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel du groupe de sécurité |
| Interface réseau du groupe de sécurité | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel du groupe de sécurité (qui est aussi le cloud privé virtuel de la carte d'interface réseau) |
| Interface réseau du groupe de sécurité | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel du groupe de sécurité (qui est aussi le cloud privé virtuel de la carte d'interface réseau) |
|—————————|—————————|—————————|
| Images | Créer, mettre à jour, supprimer |Tout utilisateur de compte |
| Images | Afficher, répertorier |Tout utilisateur de compte |
| Instances | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel de l'instance |
| Instances | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel de l'instance |
| Actions d'instance, cartes d'interface réseau, adresses IP flottantes | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le cloud privé virtuel de l'instance |
| Actions d'instance, initialisation, cartes d'interface réseau, adresses IP flottantes | Afficher, répertorier | Autorisation d'affichage pour le cloud privé virtuel de l'instance |
|————————|——————|————————|
| Passerelle VPN | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le réseau privé virtuel |
| Passerelle VPN | Afficher, répertorier | Autorisation d'affichage pour le réseau privé virtuel |
| Connexions de passerelle VPN | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le réseau privé virtuel |
| Connexions de passerelle VPN | Afficher, répertorier | Autorisation d'affichage pour le réseau privé virtuel |
| Connexions, stratégies IPSec et stratégies IKE de passerelle VPN | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le réseau privé virtuel |
| Connexions, stratégies IPSec et stratégies IKE de passerelle VPN | Afficher, répertorier | Autorisation d'affichage pour le réseau privé virtuel |
|————————|——————|————————|
| Equilibreur de charge | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour l'équilibreur de charge |
| Equilibreur de charge | Afficher, répertorier | Autorisation d'affichage pour l'équilibreur de charge |
| Pools et écouteurs d'équilibreur de charge | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour l'équilibreur de charge |
| Pools et écouteurs d'équilibreur de charge | Afficher, répertorier | Autorisation d'affichage pour l'équilibreur de charge |
|————————|——————|————————|
| Volumes | Créer, mettre à jour, supprimer | Autorisation de mise à jour pour le volume | Volumes | Afficher, répertorier | Autorisation d'affichage pour le volume |
| Profils de volume | Afficher, répertorier |Tout utilisateur de compte |


