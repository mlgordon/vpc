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
{:table: .aria-labeledby="caption"}

# Pianificazione delle autorizzazioni di {{site.data.keyword.vsi_is_short}}
{: #planning-virtual-servers-for-vpc-permissions}

Se hai intenzione di eseguire il provisioning di {{site.data.keyword.vsi_is_full}}, devi comprendere l'accesso al server virtuale disponibile in base al tuo ruolo utente.
{:shortdesc}

Quando si lavora con le VSI, agli utenti viene assegnato un ruolo in base all'{{site.data.keyword.vpc_short}} a cui viene fornito un'istanza. Se un utente dispone dell'accesso come editor o amministratore a {{site.data.keyword.vpc_short}}, eredita la capacità di creare, eliminare e modificare le istanze del server virtuale all'interno di tale {{site.data.keyword.vpc_short}}.

Esamina la seguente tabella per ulteriori informazioni sui ruoli utente e sul livello di accesso specifico di ciascun ruolo.

* Come amministratore di un account, puoi definire i ruoli ed eseguire qualsiasi azione disponibile su {{site.data.keyword.vsi_is_short}}.
* Come editor di un account, puoi modificare lo stato e creare/eliminare risorse secondarie.
* Come visualizzatore di un account, puoi eseguire azioni che non modificano lo stato delle risorse.

Le risorse del server virtuale *ereditano* tutte le autorizzazioni utente dal proprio VPC principale. Le autorizzazioni non possono essere impostate a livello di istanza.
{:note}

<table>
<CAPTION>Tabella 1. Autorizzazioni utente</CAPTION>
<THEAD>
<TR>
<th>Autorizzazione VPC</th>
<th>Descrizione</th>
<th>Azioni</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>Amministratore</td>
<td>Tutte le azioni inclusa la capacità di gestire <br>
il controllo accessi.</td>
<td>
Controllo accessi:
<ul>
<li>Aggiunge e rimuove utenti</li>
<li>Assegna ruoli per ogni utente</li>
</ul>
<p>
Server virtuali:
<ul>
<li>Crea server virtuali</li>
<li>Arresta server virtuali</li>
<li>Elimina server virtuali</li>
<li>Riavvia server virtuali</li>
<li>Duplica server virtuali</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>Visualizza ed elenca server virtuali</li>
<li>Rinomina i server virtuali</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Crea e modifica chiavi SSH</li>
<li>Elimina chiavi SSH</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<!-- <li>View monitoring and log data</li> -->
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>
</p>
</td>
</tr>
<tr>
<td>Editor</td>
<td>Azioni che possono modificare lo stato, nonché <br>
creare ed eliminare risorse secondarie.</td>
<td>
Server virtuali:
<ul>
<li>Crea server virtuali</li>
<li>Arresta server virtuali</li>
<li>Elimina server virtuali</li>
<li>Riavvia server virtuali</li>
<li>Duplica server virtuali</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>Visualizza ed elenca server virtuali</li>
<li>Rinomina i server virtuali</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Crea chiavi SSH</li>
<li>Elimina chiavi SSH</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>Visualizza dati di monitoraggio e di log</li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td>Visualizzatore</td>
<td>Azioni che non modificano lo stato</td>
<td>
Server virtuali:
<ul>
<li>Visualizza ed elenca server virtuali</li>
<!-- <li>View and list image snapshots</li> -->
<li>Visualizza dati di monitoraggio e di log</li>
</ul>
</td>
</tr>
</TBODY>
</table>

## Passi successivi
Per ulteriori informazioni su come modificare le autorizzazioni di un utente, vedi [Gestione delle autorizzazioni utente per le risorse VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
