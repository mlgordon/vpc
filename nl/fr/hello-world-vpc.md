---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:table: .aria-labeledby="caption"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Création d'un cloud privé virtuel via l'interface de ligne de commande d'IBM Cloud 
{: #creating-a-vpc-using-the-ibm-cloud-cli}

Ce guide explique comment créer des ressources de cloud privé virtuel {{site.data.keyword.cloud}} via l'interface de ligne de commande d'IBM Cloud. 

## Prérequis :

1. Installez l'[interface de ligne de commande d'IBM Cloud](https://cloud.ibm.com/docs/cli/index.html#overview).

2. Installez ou mettez à jour le plug-in `infrastructure-service` dans l'interface de ligne de commande d'IBM Cloud. 

  Pour procéder à l'installation : 

  ```
  ibmcloud plugin install infrastructure-service
  ```
  {: pre}

  Pour procéder à la mise à jour : 

  ```
  ibmcloud plugin update
  ```
  {: pre}

  Pour afficher les plug-in installés et les versions : 

  ```
  ibmcloud plugin list
  ```
  {: pre}


3. Générez une clé SSH publique pour mettre à disposition des instances de serveur virtuel. 

Vous avez peut-être déjà une clé SSH publique. Recherchez un fichier appelé ``id_rsa.pub`` dans le répertoire ``.ssh``, sous votre répertoire de base, par exemple, ``/Users/<USERNAME>/.ssh/id_rsa.pub``. Le fichier commence par ``ssh-rsa`` et se termine par votre adresse électronique.

Si vous ne possédez pas de clé SSH publique ou si vous avez oublié le mot de passe d'une clé existante, générez-en une nouvelle en exécutant la commande ``ssh-keygen`` et en suivant les invites.


Pour apprendre à créer un cloud privé virtuel dans différentes régions IBM Cloud, voir la rubrique [Régions](/docs/infrastructure/vpc/vpc-regions.html).
{: tip}


## Etape 1 : connectez-vous à IBM Cloud 

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

### Etape 2 : créez un cloud privé virtuel et enregistrez l'ID de cloud privé virtuel 

Utilisez la commande ci-dessous pour créer un cloud privé virtuel nommé _helloworld-vpc_.

```
ibmcloud is vpc-create helloworld-vpc
```
{: pre}

La sortie se présente comme suit :

```
Creating VPC helloworld-vpc in resource group Default under account <Account Name> as user <User>...

ID        ba9e785a-3e10-418a-811c-56cfe5669676   
Name      helloworld-vpc   
Default   no   
Created   1 second ago   
Status    available   
```
{:screen}

Enregistrez l'ID dans une variable afin de pouvoir l'utiliser ultérieurement, par exemple :

```
vpc="ba9e785a-3e10-418a-811c-56cfe5669676"
```
{: pre}

## Etape 3 : créez un sous-réseau et enregistrez l'ID de sous-réseau 

Choisissez la zone `us-south-2` correspondant à l'emplacement du sous-réseau et nommez le sous-réseau _helloworld-subnet_.

```
ibmcloud is subnet-create helloworld-subnet $vpc us-south-2 --ipv4-address-count 8
```
{: pre}

La sortie se présente comme suit :

```
Creating Subnet helloworld-subnet in resource group Default under account <Account Name> as user <User>...

ID               50ba0da9-279a-4791-b7cb-cd3d7b2bc14d   
Name             helloworld-subnet   
IPv*             ipv4   
IPv4 CIDR        10.240.64.0/29  
IPv6 CIDR        -   
Addr available   3   
Addr Total       8   
Gen              -   
ACL              allow-all-network-acl-ba9e785a-3e10-418a-811c-56cfe5669676(e9c2790b-cee2-465a-8539-d8cd90d33621)   
Gateway          -   
Created          now   
Status           pending   
Zone             us-south-2   
VPC              helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)   
```
{:screen}

Enregistrez l'ID dans une variable afin de pouvoir l'utiliser ultérieurement, par exemple :

```
subnet="50ba0da9-279a-4791-b7cb-cd3d7b2bc14"
```
{: pre}

Notez que le statut du sous-réseau est `en attente` lorsqu'il est créé. Pour que vous puissiez continuer, le sous-réseau doit passer au statut `disponible`, ce qui prend quelques secondes. Pour vérifier le statut du sous-réseau, exécutez la commande suivante :

```
ibmcloud is subnet $subnet
```
{: pre}

## Etape 4 : créez une clé SSH dans IBM Public Cloud 

Vous allez utiliser la clé pour mettre à disposition une instance de serveur virtuel. Vous pouvez utiliser la même clé pour mettre à disposition plusieurs instances de serveur virtuel. 

Pour consulter les clés disponibles dans votre compte IBM Cloud, exécutez la commande suivante :

```
ibmcloud is keys
```
{: pre}

Pour créer une clé, exécutez la commande ci-dessous. Indiquez le chemin d'accès à votre fichier `id_rsa.pub`.

```
ibmcloud is key-create helloworld-key @$HOME/.ssh/id_rsa.pub
```
{: pre}

La sortie se présente comme suit :

```
Creating key helloworld-key in resource group Default under account <Account Name> as user <User>...

ID               859b4e97-7540-4337-9c64-384792b85653   
Name             helloworld-key   
Type             rsa   
Length           2048   
FingerPrint      SHA256:hkcAOGB5z7QXqZLHd0kGqhj735qrfMjZLH9PxS/42vA   
Key              ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC9i2joQ8eiFVdJ7pOlC6h5+IoBL6wFFygkk9Na3gV8Bi52dv44YOAjSJ2oduguHEtLp5r4eh4+5jiEBkFYkHNUhE0MxlcVZABTYWePXx4QnlmGr99xyOfi6DAHhSRQiSBhmhjcGjbADavDuIgoyKpVXbU9O1If3P0miNpaouaZmr+d68OHt4yPvNnztlluV3JBISJgqJ7pzg6wFF0SrjqtEYKBd8oxwogHu+rmRgT7IF09oSiKpKZRF0VfeLFz+REh9RuKa4Jh63aa2PRIgDKq6HO7MEdfOtGzCzoqqlFKgpl+VgGyT0b5BjQEnWv13cwx02bv5QCwma/GeAOpW0CD user@email.com   

Created          now   
```
{:screen}

Enregistrez l'ID dans une variable afin de pouvoir l'utiliser ultérieurement, par exemple :

```
key="859b4e97-7540-4337-9c64-384792b85653"
```

## Etape 5 : sélectionnez un profil et une image pour l'instance de serveur virtuel 

Pour répertorier toutes les instances de profil disponibles, exécutez la commande suivante : 

```
ibmcloud is instance-profiles
```
{: pre}

Pour répertorier toutes les images disponibles, exécutez la commande suivante : 

```
ibmcloud is images
```
{: pre}

Par exemple, sélectionnez le profil d'instance `b-2x8` et l'image `ubuntu-16.04-amd64`. Pour obtenir l'ID d'image de `ubuntu-16.04-amd64`, exécutez la commande suivante :

```
image=$(ibmcloud is images | grep "ubuntu-16.04-amd64" | cut -d" " -f1)
```
{: pre}

## Etape 6 : mettez à disposition une instance de serveur virtuel 

```
ibmcloud is instance-create helloworld-vsi $vpc us-south-2 b-2x8 $subnet 1000 --image-id $image --key-ids $key
```
{: pre}

La sortie se présente comme suit :

```
Creating instance helloworld-vsi in resource group Default under account <Account Name> as user <User>...

ID                4562c5c0-9cf7-4406-bc90-ab4baea91057   
Name              helloworld-vsi   
Gen                  
Profile           b-2x8   
CPU Arch          amd64   
CPU Cores         2   
CPU Frequency     2000   
Memory            8   
Primary Intf      primary(2e850924-b5d7-4386-a778-03556d5850c1)   
Primary Address   10.240.64.4  
Image             ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
Status            pending   
Created           5 seconds ago   
VPC               helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)   
Zone              us-south-2   
```
{:screen}

Sauvegardez l'ID de l'interface réseau principale `Primary Intf` dans une variable pour pouvoir l'utiliser ultérieurement. Exemple : 

```
nic="2e850924-b5d7-4386-a778-03556d5850c1"
```
{:pre}

Notez que le statut de l'instance est `en attente` lorsqu'elle est créée. Pour que vous puissiez continuer, l'instance doit passer au statut `en fonctionnement`, ce qui prend quelques minutes. Pour vérifier le statut de toutes les instances, exécutez la commande suivante :

```
ibmcloud is instances
```
{: pre}


## Etape 7 : créez une adresse IP flottante 

Vous avez besoin d'une adresse IP flottante pour pouvoir vous connecter à l'instance de serveur virtuel depuis Internet. 

```
ibmcloud is floating-ip-reserve helloworld-fip --nic-id $nic
```
{: pre}

La sortie se présente comme suit :

```
Creating floating ip helloworld-fip in resource group Default under account <Account Name> as user <User>...

ID               b9d1cc1f-67db-40e3-81de-9228465170a5   
Address          169.61.181.53   
Name             helloworld-fip   
Target           primary(2e850924-.)   
Target Type      intf   
Target IP        10.0.1.5   
Created          now   
Status           available   
Zone             us-south-2   
```
{:screen}

Enregistrez `Address` dans une variable afin de pouvoir l'utiliser ultérieurement :

```
address=169.61.181.53
```
{: pre}

## Etape 8 : ajoutez une règle au groupe de sécurité par défaut pour SSH 

Recherchez le groupe de sécurité pour le cloud privé virtuel : 

```
ibmcloud is vpc-sg $vpc
```
{: pre}

La sortie se présente comme suit :
```
Getting default security group of vpc ba9e785a-3e10-418a-811c-56cfe5669676 under account <Account Name> as user <User>...

ID               2d364f0a-a870-42c3-a554-000000981149
Name             errand-drastic-imperial-retail-unlocked-jester
Created          1 week ago
VPC              helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)
Resource Group   -
Tags             -

Rules
ID                                     Direction   IPv*   Protocol                  Remote
b597cff2-38e8-4e6e-999d-000002031345   inbound     ipv4   all                       errand-drastic-imperial-retail-unlocked-jester(2d364f0a-.)
b597cff2-38e8-4e6e-999d-000002031527   outbound    ipv4   all                       -

```
{:screen}

Enregistrez l'ID dans une variable afin de pouvoir l'utiliser ultérieurement :

```
sg=2d364f0a-a870-42c3-a554-000000981149
```
{: pre}

A présent, créez la règle pour autoriser SSH :

```
ibmcloud is sg-rulec $sg inbound tcp --port-min=22 --port-max=22
```
{: pre}

La sortie se présente comme suit : 

```
Creating rule for security group 2d364f0a-a870-42c3-a554-000000981149 under account <Account Name> as user <User>...

ID          b597cff2-38e8-4e6e-999d-000001949921
Direction   inbound
IPv*        ipv4
Protocol    tcp
Min Port    22
Max Port    22
Remote      -
```
{:screen}

## Etape 9 : connectez-vous à votre instance de serveur virtuel à l'aide de votre clé SSH privée 

Par exemple, vous pouvez utiliser une commande de la forme suivante :

```
ssh -i $HOME/.ssh/id_rsa root@$address
```
{:pre}

Vous recevez une réponse similaire à l'exemple qui suit. Lorsque vous êtes invité à poursuivre la connexion, entrez `yes`.

```
The authenticity of host '169.61.181.53 (169.61.181.53)' can't be established.
ECDSA key fingerprint is SHA256:9MczXIwJq892DYwu0sZpQZOXORdvNXeP1aFioZpQDsM.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '169.61.181.53' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-133-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

root@helloworld-vsi:~#
```
{:screen}

## Etape 10 : Hello, World!

Exécutez la commande suivante dans la fenêtre du terminal :

```
echo `hostname` says "Hello, World!"
```
{:pre}

La sortie se présente comme suit :

```
helloworld-vsi says Hello, World!
```
{:screen}

## Félicitations !

Vous avez mis à disposition et connecté votre instance de cloud privé virtuel via l'interface de ligne de commande d'IBM Cloud. Pour essayer d'autres commandes d'interface de ligne de commande, consultez la référence complète : 

* [Référence d'interface de ligne de commande pour VPC](/docs/cli/reference/ibmcloud?topic=infrastructure-service-cli-vpc-reference#vpc-reference)
