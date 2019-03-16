---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---
# Kontingente
{: #quotas}

Dieser Abschnitt enthält Informationen zu Kontingenten und Limits für Ihre {{site.data.keyword.cloud}} Virtual Private Cloud-Instanz und die darin verfügbaren Ressourcen.

## VPC-Kontingente

Konten haben folgende Kontingente:

|   Ressource     | Maximale Anzahl |
| ------- | :------: |
| Virtual Private Clouds | 5 pro Konto |
| VPCs mit klassischem Zugriff | 1 pro Region, pro Konto |
| Öffentliche Gateways (PGWs) | 1 pro Zone |
| Adresspräfixe | 5 pro VPC pro Zone |

## Teilnetzkontingente

|   Ressource     | Maximale Anzahl |
| ------- | :------: |
| Teilnetze | 15 pro VPC |


## VSI-Kontingente
|   Ressource     | Maximale Anzahl |
| ------- | :------: |
| Virtuelle Serverinstanzen (VSIs) | Standardmäßig 100 pro Konto |
| vNICs pro VSI | 5 pro VSI |
| Variable IP-Adressen | 1 pro VSI |
| SSH-Schlüssel | 100 pro Konto |


## Kontingente für Sicherheitsgruppen

Für Sicherheitsgruppen und die zugehörigen Regeln sind einige kontobasierte Kontingente (Grenzwerte) vorhanden.

|Ressource|Kontingent|
|--------|-----|
|Sicherheitsgruppen|5 pro Netzschnittstelle|
|Sicherheitsgruppen|500 pro Konto|
|Regeln|50 pro Sicherheitsgruppe|
|Ferne Regeln |5 pro Sicherheitsgruppe|
|Netzschnittstellen|100 pro Sicherheitsgruppe|

## ACL-Kontingente

|Ressource|Kontingent|
|--------|-----|
|ACLs| 30 pro Konto|
|ACLs|200 pro Region |
|Eingangsregeln|20 pro ACL |
|Ausgangsregeln |20 pro ACL |

## VPN-Kontingente

Nachfolgend finden Sie die aktuellen Beschränkungen für VPN-Ressourcen pro Konto:

|Ressource|Kontingent|
|--------|-----|
| VPN-Gateways| 7 pro Konto |
| VPN-Gateways| 3 pro Zone |
| VPN-Verbindungen | 10 pro VPN-Gateway |
| IKE-Richtlinien | 20 pro Konto |
| IPSec-Richtlinien | 20 pro Konto |
| Peer-Teilnetze für ein beliebiges VPN-Gateway | 50 für alle VPN-Verbindungen|
| Peer-Teilnetze  | 15 für eine einzelne VPN-Verbindung|
| Lokale Teilnetze für ein einzelnes VPN-Gateway | 50 für alle VPN-Verbindungen|
| Lokale Teilnetze | 15 für eine einzelne VPN-Verbindung|


## Kontingente für Lastausgleichsfunktion

Nachfolgend finden Sie die aktuellen Ressourcenkontingente für die Lastausgleichsfunktion:

|Ressource|Kontingent|
|--------|-----|
| Lastausgleichsfunktion | 50 pro Konto |
| Listener | 10 pro Lastausgleichsfunktion |
| Pool | 10 pro Lastausgleichsfunktion |
| Mitglied | 50 pro Pool |
