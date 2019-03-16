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

# {{site.data.keyword.vsi_is_short}}-Berechtigungen planen
{: #planning-virtual-servers-for-vpc-permissions}

Wenn Sie {{site.data.keyword.vsi_is_full}} bereitstellen möchten, müssen Sie mit dem Zugriff auf den virtuellen Server vertraut sein, der Ihnen je nach Ihrer Rolle zur Verfügung steht.
{:shortdesc}

Bei der Arbeit mit VSIs wird Benutzern eine Rolle zugeordnet, die auf der {{site.data.keyword.vpc_short}} basiert, für die eine Instanz bereitgestellt wird. Wenn ein Benutzer über Editor- oder Administratorzugriff auf die {{site.data.keyword.vpc_short}} verfügt, übernehmen die Benutzer die Fähigkeit, Instanzen von virtuellen Servern in dieser {{site.data.keyword.vpc_short}} zu erstellen, zu löschen und zu ändern.

Sehen Sie sich die folgende Tabelle an, um mehr über Benutzerrollen und die spezifische Zugriffsebene zu erfahren, die jede Rolle umfasst.

* Als Administrator eines Kontos können Sie Rollen definieren und alle verfügbaren Aktionen für {{site.data.keyword.vsi_is_short}} ausführen.
* Als Editor eines Kontos können Sie den Status ändern und Unterressourcen erstellen/löschen.
* Als Anzeigeberechtigter eines Kontos können Sie Aktionen ausführen, die den Status der Ressourcen nicht ändern.

Die Ressourcen des virtuellen Servers *übernehmen* alle Benutzerberechtigungen von ihrer übergeordneten VPC. Berechtigungen können nicht auf Instanzebene festgelegt werden.
{:note}

<table>
<CAPTION>Tabelle 1. Benutzerberechtigungen</CAPTION>
<THEAD>
<TR>
<th>VPC-Berechtigung</th>
<th>Beschreibung</th>
<th>Aktionen</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>Administrator</td>
<td>Alle Aktionen einschließlich der Fähigkeit, die Zugriffssteuerung <br>
zu verwalten</td>
<td>
Zugriffssteuerung:
<ul>
<li>Benutzer hinzufügen und entfernen</li>
<li>Rollen für jeden Benutzer zuordnen</li>
</ul>
<p>
Virtuelle Server:
<ul>
<li>Virtuelle Server erstellen</li>
<li>Virtuelle Server stoppen</li>
<li>Virtuelle Server löschen</li>
<li>Virtuelle Server erneut starten</li>
<li>Virtuelle Server duplizieren</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>Virtuelle Server anzeigen und auflisten</li>
<li>Virtuelle Server umbenennen</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>SSH-Schlüssel erstellen und bearbeiten</li>
<li>SSH-Schlüssel löschen</li>
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
<td>Aktionen, die den Status ändern können, sowie <br>
Unterressourcen erstellen und löschen</td>
<td>
Virtuelle Server:
<ul>
<li>Virtuelle Server erstellen</li>
<li>Virtuelle Server stoppen</li>
<li>Virtuelle Server löschen</li>
<li>Virtuelle Server erneut starten</li>
<li>Virtuelle Server duplizieren</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>Virtuelle Server anzeigen und auflisten</li>
<li>Virtuelle Server umbenennen</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>SSH-Schlüssel erstellen</li>
<li>SSH-Schlüssel löschen</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>Überwachungs- und Protokolldaten anzeigen</li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td>Anzeigeberechtigter</td>
<td>Aktionen, die den Status nicht ändern</td>
<td>
Virtuelle Server:
<ul>
<li>Virtuelle Server anzeigen und auflisten</li>
<!-- <li>View and list image snapshots</li> -->
<li>Überwachungs- und Protokolldaten anzeigen</li>
</ul>
</td>
</tr>
</TBODY>
</table>

## Nächste Schritte
Weitere Informationen zum Ändern der Berechtigungen eines Benutzers finden Sie im Abschnitt [Benutzerberechtigungen für VPC-Ressourcen verwalten](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
