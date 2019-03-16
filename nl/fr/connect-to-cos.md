---
copyright:
  years: 2018-2019
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

# Connexion à IBM Cloud Object Storage depuis un cloud privé virtuel 
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

Ce document explique comment se connecter à IBM® Cloud Object Storage depuis un cloud privé virtuel. 

## Qu'est-ce qu'IBM Cloud Object Storage (COS) ?

IBM Cloud Object Storage (COS) est une plateforme basée sur le Web qui stocke des données non structurées. Elle fournit fiabilité, sécurité, disponibilité et reprise après incident sans réplication manuelle. Les informations stockées dans IBM Cloud Object Storage sont chiffrées et réparties à plusieurs emplacements géographiques. Elles sont accessibles via une implémentation de l'API S3. Ce service utilise les technologies de stockage réparti fournies par le service IBM Cloud Object Storage. 

IBM COS est disponible dans trois configurations : **Inter-régional**, **Régional** et **Site unique**.
 * Le service **Inter-régional** permet une plus grande durabilité et une meilleure disponibilité que lorsqu'une seule région est utilisée, mais au détriment de temps d'attente légèrement plus élevés. 
 * Le service **Régional** permet le contraire : il distribue des objets sur plusieurs zones de disponibilité dans une seule région. Si une région ou une zone de disponibilité donnée est inaccessible, le conteneur d'objets continue de fonctionner sans problème. Les éventuelles modifications manquées sont appliquées lorsque le centre de données inaccessible est à nouveau en ligne.
 * Le service **Site unique** permet l'accès à Cloud Object Storage dans un centre de données sélectionné. 
 
### Noeuds finaux directs de COS pour une utilisation avec le cloud privé virtuel 

Les noeuds finaux sont des URL que les applications utilisent pour exécuter des commandes COS et échanger des données avec COS. Chaque noeud final utilise la même API pour interagir avec COS. Les serveurs mis à disposition dans IBM Cloud utilisent des noeuds finaux d'API pour les services, notamment COS. Les noeuds finaux directs fournissent aux serveurs IBM Cloud des clients des connexions directes à vitesse élevée aux services, sans coût supplémentaire lié à la bande passante. 
 
## Connexion à IBM Cloud Object Storage (COS) depuis un cloud privé virtuel 
 1. Mettez à disposition COS depuis le [catalogue ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window}.
 2. Créez un compartiment COS dans l'une des régions répertoriées ci-dessous. 
 3. Utilisez le noeud final direct pour le cloud privé virtuel afin de créer une interface avec votre compartiment COS. 
 
## Noeuds finaux inter-régionaux pour les Etats-Unis 
 
| **Inter-régional pour les Etats-Unis** | **Noeud final direct pour le cloud privé virtuel**|
|------------|-------------------------------|
|Inter-régional pour les Etats-Unis | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| Point d'accès à Dallas | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| Point d'accès à San Jose | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| Point d'accès à Washington, DC | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## Noeuds finaux régionaux pour les Etats-Unis 
 
| **Région** | **Noeud final direct pour le cloud privé virtuel**|
|------------|-------------------------------|
| Sud des Etats-Unis | `s3.direct.us-south.cloud-object-storage.appdomain.cloud`|
| Est des Etats-Unis | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`|

 ## Noeuds finaux de centre de données unique 
 
| **Région** | **Noeud final direct pour le cloud privé virtuel**|
|------------|-------------------------------|
| Toronto, Canada | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| Montréal, Canada | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
