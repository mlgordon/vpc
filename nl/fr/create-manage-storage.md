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

# Création et gestion du stockage dans le cloud privé virtuel 
{: #creating-and-managing-storage-in-vpc}

Actuellement, votre cloud privé virtuel {{site.data.keyword.cloud}} n'admet que des volumes de stockage d'amorçage. 

Lorsque vous mettez à disposition une instance de serveur virtuel, un volume de stockage par blocs de 100 Go est créé comme volume d'amorçage principal et associé à l'instance, automatiquement. Le volume d'amorçage offre une performance de 3 E-S/s/Go et existe pendant tout le cycle de vie de l'instance de serveur virtuel.  

Lorsque vous supprimez l'instance, le volume d'amorçage est supprimé. 

## Meilleures pratiques pour la création et la désignation de vos volumes de stockage VPC : 

* Assurez-vous de nommer TOUS vos volumes au moment de la mise à disposition, y compris le volume d'amorçage. 
* Assurez-vous de nommer TOUTES vos connexions de volume au moment de l'association. 
* Chaque volume doit avoir un nom différent dans une région sur un compte.  

Vous pouvez réutiliser le nom d'un volume après la suppression de ce volume. Toutefois, sachez que la réutilisation du nom d'un volume peut prêter à confusion au moment de la facturation.
{:note}
