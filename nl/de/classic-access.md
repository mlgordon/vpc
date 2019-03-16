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
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# Zugriff auf die klassische Infrastruktur über eine VPC einrichten
{: #setting-up-access-to-your-classic-infrastructure-from-vpc}

Sie können für jedes beliebige Konto die klassische {{site.data.keyword.cloud}}-Infrastruktur, einschließlich Direct Link-Konnektivität, über eine VPC in jeder Region einrichten. Diese speziellen "VPCs mit klassischem Zugriff" verwenden den gleichen impliziten Router wie Ihre klassische {{site.data.keyword.cloud}}-Infrastruktur.

Wenn Sie eine VPC-Instanz für den klassischen Zugriff einrichten, kann jeder Rechenhost (VSI- oder Bare-Metal-Host) in Ihrem klassischen Konto Pakete über die VPC mit klassischem Zugriff senden und empfangen. Denken Sie jedoch daran, dass Firewalls, Gateways, Netz-ACLs oder Sicherheitsgruppen diesen Datenverkehr filtern können. Es wird empfohlen, dass nur der Datenverkehr zugelassen wird, der für die ordnungsgemäße Funktion Ihrer Anwendungen erforderlich ist.

## Voraussetzungen:
1. Ihr klassisches Konto muss mit Ihrem IBM Cloud-Konto verknüpft sein. Entsprechende Anweisungen dazu finden Sie im Abschnitt zum [Verknüpfen von IBMid-Konten](/docs/account/softlayerlink.html).
1. Ihr klassisches Konto muss für VRF aktiviert sein.
    * Wenn Sie bereits über Direct Link für Ihr Konto verfügen, sind Sie bereit.
    * Wenn Ihr Konto nicht VRF-fähig ist, öffnen Sie ein Ticket, um "VRF-Migration" für Ihr Konto zu beantragen. Weitere Informationen zu diesem Konvertierungsprozess finden Sie im Abschnitt zur [Vorgehensweise bei der Initiierung der Konvertierung](/docs/infrastructure/direct-link?topic=direct-link-how-you-can-initiate-the-conversion) in der Dokumentation zu Direct Link.

Firewalls, Gateways, Netz-ACLs oder Sicherheitsgruppen können einen Teil oder den gesamten Netzwerkverkehr zwischen klassischen und VPC-Ressourcen herausfiltern.
{: important}

## VPC mit klassischem Zugriff erstellen
Sie können eine VPC mit klassischem Zugriff über die Benutzerschnittstelle (UI), die Befehlszeilenschnittstelle (CLI) oder die Anwendungsprogrammierschnittstelle (API) erstellen.

Eine VPC muss bei ihrer Erstellung für den klassischen Zugriff konfiguriert werden: Sie können eine VPC nicht so aktualisieren, dass der klassische Zugriff hinzugefügt oder entfernt wird.
{: note}

### VPC mit klassischem Zugriff über die Benutzerschnittstelle erstellen

Erstellen Sie eine VPC mit klassischem Zugriff über die Seite **VPC erstellen**, indem Sie das Kontrollkästchen **Zugriff auf klassische Ressource aktivieren** unter der Beschriftung **Klassischer Zugriff** auswählen.

![UI für klassischen Zugriff](/images/classic-access-ui.png)

### VPC mit klassischem Zugriff über die Befehlszeilenschnittstelle erstellen

Verwenden Sie das Flag `--classic-access` beim Erstellen der VPC. Zum Beispiel:

```
ibmcloud is vpc-create my-access-vpc --classic-access
```
{: pre}


### VPC mit klassischem Zugriff über die API erstellen

Übergeben Sie den Parameter `classic_access` beim Erstellen der VPC. Zum Beispiel:

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "my-access-vpc",
        "classic_access": true
      }'
```
{: pre}


## Einschränkungen

* Nur Ihre privaten Netze sind mit dem impliziten privaten Router Ihres Kontos verbunden.
* Nur Teilnetze, die mit klassischen APIs zugeordnet sind, werden mit dem klassischen Teil Ihres impliziten privaten Routers verbunden. Teilnetze in klassischen VLANs werden nicht vom impliziten Router weitergeleitet.
* Es kann nur eine VPC pro Region und pro Konto für den klassischen Zugriff aktiviert werden.
