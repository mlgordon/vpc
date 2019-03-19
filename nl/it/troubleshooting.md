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

# Risoluzione dei problemi relativi a IBM Cloud VPC
{: #troubleshooting-your-ibm-cloud-vpc}

Questo documento analizza le difficoltà comuni che potresti incontrare e offre alcuni suggerimenti utili.

## Attivazione della modalità `TRACE` quando si utilizza la CLI

Per attivare la modalità `TRACE` (debug) quando utilizzi la CLI, imposta `IBMCLOUD_TRACE=true` prima del comando della CLI.

Ad esempio:

 ```
IBMCLOUD_TRACE=true ibmcloud is pubgws
```

## Utilizzo della modalità DEBUG o della modalità `verbose` quando si utilizza l'API

Ad esempio, puoi aggiungere `--verbose` al tuo comando `curl` e inviarci il valore `X-Request-Id:` in modo che possiamo risolvere il problema. L'indicatore `--verbose` è particolarmente utile se riscontri problemi di connettività.

Un'altra opzione è quella di aggiungere l'indicatore `-i` al tuo comando `curl` in modo che il team di supporto possa visualizzare le intestazioni nella risposta della tua richiesta. Questo indicatore è utile nella maggior parte delle situazioni in cui hai bisogno di contattare il supporto.

## Le chiamate API richiedono un token Bearer

Quando utilizzi l'API con un comando cURL, potresti dover includere "Bearer" nell'intestazione dell'autorizzazione, a seconda di ciò che si trova in `$iam_token`. Se include la parola "Bearer", non includerla di nuovo nell'intestazione. La maggior parte dei nostri esempi presuppone che "Bearer" sia incluso nell'intestazione.

## Utilizzo di un endpoint diverso per la CLI

Per modificare l'endpoint che la CLI {{site.data.keyword.cloud}} utilizza per RIAS per impostazione predefinita, imposta la variabile di ambiente `IBMCLOUD_IS_API_ENDPOINT` prima di utilizzare la CLI. Ad esempio:

```
export IBMCLOUD_IS_API_ENDPOINT=api.dev.domain.com
```
{: pre}


## Problemi comuni

Di seguito sono riportate alcune difficoltà che potresti incontrare.

### Non autorizzato (errore 401 o 403)

Il tuo account potrebbe non essere autorizzato per VPC. Assicurati di utilizzare un account che sia stato integrato.

### Impossibile creare le risorse

Se non puoi creare un VPC o altre risorse, assicurati che il proprietario dell'account ti abbia concesso le [autorizzazioni](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) corrette.

### Le istanze sono tutte in stato Sconosciuto

Assicurati che il proprietario dell'account ti abbia concesso le [autorizzazioni](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) corrette per visualizzare e gestire le istanze.

### Nessuna risposta dall'API

Se l'API non restituisce più alcun JSON, è probabile che il tuo token IAM sia scaduto e debba essere aggiornato. Accedi di nuovo a IBM Cloud oppure aggiorna il tuo token eseguendo `iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $4; }')`.

### Errore: 409 conflitto durante il richiamo di un'azione su un'istanza

Non puoi richiamare determinate azioni di istanza se lo stato della tua istanza è in conflitto con l'azione. Ad esempio, se lo stato dell'istanza è `interrotto` e provi ad eseguire un'azione di `riavvio`, il sistema restituisce un errore 409.

| stato      | azione     | conflitto |
| ----------- | ---------- | -------- |
| In esecuzione     | avvio      | sì      |
| Interrotto     | qualsiasi azione eccetto avvio  | sì      |
| Non in esecuzione | pausa      | sì      |
| Non in esecuzione | riavvio     | sì      |
| Non in pausa  | ripristino     | sì      |
| In pausa      | qualsiasi azione eccetto ripristino | sì      |


### L'istanza non risponde alla richiesta `instance-reboot`

Se la tua istanza non risponde a una richiesta `instance-reboot`, puoi provare una richiesta `instance-reset`. Puoi considerare `instance-reboot` come una richiesta soft e `instance-reset` come una richiesta hard. La richiesta `instance-reboot` invia una richiesta di riavvio del sistema operativo all'istanza, ma una richiesta `instance-reset` esegue un hard reset dell'istanza VSI. Potresti pensare alla differenza che esiste tra digitare "ctrl-alt-canc" sulla tastiera del tuo computer e premere il pulsante di ripristino o di accensione. È bene ricordare che il completamento della richiesta `instance-reset` impiega più tempo rispetto alla richiesta `instance-reboot`.

### Impossibile eliminare le risorse

Alcune operazioni, come ad esempio la creazione e l'eliminazione di VSI e la creazione e l'eliminazione di sottoreti, vengono completate in modo asincrono tramite l'API. Per questo motivo, si consiglia di eseguire il polling delle risorse che stai eliminando, per controllare l'eliminazione prima di procedere.

A causa di queste operazioni asincrone, possono essere necessari diversi minuti per eliminare le risorse dal sistema. Per facilitare l'eliminazione, è meglio procedere in questo ordine:

1. Elimina le tue istanze
2. Elimina i tuoi gateway pubblici
3. Elimina le tue sottoreti
4. Elimina i tuoi VPC
