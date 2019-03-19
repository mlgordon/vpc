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
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# Configurazione dell'accesso alla tua infrastruttura classica da VPC
{: #setting-up-access-to-your-classic-infrastructure-from-vpc}

Puoi configurare l'accesso alla tua infrastruttura classica di {{site.data.keyword.cloud}}, inclusa la connettività Direct Link, da un VPC in ogni regione, per qualsiasi account. Questi speciali "VPC con accesso classico" utilizzano lo stesso router implicito della tua infrastruttura classica {{site.data.keyword.cloud}}.

Quando configuri un VPC per l'accesso classico, ogni host di calcolo (VSI o Bare Metal) nel tuo account classico può inviare e ricevere pacchetti dal VPC con accesso classico. Tuttavia, ricorda che firewall, gateway, ACL di rete o gruppi di sicurezza possono filtrare questo traffico. Come procedura ottimale, ti consigliamo di consentire solo il traffico necessario per il corretto funzionamento delle tue applicazioni.

## Prerequisiti:
1. Il tuo account classico deve essere collegato al tuo account IBM Cloud. Per istruzioni su come effettuare questa operazione, vedi [Collegamento degli account ID IBM](/docs/account/softlayerlink.html).
1. Il tuo account classico deve essere abilitato per VRF.
    * Se hai già Direct Link sul tuo account, sei pronto.
    * Se il tuo account non è abilitato per VRF, apri un ticket per richiedere la "Migrazione VRF" per il tuo account. Consulta l'argomento su [come poter iniziare la conversione](/docs/infrastructure/direct-link?topic=direct-link-how-you-can-initiate-the-conversion) nella nostra documentazione di Direct Link per ulteriori informazioni sul processo di conversione.

I firewall, gateway, ACL di rete o gruppi di sicurezza possono filtrare tutto o parte del traffico di rete tra le risorse classiche e VPC.
{: important}

## Crea un VPC con accesso classico
Puoi creare un VPC con funzionalità di accesso classico utilizzando l'IU (interfaccia utente), la CLI (interfaccia della riga di comando) o l'API (Application Programming Interface).

Un VPC deve essere configurato per l'accesso classico quando viene creato: non puoi aggiornare un VPC per aggiungere o rimuovere la funzionalità di accesso classico.
{: note}

### Crea un VPC con accesso classico dall'interfaccia utente

Crea un VPC con accesso classico dalla pagina **Create VPC**, facendo clic sulla casella di spunta intitolata **Enable access to classic resource**, sotto l'etichetta **Classic access**.

![iu-accesso-classico](/images/classic-access-ui.png)

### Crea un VPC con accesso classico utilizzando la CLI

Utilizza l'indicatore `--classic-access` quando crei il VPC. Ad esempio:

```
ibmcloud is vpc-create my-access-vpc --classic-access
```
{: pre}


### Crea un VPC con accesso classico utilizzando l'API

Passa il parametro `classic_access` quando crei il VPC. Ad esempio:

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "my-access-vpc",
        "classic_access": true
      }'
```
{: pre}


## Limitazioni

* Solo le tue reti private (posteriori) saranno connesse al router implicito privato del tuo account.
* Solo le sottoreti allocate con le API classiche sono connesse al lato classico del tuo router implicito privato. Le sottoreti sulle VLAN classiche non vengono instradate dal router implicito.
* Solo un VPC per regione, per ogni account, può essere abilitato per l'accesso classico.
