---

copyright:

  years: 2018, 2019

lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}

# Fehlernachrichten in der IBM Cloud Virtual Private Cloud-API
{: #rias-error-messages}

Wenn Sie eine Fehlernachricht von den {{site.data.keyword.cloud}} Virtual Private Cloud-APIs erhalten, können Sie die Nachrichten-ID verwenden, um weitere Informationen zur Lösung des Problems zu erhalten.
{:shortdesc}

## acl_in_use
**Nachricht**: Die Netz-ACL kann nicht gelöscht werden, weil sie an Ressourcen angehängt ist.

Die Netz-ACL kann nicht gelöscht werden, weil sie mit Ressourcen verbunden ist. Versuchen Sie, Ihre Teilnetze zu überprüfen.

## address_prefix_conflict
**Nachricht**: Das Adresspräfix mit diesem CIDR wird verwendet.

Der CIDR für das angeforderte Adresspräfix steht in Konflikt mit einem vorhandenen Adresspräfix.

## address_prefix_in_use
**Nachricht**: Ein Adresspräfix, das aktuell verwendet wird, kann nicht gelöscht werden.

Ein oder mehrere Teilnetze verwenden das Adresspräfix. Sie müssen die Zuordnung aller Teilnetze aufheben, bevor Sie ein Präfix löschen können.

## backend_service_unavailable
**Nachricht**: Der Back-End-Service ist nicht verfügbar.

Ein Back-End-Cloud-Service konnte nicht antworten. Ein Grund für den Empfang dieses Fehlers könnte ein fehlendes IAM-Token oder ein abgelaufenes IAM-Token sein. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, wenden Sie sich an den Support.

## bad_field
**Nachricht**: Korrekte Instanz-UUID muss angegeben werden.

Es sollte ein neuer Datenträgername angegeben werden.

Versuchen Sie es erneut und geben Sie in Ihrer Anforderung eine gültige UUID oder einen gültigen Datenträger an. 

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## bad_request                                   
**Nachricht**: Die angegebenen Informationen waren ungültig, fehlerhaft oder es fehlt ein erforderliches Feld.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## classic_access_vpc_conflict_duplicate_res
**Nachricht**: Es kann nur eine VPC mit klassischem Zugriff erstellt werden.

Es kann nicht mehr als eine VPC mit klassischem Zugriff für ein Konto erstellt werden.

## default_address_prefix_not_found
**Nachricht**: Das Standardadresspräfix wurde nicht gefunden.

Diese Fehlernachricht wird möglicherweise angezeigt, wenn das Standardadressenpräfix nicht gefunden wird.

## duplicate_error
**Nachricht**: Die bereitgestellte Eingabe ist bereits vorhanden.

Die von Ihnen angegebene Ressource ist bereits vorhanden. Um dieses Problem zu beheben, verwenden Sie einen anderen Namen für die Ressource, die Sie erstellen möchten. Wenn Sie beispielsweise eine neue VPC erstellen, können Sie eine Namensliste für die bereits erstellten VPCs überprüfen und einen Namen auswählen, der keinen Konflikt verursacht, wenn Sie zuerst `get VPC` unter Verwendung der ID aufrufen, z. B. `GET "/v1/vpcs/{id}” -H  "accept: application/json"`. 

## floating_ip_in_use
**Nachricht**: Die variable IP-Adresse wird verwendet.

Diese variable IP-Adresse ist bereits einer Netzschnittstelle oder einem öffentlichen Gateway zugeordnet.

## floating_ip_not_empty
**Nachricht**: Löschen eines Servers mit einer variablen IP-Adresse nicht möglich.

Heben Sie die Zuordnung der variablen IP-Adresse unbedingt auf, bevor Sie den Server löschen. 

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## gateway_too_many
**Nachricht**: Es kann nur ein öffentliches Gateway pro Zone in einer VPC vorhanden sein.

Es ist nur ein öffentliches Gateway pro Zone in einer VPC zulässig, aber das öffentliche Gateway kann mehreren Teilnetzen in der Zone zugeordnet werden. Um das öffentliche Gateway für eine Zone zu finden, führen Sie die API "GET public_gateways" aus und sehen Sie sich die Werte für "vpc" und "zone" an. Wenn Sie die CLI verwenden, können Sie den Befehl `ibmcloud is public-gateways` ausführen und den Wert für "vpc" und "zone" anzeigen.

Verwenden Sie die ID des öffentlichen Gateways, um sie einem Teilnetz zuzuordnen. Sehen Sie sich hierzu ein Beispiel in den [API-Beispielen](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis#step-13-attach-the-public-gateway-to-the-subnet-) an. Wenn Sie die CLI verwenden, können Sie den Befehl zum Aktualisieren des Teilnetzes verwenden, um es einem öffentlichen Gateway zuzuordnen, z. B. `ibmcloud is subnet-update TEILNETZ-ID --public-gateway-id ID_DES_ÖFFENTLICHEN_GATEWAYS`.


## http_request_size_exceeded                    
**Nachricht**: Die HTTP-Anforderung ist zu groß.

Dieses Problem tritt auf, wenn die von Ihnen in Ihrer Anforderung gesendeten Nutzdaten zu viele Zeichen enthalten. Versuchen Sie es erneut mit einer kleineren Nutzlast. Anstatt zu versuchen, alles in einer einzigen Anforderung zu verarbeiten, versuchen Sie, eine minimale Ressource in einer Anforderung zu erstellen und anschließend den Status in mehreren nachfolgenden Anforderungen inkrementell entsprechend anhängen. 

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## iam_failure
**Nachricht**: Keine

Diese Nachricht kann angezeigt werden, wenn im IAM-Service ein Fehler bei der Authentifizierung oder Autorisierung aufgetreten ist. Diese Ausfallzeit des IAM-Service kann temporär sein. Wiederholen Sie die Anforderung nach einigen Minuten. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policies_quota_exceeded
**Nachricht**: Das Kontingent für IKE-Richtlinien wurde für das Konto überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen IKE-Richtlinien anzuzeigen, verwenden Sie die API `GET /ike_policies`.

## ike_policy_duplicate_name
**Nachricht**: Der Name `<ike_policy_name>` wird bereits von der IKE-Richtlinie `<ike_policy_id>` verwendet.

Geben Sie einen anderen IKE-Richtlinienname an. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policy_in_use
**Nachricht**: Die IKE-Richtlinie `<ike_policy_id>` wird von mindestens einer anderen Verbindung verwendet.

Eine IKE-Richtlinie kann nicht gelöscht werden, wenn sie von einer oder mehreren Verbindungen verwendet wird.

## ike_policy_invalid_name
**Nachricht**: Der Name `<ike_policy_name>` ist kein gültiger IKE-Richtlinienname.

Ein gültiger IKE-Richtlinienname beginnt mit einem Buchstaben, gefolgt von Buchstaben, Ziffern, Unterstrichen oder Bindestrichen.

## ike_policy_not_found
**Nachricht**: Die IKE-Richtlinie `<ike_policy_id>` wurde nicht gefunden.

Sie haben auf eine IKE-Richtlinie verwiesen, die nicht vorhanden ist. Überprüfen Sie Ihre Anforderung, um sicherzustellen, dass Sie die richtige IKE-Richtlinien-ID angegeben haben. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## insufficient_space_for_subnet
**Nachricht**: Unzureichender Platz für Teilnetz in Adresspräfix.

Dieser Fehler kann auftreten, wenn Sie versuchen, ein Teilnetz zu erstellen und das Teilnetz nicht erstellt werden kann, da die Anzahl der angeforderten Adressen nicht zugeordnet werden kann.

## internal_error
**Nachricht**: Es ist ein interner Fehler aufgetreten.

Versuchen Sie es erneut. Tritt dieser Fehler weiterhin auf, wenden Sie sich an den Support.

## internal_server_error
**Nachricht**: Keine

Dieser Fehler tritt auf, wenn für den Service ein unerwarteter Fehler auftritt. Dieses Problem kann temporär sein. Wiederholen Sie die Anforderung in ein paar Minuten.

Bleibt das Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## internal_solution
**Nachricht**: Wenden Sie sich an Ihren Administrator.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_id_format
**Nachricht**: Fehlerhaftes ID-Format. Stellen Sie sicher, dass das Format korrekt ist.

Stellen Sie sicher, dass die ID, die Sie angegeben haben, keine fehlerhaften Daten enthält.

Dieser Fehler kann aufteten, wenn eine fehlerhafte Startabfrage beim Herstellen einer Anforderung für die Seitenaufteilung verwendet wird. Beispiel:
`GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` enthält zwei Fragezeichen (`?`). Korrigieren Sie die Abfrage und versuchen Sie es erneut.

## invalid_state
**Nachricht**: Keine

Der RIAS-Befehl `ibmcloud is in-reboot Instance_uuid` kann den Nachrichtencode "invalid_state" zurückgeben.

Die Nachricht wird in einer Situation ausgegeben, in der versucht wird, eine Warmstartoperation auszuführen, während die VSI bereits neu gestartet wird. Diese Nachricht kann auch in einer Situation empfangen werden, in der mehrere Warmstarts nicht gleichzeitig stattfinden.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_version
**Nachricht**: Der Parameter `version` ist ungültig. Er muss das Format `JJJJ-MM-TT` haben.

Die Version muss das Format _JJJJ-MM-TT_ einhalten. Für einstellige Monats- oder Datumsangaben, wie z. B. den 1. Januar, sollte die Version folgendermaßen aussehen: `2019-01-01`. Der Versionsparameter muss in der URL vorhanden sein. Das im Versionsparameter angegebene Datum muss nach '2019-01-01' und vor dem aktuellen Datum liegen. Wenn Sie beispielsweise eine Liste mit VPCs abrufen möchten, hängen Sie die Version am Ende der Anforderung `GET "/v1/vpcs?version=2019-01-01”` an.

## invalid_version_range
**Nachricht**: Der Wert für `version` kann nicht auf ein zukünftiges Datum oder auf ein Datum vor `2019-01-01` gesetzt werden.

Die Version muss das Format _JJJJ-MM-TT_ einhalten. Für einstellige Monats- oder Datumsangaben, wie z. B. den 1. Januar, sollte die Version folgendermaßen aussehen: `2019-01-01`. Der Versionsparameter muss in der URL vorhanden sein. Das im Versionsparameter angegebene Datum muss nach '2019-01-01' und vor dem aktuellen Datum liegen. Wenn Sie beispielsweise eine Liste mit VPCs abrufen möchten, hängen Sie die Version am Ende der Anforderung `GET "/v1/vpcs?version=2019-01-01”` an.

## invalid_zone
**Nachricht**: Überprüfen Sie, ob die Ressourcen, die Sie anfordern, sich in derselben Zone befinden.

Diese Nachricht wird möglicherweise angezeigt, wenn die angeforderte Ressource nicht in einer gültigen Zone ist.

## ipsec_policies_quota_exceeded
**Nachricht**: Das Kontingent für IPsec-Richtlinien wurde für das Konto überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen IPsec-Richtlinien anzuzeigen, verwenden Sie die API `GET /ipsec_policies`.

## ipsec_policy_duplicate_name
**Nachricht**: Der Name `<ipsec_policy_name>` wird bereits von der IPsec-Richtlinie `<ipsec_policy_id>` verwendet.

Geben Sie einen anderen IPsec-Richtliniennamen an. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ipsec_policy_in_use
**Nachricht**: Die IPsec-Richtlinie `<ipsec_policy_id>` wird von mindestens einer anderen Verbindung verwendet.

Eine IPsec-Richtlinie kann nicht gelöscht werden, wenn sie von einer oder mehreren Verbindungen verwendet wird.

## ipsec_policy_invalid_name
**Nachricht**: Der Name `<ipsec_policy_name>` ist kein gültiger IPsec-Richtlinienname.

Ein gültiger IPsec-Richtlinienname beginnt mit einem Buchstaben, gefolgt von Buchstaben, Ziffern, Unterstrichen oder Bindestrichen.

## ipsec_policy_not_found
**Nachricht**: Die IPsec-Richtlinie `<ipsec_policy_id>` wurde nicht gefunden.

Sie haben auf eine IPsec-Richtlinie verwiesen, die nicht vorhanden ist. Überprüfen Sie Ihre Anfrage und stellen Sie sicher, dass Sie die richtige IPsec-Richtlinien-ID angegeben haben. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## key_exists
**Nachricht**: Der gleiche Schlüsselinhalt ist bereits vorhanden.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## listener_certificate_not_found
**Nachricht**: Zertifikatinstanzen mit dem CRN `<listener_certificate_crn>` wurden nicht gefunden oder Sie haben keine Berechtigung für den Zugriff auf die Zertifikatinstanz.

Geben Sie einen vorhandenen CRN für die Zertifikatsinstanz an oder bitten Sie Ihren Kontoadministrator, Ihnen Zugriffsberechtigungen für die bereitgestellte Zertifikatinstanz zu erteilen.

## listener_duplicate_port
**Nachricht**: Port `<listener_port>` wird von einer anderen Listenerinstanz verwendet. Wählen Sie einen anderen Port aus.

Wählen Sie einen anderen Port aus.

## listener_invalid_certificate
**Nachricht**: Der CRN der Zertifikatsinstanz für den HTTPS-Listener ist ungültig.

Geben Sie einen gültigen CRN für die Zertifikatinstanz an.

## listener_invalid_connection_limit
**Nachricht**: Limit `<listener_connection_limit>` für Listenerverbindung ist ungültig.

Geben Sie ein gültiges Verbindungslimit an. Das Verbindungslimit muss eine ganze Zahl zwischen 1 und 15000 sein.

## listener_invalid_port
**Nachricht**: Listener-Port `<listener_port>` ist ungültig.

Wählen Sie einen anderen Port aus.

## listener_invalid_protocol
**Nachricht**: Das Listenerprotokoll `<listener_protocol>` ist ungültig.

Geben Sie ein gültiges Listenerprotokoll an. Zulässige Werte für das Listenerprotokoll sind `http`, `https` und `tcp`.

## listener_missing_certificate_crn
**Nachricht**: CRN der Zertifikatinstanz für den `https `-Listener fehlt.

Der CRN der Zertifikatinstanz ist ein erforderliches Feld.

## listener_missing_port
**Nachricht**: Der Listener-Port fehlt.

Der Listener-Port ist ein erforderliches Feld.

## listener_missing_protocol
**Nachricht**: Das Listenerprotokoll fehlt.

Das Listenerprotokoll ist ein erforderliches Feld. Geben Sie das Listenerprotokoll in Ihrer Anforderung an. Die zulässigen Werte sind `http`, `https` und `tcp`.

## listener_not_found
**Nachricht**: Der Listener mit der ID `<listener_id>` wurde nicht gefunden.

Geben Sie eine vorhandene Listener-ID an.

## listener_over_quota
**Nachricht**: Der Listener kann nicht erstellt werden. Das Kontingent von Listener für die Ressource der Lastausgleichsfunktion hat den Maximalwert erreicht.

Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window} angegeben.

## listener_pool_protocols_conflict
**Nachricht**: Das Listenerprotokoll (`<listener_protocol>`) und das Poolprotokoll (`<pool_protocol>`) stehen in Konflikt.

Ein Listener mit dem Protokoll `https` oder `http` kann nur einem Pool mit dem Protokoll `http` zugeordnet werden. In ähnlicher Weise kann ein `tcp`-Listener nur einem `tcp`-Pool zugeordnet werden.

## listener_reserved_port_conflict
**Nachricht**: Der Listener-Port `<listener_port>` ist einer der reservierten Ports. Der Portbereich 56500 bis 56520 ist für Verwaltungszwecke reserviert. Wählen Sie einen anderen Port aus.

Wählen Sie einen anderen Port aus.

## load_balancer_duplicate_name
**Nachricht**: Der Name `<load_balancer_name>` wird von einer anderen Instanz der Lastausgleichsfunktion verwendet. Wählen Sie einen anderen Namen aus.

Geben Sie einen anderen Namen für die Instanz der Lastausgleichsfunktion an.

## load_balancer_invalid_description
**Nachricht**: Die Beschreibung `<load_balancer_description>` der Lastausgleichsfunktion ist ungültig.

Die Beschreibung der Lastausgleichsfunktion darf 255 Zeichen nicht überschreiten.

## load_balancer_invalid_is_public
**Nachricht**: Der Wert von 'is_public' für `<load_balancer_is_public>` ist ungültig.

Der Wert von 'is_public' der Lastausgleichsfunktion sollte entweder 'true' oder 'false' sein.

## load_balancer_invalid_is_public_value
**Nachricht**: Es werden nur öffentliche Lastausgleichsfunktionen unterstützt.

Private Lastausgleichsfunktionen werden noch nicht unterstützt.

## load_balancer_invalid_name
**Nachricht**: Der Name `<load_balancer_name>` ist ungültig.

Der Name darf nicht leer sein. Die Länge des Namens darf 40 Zeichen nicht überschreiten. Ein gültiger Name für die Lastausgleichsfunktion beginnt mit einem Buchstaben gefolgt von Buchstaben, Ziffern und Unterstrichen.

## load_balancer_missing_is_public
**Nachricht**: Das Feld 'is_public' fehlt.

'is_public' ist ein erforderliches Feld. Geben Sie das Feld 'is_public' der Lastausgleichsfunktion an.

## load_balancer_missing_name
**Nachricht**: Der Name der Lastausgleichsfunktion fehlt.

Geben Sie den Namen der Lastausgleichsfunktion an. Der Name der Lastausgleichsfunktion ist ein erforderliches Feld.

## load_balancer_missing_subnets
**Nachricht**: Die Teilnetze der Lastausgleichsfunktion fehlen.

'subnets' ist ein erforderliches Feld. Geben Sie die Teilnetze an, in denen die Lastausgleichsfunktion in Ihrer Anforderung erstellt werden soll.

## load_balancer_not_found
**Nachricht**: Die Lastausgleichsfunktion mit der ID `<load_balancer_id>` wurde nicht gefunden.

Geben Sie eine vorhandene Lastausgleichs-ID an.

## load_balancer_over_quota
**Nachricht**: Die Lastausgleichsfunktion kann nicht erstellt werden. Das Kontingent von Instanzen der Lastausgleichsfunktion unter Ihrem Konto hat den Maximalwert erreicht.

Löschen Sie eine vorhandene Lastausgleichsfunktion oder wenden Sie sich an den Support, um das Kontingent der Lastausgleichsfunktion für Ihr Konto zu erhöhen.

Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window} angegeben.

## load_balancer_unchanged_update
**Nachricht**: Es gibt nichts, mit dem die ID `<load_balancer_id>` der Lastausgleichsfunktion aktualisiert werden kann.

Es gibt nichts, um die Instanz der Lastausgleichsfunktion zu aktualisieren.

## member_invalid_port
**Nachricht**: Der angegebene Mitgliedsport `<member_port>` ist ungültig.

Geben Sie eine gültige Portnummer an. Eine gültige Portnummer liegt zwischen 1 und 65535.

## member_invalid_weight
**Nachricht**: Die angegebene Gewichtung `<member_weight>` für das Mitglied ist ungültig.

Geben Sie eine gültige Gewichtung für das Mitglied an. Es muss eine ganze Zahl zwischen 0 und 100 sein.

## member_missing_address
**Nachricht**: Die Mitgliedsadresse fehl.

Die Mitgliedsadresse ist ein erforderliches Feld. Geben Sie die Mitgliedsadresse in Ihrer Anforderung an.

## member_missing_protocol_port
**Nachricht**: Der Mitgliedsport fehlt.

Der Mitgliedsport ist ein erforderliches Feld. Geben Sie den Mitgliedsport in Ihrer Anforderung an.

## member_over_quote
**Nachricht**: Das Mitglied kann nicht erstellt werden. Das Kontingent von Mitgliedsinstanzen unter dem Pool hat den Maximalwert erreicht.

Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window} angegeben.

## missing_ims_account_id
**Nachricht**: Keine

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## missing_version
**Nachricht**: Der Parameter `version` ist erforderlich und muss das Format `JJJJ-MM-TT` haben.

Die Version muss das Format _JJJJ-MM-TT_ einhalten. Für einstellige Monats- oder Datumsangaben, wie z. B. den 1. Januar, sollte die Version folgendermaßen aussehen: `2019-01-01`. Der Versionsparameter muss in der URL vorhanden sein. Das im Versionsparameter angegebene Datum muss nach '2019-01-01' und vor dem aktuellen Datum liegen. Wenn Sie beispielsweise eine Liste mit VPCs abrufen möchten, hängen Sie die Version am Ende der Anforderung an: `GET "/v1/vpcs?version=2019-01-01”`.cs?version=2019-01-01”`.

## network_conflict
**Nachricht**: CIDR-Konflikte mit vorhandenem Adresspräfix in VPC.

Diese Nachricht wird möglicherweise angezeigt, wenn Sie ein Netz-CIDR angeben, das mit einem vorhandenen Netz-CIDR in demselben IP-Bereich in Konflikt steht.

## not_authorized                               
**Nachricht**: Die Anforderung ist nicht autorisiert.

Ein häufiger Grund, warum Sie diesen Fehler sehen, ist ein fehlendes oder abgelaufenes IAM-Token. Anweisungen zum Generieren eines Tokens finden Sie im Abschnitt [VPC mit den REST-APIs erstellen](/docs/infrastructure/vpc/example-code.html#creating-a-vpc-using-the-rest-apis). Wenn das Token nicht abgelaufen ist, müssen Sie möglicherweise Ihre Berechtigungen überprüfen und sich an Ihren Administrator wenden. 

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_found
**Nachricht**: Überprüfen Sie, ob die Ressource, die Sie anfordern, vorhanden ist.

Sie haben auf eine Ressource verwiesen, die nicht vorhanden ist, oder auf eine Ressource, auf die Sie keinen Zugriff haben. Überprüfen Sie Ihre Anforderung, um sicherzustellen, dass Sie die richtigen IDs und Verweise angegeben haben.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_implemented
**Nachricht**: Keine

Die Methode ist nicht implementiert.

## not_in_address_prefix
**Nachricht**: Der angegebene CIDR passt in keine der Adresspräfixe in der bereitgestellten Zone.

Dieser Fehler tritt auf, wenn ein Benutzer versucht, ein Teilnetz mit einem CIDR zu erstellen, das nicht in die Adresspräfixe für die angegebene Zone fällt.

Führen Sie 'GET /vpcs/{vpc_id}/adresspräfixe' aus, um die Liste der Adresspräfixe für die VPC abzurufen. Sehen Sie sich die Werte für `cidr` und `zone` der Antwort an und stellen Sie sicher, dass der Wert für `cidr` des Teilnetzes eine Untergruppe von `cidr` des Adresspräfixes für die Zone ist, die Sie erstellen möchten.

## over_quota                                    
**Nachricht**: Die Anforderung würde das Kontingent für einen Ressourcentyp überschreiten.

Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window} angegeben.

## password_not_ready
**Nachricht**: Keine

Ihre Instanz muss aktiv sein, bevor Sie eine variable IP-Adresse zuordnen können. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, wenden Sie sich an den Support.

## pool_delete_conflict
**Nachricht**: Der Pool kann nicht gelöscht werden, weil er immer noch einem oder mehreren Listenern zugeordnet ist.

Stellen Sie sicher, dass die Zuordnung zwischen Pool und Listener aufgehoben wurde und wiederholen Sie den Vorgang.

## pool_duplicate_name
**Nachricht**: Der Poolname `<pool_name>` wird bereits von einem anderen Pool verwendet. Wählen Sie einen anderen Namen aus.

Wählen Sie einen anderen Poolnamen aus.

## pool_missing_algorithm
**Nachricht**: Der Lastausgleichsalgorithmus fehlt.

Der Lastausgleichsalgorithmus ist ein erforderliches Feld. Geben Sie den Lastausgleichsalgorithmus in Ihrer Anforderung an. Die zulässigen Werte sind `round_robin`, `weighted_round_robin` und `least_connections`.

## pool_missing_health_monitor
**Nachricht**: Der Diagnosemonitor für den Pool fehlt.

Der Diagnosemonitor für den Pool ist ein erforderliches Feld.

## pool_missing_name
**Nachricht**: Der Poolname fehlt.

Der Poolname ist ein erforderliches Feld.

## pool_missing_protocol
**Nachricht**: Das Poolprotokoll fehlt.

Das Poolprotokoll ist ein erforderliches Feld. Geben Sie das Poolprotokoll in Ihrer Anforderung an. Die zulässigen Werte sind `http` und `tcp`.

## pool_not_found
**Nachricht**: Der Pool mit der ID `<pool_id>` wurde nicht gefunden.

Geben Sie eine vorhandene Pool-ID an.

## pool_over_quota
**Nachricht**: Der Pool kann nicht erstellt werden. Das Kontingent von Pools für die Ressource der Lastausgleichsfunktion hat den Maximalwert erreicht.

Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window} angegeben.

## public_gateway_in_use
**Nachricht**: Ein öffentliches Gateway kann nicht gelöscht werden, wenn es im Gebrauch ist.

Das öffentliche Gateway ist derzeit an ein oder mehrere Teilnetze angeschlossen. Sie müssen das öffentliche Gateway von allen Teilnetzen abhängen, bevor Sie es löschen können.

## rate_limit_exceeded
**Nachricht**: Zu viele Anforderungen innerhalb einer kurzen Zeit.

Diese Fehlernachricht wird zurückgegeben, wenn zu viele Anforderungen innerhalb eines angegebenen Zeitintervalls empfangen werden. Warten Sie eine Weile und versuchen Sie es erneut. 

## security_group_active_transactions
**Nachricht**: Die Schnittstelle kann erst angehängt oder abgehängt werden, wenn die Instanz einen aktiven Status aufweist.

Die Instanz muss aktiv sein, bevor ihre Netzschnittstellen einer Sicherheitsgruppe zugeordnet werden können. Verwenden Sie `GET /v1/instances/{id}?version=2019-01-01` oder `ibmcloud is instance`, um den Status der Instanz zu überprüfen. Sobald der Status `running` (aktiv) ist, versuchen Sie es erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_already_attached
**Nachricht**: Die Schnittstelle ist bereits der Sicherheitsgruppe zugeordnet.


Die Schnittstelle ist bereits der Sicherheitsgruppe zugeordnet. Verwenden Sie `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` oder `ibmcloud is security-group-network-interfaces`, um die zugeordneten Schnittstellen anzuzeigen.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_exists
**Nachricht**: Die Sicherheitsgruppe ist bereits vorhanden.


Sicherheitsgruppennamen müssen eindeutig sein. Es ist bereits eine Sicherheitsgruppe mit diesem Namen vorhanden. Verwenden Sie `GET /v1/security_groups?version=2019-01-01` oder `ibmcloud is security-groups`, um die aktuellen Sicherheitsgruppen anzuzeigen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias) oder dem [Dokument zum Verwenden von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_attached
**Nachricht**: Die Sicherheitsgruppe kann nicht gelöscht werden, während Schnittstellen zugeordnet sind.


Heben Sie die Zuordnung für alle Schnittstellen auf, bevor Sie die Sicherheitsgruppe löschen. Verwenden Sie `DELETE /v1/security_groups/{id}/network_interfaces/` oder `ibmcloud is security-group-network-interface-remove`, um die Zuordnung einer Schnittstelle aufzuheben.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias) oder dem [Dokument zum Verwenden von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_per_sg_exceeded
**Nachricht**: Das Limit der Schnittstellen pro Sicherheitsgruppe wurde überschritten.

Das Zuordnen einer weiteren Schnittstelle zu der Sicherheitsgruppe würde das Limit der Schnittstellen pro Sicherheitsgruppe überschreiten. Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas) {: new_window} angegeben. Bewerten Sie Ihre Strategie und überlegen Sie, eine weitere Sicherheitsgruppe mit ähnlichen Regeln zu erstellen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias) oder dem [Dokument zum Verwenden von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_last_security_group_is_default
**Nachricht**: Die Standardsicherheitsgruppe kann nicht entfernt werden, wenn sie die einzige zugeordnete Sicherheitsgruppe ist.

Eine Netzschnittstelle muss mindestens einer Sicherheitsgruppe zugeordnet sein.
Sie wird der Standardsicherheitsgruppe der VPC zugeordnet, wenn keine Sicherheitsgruppe angegeben ist.
Hängen Sie die Schnittstelle an eine andere Sicherheitsgruppe an und versuchen Sie erneut, sie von der Standardsicherheitsgruppe abzuhängen.
Informationen zur Standardsicherheitsgruppe finden Sie im [Dokument zur Verwendung von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_limit_exceeded
**Nachricht**: Das Limit für die Sicherheitsgruppe wurde überschritten.

Sie haben versucht, eine neue Sicherheitsgruppe zu erstellen, aber Sie bewegen sich derzeit im Rahmen Ihres Kontokontingents. Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window} angegeben. Bewerten Sie Ihre Strategie für die Zuordnung von Instanzen zu Sicherheitsgruppen. Es ist häufig möglich, die Gesamtzahl der Sicherheitsgruppen durch die Zuordnung mehrerer Instanzen zu derselben Sicherheitsgruppe zu reduzieren. Mit dieser Strategie wird die Anzahl der Sicherheitsgruppen reduziert und Sie bleiben im Rahmen des Kontingents für Ihr Konto. In einigen wenigen Fällen, in der Regel für große Organisationen, besteht die Notwendigkeit, das Kontingent zu erweitern. In diesem Fall [wenden Sie sich bitte an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support), um zu erfragen, ob dies möglich ist.

## security_group_network_interface_not_active
**Nachricht**: Die Schnittstelle kann nicht zugeordnet werden, da sie nicht aktiv ist.

Netzschnittstellen müssen aktiv sein, bevor sie mit Sicherheitsgruppen verbunden werden. Verwenden Sie `GET /v1/instances/{id}/network_interfaces/{id}?version=2019-01-01` oder `ibmcloud is instance-network-interface`, um den Status einer Schnittstelle anzuzeigen. Sobald der Status 'available' (verfügbar) lautet, versuchen Sie es erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_not_attached
**Nachricht**: Die Schnittstelle ist nicht zugeordnet.

Die Schnittstelle ist der Sicherheitsgruppe nicht zugeordnet. Verwenden Sie `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` oder ` ibmcloud is security-group-network-interfaces`, um die zugeordneten Schnittstellen anzuzeigen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias) oder dem [Dokument zum Verwenden von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group-using-the-cli){: new_window}.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_not_in_vpc
**Nachricht**: Die Schnittstelle und die Sicherheitsgruppe befinden sich in verschiedenen VPCs.

Wenn eine Netzschnittstelle einer Sicherheitsgruppe zugeordnet werden soll, muss sich die Instanz in derselben VPC wie die Sicherheitsgruppe befinden. Verwenden Sie `GET /v1/security_groups/{id}?version=2019-01-01` oder `ibmcloud is security-group`, um die Sicherheitsgruppendetails und die VPC anzuzeigen. Mit `GET /v1/instances/{id}?version=2019-01-01` oder `ibmcloud is instance` können Sie die Instanzdetails und die VPC anzeigen.

## security_group_order_bindings
**Nachricht**: Die Sicherheitsgruppe kann nicht gelöscht werden, solange noch Aufträge für Instanzen vorhanden sind.

Wenn eine Instanz erstellt wurde und Sicherheitsgruppen für die Netzschnittstelle angegeben sind, müssen die Instanz und Netzschnittstellen aktiv sein, bevor die Sicherheitsgruppe gelöscht werden kann. Verwenden Sie `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` oder `ibmcloud is security-group-network-interfaces`, um die zugeordneten Netzschnittstellen und deren Status anzuzeigen. Sobald der Status der Schnittstellen 'available' (verfügbar) lautet, versuchen Sie es erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_port_max_less_than_port_min
**Nachricht**: Der maximale Wert für den TCP/UDP-Port kann nicht kleiner sein als der Mindestwert für den Port.

Der maximale Wert für den Port kann nicht kleiner sein als der Mindestwert für den Port. Geben Sie einen maximalen Portwert an, der größer als der minimale Portwert ist.

## security_group_port_range_both_or_neither
**Nachricht**: Der Portbereich darf nicht festgelegt sein oder es müssen sowohl der minimale und maximale Portbereich für 'tcp' und 'udp' festgelegt sein.

Regeln mit dem 'tcp'- oder 'udp'-Protokoll weisen möglicherweise einen nicht festgelegten Portbereich auf (um die Regel auf den gesamten Datenverkehr anzuwenden) oder sie können einen Portbereich angeben. Um den Datenverkehr auf einen einzelnen Port zu beschränken, setzen Sie sowohl den minimalen als auch den maximalen Port auf den Portwert. Der folgende Befehl würde z. B. eine Regel erstellen, um SSH an Port 22 zu ermöglichen: `ibmcloud is security-group-rule-add <id> inbound tcp --port-min 22 --port-max 22`.

Weitere Informationen zu den Konfigurationen der Sicherheitsgruppenregeln finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias).


## security_group_port_range_invalid_protocol
**Nachricht**: Es wurde ein Portbereich mit einem Protokoll 'icmp' angegeben. Ein Portbereich ist nur für ein Protokoll des Typs 'tcp' oder 'udp' gültig.

Regeln mit einem Protokoll des Typ 'icmp' haben einen Typ und Code. Regeln mit den Protokollen 'tcp' oder 'udp' weisen einen Portbereich auf. Weitere Informationen zu den Konfigurationen der Sicherheitsgruppenregeln finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias).

## security_group_remote_group_not_in_vpc
**Nachricht**: Die ferne Gruppe befindet sich nicht in derselben VPC wie diese Sicherheitsgruppe.

Sicherheitsgruppenregeln können sich auf eine ferne Sicherheitsgruppe beziehen, die den Datenaustausch zwischen verbundenen Schnittstellen der beiden Gruppen ermöglicht. Ferne Sicherheitsgruppen müssen sich in derselben VPC befinden. Verwenden Sie `GET /v1/security_groups?2019-01-01` oder `ibmcloud is security-groups`, um die aktuellen Sicherheitsgruppen und deren VPCs anzuzeigen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie im [Dokument zum Verwenden von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules
**Nachricht**: Die Sicherheitsgruppe kann nicht gelöscht werden, während die Regeln für das Remoting angehängt sind.

Die Sicherheitsgruppe enthält eine oder mehrere Regeln, die auf eine ferne Sicherheitsgruppe verweisen. Verwenden Sie `GET /v1/security_groups/{id}/rules?version=2019-01-01` oder `ibmcloud is security-group-rules`, um die Regeln anzuzeigen. Im Feld 'remote' werden alle fernen Sicherheitsgruppen angegeben. Wiederholen Sie den Vorgang, nachdem Sie die Regel für das Remoting gelöscht oder bearbeitet haben.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias) oder dem [Dokument zum Verwenden von Sicherheitsgruppen](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules_per_sg_exceeded
**Nachricht**: Das Limit der Regeln für das Remoting pro Sicherheitsgruppe wurde überschritten.


Das Hinzufügen einer weiteren Regel, die sich auf eine ferne Sicherheitsgruppe bezieht, würde das Limit der Regeln für das Remoting pro Sicherheitsgruppe überschreiten. Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window} angegeben.


## security_group_rules_per_sg_exceeded
**Nachricht**: Das Limit der Regeln pro Sicherheitsgruppe wurde überschritten.

Das Hinzufügen einer Regel würde das Limit der Regeln pro Sicherheitsgruppe überschreiten. Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window} angegeben. Bewerten Sie Ihre Strategie und ziehen Sie in Betracht, eine weitere Sicherheitsgruppe zu erstellen.


## security_group_sgs_per_interface_exceeded
**Nachricht**: Das Limit der Sicherheitsgruppen pro Schnittstelle wurde überschritten.

Die Zuordnung dieser Schnittstelle zu einer anderen Sicherheitsgruppe würde das Limit der Sicherheitsgruppen pro Schnittstelle überschreiten. Die Kontingente pro Ressource sind im Abschnitt [Kontingente und Limits für VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window} angegeben. Bewerten Sie Ihre Strategie und ziehen Sie in Betracht, Regeln zu einer vorhandenen Sicherheitsgruppe hinzuzufügen.


## security_group_type_code_invalid_protocol
**Nachricht**: Es wurde der Typ/Code 'icmp' angegeben, das angeforderte Protokoll war jedoch nicht 'icmp'. Setzen Sie das Protokoll auf 'icmp' oder geben Sie einen Portbereich an.

Nur Regeln mit dem 'icmp'-Protokoll haben einen Typ und einen Code. Regeln mit den 'tcp'- oder 'udp'-Protokoll weisen einen Portbereich auf. Weitere Informationen zu den Konfigurationen der Sicherheitsgruppenregeln finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias).

## security_group_vpc_default
**Nachricht**: Die Standardsicherheitsgruppe für eine VPC kann nicht gelöscht werden.

Die Standardsicherheitsgruppe kann nicht gelöscht werden. Informationen zur Standardsicherheitsgruppe finden Sie im Leitfaden zum [Aktualisieren der Standardsicherheitsgruppe](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group).

## service_manager_service_failure
**Nachricht**: Keine

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_acl_conflict
**Nachricht**: Die Netz-ACL kann nicht gelöscht werden, da sie einem Teilnetz zugeordnet ist.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_conflict
**Nachricht**: Das CIDR steht im Konflikt mit dem vorhandenen Teilnetz in VPC.

Führen Sie die API zum Abrufen von Teilnetzen aus, um alle Teilnetze in VPC abzurufen. Stellen Sie sicher, dass das von Ihnen bereitgestellte CIDR nicht von anderen Teilnetzen verwendet wird, indem Sie den Wert von `ipv4_cidr_block` überprüfen.

Wenn Sie die CLI verwenden, können Sie den Befehl `ibmcloud is subnets` ausführen und den Wert für "Teilnetz-CIDR" auf mögliche Konflikte überprüfen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty
**Nachricht**: Das Teilnetz ist nicht leer. Wenden Sie sich an Ihren Administrator.

Es gab eine Anforderung zum Löschen des Teilnetzes, dieses enthält jedoch noch Ressourcen. Teilnetze können Instanzen, VPNs, Lastausgleichsfunktionen oder öffentliche Gateways enthalten. Sie müssen Ihre Ressourcen in dem Teilnetz löschen, bevor Sie das Teilnetz löschen können. 

In einigen Situationen kann dieser Fehler auch auftreten, wenn die Konsole 0 VSIs und 0 Lastausgleichsfunktionen anzeigt, da das Löschen asynchron ist und es einige Minuten dauern kann, bis der interne Status geändert wird. Wiederholen Sie die Teilnetzlöschung in ein paar Minuten.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_pgway_exists
**Nachricht**: Das Teilnetz kann nicht gelöscht werden, wenn es an ein öffentliches Gateway angeschlossen ist. Heben Sie die Zuordnung auf und versuchen Sie es erneut.

Es gab eine Anforderung zum Löschen eines Teilnetzes, diesem ist jedoch noch ein öffentliches Gateway zugeordnet. Sie müssen das öffentliche Gateway löschen oder die Zuordnung aufheben, bevor Sie das Teilnetz löschen können. 

Wenn Sie die CLI verwenden, können Sie den Befehl `ibmcloud is public-gateways` zum Auflisten der öffentlichen Gateways und den Befehl `ibmcloud is subnet-public-gateway-detach` zum Abhängen eines öffentlichen Gateways von einem Teilnetz ausführen. 

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_ipaddr_exists
**Nachricht**: Das Teilnetz kann nicht gelöscht werden, während es IP-Adressen enthält. Löschen Sie eine beliebige Serverinstanz, die der IP-Adresse zugeordnet ist, und wiederholen Sie den Vorgang.

Es gab eine Anforderung zum Löschen eines Teilnetzes, dieses enthält jedoch noch IP-Adressen. Sie müssen die Serverinstanz löschen, die der IP-Adresse zugeordnet ist, bevor Sie das Teilnetz löschen können.

Wenn Sie die CLI verwenden, können Sie den Befehl `ibmcloud is instances` zum Auflisten der Serverinstanzen ausführen und sich dann den Wert für "Address" ansehen, um die IP-Adresse zu ermitteln, und den Wert für "Status" zur Statusermittlung. Führen Sie den Befehl `ibmcloud is instance-delete` aus, um eine Serverinstanz zu löschen, die noch nicht den Status "deleting" (wird gelöscht) aufweist. 

In einigen Situationen kann dieser Fehler auch dann auftreten, wenn die Konsole 0 VSIs anzeigt, da das Löschen asynchron ist und es einige Minuten dauern kann, bis der interne Status geändert wird. Wiederholen Sie die Teilnetzlöschung in ein paar Minuten.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_loadbalancer_exists
**Nachricht**: Das Teilnetz kann nicht gelöscht werden, solange es eine Lastausgleichsfunktion enthält. Löschen Sie die Lastausgleichsfunktion und versuchen Sie es erneut.

Es gab eine Anforderung zum Löschen eines Teilnetzes, dieses enthält jedoch noch eine Lastausgleichsfunktion. Sie müssen die Lastausgleichsfunktion löschen, bevor Sie das Teilnetz löschen können.

Wenn Sie die CLI verwenden, können Sie den Befehl `ibmcloud is load-balancers` zum Auflisten der Lastausgleichsfunktionen ausführen und sich dann den Wert für "Teilnetze" ansehen, um das Teilnetz zu ermitteln, und den Wert "Status" zur Statusermittlung. Führen Sie den Befehl `ibmcloud is load-balancer-delete` aus, um eine Lastausgleichsfunktion zu löschen, die noch nicht den Status "deleting" (wird gelöscht) aufweist. 

In einigen Situationen kann dieser Fehler auch auftreten, wenn die Konsole 0 Lastausgleichsfunktionen anzeigt, da das Löschen asynchron ist und es einige Minuten dauern kann, bis sich der interne Status geändert hat. Wiederholen Sie die Teilnetzlöschung in ein paar Minuten.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_vpn_gway_exists
**Nachricht**: Das Teilnetz kann nicht gelöscht werden, solange es ein VPN-Gateway enthält. Löschen Sie das VPN-Gateway und versuchen Sie es erneut.

Es gab eine Anforderung zum Löschen eines Teilnetzes, diesem ist jedoch noch ein VPN-Gateway zugeordnet. Sie müssen das VPN-Gateway löschen, bevor Sie das Teilnetz löschen können. 

Wenn Sie die CLI verwenden, können Sie den Befehl `ibmcloud is vpn-gateways` zum Auflisten der VPN-Gateways ausführen und sich dann den Wert für "Teilnetze" ansehen, um das Teilnetz zu ermitteln, und den Wert "Status" zur Statusermittlung. Führen Sie den Befehl `ibmcloud is vpn-gateway-delete` aus, um ein VPN-Gateway zu löschen, die noch nicht den Status "deleting" (wird gelöscht) aufweist. 

In einigen Situationen kann dieser Fehler auch auftreten, wenn die Konsole 0 VPN-Gateways anzeigt, da das Löschen asynchron ist und es einige Minuten dauern kann, bis der interne Status geändert wird. Wiederholen Sie die Teilnetzlöschung in ein paar Minuten.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_unknown_state
**Nachricht**: Keine

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## system_limit_exceeded
**Nachricht**: Diese Operation würde eine Systembegrenzung überschreiten.

Ein mögliches Szenario für den Empfang dieser Fehlernachricht ist, wenn Sie versuchen, ein Adresspräfix zu erstellen, aber die maximale Anzahl von Adresspräfixen bereits vorhanden ist.

## target_in_use
**Nachricht**: Das Ziel verfügt bereits über eine variable IP-Adresse.

## token_invalid
**Nachricht**: Das Service-Token war abgelaufen oder ungültig.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## token_missing
**Nachricht**: Das Service-Token war leer oder nicht in der Anforderung vorhanden.

Erstellen Sie ein Token erneut und wiederholen Sie den Vorgang.

## validation_enum
**Nachricht**: Der angegebene Wert war keine gültige Option.

Eines der angegebenen Felder hat einen Wert, der aus einer Aufzählung möglicher Werte stammen muss.

Für ACL-Regeln für Netze können Sie eine Richtung angeben:

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum:
[ inbound, outbound ]
```

Der folgende Beispiel wäre beispielsweise ungültig, da `northbound` keine gültige Option in der Aufzählung `[ inbound, outbound ]` ist.

```json
{
    "direction":"northbound"
}
```

## validation_failure                            
**Nachricht**: Die angegebene JSON stimmt nicht mit der erwarteten Struktur überein.

Um dieses Problem zu beheben, stellen Sie sicher, dass der Inhalt Ihrer Anforderung eine gültige JSON ist und dass Ihre Anforderung dem entspricht, was in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window} angegeben ist.

## validation_invalid_cidr                       
**Nachricht**: Der Wert ist kein gültiges CIDR.

Der Wert muss ein gültiger interner CIDR-Block mit dem Host-Bit '0' (Hostteil) sein.

Bestimmte IP-Adressbereiche sind reserviert. Weitere Informationen zu den reservierten IP-Bereichen finden Sie in der Übersicht zur [Verwendung der VPC mit Regionen und Teilnetzen](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv4_cidr        
**Nachricht**: Der Wert ist kein gültiges IPv4-CIDR.

Der Wert muss ein gültiger interner IPv4-CIDR-Block mit dem Host-Bit '0' (Hostteil) sein.

Bestimmte IP-Adressbereiche sind reserviert. Weitere Informationen zu den reservierten IP-Bereichen finden Sie in der Übersicht zur [Verwendung der VPC mit Regionen und Teilnetzen](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv6_cidr
**Nachricht**: Der Wert ist kein gültiges IPv6-CIDR.

Derzeit wird IPv6 nicht unterstützt. Verwenden Sie eine IPv4-Adresse.

## validation_invalid_address
**Nachricht**: Der Wert ist keine gültige Adresse.

Muss eine gültige IP-Adresse sein.

Eine Liste der einzeln reservierten IP-Adressen ist im Dokument [Regionen und Teilnetze](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets) angegeben.

## validation_invalid_ipv4_address
**Nachricht**: Der Wert ist keine gültige IPv4-Adresse.

Geben Sie eine gültige IPv4-Adresse an.

## validation_invalid_ipv6_address
**Nachricht**: Der Wert ist keine gültige IPv6-Adresse.

Geben Sie eine gültige IPv6-Adresse an. Derzeit wird IPv6 nicht unterstützt; verwenden Sie eine IPv4-Adresse.

## validation_invalid_field_type
**Nachricht**: Der Werttyp stimmt nicht mit dem Feldtyp überein.

Um dieses Problem zu beheben, stellen Sie sicher, dass der Inhalt Ihrer Anforderung dem entspricht, was in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window} zu dem Endpunkt angegeben ist, den Sie aufrufen.

## validation_max_value
**Nachricht**: Der angegebene Wert war zu groß.

Geben Sie einen kleineren Wert an, der dem in der Spezifikation angegebenen Maximum entspricht. Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_min_value
**Nachricht**: Der angegebene Wert war zu klein.

Geben Sie einen größeren Wert an, der dem in der Spezifikation angegebenen Minimum entspricht. Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_not_null
**Nachricht**: Das angegebene Feld muss null sein.

Stellen Sie sicher, dass der Wert null ist. Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

Es folgt ein ungültiges Beispiel:

```json
{
    "name": null
}
```

## validation_only_one
**Nachricht**: Der Wert muss einem der Unterschemas entsprechen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_discriminator_forbidden
**Nachricht**: Das Diskriminatorfeld verbietet diese Unterstruktur.

Wenn Sie z. B. Folgendes angeben:
```
{
protocol: icmp
port_min: 5
port_max: 100
}
```

Das Protokoll ist `icmp` und _port_min_ ist ein `tcp`-Feld, sodass Sie einen Fehler erhalten.
1. validation_discriminator_required für fehlende `icmp`-Regeln
2. validation_discriminator_forbidden für `tcp`-Felder mit angegebenem Wert `icmp`

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_internal_error
**Nachricht**: Keine

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_invalid_name
**Nachricht**: Der Wert ist kein gültiger Name.


## validation_invalid_ref
**Nachricht**: Der Wert ist kein gültiges HREF-Attribut.


## validation_non_empty_uuid
**Nachricht**: Keine

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_required_field
**Nachricht**: Es fehlt ein erforderliches Feld.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_unique_failed
**Nachricht**: Das angegebene Feld muss eindeutig sein.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

Möglicherweise haben Sie einen Namen angegeben, der bereits verwendet wird. Versuchen Sie es mit einem anderen Wert.

## vpc_acl_conflict                           
**Nachricht**: Die Standardnetz-ACL kann nicht gelöscht werden, das sie an eine VPC angeschlossen ist.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias) oder dem [Dokument zum Verwenden von Netz-ACLs](/docs/infrastructure/vpc-network?topic=vpc-network-setting-up-network-acls-using-the-cli){: new_window}.

Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_not_empty
**Nachricht**: Die VPC kann nicht gelöscht werden, da sie nicht leer ist.

Alle Ressourcen müssen aus einer VPC entfernt werden, bevor sie gelöscht werden kann.

Dieser Fehler kann auftreten, wenn noch ein Gateway in Ihrer VPC vorhanden ist, selbst wenn alle Teilnetze gelöscht werden, da das Gateway in der VPC ohne Teilnetz existieren kann. Es kann erforderlich sein, die CLI zu verwenden, um nach verwaisten Ressourcen zu suchen.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_resource_separation
**Nachricht**: Die Ressourcen befinden sich in verschiedenen VPCs.

## vpn_connection_cidr_not_created
**Nachricht**: Ein CIDR-Block konnte der VPN-Verbindung `<vpn_connection_id>` nicht hinzugefügt werden.

Geben Sie ein gültiges CIDR an, das die in der Spezifikation angegebenen Anforderungen erfüllt. 

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_cidr_not_deleted
**Nachricht**: Ein CIDR-Block konnte nicht aus der VPN-Verbindung `<vpn_connection_id>` gelöscht werden.

Geben Sie ein gültiges CIDR an, das in der Verbindung vorhanden ist. Eine Verbindung muss über mindestens ein lokales und ein Peer-CIDR verfügen.

Um die CIDR-Blöcke der Verbindung anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` und überprüfen Sie die Felder `local_cidrs` und `peer_cidrs`.

## vpn_connection_cidr_not_found
**Nachricht**: Der CIDR-Block wurde in der VPN-Verbindung `<vpn_connection_id>` nicht gefunden.

Geben Sie ein gültiges CIDR an, die sich in der Verbindung befindet.

Um die CIDR-Blöcke der Verbindung anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` und überprüfen Sie die Felder `local_cidrs` und `peer_cidrs`.

## vpn_connection_cidr_not_valid
**Nachricht**: Der CIDR-Block `<cidr_block>` stellt keine gültige Adresse dar.

Der Wert muss ein gültiger interner CIDR-Block ohne festgelegte Hostbits sein.

Um die CIDR-Blöcke der Verbindung anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` und überprüfen Sie die Felder `local_cidrs` und `peer_cidrs`.

## vpn_connection_cidr_overlap
**Nachricht**: Der CIDR-Block `<cidr_block_1>` weist eine Überschneidung mit `<cidr_block_2>` auf. Zwei Peer-CIDR-Blöcke dürfen sich nicht auf derselben VPC überschneiden und zwei lokale CIDR-Blöcke dürfen sich nicht in derselben Verbindung überschneiden.

Geben Sie einen gültigen CIDR-Wert an, der die in der Spezifikation angegebenen Anforderungen erfüllt.

Um die CIDR-Blöcke der Verbindung anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` und überprüfen Sie die Felder `local_cidrs` und `peer_cidrs`.

## vpn_connection_duplicate_name
**Nachricht**: Der Name `<vpn_connection_name>` wird bereits von der VPN-Verbindung `<vpn_connection_id>` verwendet.

Geben Sie einen anderen Verbindungsnamen an. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_invalid_name
**Nachricht**: Der Name `<vpn_connection_name>` ist kein gültiger VPN-Verbindungsname.

Ein gültiger Verbindungsname beginnt mit einem Buchstaben, gefolgt von Buchstaben, Ziffern, Unterstreichungszeichen oder Bindestrichen.

## vpn_connection_invalid_psk_format
**Nachricht**: Der vorab bekannte gemeinsame Schlüssel (PSK, Pre-Shared Key) `<psk>` liegt nicht in einem gültigen Format vor.

Ein gültiger vorab bekannter gemeinsamer Schlüssel sollte nur 6 bis 128 Zeichen lang sein, bestehend aus Buchstaben, Ziffern, `-`,`+`,`&`,`!`,`@`,`#`,`$`,`%`,`^`,`*`,`(`,`)`,`,`,`.`,`:`,`_`.

## vpn_connection_local_cidrs_required
**Nachricht**: Beim Erstellen einer VPN-Verbindung ist mindestens ein lokaler CIDR-Block erforderlich.

Geben Sie einen gültigen lokalen CIDR-Wert an, der die in der Spezifikation angegebenen Anforderungen erfüllt.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_connection_local_subnets_quota_exceeded
**Nachricht**: Das Kontingent für lokale Teilnetze über VPN-Verbindungen hinweg wurde für VPN-Gateway `<vpn_gateway_id>` überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen lokalen Teilnetze für alle VPN-Verbindungen anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections` und überprüfen Sie für jede Verbindung das Feld `local_cidrs`.

## vpn_connection_local_subnets_quota_exceeded_for_connection
**Nachricht**: Das Kontingent '<größenbeschränkung>' für lokale Teilnetze für die VPN-Verbindung wurde überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vp?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen lokalen Teilnetze für eine VPN-Verbindung anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` und überprüfen Sie das Feld `local_cidrs`.

## vpn_connection_not_found
**Nachricht**: Die VPN-Verbindung `<vpn_connection_id>` wurde nicht gefunden.

Überprüfen Sie, ob die Verbindungs-ID richtig ist. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_peer_cidrs_required
**Nachricht**: Bei der Erstellung einer VPN-Verbindung ist mindestens ein Peer-CIDR-Block erforderlich.

Geben Sie einen gültigen Peer-CIDR-Wert an, der die in der Spezifikation angegebenen Anforderungen erfüllt.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_connection_peer_subnets_quota_exceeded
**Nachricht**: Das Kontingent für lokale Teilnetze über VPN-Verbindungen hinweg wurde für das VPN-Gateway `<vpn_gateway_id>` überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen Peer-Teilnetze für alle VPN-Verbindungen anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections` und überprüfen Sie für jede Verbindung das Feld `peer_cidrs`.

## vpn_connection_peer_subnets_quota_exceeded_for_connection
**Nachricht**: Das Kontingent `<quota_limit>` für Peer-Teilnetze für die VPN-Verbindung wurde überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen Peer-Teilnetze für eine VPN-Verbindung anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` und überprüfen Sie das Feld `peer_cidrs`.

## vpn_connections_quota_exceeded
**Nachricht**: Das Kontingent für VPN-Verbindungen wurde für das VPN-Gateway `<vpn_gateway_id>` überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen VPN-Verbindungen für ein VPN-Gateway anzuzeigen, verwenden Sie die API `GET /vpn_gateways/<vpn_gateway_id>/connections`.

## vpn_connection_static_route_not_created
**Nachricht**: Es konnte keine statische Route für den CIDR-Block `<peer_cidr>` hinzugefügt werden.

Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_static_route_not_deleted
**Nachricht**: Es konnte keine statische Route für den CIDR-Block `<peer_cidr>` entfernt werden.

Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_update_cidrs_not_permitted
**Nachricht**: Beim Aktualisieren einer Verbindung können CIDR-Blöcke nicht geändert werden. Verwenden Sie die richtige API beim Erstellen oder Löschen von CIDRs.

Geben Sie einen gültigen Anforderungswert an, der die in der Spezifikation angegebenen Anforderungen erfüllt.

Weitere Anweisungen zum Beheben dieses Problems finden Sie in der [API-Dokumentation](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_gateway_duplicate_name
**Nachricht**: Der Name `<vpn_gateway_name>` wird bereits vom VPN-Gateway `<vpn_gateway_id>` verwendet.

Geben Sie einen anderen VPN-Gateway-Namen an. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_initialization_error
**Nachricht**: Das VPN-Gateway konnte nicht initialisiert werden.

Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_invalid_name
**Nachricht**: Der Name `<vpn_gateway_name>` ist kein gültiger VPN-Gateway-Name.

Ein gültiger VPN-Gateway-Name beginnt mit einem Buchstaben, gefolgt von Buchstaben, Ziffern, Unterstreichungszeichen oder Bindestrichen.

## vpn_gateway_invalid_state
**Nachricht**: Das VPN-Gateway `<vpn_gateway_id>` weist für die angeforderte Operation einen ungültigen Status auf.

Das VPN-Gateway muss den Status `available` (verfügbar) haben, bevor Sie es betreiben können. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_ip_create_error
**Nachricht**: Es konnte keine IP-Adresse für das VPN-Gateway erstellt werden.

Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_not_found
**Nachricht**: Das VPN-Gateway `<vpn_gateway_id>` wurde nicht gefunden.

Überprüfen Sie, ob die VPN-Gateway-ID richtig ist. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_not_found
**Nachricht**: Das Teilnetz `<subnet_id>` wurde für das angegebene VPN-Gateway nicht gefunden.

Sie haben auf ein Teilnetz verwiesen, das nicht vorhanden ist. Überprüfen Sie Ihre Anforderung, um sicherzustellen, dass Sie die richtige Teilnetz-ID angegeben haben. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_status_error
**Nachricht**: Das VPN-Gateway konnte aufgrund des Teilnetzstatus nicht erstellt werden.

Geben Sie ein Teilnetz an, das sich im Status `available` (verfügbar) befindet. Versuchen Sie es in ein paar Minuten erneut. Bleibt dieses Problem bestehen, [wenden Sie sich an den Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateways_quota_exceeded
**Nachricht**: Das Kontingent für VPN-Gateways wurde für das Konto und/oder die Region überschritten.

Die Kontingente pro Ressource sind auf der Seite mit den [Kontingenten](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window} angegeben.

Um die aktuellen VPN-Gateways anzuzeigen, verwenden Sie die API `GET /vpn_gateways`.
