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

# Assegnazione dell'accesso basato sui ruoli alle risorse VPC
{: #assigning-role-based-access-to-vpc-resources}

Gli amministratori di account possono utilizzare le _politiche_ di autorizzazione, che controllano l'accesso alle _risorse_ in base al _ruolo_ di un singolo utente. Le politiche possono anche essere applicate per:

(1) l'autorizzazione di un gruppo di utenti, denominato _gruppo di accesso_,

(2) le caratteristiche assegnate di una singola _risorsa_ oppure

(3) una raccolta di risorse denominata _gruppo di risorse_.

Le autorizzazioni per le risorse e le autorizzazioni per gli utenti possono essere assegnate indipendentemente l'una dall'altra.

Per ulteriori informazioni sulla creazione di utenti, gruppi di accesso utente, gruppi di risorse e politiche, fai riferimento a [Informazioni sulle risorse](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources).

## Controllo dell'accesso basato su IAM

In generale, le pratiche di autorizzazione e gestione delle risorse di {{site.data.keyword.cloud}} Virtual Private Cloud si coordinano con i servizi IBM Cloud IAM (Identity and Access Management). Per ulteriori informazioni su IAM, gruppi di risorse e gruppi di accesso in generale, fai riferimento a questi documenti IBM Cloud:

* [IBM Cloud IAM](https://{DomainName}/docs/iam/quickstart.html#getstarted)
* [Gruppi di risorse](https://{DomainName}/docs/overview/resource-groups.html#whatis)
* [Gruppi di accesso](https://{DomainName}/docs/overview/manageaccess.html#cloudaccess)

Alcune funzioni del servizio IBM Cloud IAM sono state personalizzate per l'utilizzo in IBM Cloud VPC. Il documento [Informazioni sulle risorse](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources) fornisce ulteriori dettagli sulle politiche di autorizzazione IAM man mano che vengono applicate in VPC.

Per riepilogare, puoi assegnare autorizzazioni basate su IAM in base a:

* singoli utenti
* gruppi di accesso (gruppi di utenti)
* specifici tipi di risorse
* gruppi di risorse

## Assegnazione delle autorizzazioni utente

Per gli utenti, l'accesso viene controllato assegnando ruoli IAM definiti dal sistema:

*  Amministratore
* Editor
* Operatore
* Visualizzatore

Di seguito è riportata una tabella che mostra la corrispondenza tra ciascun ruolo utente e il tipo di controllo che consente per i VPC:

| Nome ruolo | Tipo di accesso consentito |
|-----------|-------------------------|
| Visualizzatore | Visualizza il VPC, Elenca i VPC  |
| Editor | Visualizza il VPC, Elenca i VPC, Crea i VPC, Elimina i VPC, Aggiorna i VPC |
| Operatore | Visualizza il VPC, Elenca i VPC  |
| Amministratore|Visualizza il VPC, Elenca i VPC, Crea i VPC, Elimina i VPC, Aggiorna i VPC, Assegna politiche ad altri utenti.|


## Passi successivi

Per istruzioni dettagliate sulla concessione di autorizzazioni basate sui ruoli agli utenti per determinate attività, fai riferimento all'argomento [Gestione delle autorizzazioni utente per le risorse VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
