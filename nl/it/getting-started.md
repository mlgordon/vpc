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

# Introduzione all'infrastruttura IBM Cloud Virtual Private Cloud
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

IBM accetterà un numero limitato di partecipanti a un programma di accesso anticipato per VPC a partire dall'inizio di aprile 2019, il cui utilizzo verrà esteso nei mesi successivi. Se la tua organizzazione desidera ottenere l'accesso a IBM Virtual Private Cloud, completa questo [modulo di designazione](https://cloud.ibm.com/vpc){: new_window} e un rappresentante IBM ti contatterà in merito ai passi successivi.
{: important}

Per iniziare a utilizzare l'infrastruttura {{site.data.keyword.cloud}} Virtual Private Cloud:

1. Crea un VPC (Virtual Private Cloud).
2. Crea una o più sottoreti nel VPC (Virtual Private Cloud) in una o più zone.
3. Crea un gateway pubblico (PGW) su una sottorete se vuoi che le risorse nella tua sottorete abbiano accesso a Internet o viceversa.
4. Seleziona i profili delle istanze del server virtuale (VSI) che vuoi eseguire e istanziali.
5. Riserva un indirizzo IP mobile e associalo a un'istanza del server virtuale se vuoi raggiungerla da Internet.
5. Distribuisci il tuo servizio o le tue applicazioni tra le istanze del server virtuale.

## Prerequisiti

 * **Autorizzazioni utente**: assicurati che il tuo utente disponga delle autorizzazioni sufficienti per creare e gestire le risorse nel tuo VPC. Per un elenco di autorizzazioni richieste, vedi [Concessione delle autorizzazioni necessarie per gli utenti VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).

 * **Devi avere la tua chiave SSH pronta**: utilizzerai una chiave SSH per la connessione alle tue istanze del server virtuale.

   * Ricerca un file denominato `id_rsa.pub` in una directory `.ssh` all'interno della tua directory home, ad esempio `/Users/<USERNAME>/.ssh/id_rsa.pub`. Il file inizia con `ssh-rsa` e termina con il tuo indirizzo email.

   * Oppure genera una chiave SSH: se non hai una chiave SSH pubblica o se hai dimenticato la password di una chiave esistente, generane una nuova eseguendo il comando `ssh-keygen` e seguendo le istruzioni. Ad esempio, puoi generare una chiave SSH sul tuo server Linux eseguendo il comando `ssh-keygen -t rsa -C "user_ID"`. Tale comando genera due file. La chiave pubblica generata si trova nel file `<your key>.pub`.
   
## Utilizza l'interfaccia utente, la CLI o l'API REST

Puoi eseguire il provisioning e gestire tutte le tue risorse VPC tramite l'interfaccia utente, la CLI o l'API REST.

Se sei un nuovo utente di IBM Cloud Virtual Private Cloud, scegli uno dei link sottostanti che ti guideranno nel processo di creazione del tuo IBM Cloud VPC e delle sue risorse, dall'inizio alla fine. Puoi scegliere se iniziare dall'interfaccia utente della console, dalla riga di comando (CLI) o dall'API RIAS (Regional Infrastructure Services).

* Per l'accesso tramite l'interfaccia utente, accedi alla [console IBM Cloud ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]( https://{DomainName}/vpc){: new_window}. Segui la [guida IU](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console) se hai bisogno di aiuto.
* Per utilizzare l'interfaccia della riga di comando, usa il plug-in [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) della [CLI IBM Cloud](https://console.bluemix.net/docs/cli/index.html#overview) e segui l'esempio [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli).
* Per gli utenti più avanzati, puoi chiamare direttamente le [API REST](https://{DomainName}/apidocs/rias). Segui l'esercitazione sul [codice di esempio](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis) per iniziare con le API REST.

## Passi successivi
Se sei pronto ad approfondire, vai direttamente alla documentazione dettagliata su **Rete VPC** e **VSI per VPC**:

* [**IBM Virtual Private Cloud Networking**](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**IBM Virtual Servers for Virtual Private Cloud**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

