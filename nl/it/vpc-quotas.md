---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---
# Quote
{: #quotas}

Questo documento analizza le quote e i limiti per il tuo {{site.data.keyword.cloud}} Virtual Private Cloud e le risorse disponibili al suo interno.

## Quote di VPC

Gli account hanno le seguenti quote:

|   Risorsa     | Numero massimo |
| ------- | :------: |
| VPC (Virtual Private Cloud) | 5 per account|
| VPC con Accesso classico | 1 per regione, per account |
| Gateway pubblici (PGW) | 1 per zona |
| Prefissi indirizzo | 5 per VPC per zona |

## Quote di sottorete

|   Risorsa     | Numero massimo |
| ------- | :------: |
| Sottoreti | 15 per VPC (Virtual Private Cloud) |


## Quote di VSI
|   Risorsa     | Numero massimo |
| ------- | :------: |
| Istanze del server virtuale (VSI) | 100 per account per impostazione predefinita |
| vNIC per VSI | 5 per VSI |
| Indirizzi IP mobili | 1 per VSI |
| Chiavi SSH | 100 per account |


## Quote dei gruppi di sicurezza

Esistono alcune quote (limiti) basate sull'account per i gruppi di sicurezza e le loro regole associate.

|Risorsa|Quota|
|--------|-----|
|Gruppi di sicurezza|5 per interfaccia di rete|
|Gruppi di sicurezza|500 per account|
|Regole|50 per gruppo di sicurezza|
|Regole remote|5 per gruppo di sicurezza|
|Interfacce di rete|100 per gruppo di sicurezza|

## Quote di ACL

|Risorsa|Quota|
|--------|-----|
|ACL| 30 per account|
|ACL|200 per regione |
|Regole di ingresso|20 per ACL |
|Regole di uscita|20 per ACL |

## Quote di VPN

Di seguito sono riportate le attuali limitazioni delle risorse VPN per account:

|Risorsa|Quota|
|--------|-----|
| Gateway VPN| 7 per account |
| Gateway VPN| 3 per zona |
| Connessioni VPN | 10 per gateway VPN |
| Politiche IKE | 20 per account |
| Politiche IPSec | 20 per account |
| Sottoreti peer su qualsiasi singolo gateway VPN | 50 su tutte le connessioni VPN|
| Sottoreti peer | 15 su qualsiasi singola connessione VPN|
| Sottoreti locali su qualsiasi singolo gateway VPN | 50 su tutte le connessioni VPN|
| Sottoreti locali | 15 su qualsiasi singola connessione VPN|


## Quote del programma di bilanciamento del carico

Di seguito sono riportate le quote attuali delle risorse del programma di bilanciamento del carico:

|Risorsa|Quota|
|--------|-----|
| Programma di bilanciamento del carico | 50 per account |
| Listener | 10 per programma di bilanciamento del carico |
| Pool | 10 per programma di bilanciamento del carico |
| Membro | 50 per pool |
