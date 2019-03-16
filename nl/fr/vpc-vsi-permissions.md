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
{:table: .aria-labeledby="caption"}

# Planification des droits pour {{site.data.keyword.vsi_is_short}} 
{: #planning-virtual-servers-for-vpc-permissions}

Lorsque vous prévoyez de mettre à disposition {{site.data.keyword.vsi_is_full}}, vous devez comprendre les accès au serveur virtuel disponibles en fonction de votre rôle utilisateur.
{:shortdesc}

Lorsqu'ils utilisent des instances de serveur virtuel, les utilisateurs sont affectés à un rôle en fonction de l'instance d'{{site.data.keyword.vpc_short}} dans laquelle une instance est mise à disposition. Si un utilisateur dispose d'un accès d'éditeur ou d'administrateur à l'instance d'{{site.data.keyword.vpc_short}}, il hérite de la possibilité de créer, supprimer et modifier des instances de serveur virtuel dans cette instance d'{{site.data.keyword.vpc_short}}.

Reportez-vous au tableau ci-dessous pour en savoir plus sur les rôles utilisateur et le niveau spécifique d'accès que chaque rôle inclut. 

* En tant qu'administrateur de compte, vous pouvez définir des rôles et effectuer les actions disponibles pour {{site.data.keyword.vsi_is_short}}.
* En tant qu'éditeur de compte, vous pouvez modifier l'état et créer/supprimer des sous-ressources. 
* En tant qu'afficheur de compte, vous pouvez effectuer des actions qui ne changent pas l'état des ressources. 

Les ressources de serveur virtuel *héritent* de tous les droits utilisateur de leur cloud privé virtuel parent. Les droits ne peuvent pas être définis au niveau de l'instance.
{:note}

<table>
<CAPTION>Tableau 1. Droits utilisateur </CAPTION>
<THEAD>
<TR>
<th>Droit VPC </th>
<th>Description</th>
<th>Actions</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>Administrateur</td>
<td>Toutes les actions, y compris la possibilité de gérer <br>
le contrôle d'accès. </td>
<td>
Contrôle d'accès :
<ul>
<li>Ajouter et retirer des utilisateurs </li>
<li>Affecter des rôles pour chaque utilisateur </li>
</ul>
<p>
Serveurs virtuels :
<ul>
<li>Créer des serveurs virtuels</li>
<li>Arrêter des serveurs virtuels</li>
<li>Supprimer des serveurs virtuels</li>
<li>Redémarrer des serveurs virtuels</li>
<li>Dupliquer des serveurs virtuels</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>Afficher et répertorier les serveurs virtuels </li>
<li>Renommer des serveurs virtuels</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Créer et éditer des clés SSH </li>
<li>Supprimer des clés SSH </li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<!-- <li>View monitoring and log data</li> -->
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>
</p>
</td>
</tr>
<tr>
<td> Editeur </td>
<td>Actions qui changent l'état ainsi que <br>
créer et supprimer des sous-ressources. </td>
<td>
Serveurs virtuels :
<ul>
<li>Créer des serveurs virtuels</li>
<li>Arrêter des serveurs virtuels</li>
<li>Supprimer des serveurs virtuels</li>
<li>Redémarrer des serveurs virtuels</li>
<li>Dupliquer des serveurs virtuels</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>Afficher et répertorier les serveurs virtuels </li>
<li>Renommer des serveurs virtuels</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Créer des clés SSH </li>
<li>Supprimer des clés SSH </li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>Afficher les données de surveillance et de journal </li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td> Afficheur </td>
<td>Actions qui ne changent pas l'état </td>
<td>
Serveurs virtuels :
<ul>
<li>Afficher et répertorier les serveurs virtuels </li>
<!-- <li>View and list image snapshots</li> -->
<li>Afficher les données de surveillance et de journal </li>
</ul>
</td>
</tr>
</TBODY>
</table>

## Etapes suivantes
Pour plus d'informations sur la modification des droits d'un utilisateur, voir [Gestion des droits utilisateur pour les ressources de cloud privé virtuel](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
