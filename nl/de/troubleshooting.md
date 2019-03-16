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

# Fehlerbehebung bei IBM Cloud VPC
{: #troubleshooting-your-ibm-cloud-vpc}

Dieser Abschnitt enthält allgemeine Probleme, die auftreten können, und bietet einige hilfreiche Tipps.

## `TRACE`-Modus bei Verwendung der Befehlszeilenschnittstelle aktivieren

Um bei der Verwendung der Befehlszeilenschnittstelle den `TRACE`-Modus (Debug) zu aktivieren, setzen Sie `IBMCLOUD_TRACE=true` vor den CLI-Befehl.

Zum Beispiel:

 ```
IBMCLOUD_TRACE=true ibmcloud is pubgws
```

## Verwendung des DEBUG- oder 'verbose'-Modus bei Verwendung der API

Sie können beispielsweise '--verbose' zu Ihrem 'curl'-Befehl hinzufügen und den Wert für 'X-Request-Id:' an den Support senden, sodass das Problem behoben werden kann. Das Flag `--verbose` ist besonders hilfreich, wenn Konnektivitätsprobleme auftreten.

Eine weitere Möglichkeit besteht darin, das Flag '-i' dem 'curl'-Befehl hinzuzufügen, damit das Support-Team die Header in der Antwort Ihrer Anfrage sehen kann. Dieses Flag ist in den meisten Situationen hilfreich, wenn Sie sich an den Support wenden müssen.

## API-Aufrufe erfordern ein Bearer-Token

Wenn Sie die API mit einem cURL-Befehl verwenden, müssen Sie möglicherweise "Bearer" in den Berechtigungsheader aufnehmen, je nachdem, was sich im '$iam_token' befindet. Wenn das Token das Wort "Bearer" enthält, wird es nicht wieder in den Header aufgenommen. Die meisten der Beispiele gehen davon aus, dass "Bearer" in den Header eingeschlossen ist.

## Verwendung eines anderen Endpunkts für CLI

Wenn Sie den Endpunkt ändern möchten, den die {{site.data.keyword.cloud}}-CLI standardmäßig für RIAS verwendet, legen Sie die Umgebungsvariable 'IBMCLOUD_IS_API_ENDPOINT' fest, bevor Sie die CLI verwenden. Beispiel:

```
export IBMCLOUD_IS_API_ENDPOINT=api.dev.domain.com
```
{: pre}


## Allgemeine Probleme

Hier sind einige Probleme, die auftreten können.

### Nicht autorisiert (401- oder 403-Fehler)

Ihr Konto ist möglicherweise nicht für VPC autorisiert. Stellen Sie sicher, dass Sie ein Konto verwenden, für das ein Onboarding durchgeführt wurde.

### Ressourcen können nicht erstellt werden

Wenn Sie keine VPC oder andere Ressourcen erstellen können, stellen Sie sicher, dass der Eigner des Kontos Ihnen die richtigen [Berechtigungen](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) erteilt hat.

### Die Instanzen weisen alle einen unbekannten Status auf

Stellen Sie sicher, dass der Eigner des Kontos Ihnen die richtigen [Berechtigungen](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) zum Anzeigen und Verwalten von Instanzen erteilt hat.

### Keine Antwort von API

Wenn die API keine JSON mehr zurückgibt, ist es wahrscheinlich, dass Ihr IAM-Token abgelaufen ist und aktualisiert werden muss. Melden Sie sich erneut bei IBM Cloud an oder aktualisieren Sie Ihr Token, indem Sie 'iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $4; }')' ausführen.

### Fehler: 409 Konflikt beim Aufrufen einer Aktion für eine Instanz

Sie können bestimmte Instanzaktionen nicht aufrufen, wenn sich der Status Ihrer Instanz im Konflikt mit der Aktion befindet. Wenn der Instanzstatus beispielsweise 'Gestoppt' lautet und Sie versuchen, eine Aktion 'Neu starten' auszuführen, gibt das System einen Fehler 409 zurück.

| Status          | Aktion     | Konflikt          |
| --------------- | ---------- | ----------------- |
| Aktiv           | Starten    | ja                |
| Gestoppt        | Belieb. Aktion, aber starten   | ja       |
| Nicht aktiv     | Anhalten   | ja                |
| Nicht aktiv     | Neu starten| ja                |
| Nicht angehalten| Fortsetzen | ja                |
| Angehalten      | Belieb. Aktion, aber fortsetzen| ja      |


### Instanz antwortet nicht auf Anforderung 'instance-reboot'

Wenn Ihre Instanz nicht auf die Anforderung 'instance-reboot' antwortet, können Sie es mit einer Anforderung des Typs 'instance-reset' versuchen. Sie können 'instance-reboot' als Anforderung für einen Warmstart und 'instance-reset' als Anforderung für einen Kaltstart sehen. Die Anforderung 'instance-reboot' sendet eine Anforderung zum Warmstart des Betriebssystems an die Instanz, während die Anforderung 'instance-reset' einen Kaltstart der VSI-Instanz durchführt. Sie sollten sich das als den Unterschied vorstellen, wenn Sie einerseits 'Strg-Alt-Entf' auf der Tastatur Ihres Computers eingeben und andererseits den Reset- oder Netzschalter drücken. Es sollte bedacht werden, dass die Anforderung 'instance-reset' länger zum Ausführen benötigt als die Anforderung 'instance-reboot'.

### Ressourcen können nicht gelöscht werden

Bestimmte Operationen, z. B. das Erstellen und Löschen von VSIs und das Erstellen und Löschen von Teilnetzen, werden asynchron über die API ausgeführt. Aus diesem Grund wird empfohlen, die Ressourcen abzufragen, die Sie gerade löschen, bevor Sie fortfahren, um zu prüfen, ob das Löschen der Ressourcen erfolgt.

Aufgrund dieser asynchronen Operationen kann es einige Minuten dauern, bis Ressourcen aus dem System gelöscht werden. Um das Löschen zu erleichtern, wird empfohlen, in dieser Reihenfolge vorzugehen:

1. Instanzen löschen
2. Öffentliche Gateways löschen
3. Teilnetze löschen
4. VPCs löschen
