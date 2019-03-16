---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Création d'un cloud privé virtuel à l'aide des API REST 
{: #creating-a-vpc-using-the-rest-apis}

Ce guide explique comment créer des ressources de cloud privé virtuel {{site.data.keyword.cloud}} à l'aide des API régionales d'IBM Cloud (RIAS).

## Prérequis :

1. Vous avez installé l'[interface de ligne de commande d'IBM Cloud](https://cloud.ibm.com/docs/cli/index.html#overview).

## Etape 1 : connectez-vous à IBM Cloud pour obtenir un jeton IAM à utiliser dans les appels API 

Si vous disposez d'un compte fédéré : 
```
ibmcloud login -sso
```
{: pre}

sinon 

```
ibmcloud login
```
{: pre}

Cette commande renvoie une URL et vous invite à saisir un code d'accès. Accédez à cette URL dans votre navigateur et connectez-vous. Si l'opération aboutit, vous obtenez un code d'accès à usage unique. Copiez-le et collez-le dans l'invite. Une fois les étapes d'authentification terminées, vous serez invité à choisir un compte. Répondez aux autres invites éventuelles pour finaliser la connexion. 

## Etape 2 : obtenez un jeton IAM (IBM Identity and Access Management)

La commande suivante appelle l'interface de ligne de commande d'IBM Cloud, analyse le jeton IAM et l'identificateur de jeton `Bearer`, et les stocke dans une variable que vous pourrez utiliser dans des commandes ultérieures : 

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 Pour afficher votre jeton IAM, exécutez la commande ``echo $iam_token``.

Le résultat doit être similaire au code suivant : 

```
Bearer <your token>
```
{: screen}

L'en-tête de l'autorisation s'attend à ce que le jeton commence par "Bearer". Si le résultat ci-dessus n'inclut pas "Bearer", mettez à jour la variable `iam_token` pour l'inclure. Ces exemples supposent que "Bearer" est inclus dans `iam_token`.

Vous devez répéter l'étape précédente pour actualiser votre jeton IAM toutes les heures, car celui-ci expire.
{: important}

## Etape 3 : stockez le noeud final de l'API sous forme de variable 

Stockez le noeud final de l'API dans une variable pour pouvoir le réutiliser ultérieurement. Les noeuds finaux d'API existent par région et
suivent la convention `https://<region>.iaas.cloud.ibm.com`. Par exemple, le noeud final d'API `us-south` est `https://us-south.iaas.cloud.ibm.com`.

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

Pour vérifier que cette variable a été sauvegardée, exécutez `echo $rias_endpoint` et assurez-vous que la réponse n'est pas vide. 

## Etape 4 : exécutez l'API GET Regions 

Si vous rencontrez des résultats inattendus, ajoutez l'indicateur (de débogage) `--verbose` après la commande `curl` pour obtenir des informations de journalisation détaillées. Vous pouvez également consulter les erreurs rencontrées communément sur notre [page concernant le traitement des incidents](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc).
{: tip}

La commande ci-dessous renvoie les régions disponibles pour le cloud privé virtuel au format JSON. Un objet au moins doit être renvoyé. 

Notez le paramètre de requête `version` requis pour chaque commande d'API.
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Etape 5 : exécutez l'API GET Zones 

La commande ci-dessous renvoie toutes les zones disponibles pour le cloud privé virtuel dans la région `us-south` au format JSON. Trois objets au moins doivent être renvoyés. 

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Etape 6 : exécutez l'API GET Profiles 

La commande ci-dessous renvoie les profils disponibles pour vos instances au format JSON. Un objet au moins doit être renvoyé. 

Ajoutez ` | json_pp ` après la commande curl pour obtenir une chaîne JSON lisible.
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Si la sortie de l'API est limitée à cause de la pagination, définissez une limite supérieure à `total_count`, par exemple :

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## Etape 7 : exécutez l'API GET Images 

La commande ci-dessous renvoie les images disponibles pour vos instances au format JSON. Un objet au moins doit être renvoyé. 

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Etape 8 : exécutez l'API GET VPCs 

La commande ci-dessous renvoie les clouds privés virtuels qui ont été créés sur votre compte (le cas échéant) au format JSON. 

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Etape 9 : créez un cloud privé virtuel 

Créez un cloud privé virtuel IBM Cloud dont le nom est `my-vpc`.

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

Pour les autres appels, vous devez connaître l'ID du cloud privé virtuel IBM Cloud que vous venez de créer. Collez l'ID dans la variable, comme ci-dessous. 

Exemple : `vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## Etape 10 : créez un sous-réseau 

Créez un sous-réseau dans votre cloud privé virtuel IBM Cloud. Par exemple, placez-le dans la zone `us-south-2`. 

```bash
curl -X POST $rias_endpoint/v1/subnets?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-subnet",
        "ipv4_cidr_block": "10.0.1.0/24",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Comme pour le cloud privé virtuel, sauvegardez l'ID du sous-réseau dans une variable. 

```bash
subnet="<YOUR_SUBNET_ID>"
```
{: pre}

## Etape 11 : vérifiez le statut de votre sous-réseau 

Pour mettre à disposition des ressources sur votre sous-réseau, celui-ci doit avoir le statut `disponible`. Interrogez la ressource de sous-réseau et assurez-vous que le statut est `disponible` avant de continuer. Si le statut est `échec`, communiquez les détails au [support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support). Vous pouvez essayer de mettre à disposition un autre sous-réseau. 

```bash
curl $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Etape 12 : créez une passerelle publique 

Pour que les instances de serveur virtuel sur le sous-réseau aient accès à l'Internet public, ajoutez une passerelle publique au sous-réseau.   

```bash
curl -X POST $rias_endpoint/v1/public_gateways?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-gateway",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Comme pour le cloud privé virtuel et le sous-réseau, sauvegardez l'ID de la passerelle publique dans une variable. 

```bash
gateway="<YOUR_GATEWAY_ID>"
```
{: pre}

## Etape 13 : associez la passerelle publique au sous-réseau 

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## Etape 14 : créez une clé SSH 

Créez une clé avec votre clé SSH publique. Cette clé est utilisée lors de la création de l'instance de serveur virtuel et est nécessaire pour la connexion à l'instance de serveur virtuel. 

```bash
curl -X POST $rias_endpoint/v1/keys?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-key",
        "public_key": "ssh-rsa AAA....n",
        "type": "rsa"
      }'
```
{: pre}

Sauvegardez l'ID de la clé dans une variable. 

```bash
key="<YOUR_KEY_ID>"
```
{: pre}

## Etape 15 : choisissez un profil et une image pour votre instance de serveur virtuel 

Exécutez les API pour répertorier tous les profils et toutes les images disponibles pour votre instance de serveur virtuel, et choisissez une combinaison. 

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

Pour obtenir des détails supplémentaires sur les profils, vous pouvez interroger le catalogue global à l'aide de la commande d'interface de ligne de commande d'IBM Cloud `ibmcloud catalog entry <profile-name> --json`. Exemple : 

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

La commande suivante répertorie les images disponibles : 

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

Sauvegardez le nom du profil et l'ID de l'image dans des variables qui seront utilisées ultérieurement pour mettre à disposition une instance de serveur virtuel. 

```bash
profile_name="<CHOSEN_PROFILE_NAME>"
image_id="<CHOSEN_IMAGE_ID>"
```
{: pre}

## Etape 16 : mettez à disposition une instance de serveur virtuel 

Mettez à disposition une instance de serveur virtuel sur le sous-réseau que vous venez de créer. Transmettez votre clé SSH publique pour pouvoir vous connecter une fois l'instance mise à disposition. 

```bash
curl -X POST $rias_endpoint/v1/instances?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "server-1",
        "type": "virtual",
        "zone": {
          "name": "us-south-2"
        },
        "vpc": {
          "id": "'$vpc'"
        },
        "primary_network_interface": {
          "port_speed": 1000,
          "subnet": {
            "id": "'$subnet'"
          }
        },
        "keys":[{"id": "'$key'"}],
        "flavor": {
          "name": "'$profile_name'"
         },
        "image": {
          "id": "'$image_id'"
         },
        "userdata": ""
      }'
```
{: pre}

Comme pour les autres ressources, sauvegardez l'ID de l'instance de serveur virtuel dans une variable. 

```bash
server="<YOUR_INSTANCE_ID>"
```
{: pre}

## Etape 17 : vérifiez le statut de votre instance de serveur virtuel 

La mise à disposition d'une instance de serveur virtuel peut prendre de plusieurs secondes à quelques minutes. Avant de continuer, interrogez le statut du serveur et assurez-vous qu'il s'agit de `en fonctionnement`.

```bash
curl $rias_endpoint/v1/instances/$server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Sauvegardez également l'ID de l'interface réseau principale de l'instance de serveur virtuel renvoyé dans l'appel API ci-dessus.   

```bash
network_interface="<YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

Vous ne pouvez pas obtenir l'interface réseau principale si vous n'interrogez pas l'instance spécifique.
{: note}

## Etape 18 : créez une adresse IP flottante 

Créez une adresse IP flottante pour l'instance de serveur virtuel en utilisant l'interface réseau principale de l'instance comme cible pour la nouvelle adresse IP flottante. 

```bash
curl -X POST $rias_endpoint/v1/floating_ips?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-server-floatingip",
        "target": {
            "id":"'$network_interface'"
        }
      }
'
```
{: pre}


Sauvegardez l'ID de l'adresse IP flottante. 

```bash
floating_ip="<YOUR_FLOATING_IP_ID>"
```
{: pre}

## Etape 19 : établissez une liaison SSH à votre instance de serveur virtuel 

Pour établir une liaison SSH au serveur, utilisez l'élément `address` de l'adresse IP flottante que vous avez créée. Pour obtenir l'élément `address` de l'adresse IP flottante, exécutez la commande suivante : 

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Utilisez l'élément `address` de l'adresse IP flottante pour vous connecter à l'instance de serveur virtuel avec SSH : 

```bash
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

L'accès SSH au serveur virtuel peut être empêché par des groupes de sécurité. Si un accès SSH est requis, vous devez utiliser un [groupe de sécurité approprié](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups).
{: note}

Voir [Connecting to your instance using Linux](/docs/vsi-is/vsi_is_connecting_linux_gc.html) pour plus d'informations sur la connexion à votre instance. 


## Etape 20 (facultative) : supprimez les ressources 

Si vous le souhaitez, supprimez les ressources. Une ressource ne peut pas être supprimée si elle contient d'autres ressources. Par exemple, un cloud privé virtuel ne peut pas être supprimé s'il contient des sous-réseaux, et un sous-réseau ne peut pas être supprimé s'il contient des instances de serveur virtuel. En cas de suppression, l'API peut indiquer que la commande a été exécutée, alors que la suppression des ressources peut encore être en cours. Il est recommandé d'interroger la ressource pour s'assurer qu'elle a été supprimée avant de supprimer d'autres ressources. 

### Supprimez l'adresse IP flottante. 

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Supprimez l'instance de serveur virtuel. 

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Supprimez la clé. 

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### Supprimez la passerelle publique. 

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Supprimez le sous-réseau. 

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Supprimez le cloud privé virtuel. 

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Une carte d'interface réseau virtuelle ne peut pas être supprimée d'une instance de serveur virtuel ; par conséquent, il n'existe pas d'étape relative à la suppression des cartes d'interface réseau virtuel.
{: note}

## Félicitations !

Vous avez mis à disposition une instance de cloud privé virtuel à l'aide des API REST. Pour essayez d'autres commandes d'API, découvrez le document de référence complet : 

* [Référence d'API pour VPC](https://{DomainName}/apidocs/rias)
