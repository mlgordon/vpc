---

copyright:

  years: 2018, 2019

lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}

# Messaggi di errore dell'API IBM Cloud Virtual Private Cloud
{: #rias-error-messages}

Quando ricevi un messaggio di errore dalle API {{site.data.keyword.cloud}} Virtual Private Cloud, puoi utilizzare l'ID messaggio per trovare ulteriori informazioni su come risolvere il problema.
{:shortdesc}

## acl_in_use
**Messaggio**: non è possibile eliminare l'ACL di rete perché è collegato alle risorse.

Non è possibile eliminare l'ACL di rete perché è collegato alle risorse. Prova a controllare le tue sottoreti.

## address_prefix_conflict
**Messaggio**: il prefisso dell'indirizzo con questo CIDR è in uso.

Il CIDR per il prefisso dell'indirizzo richiesto è in conflitto con un prefisso di indirizzo esistente.

## address_prefix_in_use
**Messaggio**: impossibile eliminare un prefisso di indirizzo in uso.

Una o più sottoreti stanno utilizzando il prefisso dell'indirizzo. Devi scollegare tutte le sottoreti prima di poter eliminare un prefisso.

## backend_service_unavailable
**Messaggio**: il servizio di back-end non è disponibile.

Un servizio cloud di back-end non è riuscito a rispondere. Una causa per la ricezione di questo errore potrebbe essere un token IAM mancante o scaduto. Riprova tra qualche minuto. Se il problema persiste, contatta il supporto.

## bad_field
**Messaggio**: è necessario fornire l'UUID istanza corretto

È necessario fornire il nuovo nome del volume

Prova di nuovo, fornendo un UUID o un volume valido nella tua richiesta. 

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## bad_request                                   
**Messaggio**: le informazioni fornite non erano valide, non erano corrette o mancava un campo obbligatorio.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## classic_access_vpc_conflict_duplicate_res
**Messaggio**: è possibile creare un solo VPC con accesso classico.

Non è possibile creare più di un VPC con accesso classico per un account

## default_address_prefix_not_found
**Messaggio**: prefisso dell'indirizzo predefinito non trovato.

Potresti visualizzare questo messaggio di errore quando il prefisso dell'indirizzo predefinito non viene trovato.

## duplicate_error
**Messaggio**: l'input fornito esiste già.

La risorsa che hai specificato esiste già. Per risolvere questo problema, utilizza un nome diverso per la risorsa che vuoi creare. Ad esempio, quando crei un nuovo VPC, puoi riesaminare un elenco di nomi per i VPC già creati e scegliere un nome che non sia in conflitto, se prima chiami `get VPC` utilizzando l'ID come in questo esempio:`GET "/v1/vpcs/{id}” -H  "accept: application/json"`. 

## floating_ip_in_use
**Messaggio**: l'IP mobile è in uso.

Questo IP mobile è già associato a un'interfaccia di rete o a un gateway pubblico.

## floating_ip_not_empty
**Messaggio**: impossibile eliminare un server con un IP mobile associato.

Assicurati di disassociare l'IP mobile prima di eliminare il server. 

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## gateway_too_many
**Messaggio**: è possibile avere solo un gateway pubblico per zona in un VPC.

È consentito un solo gateway pubblico per zona in un VPC, ma l'unico gateway pubblico può essere collegato a più sottoreti nella zona. Per trovare il gateway pubblico per una zona, esegui l'API GET public_gateways e osserva i valori "vpc" e "zone". Se utilizzi la CLI, puoi eseguire il comando `ibmcloud is public-gateways` e osservare i valori "VPC" e "Zone".

Utilizza l'ID del gateway pubblico per collegarlo a una sottorete; vedi un esempio nei nostri [esempi API](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis#step-13-attach-the-public-gateway-to-the-subnet-). Se utilizzi la CLI, puoi utilizzare il comando di aggiornamento della rete per collegarlo a un gateway pubblico, ad esempio `ibmcloud is subnet-update SUBNET_ID --public-gateway-id PUBLIC_GATEWAY_ID`.


## http_request_size_exceeded                    
**Messaggio**: la richiesta HTTP è troppo grande.

Questo problema si verifica quando il payload che hai inviato nella tua richiesta ha troppi caratteri. Prova di nuovo con un payload più piccolo. Ad esempio, anziché cercare di fare tutto in una singola richiesta, prova a creare una risorsa minima in una richiesta e quindi ad aggiungerne lo stato in modo incrementale in diverse richieste successive. 

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## iam_failure
**Messaggio**: nessuno

Questo messaggio può essere visualizzato quando si produce un errore nel servizio IAM, verificando l'autenticazione o l'autorizzazione. Questa interruzione del servizio IAM può essere temporanea. Riprova la richiesta dopo qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policies_quota_exceeded
**Messaggio**: la quota per le politiche IKE è stata superata per l'account.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le politiche IKE correnti, utilizza l'API `GET /ike_policies`.

## ike_policy_duplicate_name
**Messaggio**: il nome `<ike_policy_name>` è già utilizzato dalla politica IKE `<ike_policy_id>`.

Fornisci un nome di politica IKE diverso. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policy_in_use
**Messaggio**: la politica IKE `<ike_policy_id>` è utilizzata da una o più connessioni.

Una politica IKE non può essere eliminata se è utilizzata da una o più connessioni.

## ike_policy_invalid_name
**Messaggio**: il nome `<ike_policy_name>` non è un nome di politica IKE valido.

Un nome di politica IKE valido inizia con una lettera, seguita da lettere, cifre, caratteri di sottolineatura o trattini.

## ike_policy_not_found
**Messaggio**: la politica IKE `<ike_policy_id>` non è stata trovata.

Hai fatto riferimento a una politica IKE che non esiste. Riesamina la tua richiesta per assicurarti di aver specificato l'ID della politica IKE corretto. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## insufficient_space_for_subnet
**Messaggio**: spazio insufficiente per la sottorete nel prefisso dell'indirizzo

Potresti ottenere questo errore se tenti di creare una sottorete e la sottorete non può essere creata perché non è possibile allocare il numero di indirizzi richiesti.

## internal_error
**Messaggio**: si è verificato un errore interno.

Riprova. Se l'errore persiste, contatta il supporto.

## internal_server_error
**Messaggio**: nessuno

Questo errore si verifica quando il servizio rileva un errore imprevisto. Questo problema può essere temporaneo. Prova di nuovo la richiesta tra qualche minuto.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## internal_solution
**Messaggio**: contatta il tuo amministratore.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_id_format
**Messaggio**: formato ID errato. Assicurati che il formato sia corretto.

Assicurati che l'ID che hai fornito non contenga dati non corretti.

Potresti ottenere questo messaggio di errore se viene utilizzata una query di avvio non valida quando effettui una richiesta di impaginazione. Ad esempio,
`GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` contiene due `?`. Correggi la query e riprova.

## invalid_state
**Messaggio**: nessuno

Il comando RIAS `ibmcloud is in-reboot Instance_uuid` può restituire il codice messaggio "invalid_state"

In un caso, il messaggio viene generato quando viene tentata un'operazione di riavvio mentre la VSI è già in fase di riavvio. Questo messaggio può essere ricevuto anche nel caso in cui non si verificano più riavvii contemporaneamente.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_version
**Messaggio**: il parametro `version` non è valido, deve essere nel formato `YYYY-MM-DD`.

La versione deve essere conforme al formato _YYYY-MM-DD_. Per i mesi o le date a una sola cifra, ad esempio il 1° gennaio, la versione deve essere simile a `2019-01-01`. Il parametro della versione deve essere presente nell'URL. La data indicata nel parametro della versione deve essere successiva al 2019-01-01 e anteriore alla data corrente. Ad esempio, per ottenere un elenco di VPC, aggiungi la versione alla fine della richiesta `GET "/v1/vpcs?version=2019-01-01”`.

## invalid_version_range
**Messaggio**: il valore `version` non può essere impostato in una data futura né prima di `2019-01-01`.

La versione deve essere conforme al formato _YYYY-MM-DD_. Per i mesi o le date a una sola cifra, ad esempio il 1° gennaio, la versione deve essere simile a `2019-01-01`. Il parametro della versione deve essere presente nell'URL. La data indicata nel parametro della versione deve essere successiva al 2019-01-01 e anteriore alla data corrente. Ad esempio, per ottenere un elenco di VPC, aggiungi la versione alla fine della richiesta `GET "/v1/vpcs?version=2019-01-01”`.

## invalid_zone
**Messaggio**: controlla se le risorse che stai richiedendo si trovano nella stessa zona.

Potresti visualizzare questo messaggio se la risorsa richiesta non si trova in una zona valida.

## ipsec_policies_quota_exceeded
**Messaggio**: la quota per le politiche IPsec è stata superata per l'account.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le politiche IPsec correnti, utilizza l'API `GET /ipsec_policies`.

## ipsec_policy_duplicate_name
**Messaggio**: il nome `<ipsec_policy_name>` è già utilizzato dalla politica IPsec `<ipsec_policy_id>`.

Fornisci un nome di politica IPsec diverso. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ipsec_policy_in_use
**Messaggio**: la politica IPsec `<ipsec_policy_id>` è utilizzata da una o più connessioni.

Una politica IPsec non può essere eliminata se è utilizzata da una o più connessioni.

## ipsec_policy_invalid_name
**Messaggio**: il nome `<ipsec_policy_name>` non è un nome di politica IPsec valido.

Un nome di politica IPsec valido inizia con una lettera, seguita da lettere, cifre, caratteri di sottolineatura o trattini.

## ipsec_policy_not_found
**Messaggio**: la politica IPsec `<ipsec_policy_id>` non è stata trovata.

Hai fatto riferimento a una politica IPsec che non esiste. Riesamina la tua richiesta e assicurati di aver specificato l'ID della politica IPsec corretto. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## key_exists
**Messaggio**: esiste già lo stesso contenuto chiave.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## listener_certificate_not_found
**Messaggio**: istanza del certificato con CRN `<listener_certificate_crn>` non trovata o nessuna autorizzazione per accedere all'istanza del certificato.

Fornisci un CRN di istanza del certificato esistente o chiedi al tuo amministratore dell'account di concederti le autorizzazioni di accesso all'istanza del certificato fornita.

## listener_duplicate_port
**Messaggio**: la porta `<listener_port>` è utilizzata da un'altra istanza del listener. Scegli un'altra porta.

Scegli un'altra porta.

## listener_invalid_certificate
**Messaggio**: il CRN dell'istanza del certificato per il listener HTTPS non è valido.

Fornisci un CRN dell'istanza del certificato valido.

## listener_invalid_connection_limit
**Messaggio**: il limite di connessione con il listener `<listener_connection_limit>` non è valido.

Fornisci un limite di connessione valido. Il limite di connessione deve essere un numero intero compreso tra 1 e 15000.

## listener_invalid_port
**Messaggio**: la porta del listener `<listener_port>` non è valida.

Scegli un'altra porta.

## listener_invalid_protocol
**Messaggio**: il protocollo del listener `<listener_protocol>` non è valido.

Fornisci un protocollo del listener valido. I valori accettabili per il protocollo del listener sono `http`, `https` e `tcp`.

## listener_missing_certificate_crn
**Messaggio**: manca il CRN dell'istanza del certificato per il listener `https`.

Il CRN dell'istanza del certificato è un campo obbligatorio.

## listener_missing_port
**Messaggio**: manca la porta del listener.

La porta del listener è un campo obbligatorio.

## listener_missing_protocol
**Messaggio**: manca il protocollo del listener.

Il protocollo del listener è un campo obbligatorio. Fornisci un protocollo del listener nella tua richiesta. I valori accettabili sono `http`, `https` e `tcp`.

## listener_not_found
**Messaggio**: listener con ID `<listener_id>` non trovato.

Fornisci un ID listener esistente.

## listener_over_quota
**Messaggio**: impossibile creare il listener. La quota di listener per la risorsa del programma di bilanciamento del carico ha raggiunto il limite massimo.

Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## listener_pool_protocols_conflict
**Messaggio**: il protocollo del listener (`<listener_protocol>`) e il protocollo del pool (`<pool_protocol>`) sono in conflitto.

Un listener con il protocollo `https` o `http` può essere associato solo a un pool con il protocollo `http`. Allo stesso modo, un listener `tcp` può essere associato solo a un pool `tcp`.

## listener_reserved_port_conflict
**Messaggio**: la porta del listener `<listener_port>` è una delle porte riservate. L'intervallo di porte compreso tra 56500 e 56520 è riservato per scopi di gestione. Scegli un'altra porta.

Scegli un'altra porta.

## load_balancer_duplicate_name
**Messaggio**: il nome `<load_balancer_name>` è utilizzato da un'altra istanza del programma di bilanciamento del carico. Scegli un altro nome.

Fornisci un nome diverso per l'istanza del programma di bilanciamento del carico.

## load_balancer_invalid_description
**Messaggio**: la descrizione del programma di bilanciamento del carico `<load_balancer_description>` non è valida.

La descrizione del programma di bilanciamento del carico non può superare i 255 caratteri.

## load_balancer_invalid_is_public
**Messaggio**: il valore di is_public `<load_balancer_is_public>` non è valido.

Il valore is_public del programma di bilanciamento del carico deve essere true o false.

## load_balancer_invalid_is_public_value
**Messaggio**: sono supportati solo i programmi di bilanciamento del carico pubblici.

I programmi di bilanciamento del carico privati non sono ancora supportati.

## load_balancer_invalid_name
**Messaggio**: il nome `<load_balancer_name>` non è valido.

Il campo Nome non può essere vuoto. La lunghezza del nome non deve superare i 40 caratteri. Un nome di programma di bilanciamento del carico valido inizia con una lettera seguita da lettere, cifre e caratteri di sottolineatura.

## load_balancer_missing_is_public
**Messaggio**: manca il campo 'is_public'.

'is_public' è un campo obbligatorio. Fornisci il campo is_public del programma di bilanciamento del carico.

## load_balancer_missing_name
**Messaggio**: manca il nome del programma di bilanciamento del carico.

Fornisci il nome del programma di bilanciamento del carico. Il nome del programma di bilanciamento del carico è un campo obbligatorio.

## load_balancer_missing_subnets
**Messaggio**: mancano le sottoreti del programma di bilanciamento del carico.

Il valore delle 'sottoreti' è un campo obbligatorio. Fornisci le sottoreti in cui creare il programma di bilanciamento del carico nella tua richiesta.

## load_balancer_not_found
**Messaggio**: programma di bilanciamento del carico con ID `<load_balancer_id>` non trovato.

Fornisci un ID di programma di bilanciamento del carico esistente.

## load_balancer_over_quota
**Messaggio**: impossibile creare il programma di bilanciamento del carico. La quota di istanze del programma di bilanciamento del carico nel tuo account ha raggiunto il limite massimo.

Elimina un programma di bilanciamento del carico esistente o contatta il supporto per aumentare la quota del programma di bilanciamento del carico sul tuo account.

Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## load_balancer_unchanged_update
**Messaggio**: non c'è nulla per aggiornare il programma di bilanciamento del carico con ID `<load_balancer_id>`.

Non c'è nulla per aggiornare il programma di bilanciamento del carico.

## member_invalid_port
**Messaggio**: la porta del membro specificata `<member_port>` non è valida.

Fornisci un numero di porta valido. Un numero di porta valido è compreso tra 1 e 65535.

## member_invalid_weight
**Messaggio**: il peso del membro specificato `<member_weight>` non è valido.

Fornisci un peso del membro valido. Deve essere un numero intero compreso tra 0 e 100.

## member_missing_address
**Messaggio**: manca l'indirizzo del membro.

L'indirizzo del membro è un campo obbligatorio. Fornisci l'indirizzo del membro nella tua richiesta.

## member_missing_protocol_port
**Messaggio**: manca la porta del membro.

La porta del membro è un campo obbligatorio. Fornisci la porta del membro nella tua richiesta.

## member_over_quota
**Messaggio**: impossibile creare il membro. La quota di istanze del membro nel pool ha raggiunto il limite massimo.

Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## missing_ims_account_id
**Messaggio**: nessuno

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## missing_version
**Messaggio**: il parametro `version` è obbligatorio e deve essere nel formato `YYYY-MM-DD`.

La versione deve essere conforme al formato _YYYY-MM-DD_. Per i mesi o le date a una sola cifra, ad esempio il 1° gennaio, la versione deve essere simile a `2019-01-01`. Il parametro della versione deve essere presente nell'URL. La data indicata nel parametro della versione deve essere successiva al 2019-01-01 e anteriore alla data corrente. Ad esempio, per ottenere un elenco di VPC, aggiungi la versione alla fine della richiesta `GET "/v1/vpcs?version=2019-01-01”`.cs?version=2019-01-01”`

## network_conflict
**Messaggio**: CIDR in conflitto con il prefisso dell'indirizzo esistente in VPC

Potresti visualizzare questo messaggio se fornisci un CIDR di rete che è in conflitto con un CIDR di rete esistente nello stesso spazio IP.

## not_authorized                               
**Messaggio**: la richiesta non è autorizzata.

Un motivo comune per cui potresti visualizzare questo errore è se il tuo token IAM manca o è scaduto. Per istruzioni su come generare un token, fai riferimento a [Creazione di un VPC utilizzando le API REST](/docs/infrastructure/vpc/example-code.html#creating-a-vpc-using-the-rest-apis). Se il token non è scaduto, potresti dover verificare le tue autorizzazioni e contattare l'amministratore. 

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_found
**Messaggio**: controlla se la risorsa che stai richiedendo esiste.

Hai fatto riferimento a una risorsa che non esiste o a cui non hai accesso. Riesamina la tua richiesta per assicurarti di aver specificato gli ID e i riferimenti corretti.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_implemented
**Messaggio**: nessuno

Il metodo non è implementato.

## not_in_address_prefix
**Messaggio**: il CIDR fornito non è adatto ai prefissi dell'indirizzo nella zona fornita.

Questo errore si verifica se un utente tenta di creare una sottorete con un CIDR che non rientra in alcun prefisso dell'indirizzo per la zona specificata.

Esegui GET /vpcs/{vpc_id}/address_prefixes per ottenere l'elenco di prefissi di indirizzo per il VPC. Osserva i valori `cidr` e `zone` della risposta e assicurati che il `cidr` della rete sia un sottoinsieme del `cidr` del prefisso dell'indirizzo per la zona che stai tentando di creare.

## over_quota                                    
**Messaggio**: la richiesta potrebbe superare la quota per un tipo di risorsa.

Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## password_not_ready
**Messaggio**: nessuno

È necessario che la tua istanza sia in esecuzione prima di poter recuperare la password. Riprova tra qualche minuto. Se il problema persiste, contatta il supporto.

## pool_delete_conflict
**Messaggio**: non è possibile eliminare il pool perché è ancora associato a uno o più listener.

Assicurati che il pool sia disassociato da qualsiasi listener e riprova.

## pool_duplicate_name
**Messaggio**: il nome di pool `<pool_name>` è già utilizzato da un altro pool. Scegli un altro nome.

Scegli un nome pool diverso.

## pool_missing_algorithm
**Messaggio**: manca l'algoritmo di bilanciamento del carico.

L'algoritmo di bilanciamento del carico è un campo obbligatorio. Fornisci l'algoritmo di bilanciamento del carico nella tua richiesta. I valori accettabili sono `round_robin`, `weighted_round_robin` e `least_connections`.

## pool_missing_health_monitor
**Messaggio**: manca il monitoraggio integrità del pool.

Il monitoraggio integrità del pool è un campo obbligatorio.

## pool_missing_name
**Messaggio**: manca il nome pool.

Il nome pool è un campo obbligatorio.

## pool_missing_protocol
**Messaggio**: manca il protocollo del pool.

Il protocollo del pool è un campo obbligatorio. Fornisci un protocollo del pool nella tua richiesta. I valori accettabili sono `http` e `tcp`.

## pool_not_found
**Messaggio**: pool con ID `<pool_id>` non trovato.

Fornisci un ID pool esistente.

## pool_over_quota
**Messaggio**: impossibile creare il pool. La quota di pool per la risorsa del programma di bilanciamento del carico ha raggiunto il limite massimo.

Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## public_gateway_in_use
**Messaggio**: impossibile eliminare un gateway pubblico quando è in uso.

Il gateway pubblico è attualmente collegato a una o più sottoreti. Devi scollegare il gateway pubblico da tutte le sottoreti prima di poterlo eliminare.

## rate_limit_exceeded
**Messaggio**: troppe richieste in breve tempo.

Questo messaggio di errore viene restituito se vengono ricevute troppe richieste entro un intervallo di tempo specificato. Attendi qualche istante e riprova. 

## security_group_active_transactions
**Messaggio**: non è possibile collegare o scollegare l'interfaccia finché l'istanza non sarà in stato Attivo.

L'istanza deve essere attiva prima che le sue interfacce di rete possano essere collegate a un gruppo di sicurezza. Utilizza `GET /v1/instances/{id}?version=2019-01-01` o `ibmcloud is instance` per controllare lo stato dell'istanza. Una volta che lo stato è `running`, prova di nuovo. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_already_attached
**Messaggio**: l'interfaccia è già collegata al gruppo di sicurezza.


L'interfaccia è già collegata al gruppo di sicurezza. Utilizza `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` o `ibmcloud is security-group-network-interfaces` per visualizzare le interfacce collegate.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_exists
**Messaggio**: il gruppo di sicurezza esiste già.


I nomi dei gruppi di sicurezza devono essere univoci. Un gruppo di sicurezza con tale nome esiste già. Utilizza `GET /v1/security_groups?version=2019-01-01` o `ibmcloud is security-groups` per visualizzare i gruppi di sicurezza correnti.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias) o al [documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_attached
**Messaggio**: impossibile eliminare il gruppo di sicurezza mentre le interfacce sono collegate.


Scollega tutte le interfacce prima di eliminare il gruppo di sicurezza. Utilizza `DELETE /v1/security_groups/{id}/network_interfaces/{id}?version=2019-01-01` o `ibmcloud is security-group-network-interface-remove` per scollegare un'interfaccia.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias) o al
[documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_per_sg_exceeded
**Messaggio**: è stato superato il limite di interfacce per gruppo di sicurezza.

Collegando un'altra interfaccia al gruppo di sicurezza si supererebbe il limite di interfacce per gruppo di sicurezza. Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas). {: new_window}. Valuta la tua strategia e considera la possibilità di creare un altro gruppo di sicurezza con regole simili.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias) o al
[documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_last_security_group_is_default
**Messaggio**: il gruppo di sicurezza predefinito non può essere rimosso se è l'unico gruppo di sicurezza collegato.

Un'interfaccia di rete deve essere collegata ad almeno un gruppo di sicurezza.
Se non ne viene specificato uno, verrà collegata al gruppo di sicurezza predefinito del VPC.
Collega l'interfaccia a un gruppo di sicurezza diverso, quindi riprova a scollegarla dal gruppo di sicurezza predefinito.
Per informazioni sul gruppo di sicurezza predefinito, fai riferimento al [documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_limit_exceeded
**Messaggio**: limite del gruppo di sicurezza superato.

Hai tentato di creare un nuovo gruppo di sicurezza, ma al momento sei al limite della tua quota di account. Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Valuta la tua strategia per l'assegnazione di istanze ai gruppi di sicurezza. Spesso è possibile ridurre il numero complessivo dei gruppi di sicurezza assegnando più istanze allo stesso gruppo di sicurezza. Questa strategia ridurrà il numero di gruppi di sicurezza e ti lascerà sotto la tua quota di account. In rari casi, generalmente per le grandi organizzazioni, è necessario espandere la quota. In questo caso, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) per chiedere se è possibile.

## security_group_network_interface_not_active
**Messaggio**: non è possibile collegare l'interfaccia perché non è attiva.

Le interfacce di rete devono essere attive prima di collegarle ai gruppi di sicurezza. Utilizza `GET /v1/instances/{id}/network_interfaces/{id}?version=2019-01-01` o `ibmcloud is instance-network-interface` per visualizzare lo stato di un'interfaccia. Una volta che lo stato è 'available', prova di nuovo. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_not_attached
**Messaggio**: l'interfaccia non è collegata.

L'interfaccia non è collegata al gruppo di sicurezza. Utilizza `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` o `ibmcloud is security-group-network-interfaces` per visualizzare le interfacce collegate.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias) o al [documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group-using-the-cli){: new_window}.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_not_in_vpc
**Messaggio**: l'interfaccia e il gruppo di sicurezza sono in diversi VPC.

Per collegare un'interfaccia di rete a un gruppo di sicurezza, l'istanza deve trovarsi nello stesso VPC del gruppo di sicurezza. Utilizza `GET /v1/security_groups/{id}?version=2019-01-01` o `ibmcloud is security-group` per visualizzare i dettagli e il VPC dei gruppi di sicurezza. Utilizza `GET /v1/instances/{id}?version=2019-01-01` o `ibmcloud is instance` per visualizzare i dettagli e il VPC dell'istanza. 

## security_group_order_bindings
**Messaggio**: impossibile eliminare il gruppo di sicurezza mentre ha ordini di istanza in sospeso.

Se è stata creata un'istanza con i gruppi di sicurezza specificati sulle interfacce di rete, l'istanza e le interfacce di rete devono essere attive prima che il gruppo di sicurezza possa essere eliminato. Utilizza `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` o `ibmcloud is security-group-network-interfaces` per visualizzare le interfacce di rete collegate e il loro stato. Una volta che lo stato delle interfacce è 'available', prova di nuovo. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_port_max_less_than_port_min
**Messaggio**: il numero di porta massimo TCP/UDP non può essere inferiore al numero di porta minimo.

Il valore di porta massimo non può essere inferiore al valore di porta minimo. Specifica un valore di porta massimo maggiore del valore di porta minimo.

## security_group_port_range_both_or_neither
**Messaggio**: l'impostazione dell'intervallo di porte deve essere annullata oppure è necessario impostare un numero di porta minimo e massimo per 'tcp' e 'udp'.

Le regole con un protocollo 'tcp' o 'udp' possono avere un intervallo di porte non impostato (per applicare la regola a tutto il traffico) oppure possono specificare un intervallo di porte. Per limitare il traffico a una singola porta, imposta sia il numero di porta minimo che massimo sul valore della porta. Ad esempio, il seguente comando crea una regola per consentire SSH sulla porta 22: `ibmcloud is security-group-rule-add <id> inbound tcp --port-min 22 --port-max 22`.

Per ulteriori informazioni sulle configurazioni delle regole del gruppo di sicurezza, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias).


## security_group_port_range_invalid_protocol
**Messaggio**: è stato specificato un intervallo di porte con il protocollo 'icmp'. Un intervallo di porte è valido solo per un protocollo di tipo 'tcp' o 'udp'.

Le regole con un protocollo 'icmp' hanno un tipo e un codice. Le regole con i protocolli 'tcp' o 'udp' hanno un intervallo di porte. Per ulteriori informazioni sulle configurazioni delle regole del gruppo di sicurezza, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias).

## security_group_remote_group_not_in_vpc
**Messaggio**: il gruppo remoto non si trova nello stesso VPC di questo gruppo di sicurezza.

Le regole del gruppo di sicurezza possono fare riferimento a un gruppo di sicurezza remoto, consentendo il traffico tra le interfacce collegate dei due gruppi. I gruppi di sicurezza remoti devono trovarsi nello stesso VPC. Utilizza `GET /v1/security_groups?2019-01-01` o `ibmcloud is security-groups` per visualizzare i gruppi di sicurezza correnti e i loro VPC.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento al [documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules
**Messaggio**: impossibile eliminare il gruppo di sicurezza mentre le regole remote sono collegate.

Il gruppo di sicurezza contiene una o più regole che fanno riferimento a un gruppo di sicurezza remoto. Utilizza `GET /v1/security_groups/{id}/rules?version=2019-01-01` o `ibmcloud is security-group-rules` per visualizzare le regole. Il campo 'remote' specificherà qualsiasi gruppo di sicurezza remoto. Prova di nuovo dopo aver eliminato o modificato la regola remota.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias) o al [documento sull'utilizzo dei gruppi di sicurezza](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules_per_sg_exceeded
**Messaggio**: è stato superato il limite di regole remote per gruppo di sicurezza.


Aggiungendo un'altra regola che fa riferimento a un gruppo di sicurezza remoto si supererebbe il limite di regole remote per gruppo di sicurezza. Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}.


## security_group_rules_per_sg_exceeded
**Messaggio**: è stato superato il limite di regole per gruppo di sicurezza.

Aggiungendo una regola si supererebbe il limite di regole per gruppo di sicurezza. Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Valuta la tua strategia e considera la possibilità di creare un altro gruppo di sicurezza.


## security_group_sgs_per_interface_exceeded
**Messaggio**: è stato superato il limite di gruppi di sicurezza per interfaccia.

Collegando questa interfaccia a un altro gruppo di sicurezza si supererebbe il limite di gruppi di sicurezza per interfaccia. Le quote per ciascuna risorsa sono indicate in [Quote e limiti per VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Valuta la tua strategia e considera la possibilità di aggiungere regole a un gruppo di sicurezza esistente.


## security_group_type_code_invalid_protocol
**Messaggio**: è stato fornito un tipo/codice 'icmp', ma il protocollo richiesto non era 'icmp'. Imposta il protocollo su 'icmp' o specifica un intervallo di porte.

Solo le regole con un protocollo 'icmp' hanno un tipo e un codice. Le regole con i protocolli 'tcp' o 'udp' hanno un intervallo di porte. Per ulteriori informazioni sulle configurazioni delle regole del gruppo di sicurezza, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias).

## security_group_vpc_default
**Messaggio**: impossibile eliminare il gruppo di sicurezza predefinito per un VPC.

Non è possibile eliminare il gruppo di sicurezza predefinito. Per informazioni sul gruppo di sicurezza predefinito, fai riferimento alla guida sull'[aggiornamento del gruppo di sicurezza predefinito](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group).

## service_manager_service_failure
**Messaggio**: nessuno

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_acl_conflict
**Messaggio**: impossibile eliminare l'ACL di rete, è collegato a una sottorete.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_conflict
**Messaggio**: CIDR in conflitto con la sottorete esistente in VPC.

Esegui l'API GET /subnets per recuperare tutte le sottoreti in VPC. Assicurati che il CIDR che hai fornito non sia utilizzato da altre sottoreti controllando il valore di `ipv4_cidr_block`.

Se utilizzi la CLI, puoi eseguire `ibmcloud is subnets` e osservare il valore "Subnet CIDR" per eventuali conflitti.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty
**Messaggio**: la sottorete non è vuota, contatta il tuo amministratore.

È stata effettuata una richiesta per eliminare una sottorete, ma la sottorete contiene ancora delle risorse. Le sottoreti possono contenere istanze, VPN, programmi di bilanciamento del carico o gateway pubblici. Devi eliminare le tue risorse presenti nella sottorete prima di poter eliminare la sottorete. 

In alcune situazioni, questo errore può verificarsi anche quando la console mostra 0 VSI e 0 programmi di bilanciamento del carico, poiché l'eliminazione è asincrona e la modifica dello stato interno potrebbe richiedere alcuni minuti. Prova di nuovo l'eliminazione della tua sottorete tra qualche minuto.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_pgway_exists
**Messaggio**: impossibile eliminare la sottorete mentre è collegata a un gateway pubblico. Scollega il gateway pubblico e riprova.

È stata effettuata una richiesta per eliminare una sottorete, ma alla sottorete è ancora collegato un gateway pubblico. Devi eliminare o scollegare il gateway pubblico prima di poter eliminare la sottorete. 

Se utilizzi la CLI, puoi eseguire `ibmcloud is public-gateways` per elencare i gateway pubblici e `ibmcloud is subnet-public-gateway-detach` per scollegare un gateway pubblico da una sottorete. 

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_ipaddr_exists
**Messaggio**: impossibile eliminare la sottorete mentre contiene indirizzi IP. Elimina qualsiasi istanza del server associata all'indirizzo IP e riprova.

È stata effettuata una richiesta per eliminare una sottorete, ma la sottorete contiene ancora indirizzi IP. Devi eliminare l'istanza del server associata all'indirizzo IP prima di poter eliminare la sottorete.

Se utilizzi la CLI, puoi eseguire `ibmcloud is instances` per elencare le istanze del server e osservare il valore "Address" per determinare il suo indirizzo IP e il valore "Status" per determinare il suo stato. Esegui `ibmcloud is instance-delete` per eliminare un'istanza del server che non abbia già uno stato "deleting". 

In alcune situazioni, questo errore può verificarsi anche quando la console mostra 0 VSI, poiché l'eliminazione è asincrona e la modifica dello stato interno potrebbe richiedere alcuni minuti. Prova di nuovo l'eliminazione della tua sottorete tra qualche minuto.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_loadbalancer_exists
**Messaggio**: impossibile eliminare la sottorete mentre contiene un programma di bilanciamento del carico. Elimina il programma di bilanciamento del carico e riprova.

È stata effettuata una richiesta per eliminare una sottorete, ma la sottorete contiene ancora un programma di bilanciamento del carico. Devi eliminare il programma di bilanciamento del carico prima di poter eliminare la sottorete.

Se utilizzi la CLI, puoi eseguire `ibmcloud is load-balancers` per elencare i programmi di bilanciamento del carico e osservare il valore "Subnets" per determinare la sua sottorete e il valore "Status" per determinare il suo stato. Esegui `ibmcloud is load-balancer-delete` per eliminare un programma di bilanciamento del carico che non abbia già uno stato "deleting". 

In alcune situazioni, questo errore può verificarsi anche quando la console mostra 0 programmi di bilanciamento del carico, poiché l'eliminazione è asincrona e la modifica dello stato interno potrebbe richiedere alcuni minuti. Prova di nuovo l'eliminazione della tua sottorete tra qualche minuto.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_vpn_gway_exists
**Messaggio**: impossibile eliminare la sottorete mentre contiene un gateway VPN. Elimina il gateway VPN e riprova.

È stata effettuata una richiesta per eliminare una sottorete, ma alla sottorete è ancora collegato un gateway VPN. Devi eliminare il gateway VPN prima di poter eliminare la sottorete. 

Se utilizzi la CLI, puoi eseguire `ibmcloud is vpn-gateways` per elencare i programmi di bilanciamento del carico e osservare il valore "Subnets" per determinare la sua sottorete e il valore "Status" per determinare il suo stato. Esegui `ibmcloud is vpn-gateway-delete` per eliminare un gateway VPN che non abbia già uno stato "deleting". 

In alcune situazioni, questo errore può verificarsi anche quando la console mostra 0 gateway VPN, poiché l'eliminazione è asincrona e la modifica dello stato interno potrebbe richiedere alcuni minuti. Prova di nuovo l'eliminazione della tua sottorete tra qualche minuto.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_unknown_state
**Messaggio**: nessuno

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## system_limit_exceeded
**Messaggio**: questa operazione supererebbe un limite di sistema

Uno scenario possibile per la ricezione di questo messaggio di errore è se tenti di creare un prefisso dell'indirizzo, ma il numero massimo di prefissi dell'indirizzo esiste già.

## target_in_use
**Messaggio**: la destinazione ha già un IP mobile collegato.

## token_invalid
**Messaggio**: il token di servizio è scaduto o non è valido.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## token_missing
**Messaggio**: il token di servizio era vuoto o non esisteva nella richiesta.

Ricrea un token e prova di nuovo.

## validation_enum
**Messaggio**: il valore fornito non era un'opzione valida.

Uno dei campi forniti ha un valore che deve provenire da un'enumerazione di valori possibili.

Per le regole dell'ACL di rete, puoi specificare una direzione:

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum:
[ inbound, outbound ]
```

Ad esempio, il seguente valore non è valido poiché `northbound` non è un'opzione valida nell'enumerazione `[ inbound, outbound ]`.

```json
{
    "direction":"northbound"
}
```

## validation_failure                            
**Messaggio**: il JSON fornito non corrispondeva alla struttura prevista.

Per risolvere questo problema, assicurati che il contenuto della tua richiesta sia un JSON valido e che la tua richiesta sia conforme alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_invalid_cidr                       
**Messaggio**: il valore non è un CIDR valido.

Il valore deve essere un blocco CIDR interno valido con una parte host 0.

Alcuni intervalli di indirizzi IP sono riservati. Ulteriori informazioni sugli intervalli IP riservati sono disponibili nella nostra panoramica di [Utilizzo del VPC con regioni e sottoreti](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv4_cidr        
**Messaggio**: il valore non è un CIDR IPv4 valido.

Deve essere un blocco CIDR interno IPv4 con una parte host 0.

Alcuni intervalli di indirizzi IP sono riservati. Ulteriori informazioni sugli intervalli IP riservati sono disponibili nella nostra panoramica di [Utilizzo del VPC con regioni e sottoreti](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv6_cidr
**Messaggio**: il valore non è un CIDR IPv6 valido.

Attualmente, IPv6 non è supportato. Utilizza un indirizzo IPv4.

## validation_invalid_address
**Messaggio**: il valore non è un indirizzo valido.

Deve essere un indirizzo IP valido

Un elenco di indirizzi IP riservati singolarmente è fornito nel documento [Regioni e sottoreti](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets).

## validation_invalid_ipv4_address
**Messaggio**: il valore non è un indirizzo IPv4 valido.

Fornisci un indirizzo IPv4 valido.

## validation_invalid_ipv6_address
**Messaggio**: il valore non è un indirizzo IPv6 valido.

Fornisci un indirizzo IPv6 valido. Attualmente, IPv6 non è supportato; utilizza un indirizzo IPv4.

## validation_invalid_field_type
**Messaggio**: il tipo di valore non corrisponde al tipo di campo.

Per risolvere questo problema, assicurati che il contenuto della tua richiesta sia conforme alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window} per l'endpoint che stai chiamando.

## validation_max_value
**Messaggio**: il valore fornito è troppo grande.

Fornisci un valore inferiore che soddisfi il massimo indicato nella specifica. Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_min_value
**Messaggio**: il valore fornito è troppo piccolo.

Fornisci un valore maggiore che soddisfi il minimo indicato dalla specifica. Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_not_null
**Messaggio**: il campo fornito deve essere null.

Assicurati che il valore sia null. Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

Di seguito è riportato un esempio non valido:

```json
{
    "name": null
}
```

## validation_only_one
**Messaggio**: il valore deve corrispondere a uno dei sottoschemi.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_discriminator_forbidden
**Messaggio**: il campo discriminator vieta questa sottostruttura.

Ad esempio, se specifichi:
```
{
protocol: icmp
port_min: 5
port_max: 100
}
```

Il protocollo è `icmp` e _port_min_ è un campo `tcp`, quindi riceverai un errore.
1. validation_discriminator_required per le regole `icmp` mancanti
2. validation_discriminator_forbidden per i campi `tcp` con `icmp` specificato

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_internal_error
**Messaggio**: nessuno

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_invalid_name
**Messaggio**: il valore non è un nome valido.


## validation_invalid_ref
**Messaggio**: il valore non è un HREF valido.


## validation_non_empty_uuid
**Messaggio**: nessuno

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_required_field
**Messaggio**: manca un campo obbligatorio.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_unique_failed
**Messaggio**: il campo fornito deve essere univoco.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

Potresti aver specificato un nome che è già in uso. Prova un valore diverso.

## vpc_acl_conflict                           
**Messaggio**: impossibile eliminare l'ACL di rete predefinito, è collegato a un VPC.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias) o al [documento sull'utilizzo degli ACL di rete](/docs/infrastructure/vpc-network?topic=vpc-network-setting-up-network-acls-using-the-cli){: new_window}.

Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_not_empty
**Messaggio**: non è possibile eliminare il VPC perché non è vuoto.

È necessario rimuovere tutte le risorse da un VPC prima di poterlo eliminare.

Potresti ricevere questo errore se hai ancora un gateway nel VPC, anche quando tutte le sottoreti sono state eliminate, poiché il gateway può esistere nel VPC senza una sottorete. Potrebbe essere necessario utilizzare la CLI per verificare la presenza di risorse orfane.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_resource_separation
**Messaggio**: le risorse si trovano in diversi VPC

## vpn_connection_cidr_not_created
**Messaggio**: non è stato possibile aggiungere un blocco CIDR alla connessione VPN `<vpn_connection_id>`.

Fornisci un CIDR valido che soddisfi i requisiti indicati dalla specifica. 

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_cidr_not_deleted
**Messaggio**: non è stato possibile eliminare un blocco CIDR dalla connessione VPN `<vpn_connection_id>`.

Fornisci un CIDR valido che esista sulla connessione. Una connessione deve avere almeno un CIDR locale e peer.

Per visualizzare i blocchi CIDR della connessione, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e controlla i campi `local_cidrs` e `peer_cidrs`.

## vpn_connection_cidr_not_found
**Messaggio**: il blocco CIDR non è stato trovato nella connessione VPN `<vpn_connection_id>`.

Fornisci un CIDR valido che sia presente nella connessione.

Per visualizzare i blocchi CIDR della connessione, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e controlla i campi `local_cidrs` e `peer_cidrs`.

## vpn_connection_cidr_not_valid
**Messaggio**: il blocco CIDR `<cidr_block>` non rappresenta un indirizzo valido.

Il valore deve essere un blocco CIDR interno valido senza bit host impostati.

Per visualizzare i blocchi CIDR della connessione, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e controlla i campi `local_cidrs` e `peer_cidrs`.

## vpn_connection_cidr_overlap
**Messaggio**: il blocco CIDR `<cidr_block_1>` si sovrappone a `<cidr_block_2>`. Due blocchi CIDR peer non possono sovrapporsi sullo stesso VPC e due blocchi CIDR locali non possono sovrapporsi sulla stessa connessione.

Fornisci un valore CIDR valido che soddisfi i requisiti indicati dalla specifica.

Per visualizzare i blocchi CIDR della connessione, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e controlla i campi `local_cidrs` e `peer_cidrs`.

## vpn_connection_duplicate_name
**Messaggio**: il nome `<vpn_connection_name>` è già utilizzato dalla connessione VPN `<vpn_connection_id>`.

Fornisci un nome di connessione diverso. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_invalid_name
**Messaggio**: il nome `<vpn_connection_name>` non è un nome di connessione VPN valido.

Un nome di connessione valido inizia con una lettera, seguita da lettere, cifre, caratteri di sottolineatura o trattini.

## vpn_connection_invalid_psk_format
**Messaggio**: la PSK (pre-shared key) `<psk>` non è nel formato valido.

Una PSK valida deve contenere solo da 6 a 128 caratteri che includono lettere, cifre, `-`,`+`,`&`,`!`,`@`,`#`,`$`,`%`,`^`,`*`,`(`,`)`,`,`,`.`,`:`,`_`.

## vpn_connection_local_cidrs_required
**Messaggio**: è necessario almeno un blocco CIDR locale quando si crea una connessione VPN.

Fornisci un valore CIDR locale valido che soddisfi i requisiti indicati dalla specifica.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_connection_local_subnets_quota_exceeded
**Messaggio**: la quota delle sottoreti locali per tutte le connessioni VPN è stata superata per il gateway VPN `<vpn_gateway_id>`.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le sottoreti locali correnti per tutte le connessioni VPN, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections` e controlla il campo `local_cidrs` per ogni connessione.

## vpn_connection_local_subnets_quota_exceeded_for_connection
**Messaggio**: la quota delle sottoreti locali '<quota_limit>' per la connessione VPN è stata superata.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vp?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le sottoreti locali correnti per una connessione VPN, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e controlla il campo `local_cidrs`.

## vpn_connection_not_found
**Messaggio**: la connessione VPN `<vpn_connection_id>` non è stata trovata.

Controlla se l'ID di connessione è corretto. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_peer_cidrs_required
**Messaggio**: è necessario almeno un blocco CIDR peer quando si crea una connessione VPN.

Fornisci un valore CIDR peer valido che soddisfi i requisiti indicati dalla specifica.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_connection_peer_subnets_quota_exceeded
**Messaggio**: la quota delle sottoreti peer per tutte le connessioni VPN è stata superata per il gateway VPN `<vpn_gateway_id>`.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le sottoreti peer correnti per tutte le connessioni VPN, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections` e controlla il campo `peer_cidrs` per ogni connessione.

## vpn_connection_peer_subnets_quota_exceeded_for_connection
**Messaggio**: la quota delle sottoreti peer `<quota_limit>` per la connessione VPN è stata superata.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le sottoreti peer correnti per una connessione VPN, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e controlla il campo `peer_cidrs`.

## vpn_connections_quota_exceeded
**Messaggio**: la quota delle connessioni VPN è stata superata per il gateway VPN `<vpn_gateway_id>`.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare le connessioni VPN correnti per un gateway VPN, utilizza l'API `GET /vpn_gateways/<vpn_gateway_id>/connections`.

## vpn_connection_static_route_not_created
**Messaggio**: impossibile aggiungere una rotta statica per il blocco CIDR `<peer_cidr>`.

Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_static_route_not_deleted
**Messaggio**: impossibile rimuovere una rotta statica per il blocco CIDR `<peer_cidr>`.

Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_update_cidrs_not_permitted
**Messaggio**: non è possibile modificare i blocchi CIDR durante l'aggiornamento di una connessione. Utilizza l'API corretta durante la creazione o l'eliminazione dei CIDR.

Fornisci un valore di richiesta valido che soddisfi i requisiti indicati dalla specifica.

Per ulteriori istruzioni per risolvere questo problema, fai riferimento alla [documentazione API](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_gateway_duplicate_name
**Messaggio**: il nome `<vpn_gateway_name>` è già utilizzato dal gateway VPN `<vpn_gateway_id>`.

Fornisci un nome gateway VPN diverso. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_initialization_error
**Messaggio**: non è stato possibile inizializzare il gateway VPN.

Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_invalid_name
**Messaggio**: il nome `<vpn_gateway_name>` non è un nome di gateway VPN valido.

Un nome di gateway VPN valido inizia con una lettera, seguita da lettere, cifre, caratteri di sottolineatura o trattini.

## vpn_gateway_invalid_state
**Messaggio**: il gateway VPN `<vpn_gateway_id>` è in uno stato non valido per l'operazione richiesta.

Il gateway VPN deve trovarsi nello stato `available` prima di poterlo utilizzare. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_ip_create_error
**Messaggio**: impossibile creare un indirizzo IP per il gateway VPN.

Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_not_found
**Messaggio**: il gateway VPN `<vpn_gateway_id>` non è stato trovato.

Controlla se l'ID del gateway VPN è corretto. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_not_found
**Messaggio**: non è stato possibile trovare la sottorete `<subnet_id>` per il gateway VPN fornito.

Hai fatto riferimento a una sottorete che non esiste. Riesamina la tua richiesta per assicurarti di aver specificato l'ID di sottorete corretto. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_status_error
**Messaggio**: non è stato possibile creare il gateway VPN a causa dello stato della sottorete.

Fornisci una sottorete che sia nello stato `available`. Riprova tra qualche minuto. Se il problema persiste, [contatta il supporto](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateways_quota_exceeded
**Messaggio**: la quota dei gateway VPN è stata superata per l'account e/o la regione.

Le quote per ciascuna risorsa sono indicate nella pagina [Quote](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Per visualizzare i gateway VPN correnti, utilizza l'API `GET /vpn_gateways`.
