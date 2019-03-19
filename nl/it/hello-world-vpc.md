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

# Creazione di un VPC utilizzando la CLI IBM Cloud
{: #creating-a-vpc-using-the-ibm-cloud-cli}

Questa guida ti mostra come creare le risorse {{site.data.keyword.cloud}} Virtual Private Cloud utilizzando la CLI IBM Cloud.

## Prerequisiti:

1. Installa la CLI [IBM Cloud](https://cloud.ibm.com/docs/cli/index.html#overview).

2. Installa o aggiorna il plug-in `infrastructure-service` nella CLI IBM Cloud.

  Per eseguire l'installazione:

  ```
  ibmcloud plugin install infrastructure-service
  ```
  {: pre}

  Per eseguire l'aggiornamento:

  ```
  ibmcloud plugin update
  ```
  {: pre}

  Per visualizzare i plug-in e le versioni installate:

  ```
  ibmcloud plugin list
  ```
  {: pre}


3. Genera una chiave SSH pubblica per eseguire il provisioning delle istanze del server virtuale (VSI).

Potresti avere già una chiave SSH pubblica. Ricerca un file denominato ``id_rsa.pub`` in una directory ``.ssh`` all'interno della tua directory home, ad esempio ``/Users/<USERNAME>/.ssh/id_rsa.pub``. Il file inizia con ``ssh-rsa`` e termina con il tuo indirizzo email.

Se non hai una chiave SSH pubblica o se hai dimenticato la password di una chiave esistente, generane una nuova eseguendo il comando ``ssh-keygen`` e seguendo le istruzioni.


Per informazioni su come creare un VPC (Virtual Private Cloud) in diverse regioni IBM Cloud, consulta l'argomento [Regioni](/docs/infrastructure/vpc/vpc-regions.html).
{: tip}


## Passo 1: accedi a IBM Cloud.

Se hai un account federato:
```
ibmcloud login -sso
```
{: pre}

altrimenti

```
ibmcloud login
```
{: pre}

### Passo 2: crea un VPC e salva l'ID VPC.

Utilizza il seguente comando per creare un VPC denominato _helloworld-vpc_.

```
ibmcloud is vpc-create helloworld-vpc
```
{: pre}

Dovresti vedere un output simile a questo:

```
Creating VPC helloworld-vpc in resource group Default under account <Account Name> as user <User>...

ID        ba9e785a-3e10-418a-811c-56cfe5669676   
Name      helloworld-vpc   
Default   no   
Created   1 second ago   
Status    available   
```
{:screen}

Salva l'ID in una variabile in modo che possiamo utilizzarlo successivamente, ad esempio:

```
vpc="ba9e785a-3e10-418a-811c-56cfe5669676"
```
{: pre}

## Passo 3: crea una sottorete e salva l'ID sottorete.

Scegli la zona `us-south-2` per l'ubicazione della sottorete e chiama la sottorete _helloworld-subnet_.

```
ibmcloud is subnet-create helloworld-subnet $vpc us-south-2 --ipv4-address-count 8
```
{: pre}

Dovresti vedere un output simile a questo:

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

Salva l'ID in una variabile in modo che possiamo utilizzarlo successivamente, ad esempio:

```
subnet="50ba0da9-279a-4791-b7cb-cd3d7b2bc14"
```
{: pre}

Nota che lo stato della sottorete è `pending` appena viene creata. Prima di poter procedere, la sottorete deve passare allo stato `available`, il che richiede alcuni secondi. Per controllare lo stato della sottorete, esegui questo comando:

```
ibmcloud is subnet $subnet
```
{: pre}

## Passo 4: crea una chiave SSH nel cloud pubblico di IBM.

Utilizzerai la chiave per eseguire il provisioning di un'istanza del server virtuale. Puoi utilizzare la stessa chiave per eseguire il provisioning di più istanze del server virtuale.

Per visualizzare le chiavi disponibili nel tuo account IBM Cloud, esegui questo comando:

```
ibmcloud is keys
```
{: pre}

Per creare una chiave, immetti il seguente comando. Sostituisci il percorso al tuo file `id_rsa.pub`.

```
ibmcloud is key-create helloworld-key @$HOME/.ssh/id_rsa.pub
```
{: pre}

Dovresti vedere un output simile a questo:

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

Salva l'ID in una variabile in modo che possiamo utilizzarlo successivamente, ad esempio:

```
key="859b4e97-7540-4337-9c64-384792b85653"
```

## Passo 5: seleziona un profilo e un'immagine per l'istanza del server virtuale.

Per elencare tutti i profili di istanza disponibili, immetti il seguente comando:

```
ibmcloud is instance-profiles
```
{: pre}

Per elencare tutte le immagini disponibili, immetti il seguente comando:

```
ibmcloud is images
```
{: pre}

Scegli il profilo di istanza `b-2x8` e l'immagine `ubuntu-16.04-amd64`. Per ottenere l'ID dell'immagine di `ubuntu-16.04-amd64`, immetti il seguente comando:

```
image=$(ibmcloud is images | grep "ubuntu-16.04-amd64" | cut -d" " -f1)
```
{: pre}

## Passo 6: esegui il provisioning di un'istanza del server virtuale.

```
ibmcloud is instance-create helloworld-vsi $vpc us-south-2 b-2x8 $subnet 1000 --image-id $image --key-ids $key
```
{: pre}

Dovresti vedere un output simile a questo:

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

Salva l'ID dell'interfaccia di rete primaria `Primary Intf` in una variabile in modo che possiamo utilizzarlo successivamente, ad esempio:

```
nic="2e850924-b5d7-4386-a778-03556d5850c1"
```
{:pre}

Nota che lo stato dell'istanza è `pending` appena viene creata. Prima di poter procedere, l'istanza deve passare allo stato `running`, il che richiede alcuni minuti. Per controllare lo stato di tutte le istanze, esegui questo comando:

```
ibmcloud is instances
```
{: pre}


## Passo 7: crea un indirizzo IP mobile.

Hai bisogno di un indirizzo IP mobile per poter accedere all'istanza del server virtuale (VSI) da Internet.

```
ibmcloud is floating-ip-reserve helloworld-fip --nic-id $nic
```
{: pre}

Dovresti vedere un output simile a questo:

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

Salva l'indirizzo (`Address`) in una variabile in modo che possiamo utilizzarlo successivamente:

```
address=169.61.181.53
```
{: pre}

## Passo 8: aggiungi una regola al gruppo di sicurezza predefinito per SSH

Trova il gruppo di sicurezza per il VPC:

```
ibmcloud is vpc-sg $vpc
```
{: pre}

Dovresti vedere un output simile a questo:
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

Salva l'ID in una variabile in modo che possiamo utilizzarlo successivamente:

```
sg=2d364f0a-a870-42c3-a554-000000981149
```
{: pre}

Ora crea la regola per consentire SSH:

```
ibmcloud is sg-rulec $sg inbound tcp --port-min=22 --port-max=22
```
{: pre}

Dovresti vedere un output simile a questo:

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

## Passo 9: accedi alla tua istanza del server virtuale utilizzando la tua chiave SSH privata.

Ad esempio, puoi utilizzare un comando di questo formato:

```
ssh -i $HOME/.ssh/id_rsa root@$address
```
{:pre}

Riceverai una risposta simile al seguente esempio. Quando ti viene richiesto di continuare con la connessione, digita `yes`.

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

## Passo 10: Hello, World!

Immetti il seguente comando nella finestra del terminale:

```
echo `hostname` says "Hello, World!"
```
{:pre}

Dovresti vedere il seguente output:

```
helloworld-vsi says Hello, World!
```
{:screen}

## Congratulazioni!

Hai eseguito correttamente il provisioning e la connessione alla tua istanza Virtual Private Cloud tramite la CLI IBM Cloud. Per provare ulteriori comandi della CLI, esplora il riferimento completo:

* [Riferimento CLI per VPC](/docs/cli/reference/ibmcloud?topic=infrastructure-service-cli-vpc-reference#vpc-reference)
