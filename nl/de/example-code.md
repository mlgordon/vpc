---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# VPC mithilfe der REST-APIs verwenden
{: #creating-a-vpc-using-the-rest-apis}

In diesem Leitfaden erfahren Sie, wie Sie {{site.data.keyword.cloud}} Virtual Private Cloud-Ressourcen mithilfe der Regional APIs (RIAS) von IBM Cloud erstellen.

## Voraussetzungen:

1. Installieren Sie die [IBM Cloud-CLI](https://cloud.ibm.com/docs/cli/index.html#overview).

## Schritt 1: Bei IBM Cloud anmelden, um ein IAM-Token abzurufen, das in den API-Aufrufen verwendet werden soll

Wenn Sie über ein föderiertes Konto verfügen, setzen Sie den folgenden Befehl ab:
```
ibmcloud login -sso
```
{: pre}

Andernfalls verwenden Sie den folgenden Befehl:

```
ibmcloud login
```
{: pre}

Dieser Befehl gibt eine URL zurück und fordert Sie zur Eingabe eines Kenncodes auf. Rufen Sie diese URL in Ihrem Browser auf und melden Sie sich an. Wenn Sie erfolgreich sind, erhalten Sie einen Einmalkenncode. Kopieren Sie diesen Kenncode und fügen Sie ihn als Antwort in die Eingabeaufforderung ein. Nach den Authentifizierungsschritten werden Sie aufgefordert, ein Konto auszuwählen. Beantworten Sie alle verbleibenden Eingabeaufforderungen, um die Anmeldung abzuschließen.

## Schritt 2: IBM IAM-Token (IAM, Identity and Access Management) abrufen

Der folgende Befehl ruft die IBM Cloud-CLI auf, ermittelt die Kennung des IAM-Token und des `Bearer`-Token durch eine Syntaxanalyse und speichert diese als Variable, die Sie zu einem späteren Zeitpunkt in anderen Befehlen verwenden können.

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 Um das IAM-Token anzuzeigen, führen Sie den Befehl ``echo $iam_token`` aus.

Das Ergebnis sollte wie folgt aussehen:

```
Bearer <ihr token>
```
{: screen}

Der Berechtigungsheader erwartet, dass das Token mit "Bearer" beginnt. Wenn das Ergebnis oben nicht "Bearer" enthält, aktualisieren Sie die Variable `iam_token` so, dass "Bearer" eingeschlossen wird. Diese Beispiele setzen voraus, dass "Bearer" in `iam_token` enthalten ist.

Sie müssen den vorherigen Schritt wiederholen, um das IAM-Token stündlich zu aktualisieren, da das Token entsprechend abläuft.
{: important}

## Schritt 3: API-Endpunkt als Variable speichern

Speichern Sie den API-Endpunkt in einer Variablen, sodass er später wiederverwendet werden kann. Die API-Endpunkte sind pro Region angegeben und folgen der Konvention `https://<region>.iaas.cloud.ibm.com`. Beispielsweise wird der API-Endpunkt `us-south` als `https://us-south.iaas.cloud.ibm.com` wiedergegeben.

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

Um zu überprüfen, ob diese Variable gespeichert wurde, führen Sie `echo $rias_endpoint` aus, und stellen Sie sicher, dass die Antwort nicht leer ist.

## Schritt 4: API zum Abrufen von Regionen ausführen

Wenn unerwartete Ergebnisse auftreten, fügen Sie nach dem `curl`-Befehl das Flag `--verbose` (Debug) hinzu, hinzu, um detaillierte Protokollierungsinformationen zu erhalten. Informationen zu den häufig auftretenden Fehlern finden Sie auch auf der [Fehlerbehebungsseite](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc).
{: tip}

Der folgende Befehl gibt die für VPC verfügbaren Regionen im JSON-Format zurück. Es sollte mindestens ein Objekt zurückgegeben werden.

Beachten Sie den erforderlichen Abfrageparameter `version` für jeden API-Befehl.
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Schritt 5: API zum Abrufen von Zonen ausführen

Der folgende Befehl gibt alle für VPC in der Region `us-south` verfügbaren Zonen im JSON-Format zurück. Es sollten mindestens drei Objekte zurückgegeben werden.

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Schritt 6: API zum Abrufen von Profilen ausführen

Der folgende Befehl gibt die für Ihre Instanzen verfügbaren Profile im JSON-Format zurück. Es sollte mindestens ein Objekt zurückgegeben werden.

Fügen Sie ` | json_pp ` nach dem 'curl'-Befehl hinzu, um eine lesbare JSON-Zeichenfolge zu erhalten.
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Wenn die API-Ausgabe durch die Seitenaufteilung begrenzt ist, legen Sie den Grenzwert höher als den Wert für `total_count` fest, z. B.:

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## Schritt 7: API zum Abrufen von Images ausführen

Der folgende Befehl gibt die für Ihre Instanzen verfügbaren Images im JSON-Format zurück. Es sollte mindestens ein Objekt zurückgegeben werden.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Schritt 8: API zum Abrufen von VPCs ausführen

Der folgende Befehl gibt die VPCs zurück, die unter Ihrem Konto (falls vorhanden) im JSON-Format erstellt wurden.

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Schritt 9: VPC erstellen

Erstellen Sie eine IBM Cloud VPC-Instanz namens `my-vpc`.

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

Für den Rest der Anrufe müssen Sie die ID der neu erstellten IBM Cloud VPC-Instanz kennen. Fügen Sie die ID in die Variable ein, wie nachfolgend dargestellt:

Beispiel: `vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<ihre_vpc-id>"
```
{: pre}

## Schritt 10: Teilnetz erstellen

Erstellen Sie ein Teilnetz in der IBM Cloud VPC-Instanz. Erstellen Sie es beispielsweise in der Zone `us-south-2`.

```bash
curl -X POST $rias_endpoint/v1/subnets?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-subnet",
        "ipv4_cidr_block": "10.0.1.0/24",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Speichern Sie die ID des Teilnetzes wie bei der VPC in einer Variablen.

```bash
subnet="<ihre_teilnetz-id>"
```
{: pre}

## Schritt 11: Status des Teilnetzes überprüfen

Damit Ressourcen im Teilnetz bereitgestellt werden können, muss das Teilnetz den Status `available` (verfügbar) aufweisen. Fragen Sie die Teilnetzressource ab und stellen Sie sicher, dass der Status `available` lautet, bevor Sie fortfahren. Falls der Status `failed` (fehlgeschlagen) lautet, wenden Sie sich mit den entsprechenden Details an den [Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support). Sie können versuchen fortzufahren, indem Sie versuchen, ein weiteres Teilnetz bereitzustellen.

```bash
curl $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Schritt 12: Öffentliches Gateway erstellen

Um Instanzen virtueller Server im Teilnetz Zugriff auf das öffentliche Internet zu ermöglichen, fügen Sie dem Teilnetz ein öffentliches Gateway (PGW) hinzu.  

```bash
curl -X POST $rias_endpoint/v1/public_gateways?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-gateway",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Wie bei der VPC-Instanz und dem Teilnetz speichern Sie die ID des öffentlichen Gateways in einer Variablen.

```bash
gateway="<ihre_gateway-id>"
```
{: pre}

## Schritt 13: Öffentliches Gateway an das Teilnetz anhängen

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## Schritt 14: SSH-Schlüssel erstellen

Erstellen Sie einen Schlüssel mit dem öffentlichen SSH-Schlüssel. Dieser Schlüssel wird beim Erstellen der virtuellen Serverinstanz verwendet und wird benötigt, um sich bei der virtuellen Serverinstanz anzumelden.

```bash
curl -X POST $rias_endpoint/v1/keys?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-key",
        "public_key": "ssh-rsa AAA....n",
        "type": "rsa"
      }'
```
{: pre}

Speichern Sie die ID des Schlüssels in einer Variablen.

```bash
key="<ihre_schlüssel-id>"
```
{: pre}

## Schritt 15: Profil und Image für die virtuelle Serverinstanz auswählen

Führen Sie die APIs aus, um alle Profile und Images aufzulisten, die für Ihre virtuelle Serverinstanz verfügbar sind, und wählen Sie eine Kombination aus.

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

Wenn Sie weitere Details zu den Profilen abrufen möchten, können Sie den globalen Katalog mit Hilfe des IBM Cloud-CLI-Befehls `ibmcloud catalog entry <profile-name> --json` abfragen. Zum Beispiel:

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

Mit dem folgenden Befehl werden die verfügbaren Images aufgelistet.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

Speichern Sie den Namen des Profils und die ID des Images in Variablen, die später für die Bereitstellung einer virtuellen Serverinstanz verwendet werden.

```bash
profile_name="<ausgewählter_profilname>"
image_id="<ausgewählte_image-id>"
```
{: pre}

## Schritt 16: Instanz eines virtuellen Servers bereitstellen

Stellen Sie eine virtuelle Serverinstanz in dem neu erstellten Teilnetz bereit. Geben Sie Ihren öffentlichen SSH-Schlüssel an, damit Sie sich anmelden können, nachdem die Instanz bereitgestellt wurde.

```bash
curl -X POST $rias_endpoint/v1/instances?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "server-1",
        "type": "virtual",
        "zone": {
          "name": "us-south-2"
        },
        "vpc": {
          "id": "'$vpc'"
        },
        "primary_network_interface": {
          "port_speed": 1000,
          "subnet": {
            "id": "'$subnet'"
          }
        },
        "keys":[{"id": "'$key'"}],
        "flavor": {
          "name": "'$profile_name'"
         },
        "image": {
          "id": "'$image_id'"
         },
        "userdata": ""
      }'
```
{: pre}

Speichern Sie die ID der virtuellen Serverinstanz wie bei den anderen Ressourcen in einer Variablen.

```bash
server="<ihre_instanz-id>"
```
{: pre}

## Schritt 17: Status der Instanz des virtuellen Servers überprüfen

Die Bereitstellung einer virtuellen Serverinstanz kann einige Sekunden bis Minuten dauern. Bevor Sie fortfahren, fragen Sie den Status des Servers ab und stellen Sie sicher, dass der Server aktiv (`running`) ist.

```bash
curl $rias_endpoint/v1/instances/$server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Speichern Sie außerdem die ID der primären Netzschnittstelle der Instanz des virtuellen Servers, die im oben genannten API-Aufruf zurückgegeben wurde.  

```bash
network_interface="<ihre_netzschnittstellen-id>"
```
{: pre}

Sie können die primäre Netzschnittstelle erst abrufen, wenn Sie die spezielle Instanz abfragen.
{: note}

## Schritt 18: Variable IP-Adresse erstellen

Erstellen Sie eine variable IP-Adresse für die virtuelle Serverinstanz, indem Sie die primäre Netzschnittstelle der Instanz als Ziel für die neue variable IP-Adresse verwenden.

```bash
curl -X POST $rias_endpoint/v1/floating_ips?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-server-floatingip",
        "target": {
            "id":"'$network_interface'"
        }
      }
'
```
{: pre}


Speichern Sie die ID der variablen IP-Adresse.

```bash
floating_ip="<id_der_variablen_ip-adresse>"
```
{: pre}

## Schritt 19: Verbindung mit SSH zur virtuellen Serverinstanz herstellen

Um eine Verbindung mit SSH zum Server herzustellen, verwenden Sie die `Adresse` der von Ihnen erstellen variablen IP-Adresse. Führen Sie den folgenden Befehl aus, um die Adresse (`address`) der variablen IP-Adresse abzurufen:

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Verwenden Sie die `Adresse` der variablen IP-Adresse, um eine Verbindung zur virtuellen Serverinstanz mit SSH herzustellen:

```bash
ssh -i <private_schlüsseldatei> root@<variable_ip-adresse>
```
{: pre}

Der SSH-Zugriff auf den virtuellen Server kann durch Sicherheitsgruppen verhindert werden. Wenn SSH-Zugriff erforderlich ist, müssen Sie eine [entsprechende Sicherheitsgruppe](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups) verwenden.
{: note}

Weitere Informationen zum Herstellen einer Verbindung zu Ihrer Instanz finden Sie im Abschnitt zum [Herstellen einer Verbindung zu Ihrer Instanz unter Verwendung von Linux](/docs/vsi-is/vsi_is_connecting_linux_gc.html).


## Schritt 20 (Optional): Ressourcen löschen

Löschen Sie die Ressourcen bei Bedarf. Eine Ressource kann nicht gelöscht werden, wenn sie andere Ressourcen enthält. Beispiel: Eine VPC kann nicht gelöscht werden, wenn sie Teilnetze enthält, und ein Teilnetz kann nicht gelöscht werden, wenn es virtuelle Serverinstanzen enthält. Bei einem Löschvorgang kann es sein, dass die API den Vorgang schnell als abgeschlossen anerkennt, der Löschvorgang jedoch noch läuft. Es wird empfohlen, die Ressource abzufragen, um sicherzustellen, dass sie vor dem Löschen anderer Ressourcen gelöscht wird.

### Löschen Sie die variable IP-Adresse.

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Löschen Sie die Instanz des virtuellen Servers.

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Löschen Sie den Schlüssel.

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### Löschen Sie das öffentliche Gateway.

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Löschen Sie das Teilnetz.

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Löschen Sie die VPC.

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Da vNICs nicht aus einer virtuellen Serverinstanz (VSI) gelöscht werden können, ist kein Schritt zum Löschen von vNICs erforderlich.
{: note}

## Herzlichen Glückwunsch!

Sie haben erfolgreich eine VPC-Instanz mithilfe der REST-APIs bereitgestellt. Wenn Sie weitere API-Befehle testen möchten, sollten Sie sich die vollständige Referenz ansehen:

* [API-Referenz für VPC](https://{DomainName}/apidocs/rias)
