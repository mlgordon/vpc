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
{:DomainName: data-hd-keyref="DomainName"}

# Erforderliche Ressourcenberechtigungen für API- und CLI-Aufrufe
{: #resource-authorizations-required-for-api-and-cli-calls}

In der folgenden Tabelle sind die Berechtigungen aufgelistet, die für die Interaktion mit {{site.data.keyword.cloud}} Virtual Private Cloud-Infrastrukturobjekten erforderlich sind. Diese Informationen sind besonders hilfreich, wenn Sie API-Aufrufe vornehmen. Hier ist, was Sie wissen müssen, um diese Tabelle zu verwenden:

Die Begriffe _zugeordnet_ bzw. _nicht zugeordnet_ beziehen sich darauf, ob die Ressource einer VPC oder VPCs zugeordnet ist (entweder direkt oder indirekt über die Teilnetze der Ressource). Eine nicht zugeordnete variable IP-Adresse oder Netzzugriffssteuerungsliste (ACL) verfügt über keine Teilnetze und ist daher keiner VPC zugeordnet, sodass die Autorisierung durch VPC nicht maßgeblich ist.

* Die Aktionen **Anzeigen** und **Auflisten** gelten für die Rolle **Anzeigeberechtigter** oder **Operator**.
* Die Aktion **Aktualisieren** und zugehörige Aktionen gelten für die Rolle **Editor** oder **Administrator**.
* Ressourcen sind durch entsprechende Berechtigungen geschützt, Referenzobjekte für Ressourcen jedoch nicht (ID, CRN usw.).


| Ressource | Operation | Erforderliche Berechtigung |
|--------|--------|---------|
| VPC | Erstellen | Berechtigung zum Anzeigen für die Ressourcengruppe für diese VPC und Berechtigung zum Aktualisieren für VPC-Ressourcen |
| VPC | Aktualisieren, Löschen |  Berechtigung zum Aktualisieren für VPC |
| VPC |  Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC |
| Standard-ACL für VPC, Standard-SG|  Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC |
| Adresspräfixe für VPC |  Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC |
| Adresspräfixe für VPC |  Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC |
|—————|——————|———————|
| Variable IP-Adresse (nicht zugeordnet) | Erstellen, Aktualisieren, Löschen | Alle Kontobenutzer und Berechtigungen zum Anzeigen für alle Kontomanagement-Services, wenn die Ressource in der Standardressourcengruppe erstellt wird. Klicken Sie [hier](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources#setting-up-viewer-access), um Anweisungen zum Einrichten des Zugriffs für Anzeigeberechtigte zu erhalten. **Hinweis: Das Zuordnen und Aufheben von Zuordnungen sind Teil der Aktualisierungsoperation für variable IP-Adressen**|
| Variable IP-Adresse (nicht zugeordnet) | Anzeigen, Auflisten | Kontobenutzer |
| Variable IP-Adresse (zugeordnet) | Aktualisieren | Berechtigung zum Aktualisieren für das zugehörige Teilnetz und die entsprechende VPC (nachdem sie zugeordnet wurde, kann eine variable IP-Adresse nicht erstellt oder gelöscht werden) |
| Variable IP-Adresse (zugeordnet) | Anzeigen, Auflisten | Berechtigung zum Anzeigen für das Teilnetz der variablen IP-Adresse | 
|——————|———————|————————|
| Netz-ACL (nicht zugeordnet), ACL-Regeln | Erstellen, Aktualisieren, Löschen | Jeder Kontobenutzer |
| Netz-ACL (nicht zugeordnet), ACL-Regeln | Anzeigen, Auflisten | Jeder Kontobenutzer |
| Netz-ACL (zugeordnet), ACL-Regeln | Erstellen, Aktualisieren, Löschen | Berechtigungen zum Aktualisieren für alle zugeordneten Teilnetze und VPC |
| Netz-ACL (zugeordnet), ACL-Regeln | Anzeigen, Auflisten | Berechtigung zum Anzeigen für mindestens eines der zugeordneten Teilnetze und VPC |
|——————|———————|————————|
| Öffentliches Gateway | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC des PGW |
| Öffentliches Gateway | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC des PGW |
|—————————|————————|———————————|
| Geografie | Anzeigen, Auflisten |  Für Regionen und Zonen, jeder Kontobenutzer |
|———————|————————|—————————|
| SSH-Schlüssel | Erstellen, Aktualisieren, Löschen | Jeder Kontobenutzer |
| SSH-Schlüssel | Anzeigen, Auflisten | Jeder Kontobenutzer |
|————————|—————————|————————|
| Teilnetz | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC des Teilnetzes |
| Teilnetz | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC des Teilnetzes |
| Teilnetz-ACL oder PGW | Zuordnen, Zuordnung aufheben | Berechtigung zum Aktualisieren für VPC des Teilnetzes |
| Teilnetz-ACL oder PGW | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC des Teilnetzes |
|——————|—————————|————————|
| Sicherheitsgruppe, SG-Regeln | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC der Sicherheitsgruppe |
| Sicherheitsgruppe, SG-Regeln | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC der Sicherheitsgruppe |
|Netzschnittstelle der Sicherheitsgruppe | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC der Sicherheitsgruppe (die auch die VPC der Netzschnittstellenkarte ist) |
|Netzschnittstelle der Sicherheitsgruppe | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC der Sicherheitsgruppe (die auch die VPC der Netzschnittstellenkarte ist) |
|—————————|—————————|—————————|
| Images | Erstellen, Aktualisieren, Löschen | Jeder Kontobenutzer |
| Images | Anzeigen, Auflisten | Jeder Kontobenutzer |
| Instanzen | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC der Instanz |
| Instanzen | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC der Instanz |
| Instanzaktionen, NICs, variable IP-Adressen | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für VPC der Instanz |
| Instanzaktionen, Initialisierung, NICs, variable IP-Adressen | Anzeigen, Auflisten | Berechtigung zum Anzeigen für VPC der Instanz |
|————————|——————|————————|
| VPN-Gateway | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für das VPN |
| VPN-Gateway | Anzeigen, Auflisten | Berechtigung zum Anzeigen für das VPN |
| VPN-Gateway-Verbindungen | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für das VPN |
| VPN-Gateway-Verbindungen | Anzeigen, Auflisten | Berechtigung zum Anzeigen für das VPN |
| VPN-Gateway IKE-Richtlinien, IPSec-Richtlinien und Verbindungen | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für das VPN |
| VPN-Gateway IKE-Richtlinien, IPSec-Richtlinien und Verbindungen | Anzeigen, Auflisten | Berechtigung zum Anzeigen für das VPN |
|————————|——————|————————|
| Lastausgleichsfunktion | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren der Lastausgleichsfunktion |
| Lastausgleichsfunktion | Anzeigen, Auflisten | Berechtigung zum Anzeigen für die Lastausgleichsfunkion |
| Lastausgleichsfunktion, Pools und Listener | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren der Lastausgleichsfunktion |
| Lastausgleichsfunktion, Pools und Listener | Anzeigen, Auflisten | Berechtigung zum Anzeigen für die Lastausgleichsfunkion |
|————————|——————|————————|
| Datenträger | Erstellen, Aktualisieren, Löschen | Berechtigung zum Aktualisieren für den Datenträger
| Datenträger | Anzeigen, Auflisten | Berechtigung zum Anzeigen für den Datenträger |
| Datenträgerprofile | Anzeigen, Auflisten | Jeder Kontobenutzer |


