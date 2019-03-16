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


# Häufig gestellte Fragen (FAQs)
{: #faqs}

## Wie viele Zeichen darf ein VPC-Name maximal enthalten?
{:faq}

Derzeit ist der Grenzwert 100. Wenn dieser Grenzwert überschritten wird, kann eine Nachricht des Typs 'Interner Fehler' zurückgegeben werden.

## Kann ein VPC-Ressourcenname mit einer Zahl beginnen?
{:faq}

Nein. Obwohl der Name Zahlen enthalten darf, muss er mit einem Buchstaben beginnen.

## Gibt es Einschränkungen für die Zeichen, die ich in einem Namen verwenden kann?
{:faq}

Ja, die Benutzerschnittstelle blockiert aufeinanderfolgende doppelte Gedankenstriche, Unterstreichungszeichen und Punkte, die Teil eines VSI-Namens sind.


## Bei der Zuordnung einer variable IP-Adresse in einer VPC muss ein Kunde den vNIC der VSIs angeben, ist das richtig?
{:faq}

Ja, und es muss sich dabei um die primäre Netzschnittstelle eines Servers handeln.

Wenn jedoch eine Adressenressource in der API unter dem Netzbereich hinzugefügt wird, kann die Zuordnung der variablen IP zur Adresse (und nicht zur Schnittstelle) geändert werden.

## Kann ein vNIC in einer virtuellen Serverinstanz in meiner VPC sowohl eine virtuelle als auch eine private IP-Adresse haben?
{:faq}
 
Ja.

## In der Benutzerschnittstelle der IBM Cloud-Konsole für die VPC gibt es nur eine Umschaltfunktion für jedes Teilnetz zum An- oder Abhängen an/von dem öffentlichen Gateway (PGW). Wer erstellt das PGW? Nimmt das PGW standardmäßig den Status 'Ready' (Bereit) ein, wenn ein Kunde das Teilnetz an das PGW in der Benutzerschnittstelle anhängen möchte?
{:faq}

Das PGW muss derzeitig explizit über die API erstellt werden, da die API eine explizite Zuordnung eines Teilnetzes zu einem bestimmten öffentlichen Gateway benötigt.

## Stellen Sie sich vor, VSI1 in einer VPC verfügt nur über vNIC1 und ist an Teilnetz1 angehängt. Teilnetz1 ist an ein öffentliches Gateway (PGW) angeschlossen. Kann ein Kunde VSI1 immer noch eine variable IP-Adresse zuordnen?
{:faq}

Ja, ein Server kann sich in einem Teilnetz befinden, das an ein öffentliches Gateway angeschlossen ist und auch über eine variable IP-Adresse verfügt. Die Zuordnung der variablen IP zu einer VSI steht in keinerlei Beziehung dazu, ob ein öffentliches Gateway an das Teilnetz angeschlossen ist. Eine variable IP-Adresse, die einer VSI zugeordnet ist, hat Vorrang vor dem öffentlichen Gateway, das an das Teilnetz angeschlossen ist.

## In meiner VPC verfügt VSI1 über zwei vNICs namens vNIC1 und vNIC2. Können diese beiden vNICs an dasselbe Teilnetz angeschlossen werden?
{:faq}
 
Ja, es besteht keine Einschränkung für die Verwendung mehrerer Netzschnittstellen auf demselben Server, der demselben Teilnetz zugeordnet ist. Mehrere NICs in einer VSI werden derzeit jedoch nicht unterstützt.

## Kann eine VSI ohne Teilnetz nur mit variabler IP-Adresse erstellt werden?
{:faq}

Nein.

## Kann eine VSI mehr als einer VPC zugeordnet werden?
{:faq}

Nein.

## Kann die Größe eines Teilnetzes geändert werden, nachdem es in einer VPC erstellt wurde?
{:faq}

Nein.

## Muss ich während der Erstellung eines öffentlichen Gateways die variable IP-Adresse reservieren oder tut dies das System automatisch? Wird mir die variable IP-Adresse angezeigt, wenn ich alle variablen IP-Adressen abfrage?

Laut Spezifikation erstellt RIAS automatisch eine variable IP-Adresse zusammen mit dem öffentlichen Gateway, wenn keine vorhandene variable IP-Adresse angegeben ist. Und ja, diese variable IP-Adresse wird in der Liste angezeigt.

## Wer setzt durch, dass es nur ein öffentliches Gateway pro Zone für eine VPC geben darf?
{: faq}

Der Regional Infrastructure API Service (RIAS) erzwingt diese Begrenzung.

## Wie wirkt sich VRF auf meine anderen Netzfunktionen und meine Teilnetze aus?
{:faq}

Vorbehalte gegenüber VLANs und VRF:

* Das VLAN-Spanning zwischen Konten ist in der VRF-Umgebung nicht zulässig.
* Der IPsec-VPN-Service ist begrenzt.

**Hinweis:** VRF verhindert nicht den SSL- oder PPTP-VPN-Zugriff, das Verhalten ändert sich jedoch. Ohne VRF ist eine VPN-Verbindung ausreichend, um alle Server für Ihr Konto anzuzeigen. Mit VRF können Sie nur auf Ressourcen auf dem Markt zugreifen, die mit Ihrem VPN verbunden sind. Wenn Sie also eine Verbindung zum DAL-VPN herstellen, können Sie nur Verbindungen zu DAL-Servern herstellen.

## Wie kann der Unterbefehl `instance-network-interface-floating-ip-add` in VPC korrekt verwendet werden? Wird zuvor eine variable IP-Adresse erstellt/zugeordnet?
{:faq}

 Sie müssen zuerst eine variable IP-Adresse zuordnen und diese dann im Schnittstellenbefehl `add` der variablen IP-Adresse bereitstellen.

 Beispiel: `ibmcloud is floating-ip-reserve NAME_DER_VARIABLEN_IP (--zone ZONE | --nic NIC-ID)`. Geben Sie die Zone an.

 ## Warum muss ich ein Teilnetz angeben, wenn ich meine VPN für VPC einrichte, und was genau sollte ich angeben?
 {:faq}

Wenn Sie ein VPN-Gateway einrichten, müssen Sie ein Teilnetz angeben, damit das VPN-Gateway die für den VPN-Service vorausgesetzten IP-Adressen abrufen kann. Durch die Angabe des Teilnetzes behalten Sie die Kontrolle darüber, wie der VPN-Datenverkehr gehandhabt wird, und Sie haben die Flexibilität, eine Position anzugeben, die näher an den Ressourcen liegt, die das VPN nutzen. Auf diese Weise können Sie die Latenzzeit verringern und die Leistung verbessern. 

## Fallen für den abgehenden Datenverkehr von der VPC nach COS entsprechende Bandbreitengebühren an?
{:faq}

Es fallen keine Bandbreitengebühren für abgehenden Datenverkehr an, solange der ADN-Endpunkt für die Verbindung zwischen VPC und COS verwendet wird; Gebühren für API-Aufrufen gelten jedoch weiterhin.

## Wie weiß ich, wo meine Instanzen für den Lastausgleich bereitgestellt werden?
{:faq}

Die ausgewählten Teilnetze legen fest, wo die VPC-Lastausgleichsfunktion bereitgestellt wird. Die VPC-Lastausgleichsfunktion ist eine regionale Ressource. Das bewährte Verfahren ist die Auswahl von Teilnetzen aus verschiedenen Zonen in einer bestimmten Region, um die Redundanz zu erhöhen.
