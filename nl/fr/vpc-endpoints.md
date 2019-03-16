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

# Noeuds finaux de service disponibles pour IBM Cloud VPC
{: #service-endpoints-available-for-ibm-cloud-vpc}

Une fois vous êtes prêt à exécuter des charges de travail, vous pouvez accéder à certains services de l'infrastructure IBM Cloud depuis une instance de serveur virtuel dans votre cloud privé virtuel {{site.data.keyword.cloud}} en utilisant certains noeuds finaux de réseau de distribution d'applications. Plusieurs types de service sont disponibles par le biais de noeuds finaux privés, auxquels les clients VPC peuvent accéder. En utilisant ces noeuds finaux internes, vous pouvez éviter les frais liés à l'utilisation de la bande passante, qui serait facturée si vous accédiez aux noeuds finaux depuis l'Internet public. 

Vous pouvez accéder aux services suivants : 

* Programmes de résolution DNS 
* Fonctions miroir 
* Cloud Object Storage
* Protocole de synchronisation NTP 

## Exemple de noeud final pour IBM Cloud Object Storage

Par exemple, afin d'accéder à un noeud final privé pour un service de stockage d'objets sur le réseau privé IBM Cloud, remplacez la partie "domaine" de l'URL par `objectstorage.adn.networklayer.com`.

## Noeuds finaux pour les programmes de résolution DNS et les fonctions miroir 

Les programmes de résolution DNS et les fonctions miroir utilisent le même espace 161.26/16 partout. Ces noeuds finaux à IP spécifiques sont disponibles sur tous les sites compatibles avec VPC : 

* `mirrors.adn.networklayer.com` (161.26.0.6)
* Serveurs DNS (161.26.0.10 et 161.26.0.11)
