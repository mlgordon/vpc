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

# Creazione di un VPC utilizzando le API REST
{: #creating-a-vpc-using-the-rest-apis}

Questa guida ti mostra come creare le risorse {{site.data.keyword.cloud}} Virtual Private Cloud utilizzando le API regionali di IBM Cloud (RIAS).

## Prerequisiti:

1. Installa la CLI [IBM Cloud](https://cloud.ibm.com/docs/cli/index.html#overview).

## Passo 1: accedi a IBM Cloud per ottenere un token IAM da utilizzare nelle chiamate API.

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

Questo comando restituisce un URL e richiede un passcode. Vai a tale URL nel tuo browser e accedi. Se l'operazione ha esito positivo, riceverai un passcode monouso. Copia questo passcode e incollalo come risposta al prompt. Dopo i passi di autenticazione, ti verrà richiesto di scegliere un account. Rispondi alle richieste rimanenti per completare l'accesso.

## Passo 2: ottieni un token IBM IAM (Identity and Access Management)

Il seguente comando chiama la CLI IBM Cloud, analizza il token IAM e l'identificativo token `Bearer` e lo memorizza in una variabile che puoi utilizzare nei comandi successivi.

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 Per visualizzare il tuo token IAM, esegui il comando ``echo $iam_token``.

Il risultato dovrebbe essere simile a questo:

```
Bearer <your token>
```
{: screen}

L'intestazione dell'autorizzazione prevede che il token inizi con "Bearer". Se il risultato precedente non include "Bearer", aggiorna la variabile `iam_token` per includerlo. In questi esempi si presuppone che "Bearer" sia incluso in `iam_token`.

Poiché il token scade, devi ripetere il passo precedente per aggiornare il token IAM ogni ora.
{: important}

## Passo 3: memorizza l'endpoint API come variabile

Memorizza l'endpoint API in una variabile in modo che possa essere riutilizzato in seguito. Esiste un endpoint API per ogni regione
e segue la convenzione `https://<region>.iaas.cloud.ibm.com`. Ad esempio, l'endpoint API per `us-south` è `https://us-south.iaas.cloud.ibm.com`.

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

Per verificare che questa variabile sia stata salvata, esegui `echo $rias_endpoint` e assicurati che la risposta non sia vuota.

## Passo 4: esegui l'API GET Regions

Se riscontri dei risultati imprevisti, aggiungi l'indicatore `--verbose` (debug) dopo il comando `curl` per ottenere informazioni di registrazione dettagliate. Puoi anche controllare gli errori più frequenti nella nostra [pagina di risoluzione dei problemi](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc).
{: tip}

Il seguente comando restituisce le regioni disponibili per VPC, in formato JSON. Deve essere restituito almeno un oggetto.

Nota il parametro di query `version` obbligatorio per ogni comando API.
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Passo 5: esegui l'API GET Zones

Il seguente comando restituisce tutte le zone disponibili per VPC nella regione `us-south`, in formato JSON. Devono essere restituiti almeno tre oggetti.

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Passo 6: esegui l'API GET Profiles

Il seguente comando restituisce i profili disponibili per le tue istanze, in formato JSON. Deve essere restituito almeno un oggetto.

Aggiungi ` | json_pp ` dopo il comando curl per ottenere una stringa JSON leggibile
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Se l'output dell'API è limitato dall'impaginazione, imposta un limite superiore a `total_count`, ad esempio:

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## Passo 7: esegui l'API GET Images

Il seguente comando restituisce le immagini disponibili per le tue istanze, in formato JSON. Deve essere restituito almeno un oggetto.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Passo 8: esegui l'API GET VPCs

Il seguente comando restituisce i VPC che sono stati creati con il tuo account (se presenti), in formato JSON.

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Passo 9: crea un VPC (Virtual Private Cloud)

Crea un IBM Cloud VPC chiamato `my-vpc`.

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

Per il resto delle chiamate, dovrai conoscere l'ID del nuovo IBM Cloud VPC appena creato. Incolla il suo ID nella variabile, come mostrato:

Qualcosa simile a: `vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## Passo 10: crea una sottorete

Crea una sottorete nel tuo IBM Cloud VPC. Ad esempio, utilizza la zona `us-south-2`.

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

Come con il VPC, salva l'ID della sottorete in una variabile.

```bash
subnet="<YOUR_SUBNET_ID>"
```
{: pre}

## Passo 11: controlla lo stato della tua sottorete

Per eseguire il provisioning delle risorse nella tua sottorete, è necessario che lo stato della sottorete sia `available`. Esegui una query sulla risorsa di sottorete e assicurati che lo stato sia `available` prima di continuare. Se lo stato è `failed`, contatta il [supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) fornendo i dettagli. Puoi provare a continuare tentando di eseguire il provisioning di un'altra sottorete.

```bash
curl $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Passo 12: crea un gateway pubblico

Per consentire alle istanze del server virtuale nella sottorete di accedere all'Internet pubblica, aggiungi un gateway pubblico (PGW) alla sottorete.  

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

Come hai fatto con il VPC e con la sottorete, salva l'ID del gateway pubblico in una variabile.

```bash
gateway="<YOUR_GATEWAY_ID>"
```
{: pre}

## Passo 13: collega il gateway pubblico alla sottorete.

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## Passo 14: crea una chiave SSH

Crea una chiave con la tua chiave SSH pubblica. Questa chiave viene utilizzata durante la creazione dell'istanza del server virtuale ed è necessaria per accedere a tale istanza.

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

Salva l'ID della chiave in una variabile.

```bash
key="<YOUR_KEY_ID>"
```
{: pre}

## Passo 15: scegli un profilo e un'immagine per la tua istanza del server virtuale

Esegui le API per elencare tutti i profili e le immagini disponibili per la tua istanza del server virtuale e scegli una combinazione.

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

Per ottenere ulteriori dettagli sui profili, puoi eseguire una query sul catalogo globale utilizzando il comando della CLI IBM Cloud `ibmcloud catalog entry <profile-name> --json`. Ad esempio:

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

Il seguente comando elenca le immagini disponibili.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

Salva il nome del profilo e l'ID dell'immagine nelle variabili, che verranno utilizzate in seguito per eseguire il provisioning di un'istanza del server virtuale.

```bash
profile_name="<CHOSEN_PROFILE_NAME>"
image_id="<CHOSEN_IMAGE_ID>"
```
{: pre}

## Passo 16: esegui il provisioning di un'istanza del server virtuale

Esegui il provisioning di un'istanza del server virtuale nella sottorete appena creata. Passa la tua chiave SSH pubblica in modo da poter accedere dopo aver eseguito il provisioning dell'istanza.

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

Come hai fatto per le altre risorse, salva l'ID dell'istanza del server virtuale in una variabile.

```bash
server="<YOUR_INSTANCE_ID>"
```
{: pre}

## Passo 17: controlla lo stato della tua istanza del server virtuale

Il provisioning di un'istanza del server virtuale può richiedere da alcuni secondi a pochi minuti. Prima di continuare, esegui una query sullo stato del server e assicurati che sia `running`.

```bash
curl $rias_endpoint/v1/instances/$server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Salva anche l'ID dell'interfaccia di rete primaria dell'istanza del server virtuale restituito nella chiamata API precedente.  

```bash
network_interface="<YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

Non puoi ottenere l'interfaccia di rete primaria finché non esegui una query sull'istanza specifica.
{: note}

## Passo 18: crea un IP mobile

Crea un IP mobile per l'istanza del server virtuale, utilizzando l'interfaccia di rete primaria dell'istanza come destinazione per il nuovo indirizzo IP mobile.

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


Salva l'ID dell'IP mobile.

```bash
floating_ip="<YOUR_FLOATING_IP_ID>"
```
{: pre}

## Passo 19: esegui l'accesso SSH alla tua istanza del server virtuale

Per eseguire l'accesso SSH al server, utilizza l'`address` dell'IP mobile che hai creato. Per ottenere l'`address` dell'IP mobile, esegui questo comando:

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Utilizza l'`address` dell'IP mobile per connetterti all'istanza del server virtuale con SSH:

```bash
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

L'accesso SSH al server virtuale potrebbe essere impedito dai gruppi di sicurezza. Se è richiesto l'accesso SSH, devi utilizzare un [gruppo di sicurezza appropriato](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups).
{: note}

Vedi [Connessione alla tua istanza utilizzando Linux](/docs/vsi-is/vsi_is_connecting_linux_gc.html) per ulteriori informazioni su come connetterti alla tua istanza.


## Passo 20 (facoltativo): elimina le risorse

Se vuoi, elimina le risorse. Non è possibile eliminare una risorsa se contiene altre risorse. Ad esempio, un VPC (Virtual Private Cloud) non può essere eliminato se contiene sottoreti e una sottorete non può essere eliminata se contiene istanze del server virtuale. In caso di eliminazione, l'API può ritornare rapidamente ma l'eliminazione della risorsa potrebbe ancora essere in corso. Si consiglia di eseguire una query sulla risorsa per assicurarsi che sia stata eliminata prima di eliminare altre risorse.

### Elimina l'IP mobile.

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Elimina l'istanza del server virtuale.

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Elimina la chiave.

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### Elimina il gateway pubblico.

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Elimina la sottorete.

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Elimina il VPC.

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Una vNIC non può essere eliminata da una VSI, quindi non è necessario effettuare un passo per l'eliminazione delle vNIC.
{: note}

## Congratulazioni!

Hai eseguito correttamente il provisioning di un'istanza Virtual Private Cloud utilizzando le API REST. Per provare ulteriori comandi API, esplora il riferimento completo:

* [Riferimento API per VPC](https://{DomainName}/apidocs/rias)
