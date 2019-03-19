---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:faq: data-hd-content-type='faq'}
{:DomainName: data-hd-keyref="DomainName"}


# Domande frequenti (FAQ)
{: #faqs}

## Qual è il limite al numero di caratteri in un nome VPC?
{:faq}

Attualmente, il limite è 100. Se questo limite viene superato, potresti ricevere un messaggio di "errore interno".

## I nomi di risorsa VPC possono iniziare con un numero?
{:faq}

No, anche se il nome può contenere numeri, deve iniziare con una lettera.

## Ci sono restrizioni su quali caratteri posso utilizzare in un nome?
{:faq}

Sì, l'IU non consente i doppi trattini, caratteri di sottolineatura e punti consecutivi nei nomi VSI.


## Durante l'assegnazione dell'IP mobile in un VPC, un cliente deve specificare la vNIC della VSI. È corretto?
{:faq}

Sì, e in effetti, deve essere l'interfaccia di rete primaria di un server.

Tuttavia, se aggiungiamo una risorsa "address" nell'API sotto l'area di rete, potremmo benissimo cambiare l'associazione dell'IP mobile con l'indirizzo piuttosto che con l'interfaccia.

## Una vNIC su un'istanza del server virtuale nel mio VPC può avere sia un IP mobile che un IP privato?
{:faq}
 
Sì.

## Nell'interfaccia utente della console IBM Cloud per VPC, c'è solo un ”interruttore" per ogni sottorete da collegare o scollegare dal gateway pubblico (PGW). Chi crea il PGW? L'impostazione predefinita di PGW sarà pronta quando un cliente desidera collegare la sottorete al PGW nell'interfaccia utente?
{:faq}

Il PGW deve essere creato esplicitamente tramite l'API così com'è ora, perché l'API richiede un'associazione esplicita di una sottorete a un particolare gateway pubblico.

## Immagina che VSI1 in un VPC abbia solo vNIC1 e che sia collegata alla Subnet1. La Subnet1 è collegata a un gateway pubblico (PGW). Un cliente può ancora assegnare un IP mobile a VSI1?
{:faq}

Sì, un server può trovarsi su una sottorete collegata a un gateway pubblico e avere anche un IP mobile. L'assegnazione dell'IP mobile a una VSI non è correlata alla presenza o meno di un gateway pubblico collegato alla sottorete. Un IP mobile associato a una VSI avrà la precedenza sul gateway pubblico collegato alla sottorete.

## Nel mio VPC, VSI1 ha 2 vNIC, chiamate vNIC1 e vNIC2. Queste due vNIC possono essere collegate alla stessa sottorete?
{:faq}
 
Sì, non ci sono limitazioni ad avere più interfacce di rete sullo stesso server collegate alla stessa sottorete. Tuttavia, al momento non sono supportate più NIC su una VSI.

## È possibile creare una VSI senza una sottorete, solo con IP mobile?
{:faq}

No.

## È possibile collegare una VSI a più di un VPC?
{:faq}

No.

## È possibile modificare la dimensione di una sottorete dopo che è stata creata in un VPC?
{:faq}

No.

## Durante la creazione del PGW, devo riservare l'IP mobile (FIP) o viene riservato automaticamente dal sistema? Vedrò tale IP mobile quando eseguo la query di tutti gli IP mobili?

Poiché la specifica è attualmente definita, RIAS crea automaticamente un IP mobile insieme al gateway pubblico se non viene specificato un IP mobile esistente. E sì, l'IP mobile verrà visualizzato nell'elenco.

## Chi impone l'esistenza di un solo gateway pubblico per zona per un VPC?
{: faq}

Il RIAS (Regional Infrastructure API Service) applica questo limite.

## In che modo VRF influisce sulle mie altre funzionalità di rete e sulle mie sottoreti?
{:faq}

Avvertimenti per le VLAN e VRF:

* Lo spanning della VLAN tra gli account non è consentito nell'ambiente VRF.
* Il servizio VPN IPSec è limitato.

**Nota:** VRF non impedisce l'accesso SSL o VPN PPTP, ma il suo comportamento cambia. Senza VRF, una connessione VPN è sufficiente per visualizzare tutti i server sul tuo account. Con VRF, puoi accedere solo alle risorse nel mercato associato alla tua VPN. Per cui se ti connetti alla VPN DAL, puoi connetterti solo a server DAL.

## Qual è il modo corretto di usare il sottocomando `instance-network-interface-floating-ip-add` in VPC? Si crea/alloca in anticipo un indirizzo IP mobile?
{:faq}

 Devi prima allocare un IP mobile e quindi fornire l'indirizzo FIP sul comando `add` dell'IP mobile dell'interfaccia.

 Ad esempio: `ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE | --nic NIC_ID)`. Fornisci la zona.

 ## Perché devo specificare una sottorete quando configuro la mia VPN per VPC e cosa devo specificare?
 {:faq}

Quando configuri un gateway VPN, devi specificare una sottorete in modo che il gateway VPN possa ottenere gli indirizzi IP necessari per il servizio VPN. Specificando la sottorete, mantieni il controllo su come viene gestito il traffico VPN e hai la flessibilità di specificare un'ubicazione più vicina alle risorse che utilizzano la VPN. In questo modo, puoi ridurre la latenza e migliorare le prestazioni. 

## Sono previsti addebiti per la larghezza di banda in uscita per il traffico da VPC a COS?
{:faq}

Non ci sono addebiti per la larghezza di banda in uscita fintanto che l'endpoint ADN viene utilizzato per la connessione da VPC a COS, ma gli addebiti delle chiamate API continuano ad essere applicati.

## Come faccio a sapere dove verranno distribuite le mie istanze del programma di bilanciamento del carico?
{:faq}

Le sottoreti scelte determinano dove verrà distribuito il programma di bilanciamento del carico di VPC. Il programma di bilanciamento del carico di VPC è una risorsa regionale. La procedura ottimale è quella di scegliere sottoreti da zone diverse in una determinata regione per aumentare la ridondanza
