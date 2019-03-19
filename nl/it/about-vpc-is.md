---
copyright:
  years: 2017, 2019
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

# Informazioni sull'infrastruttura di IBM Cloud Virtual Private Cloud (VPC)
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

{{site.data.keyword.cloud}} VPC fa parte della prossima generazione della piattaforma IBM One Cloud, che ridefinisce gli standard di settore tradizionali per prestazioni, crescita dei servizi, flessibilità e libertà di distribuzione.

Un VPC (Virtual Private Cloud) ti offre un punto di ingresso conveniente che fornisce la sicurezza cloud e la possibilità di ridimensionare dinamicamente in un cloud pubblico. Offre un controllo dettagliato sulla tua infrastruttura virtuale e sulla segmentazione del traffico di rete.

## Spazio privato in un cloud pubblico
IBM Cloud VPC offre un ambiente isolato e totalmente sicuro all'interno del cloud pubblico. Ti dà la sicurezza di un cloud privato, con l'agilità e la facilità di un cloud pubblico.

 * Puoi gestire i principali servizi di rete e avviare i server virtuali secondo necessità per supportare le tue applicazioni di importanza critica, a tolleranza cloud e native del cloud.
 * Puoi definire le tue politiche di rete progettate per la sicurezza e l'accesso pratico.
 * Puoi eseguire il provisioning delle tue risorse e connetterle tra loro oppure puoi isolarle l'una dall'altra.

### Isolamento logico
IBM Cloud Virtual Private Cloud (VPC) offre alle tue applicazioni un isolamento logico da altre reti in tutte le regioni, fornendo al contempo scalabilità e sicurezza.

Per rendere possibile questo isolamento logico, il VPC è suddiviso in sottoreti, utilizzando un intervallo di indirizzi IP privati. Tuttavia, per impostazione predefinita, tutte le risorse (come le VSI) all'interno dello stesso Virtual Private Cloud possono comunicare tra loro, indipendentemente dalla loro sottorete. Le sottoreti sono contenute in una singola zona e non possono estendersi su più zone, il che aiuta con la sicurezza, con la riduzione della latenza e con il ripristino di emergenza.

### Provisioning rapido di istanze e sicurezza

Crea rapidamente istanze del server virtuale (VSI), utilizzando profili predefiniti ottimizzati per i tuoi carichi di lavoro specifici. Proteggi le tue istanze con i gruppi di sicurezza.

### Funzionalità di rete
IBM Cloud VPC offre funzionalità di rete complete, compresa la selezione dell'intervallo di indirizzi IP, firewall virtuali (gruppi di sicurezza e ACL di rete), reti private virtuali (VPN) site-to-site e bilanciamento del carico (LBaaS) con elasticità.

 * Puoi configurare automaticamente la tua topologia virtuale, utilizzando gli intervalli di prefissi consigliati e le politiche di rete preconfigurate.
 * Puoi personalizzare il tuo IBM Cloud VPC e adattarlo facilmente alle tue esigenze in continua evoluzione.
 * Puoi portare il tuo intervallo IP.
 * Puoi assegnare un IP mobile da un pool pre-esistente.
 * Il bilanciamento del carico e la VPN hanno piani di controllo multiregione, il che significa che ogni regione in cui viene distribuito il piano di controllo può supportare tutte le regioni per le istanze del server virtuale del cliente. Un guasto in una singola regione non inciderà sul servizio nelle altre regioni.

### Connettività globale
Puoi estendere le tue applicazioni e le risorse disponibili per l'espansione in più regioni. Utilizzando la VPN, puoi creare connessioni private ad altri progetti e ad altre parti delle tue distribuzioni cloud ibride.

### Sicurezza di rete
La sicurezza è integrata nel tuo IBM Cloud VPC, con gruppi di sicurezza che fungono da firewall virtuali per la protezione a livello di istanza e con elenchi di controllo accessi (ACL) di rete per la protezione a livello di sottorete.

### Bilanciamento del carico
All'interno del tuo IBM Cloud VPC, utilizza il bilanciamento del carico per distribuire il traffico di rete su una serie di destinazioni per migliorare le prestazioni e l'HA. I programmi di bilanciamento del carico monitorano inoltre l'integrità delle tue applicazioni e dei tuoi servizi. Puoi configurare un programma di bilanciamento del carico per distribuire il traffico dell'applicazione in entrata tra le istanze in una singola zona o tra più zone all'interno di una regione.

### Accesso a Internet
Sono disponibili due opzioni per abilitare le comunicazioni dalle tue istanze del server virtuale (VSI) all'Internet pubblica:
* Utilizza un gateway pubblico (PGW) per abilitare la comunicazione per tutte le istanze del server virtuale sulla sottorete collegata. Non vi è alcun addebito per l'utilizzo di un PGW, fatta eccezione per la larghezza di banda utilizzata.
* Utilizza un IP mobile (FIP) per abilitare la comunicazione da una singola istanza del server virtuale (VSI).

![IBM Cloud VPC](images/vpc-experience.png)
**Figura: un esempio di configurazione di IBM Cloud VPC**

## Supporto dei carichi di lavoro nativi del cloud

Un Virtual Private Cloud è ideale per i carichi di lavoro nativi del cloud e per collegare la tua infrastruttura esistente in IBM Cloud. Puoi creare il miglior cloud per tutti i tuoi carichi di lavoro importanti come i calcoli cognitivi, AI e Machine Learning. Al tempo stesso, puoi continuare a utilizzare IBM Cloud Classic per i carichi di lavoro tradizionali, secondo le esigenze.

Ecco alcuni modi in cui VPC supporta i tuoi carichi di lavoro ibridi, a tolleranza cloud e nativi del cloud:

 * Crea e gestisci ambienti applicativi isolati tramite un'API
 * Progetta topologie di rete con BYOIP (Bring Your Own IP)
 * Utilizza i gruppi di sicurezza e gli elenchi di controllo accessi (ACL) di rete per consentire topologie flessibili basate su API
 * Le zone di disponibilità consentono connessioni ad alta velocità e bassa latenza tra le regioni, con HA
 * Ridimensionamento automatico
   * Ridimensionamento incrementale o decrementale di migliaia di server al giorno
   * Utilizza il bilanciamento del carico scalabile e affidabile con la gestione dei certificati
   * Stabilisci un monitoraggio scalabile e affidabile
   * Mantieni l'illusione di una capacità infinita per i tuoi clienti
 * Utilizza dispositivi di rete e di archiviazione ad alta velocità
 * Consenti servizi Always On (piano di controllo)
 * Copri più regioni per il ripristino di emergenza e la resilienza
 * Fornisci e utilizza servizi core: IPAM, VPN, firewall, SSH, DNS e bilanciamento del carico L4
 * Configura altri servizi: ridimensionamento automatico, CDN, NFV di terze parti
 * Consenti il provisioning rapido di VSI con affinità e anti-affinità
 * Utilizza la gestione flessibile delle immagini con immagini pre-memorizzate
 * Fornisci supporto per le GPU

## Riepilogo dei vantaggi

 * Inizio rapido utilizzando configurazioni predefinite per le tue istanze, chiamate profili
 * Ambito geografico flessibile con zone e regioni disponibili a livello globale
 * Interamente protetto, con ACL e gruppi di sicurezza
 * Facilmente scalabile e condivisibile, una rete VPC e le risorse possono estendersi dalla tua installazione in loco al cloud
 * Monitora i tuoi carichi di lavoro per prestazioni ed efficienza ottimali

## Riepilogo delle funzioni

  * Crea sottoreti e porta il tuo intervallo IP
  * Crea e gestisci le istanze del server virtuale (VSI) utilizzando Ubuntu 16.04, CentOS 7.x, Windows o Debian
  * Riserva e associa un IPv4 mobile
  * Ottieni l'accesso Internet alle sottoreti creando un gateway pubblico (PGW), uno per zona
  * Crea e assegna gruppi di sicurezza alle tue VSI
  * Utilizza gli elenchi di controllo accessi (ACL) di rete per garantire la sicurezza per le tue sottoreti
  * VSI in single-homing, utilizzando una scheda di interfaccia di rete virtuale (vNIC)
  * Istanze del server virtuale (VSI) con più vNIC in multi-homing
  * Distribuzione di zone, nella regione Stati Uniti Sud o nella regione FRA
  * Accesso a Internet tramite VPN
  * Bilanciamento del carico (LB) nativo di VPC

## Avvertimenti su BYOIP

Puoi utilizzare il tuo intervallo di indirizzi IPv4 pubblici (BYOIP) per il tuo account IBM Cloud VPC. Quando utilizzi BYOIP, IBM Cloud deve configurare questi indirizzi IPv4 sulle risorse IBM Cloud, che invieranno pacchetti da e verso gli indirizzi che hai fornito. Pertanto, in seguito all'utilizzo del tuo intervallo IPv4 fornito su IBM Cloud, tali indirizzi IP possono essere esposti a terze parti e allo staff di supporto di IBM come parte del tuo utilizzo di questo servizio.
{: important}

Per utilizzare BYOIP, devi usare l'API o la CLI. Questa funzionalità avanzata non è disponibile tramite l'interfaccia utente della console IBM Cloud.
{: note}

Per un elenco completo delle limitazioni note e delle funzioni non attualmente supportate, fai riferimento al documento [Limitazioni note](/docs/infrastructure/vpc?topic=vpc-known-limitations).

## Ulteriori informazioni

* [**Terminologia di IBM VPC**](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**Sicurezza di IBM VPC**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**Regioni e sottoreti IBM VPC disponibili**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**Creazione e gestione delle risorse di rete in VPC**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [**Creazione e gestione delle istanze del server virtuale**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
