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
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Initiation à l'infrastructure IBM Cloud Virtual Private Cloud 
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

IBM va accepter un nombre limité de clients pour un programme d'accès anticipé à VPC qui commencera début avril 2019 ; l'accès élargi ne sera ouvert que dans les mois qui suivront. Si votre organisation souhaite accéder à IBM Virtual Private Cloud, veuillez remplir le [formulaire de candidature](https://cloud.ibm.com/vpc){: new_window} ci-dessous et un représentant IBM prendra contact avec vous pour la suite.
{: important}

Pour vous initier à l'infrastructure {{site.data.keyword.cloud}} Virtual Private Cloud : 

1. Créez un cloud privé virtuel.
2. Créez un ou plusieurs sous-réseaux dans le cloud privé virtuel dans une ou plusieurs zones.
3. Créez une passerelle publique sur un sous-réseau si vous souhaitez que les ressources de votre sous-réseau aient accès à Internet ou inversement.
4. Sélectionnez les profils des instances de serveur virtuel à exécuter, et instanciez-les. 
5. Réservez une adresse IP flottante et associez-la à une instance de serveur virtuel si vous voulez y accéder depuis Internet. 
5. Déployez votre service ou vos applications dans les instances de serveur virtuel. 

## Prérequis

 * **Droits utilisateur** : assurez-vous que votre utilisateur dispose des autorisations suffisantes pour créer et gérer des ressources dans votre cloud privé virtuel. Pour obtenir la liste des droits requis, voir [Gestion des droits utilisateur pour les ressources de cloud privé virtuel](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).

 * **Préparez votre clé SSH** : vous utilisez une clé SSH pour vous connecter à votre ou vos instances de serveur virtuel.

   * Recherchez un fichier appelé `id_rsa.pub` dans le répertoire `.ssh`, sous votre répertoire de base, par exemple, `/Users/<USERNAME>/.ssh/id_rsa.pub`. Le fichier commence par `ssh-rsa` et se termine par votre adresse électronique.

   * Ou bien, générez une clé SSH : si vous ne possédez pas de clé SSH publique ou si vous avez oublié le mot de passe d'une clé existante, générez-en une nouvelle en exécutant la commande `ssh-keygen` et en suivant les invites. Par exemple, vous pouvez générer une clé SSH sur votre serveur Linux en exécutant la commande `ssh-keygen -t rsa -C "user_ID"`. Cette commande génère deux fichiers. La clé publique générée se trouve dans le fichier `<your key>.pub`. 
   
## Utilisation de l'interface utilisateur, l'interface de ligne de commande ou l'API REST 

Vous pouvez mettre à disposition et gérer toutes vos ressources de cloud privé virtuel via l'interface utilisateur, l'interface de ligne de commande ou l'API REST. 

Si vous débutez avec IBM Cloud Virtual Private Cloud, suivez l'un des liens ci-dessous, qui vous guidera tout au long du processus de création de votre cloud privé virtuel IBM Cloud et de ses ressources. Vous pouvez choisir de démarrer à partir de l'interface utilisateur de la console, de l'interface de ligne de commande ou de l'API des services d'API d'infrastructure régionales (RIAS). 

* Pour un accès via l'interface utilisateur, connectez-vous à la [console IBM Cloud ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]( https://{DomainName}/vpc){: new_window}. Suivez le [guide de l'interface utilisateur](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console) si vous avez besoin d'aide. 
* Pour utiliser l'interface de ligne de commande, servez-vous du plug-in [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) de l'[interface de ligne de commande d'IBM Cloud ](https://console.bluemix.net/docs/cli/index.html#overview) et suivez l'exemple [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli). 
* Si vous êtes un utilisateur expérimenté, vous pouvez appeler les [API REST](https://{DomainName}/apidocs/rias) directement. Suivez le tutoriel d'[exemple de code](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis) pour vous initier aux API REST. 

## Etapes suivantes
Si vous êtes prêt à aller plus loin, accédez directement à la documentation détaillée sur la **mise en réseau de cloud privé virtuel** et les **instances de serveur virtuel de cloud privé virtuel** :

* [**Mise en réseau de cloud privé virtuel IBM**](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**IBM Virtual Servers for Virtual Private Cloud**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

