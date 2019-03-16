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

# Informationen zur IBM Cloud Virtual Private Cloud-Infrastruktur (VPC)
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

{{site.data.keyword.cloud}} VPC ist Teil der nächsten Generation der IBM One Cloud-Plattform, die die traditionellen Branchenstandards für Leistung, Servicewachstum, Flexibilität und Implementierungsfreiheit neu definiert.

Eine virtuelle private Cloud (VPC) bietet Ihnen einen kosteneffizienten Einstiegspunkt für die Cloudsicherheit und die Möglichkeit der dynamischen Skalierung in einer öffentlichen Cloud. Sie bietet eine differenziert Kontrolle über Ihre virtuelle Infrastruktur und die Segmentierung des Netzverkehrs.

## Privater Raum in einer öffentlichen Cloud
IBM Cloud VPC bietet eine isolierte, sichere Umgebung in der öffentlichen Cloud. Die Lösung kombiniert die Sicherheit einer privaten Cloud mit der Agilität und einfachen Handhabung einer öffentlichen Cloud.

 * Sie können wichtige Netzservices verwalten und virtuelle Server nach Bedarf starten, um Ihre geschäftskritischen, cloudtoleranten und Cloud-nativen Anwendungen zu unterstützen.
 * Sie können eigene Netzwertrichtlinien definieren, die für optimale Sicherheit und benutzerfreundlichen Zugriff konzipiert sind.
 * Sie können Ihre Ressourcen bereitstellen und sie miteinander verbinden oder voneinander isolieren.

### Logische Isolation
Mit IBM Cloud Virtual Private Cloud (VPC) können Sie Anwendungen logisch von anderen Netzen in allen Regionen isolieren und gleichzeitig Skalierbarkeit und Sicherheit gewährleisten.

Um diese logische Isolation zu ermöglichen, ist die VPC durch die Verwendung einer Reihe privater IP-Adressen in Teilnetze unterteilt. Standardmäßig können jedoch alle Ressourcen (z. B. VSI) in derselben VPC unabhängig von ihrem Teilnetz miteinander kommunizieren. Teilnetze sind in einer einzigen Zone enthalten und können nicht mehrere Zonen umfassen, was bei der Sicherheit, bei der Verringerung der Latenzzeit und bei der Wiederherstellung nach einem Katastrophenfall hilfreich ist.

### Schnelle Bereitstellung und Sicherheit von Instanzen

Erstellen Sie virtuelle Serverinstanzen (VSIs) schnell, indem Sie vordefinierte Profile verwenden, die für Ihre spezifischen Workloads optimiert sind. Schützen Sie Ihre Instanzen mit Sicherheitsgruppen.

### Leistungsspektrum für den Netzbetrieb
IBM Cloud VPC bietet ein umfassendes Leistungsspektrum für den Netzbetrieb, einschließlich der Auswahl von IP-Adressbereichen, virtuelle Firewalls (Sicherheitsgruppen und Netz-ACLs), virtuelle private Netze (VPN) und Lastausgleichsfunktionen (LBaaS) mit Elastizität.

 * Sie können Ihre virtuelle Topologie automatisch konfigurieren, indem Sie empfohlene Präfixbereiche und vorkonfigurierte Netzrichtlinien verwenden.
 * Sie können Ihre IBM Cloud VPC-Instanz entsprechend an Ihre wechselnden Anforderungen nahtlos anpassen.
 * Sie können einen eigenen IP-Bereich angeben.
 * Sie können eine variable IP-Adresse aus einem bereits vorhandenen Pool zuordnen.
 * Lastausgleich und VPN verfügen über Steuerebenen für mehrere Regionen, was bedeutet, dass jede Region, in der die Steuerebene implementiert ist, alle Regionen für die virtuellen Serverinstanzen eines Kunden unterstützen kann. Ein Fehler in einer einzelnen Region hat keine Auswirkungen auf den Service in einer anderen Region.

### Globale Konnektivität
Sie können Ihre Anwendungen und die verfügbaren Ressourcen auf mehrere Regionen verteilt verwenden. Über ein VPN können Sie private Verbindungen zu anderen Projekten und Teilen Ihrer Hybrid-Cloudbereitstellung erstellen.

### Netzsicherheit
Die Sicherheit ist in Form von Sicherheitsgruppen, die als virtuelle Firewalls für den Schutz auf Instanzebene dienen, und Netzzugriffssteuerungslisten (ACLs) für den Schutz auf Teilnetzebene in Ihre IBM Cloud-VPC integriert.

### Lastausgleich
Verwenden Sie in Ihrer IBM Cloud-VPC den Lastausgleich, um den Netzverkehr zur Verbesserung der Leistung und Hochverfügbarkeit (HA, High Availability) auf eine Reihe von Zielen zu verteilen. Lastausgleichsfunktionen überwachen zudem den Allgemeinzustand Ihrer Anwendungen und Services. Sie können eine Lastausgleichsfunktion einrichten, um den eingehenden Anwendungsdatenverkehr über Instanzen in einer einzigen Zone oder über mehrere Zonen in einer Region zu verteilen.

### Internetzugriff
Es stehen zwei Optionen zur Verfügung, mit denen die Kommunikation zwischen den virtuellen Serverinstanzen (VSIs) und dem öffentlichen Internet ermöglicht wird:
* Verwenden Sie ein öffentliches Gateway (PGW, Public Gateway), um die Kommunikation für alle Instanzen des virtuellen Servers auf dem angeschlossenen Teilnetz zu aktivieren. Es fällt außer für die verwendete Bandbreite keine Gebühr für die Verwendung eines PGW an.
* Verwenden Sie eine variable IP-Adresse (FIP, Floating-IP), um die Kommunikation von einer einzelnen virtuellen Serverinstanz (VSI) zu ermöglichen.

![IBM Cloud VPC](images/vpc-experience.png)
**Abbildung: Eine Beispielkonfiguration für IBM Cloud VPC**

## Unterstützung für Cloud-native Workloads

Eine VPC ist ideal für Cloud-native Workloads und für die Verknüpfung Ihrer vorhandenen Infrastruktur mit IBM Cloud. Sie können die beste Cloud für alle wichtigen Workloads, wie Cognitive Computing, KI und Machine Learning, erstellen. Gleichzeitig können Sie weiterhin bei Bedarf die klassische Variante von IBM Cloud für traditionelle Workloads verwenden.

Nachfolgend finden Sie einige Beispiele dafür, wie VPC Cloud-tolerante und Cloud-native Hybrid-Workloads unterstützt:

 * Isolierte Anwendungsumgebungen über eine API erstellen und verwalten
 * Netztopologien mit BYOIP (Bring Your Own IP) gestalten
 * Sicherheitsgruppen und Netzzugriffssteuerungslisten (ACLs) für flexible, API-gesteuerte Topologien nutzen
 * Verfügbarkeitszonen ermöglichen schnelle Verbindungen mit hoher Verfügbarkeit & niedriger Latenz über verschiedene Regionen hinweg
 * Automatische Skalierung
   * Scale-up oder Scale-down von Tausenden von Servern pro Tag durchführen
   * Skalierbaren und zuverlässigen Lastausgleich mit Zertifikatsmanagement verwenden
   * Skalierbare und zuverlässige Überwachung einrichten
   * Illusion von unbegrenzter Kapazität für Ihre Kunden aufrechterhalten
 * Hochgeschwindigkeitsnetze und schnelle Speichereinheiten verwenden
 * Always-Services ermöglichen (Steuerebene)
 * Mehrere Regionen für Disaster-Recovery und Ausfallsicherheit abdecken
 * Kernservices bereitstellen und verwenden: IPAM, VPN, Firewalls, SSH, DNS und L4-Lastausgleich (Layer 4)
 * Weitere Services konfigurieren: automatische Skalierung, CDNs, NFV von Drittanbietern
 * Schnelle VSI-Bereitstellung mit Affinität und Anti-Affinität zulassen
 * Flexibles Image-Management mit vorab gespeicherten Images verwenden
 * Unterstützung für GPUs anbieten

## Zusammenfassung der Vorteile

 * Schnelleinstieg in die Verwendung vordefinierter Konfigurationen für die Instanzen, die als Profile bezeichnet werden
 * Flexibler geografischer Anwendungsbereich mit weltweit verfügbaren Zonen und Regionen
 * Sicher von Grund auf mit ACLs und Sicherheitsgruppen
 * Einfache Skalierung und gemeinsame Nutzung; ein VPC-Netz und die zugehörigen Ressourcen können sich von Ihrer On-Premises-Einrichtung bis in die Cloud erstrecken
 * Workloads für optimale Leistung und Effizienz überwachen

## Zusammenfassung der Funktionen

  * Teilnetze erstellen und eigenen IP-Bereich einbringen
  * Virtuelle Serverinstanzen (VSIs) mithilfe von Ubuntu 16.04, CentOS 7.x, Windows oder Debian erstellen und verwalten
  * Variable IPv4-Adresse reservieren und zuordnen
  * Internetzugriff auf Teilnetze durch Erstellung eines öffentlichen Gateways (PGW, eines pro Zone) erhalten
  * Sicherheitsgruppen erstellen und Ihren VSIs zuordnen
  * Netzzugriffssteuerungslisten (ACLs) verwenden, um die Sicherheit für Ihre Teilnetze zu gewährleisten
  * Einfach vernetzte (single-homed) VSIs mit einer einzelnen virtuelle Netzschnittstellenkarte (vNIC)
  * Mehrfach vernetzte (multi-homed) VSIs mit mehreren virtuellen Netzschnittstellenkarten (vNIC)
  * Zonenbereitstellung in der Region 'USA (Süden)' oder 'FRA'
  * Internetzugriff über VPN
  * Lastausgleich, der nativ für VPC ist

## BYOIP - Vorbehalte

Sie können mit BYOIP (Bring your own IP) Ihren eigenen öffentlichen IPv4-Adressbereich in Ihr IBM Cloud VPC-Konto einbringen. Wenn Sie BYOIP verwenden, muss IBM Cloud diese IPv4-Adressen für IBM Cloud-Ressourcen konfigurieren, die Pakete an und von diesen von Ihnen bereitgestellten Adressen senden. Daher können diese IP-Adressen als Ergebnis der Verwendung des bereitgestellten IPv4-Bereichs in IBM Cloud den IBM Support-Mitarbeitern und Dritten im Rahmen Ihrer Nutzung dieses Service bereitgestellt werden.
{: important}

Sie müssen die API oder die Befehlszeilenschnittstelle (CLI) verwenden, um BYOIP nutzen zu können. Diese erweiterte Funktionalität ist über die Benutzerschnittstelle der IBM Cloud-Konsole nicht verfügbar.
{: note}

Eine vollständige Liste der bekannten Einschränkungen und Funktionen, die derzeit nicht unterstützt werden, finden Sie im Abschnitt [Bekannte Einschränkungen](/docs/infrastructure/vpc?topic=vpc-known-limitations).

## Weitere Informationen

* [**Terminologie zu IBM VPC**](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**Sicherheit in IBM VPC**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**Verfügbare Regionen und Teilnetze für IBM VPC**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**Netzressourcen in VPC erstellen und verwalten**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [**Virtuelle Serverinstanzen erstellen und verwalten**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
