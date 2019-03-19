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

# Limitazioni note
{: #known-limitations}

Questo documento contiene brevi descrizioni di bug noti nella release corrente, descrizioni di funzioni e API non supportate e indicazioni su quali funzioni sono ora disponibili solo come servizi Beta. Le limitazioni note possono cambiare man mano che aggiungiamo funzionalità a {{site.data.keyword.cloud}} Virtual Private Cloud, per cui sentiti libero di ricontrollare questo documento di tanto in tanto. 

## Bug noti

* Se rinomini una sottorete, potrebbe essere necessario attendere fino a 1 ora per vedere il nuovo nome della sottorete nella pagina dei dettagli del server, a causa della sincronizzazione della cache. (#758)

## Riepilogo delle funzioni non supportate

* L'accesso Direct Link a Virtual Private Cloud è supportato solo tramite l'[**Accesso classico**](/docs/infrastructure/vpc/classic-access.html).
* Per Virtual Private Cloud è disponibile un sottoinsieme di endpoint di servizi privati, non sono disponibili tutti gli endpoint. 
* Il salvataggio e ripristino delle immagini non è supportato.

## API non supportate

Per i dettagli su ciò che è supportato, consulta la [specifica API](https://{DomainName}/apidocs/rias).

Le seguenti API non sono supportate in questa release.

| Componente | Funzioni | Commenti |
|------|------|--------|
| **Calcolo:** |   |   |
| Immagini | Creazione/Eliminazione non supportate | Ubuntu 16.04, CentOS 7.X, Windows 08, Debian|
| Interfacce_rete | Richiamo (no creazione, eliminazione, aggiornamento) | |
| Interfacce_volume | Non supportato |   |
| Velocità_porta | | Solo 100 e 1000 |
| **Archiviazione:** |   |   |
| Volumi | Non supportato |   |
| Istantanee | Non supportato |  |

## Funzioni e casi di utilizzo non ancora supportati

Questa sezione fornisce un elenco dettagliato delle funzioni e dei casi di utilizzo non supportati. 

* Un VPC (Virtual Private Cloud) non può essere associato ad altri VPC.
* Le VSI o i server bare metal IBM Cloud esistenti non possono essere migrati in un VPC.
* Non è possibile aggiungere rotte personalizzate a un VPC. Tutte le sottoreti in un Virtual Private Cloud possono comunicare tra loro per impostazione predefinita.
* IBM Cloud VPC non supporta domini multicast o broadcast.
* IBM Cloud VPC non fornisce la crittografia end-to-end. 
* Ecco i principali servizi IBM Cloud che possono essere utilizzati da Virtual Private Cloud. Gli altri servizi non sono accessibili. 
  * NTP
  * Registrazione
  * Resolver DNS
* Una sottorete non può trovarsi in più zone.
* Una sottorete non può essere spostata da una zona all'altra.
* Le sottoreti non possono essere ridimensionate dopo la loro creazione.
* I server bare metal non possono essere forniti in un Virtual Private Cloud.
* Le risorse IBM Cloud Classic non possono essere nella stessa sottorete in un Virtual Private Cloud. La connettività tra le risorse classiche e un Virtual Private Cloud nel tuo account è possibile utilizzando l'[**Accesso classico**](/docs/infrastructure/vpc/classic-access.html).
* IPv6 non è supportato.
* Non puoi utilizzare il tuo IP pubblico come IP mobile. Il pool di IP mobili è fornito da IBM.
* Un IP mobile è associato a una zona. Ad esempio, un IP mobile riservato da un pool nella Zona 1 non può essere assegnato a una VSI nella Zona 2 nello stesso VPC.
* Gli indirizzi IP privati non possono essere spostati tra le VSI.
* Le interfacce di rete non possono essere spostate tra le VSI.
* Non puoi designare l'indirizzo IP specifico della VSI. Puoi specificare solo l'intervallo IP per la sottorete. Dopo aver collegato una VSI a una sottorete, il sistema assegna un IP privato da quella sottorete.
* IBM Cloud VPC viene fornito con i propri strumenti Network as a Service quali LBaaS, ACL e gruppi di sicurezza. Non puoi utilizzare i tuoi dispositivi di rete (ad esempio, un gateway Vyatta o altri programmi di bilanciamento del carico) per controllare le risorse nel Virtual Private Cloud. Analogamente, non puoi utilizzare i tuoi propri servizi di bilanciamento del carico o di gruppi di sicurezza nell'infrastruttura classica IBM Cloud per controllare le risorse in IBM Cloud VPC.
* Il gateway pubblico non consente l'avvio del traffico da Internet a una VSI in IBM Cloud VPC. A tale scopo, deve essere utilizzato un IP mobile.
* ACL è senza stato, quindi il traffico di ritorno deve essere consentito esplicitamente nelle regole ACL.

## Componenti o funzioni disponibili come servizi Beta

* **VPN for IBM Cloud VPC** è disponibile solo come servizio Beta.
* **LBaaS for IBM Cloud VPC** è disponibile solo come servizio Beta.
