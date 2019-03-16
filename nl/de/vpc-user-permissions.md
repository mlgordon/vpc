---

copyright:
  years: 2017, 2018, 2019

lastupdated: "2019-02-20"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Benutzerberechtigungen für VPC-Ressourcen verwalten
{: #managing-user-permissions-for-vpc-resources}

{{site.data.keyword.cloud}} Virtual Private Cloud verwendet die rollenbasierte Zugriffssteuerung, die es den Kontoadministratoren ermöglicht, den Zugriff ihrer Benutzer auf die VPC und andere Infrastrukturserviceressourcen zu steuern.

Weitere Informationen darüber, wie IBM Cloud VPC die rollenbasierte Zugriffssteuerung verwendet und wie die VPC die IAM-Rollen- und Zugriffsrichtlinien verwendet, finden Sie im Abschnitt [Rollenbasierten Zugriff auf VPC-Ressourcen zuordnen](/docs/infrastructure/vpc?topic=vpc-assigning-role-based-access-to-vpc-resources).

Dieses Dokument zeigt Ihnen, wie der Administrator des Kontos zusätzliche Benutzer zum Konto hinzufügen und ihnen die korrekten Berechtigungen für die Verwaltung von [VPC-Infrastrukturressourcen](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources) erteilen kann. Es deckt zwei gängige Szenarien für einen VPC-Administrator ab:

* **Szenario für einfachen Zugriff:** Dieses Szenario zeigt, wie Sie eine Zugriffsrichtlinie zu einem Benutzer zuordnen können, damit der Benutzer Infrastrukturserviceressourcen (einschließlich Virtual Private Cloud-Instanzen) erstellen und verwenden kann.

* **Szenario für Teamzugriff:** Dieses Szenario zeigt, wie Sie Ressourcengruppen und Zugriffsrichtlinien einrichten können, mit denen zwei separate Teams die VPC-Ressourcen erstellen und verwenden können, die dem entsprechenden Team zugeordnet sind.

Es kann bis zu 10 Minuten dauern, bis Änderungen an IAM-Zugriffsrichtlinien für VPC wirksam werden.
{: note}

## Szenario für einfachen Zugriff

Dieses Szenario umfasst die grundlegenden Schritte, die zum Festlegen eines einzelnen Benutzers erforderlich sind. Dabei laden Sie einerseits einen neuen Benutzer für ein Konto ein und ändern andererseits die Berechtigungen eines vorhandenen Benutzers.

### Neuen Benutzer zum Erstellen und Verwalten von VPC-Ressourcen einladen

Laden Sie einen IBM Cloud-Benutzer für Ihr Konto ein und geben Sie ihm Zugriff auf den `Infrastrukturservice`, damit er über die entsprechenden Zugriffsberechtigungen zum Anzeigen, Erstellen und Aktualisieren von VPC-Ressourcen verfügt. Dieser Abschnitt enthält eine kurze Übersicht über die IAM-Schritte. Weitere Informationen können Sie über die Links im Abschnitt **Zugehörige Links** am Ende dieses Dokuments aufrufen.

Nachfolgend finden Sie die grundlegenden Schritte in IAM, die Sie zum Einladen von Benutzern für VPC-Services und -Ressourcen benötigen:

1. Navigieren Sie zur [Benutzerschnittstelle für IAM-Benutzer ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/iam#/users){: new_window} in der IBM Cloud-Konsole.
2. Klicken Sie auf der Seite **Benutzer** auf **Benutzer einladen**.
3. Geben Sie auf der Seite **Benutzer einladen** im Abschnitt **Benutzer** die E-Mail-Adressen der Benutzer, die Sie einladen möchten, in das Feld **E-Mail-Adresse** ein.
4. Erweitern Sie im Abschnitt **Zugriff** den Eintrag **Services** und führen Sie anschließend die folgenden Tasks aus:
  * Wählen Sie aus der Liste **Zugriff zuweisen für** die Option **Ressource** aus.
  * Wählen Sie **Infrastrukturservice** aus der Liste **Services** aus.
  * Wählen Sie die Zugriffsrolle für die Plattform aus, die Sie den Benutzern zuweisen möchten. Es kann **Administrator**, **Editor**, **Operator** oder **Anzeigeberechtigter** sein.
  * Klicken Sie auf **Benutzer einladen**.

### Vorhandenem Benutzer die Berechtigung zum Verwalten von VPC-Ressourcen erteilen

Dieses Szenario umfasst die grundlegenden Schritte, die erforderlich sind, um einem vorhandenen Benutzer in Ihrem Konto die Berechtigung zum Bearbeiten von VPC-Ressourcen zu erteilen.

In den folgenden Schritten erstellen Sie zwei IAM-Richtlinien. Beide Richtlinien werden benötigt, bevor der Benutzer Infrastrukturserviceressourcen erstellen und verwenden kann. Alle Ressourcen müssen sich in der Standardressourcengruppe des Kontos befinden.

1. Navigieren Sie zur [Benutzerschnittstelle für IAM-Benutzer ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/iam#/users){: new_window} in der IBM Cloud-Konsole.
2. Wählen Sie den Benutzer aus, dessen Berechtigung Sie aktivieren.
3. Wählen Sie auf der Registerkarte **Zugriffsrichtlinien** die Option **Zugriff zuweisen** aus.
4. Wählen Sie **Zugriff in einer Ressourcengruppe zuweisen** aus.
5. Wählen Sie die Standardressourcengruppe des Kontos aus.
6. Stellen Sie sicher, dass die Option **Zugriff für eine Ressourcengruppe zuweisen** weiterhin auf **Anzeigeberechtigter** gesetzt ist.
7. Um den richtigen Service zuzuweisen, wählen Sie **Infrastrukturservice** aus.
8. Stellen Sie sicher, dass der Wert für **Ressourcentyp** auf **Alle Ressourcentypen** gesetzt ist.
9. Wählen Sie die Rolle **Editor** aus.
10. Klicken Sie auf **Zuweisen**.

Der Benutzer ist nun zum Erstellen und Verwenden von VPC-Ressourcen in der Standardressourcengruppe des Kontos berechtigt. Die erste Richtlinie hat dem Benutzer die Rolle **Anzeigeberechtigter** für Infrastrukturserviceressourcen zugewiesen (der Zugriff ist jedoch auf Ressourcen in der Standardressourcengruppe des Kontos beschränkt). Die zweite Richtlinie ermöglicht es dem Benutzer, die Standardressourcengruppe des Kontos anzuzeigen.

Beachten Sie beim Erstellen von IAM-Richtlinien, dass einigen Konten Zugriff gewährt werden muss (d. h., sie müssen in einer Whitelist aufgeführt sein), bevor sie bestimmte Infrastrukturserviceressourcentypen verwenden können, insbesondere Ressourcen in Betaversionen oder mit Vorabzugriff.
{: tip}

## Berechtigungen des Benutzers anzeigen

Richtlinien werden auf der Registerkarte **Zugriffsrichtlinien** des Benutzers angezeigt.

Sie können die folgenden CLI-Befehle verwenden, um die Berechtigungen der Ressourcengruppe zu überprüfen, die Ihrem Benutzer, der Richtlinie oder der Zugriffsgruppe zugeordnet sind:

**Nach Richtlinie**
```
ibmcloud iam user-policies <benutzername>
```
**Nach Zugriffsgruppe**
```
ibmcloud iam access-groups -u <benutzername>
```

Es kann bis zu 10 Minuten dauern, bis Änderungen an IAM-Zugriffsrichtlinien für VPC wirksam werden.
{: note}

## Szenario für Teamzugriff

In diesem Szenario wird beschrieben, wie ein Kontoadministrator eine Berechtigung zuordnen kann, sodass verschiedene Teams Zugriff auf separate VPC-Ressourcen haben. In dem Beispiel werden _Ressourcengruppen_ verwendet, um für zwei Teams einen separaten Ressourcenzugriff einzurichten. Zum Zweck dieses Beispiels werden Ressourcen nicht von mehreren Teams gemeinsam genutzt.

Das Beispiel führt Sie durch den Prozess zum Erstellen von Ressourcengruppen, zum Erstellen von Zugriffsgruppen und zum Zuordnen der entsprechenden Richtlinien, um Ihren Teams Zugriff auf separate VPC-Ressourcen zu ermöglichen.

Angenommen, Sie richten zwei verschiedene Projektteams ein, die zwei separate Virtual Private Cloud-Instanzen verwenden sollen. Sie ordnen den Teammitgliedern Zugriff zu, sodass jedes Team (ausschließlich) Zugriff auf die eigenen VPC-Ressourcen hat.

* Ihr erstes Team ist ein Testteam. Sie haben sich entschieden, diesen Team Zugriff auf VPCs in einer Ressourcengruppe mit dem Namen `test_vpcs` zuzuweisen.
* Das zweite Team ist Ihr Produktionsteam. Das Team erhält Zugriff auf VPCs in einer Ressourcengruppe namens `production_vpcs`.

Diese Strategie kann verwendet werden, um einer beliebigen Anzahl von Teams separate VPC-Ressourcen zuzuordnen. Alle Ressourcen verwenden jedoch die gleichen VPC-Kontingente für das Konto. Weitere Informationen zu Kontingenten und Limits finden Sie im Abschnitt [VPC-Kontingente](/docs/infrastructure/vpc?topic=vpc-quotas#quotas).
{: tip}

### Schritt 1: Ressourcengruppen erstellen

Kontoadministratoren verfügen standardmäßig über den entsprechenden Zugriff zum Erstellen neuer Ressourcengruppen. Den anderen Benutzern muss zuerst die Rolle **Editor** für **Alle Kontoverwaltungsservices** zugeordnet werden, die es ihnen ermöglicht, Ressourcengruppen zu erstellen.

Ihre erste Aufgabe ist es, Ressourcengruppen zu erstellen, die die einzelnen VPC-Ressourcen Ihres Teams enthalten.

1. Erstellen Sie eine Ressourcengruppe mit dem Namen `test_team`.  
2. Erstellen Sie eine Ressourcengruppe mit dem Namen `production_team`.  

Weitere Informationen zum Erstellen von Ressourcengruppen finden Sie im Abschnitt [Ressourcengruppen verwalten](/docs/resources/resourcegroups.html#rgs).

### Schritt 2: Zugriffsgruppen erstellen

Der Ressourcenzugriff kann einzelnen Benutzern oder Gruppen von Benutzern zugeordnet werden. Gruppen von Benutzern mit den gleichen Zugriffsberechtigungen werden als _Zugriffsgruppen_ bezeichnet. In diesem Szenario erstellen Sie eine Zugriffsgruppe, um jede Gruppierung von Teammitgliedern darzustellen, die einen bestimmten Typ von VPC-Zugriff benötigen (insgesamt vier eindeutige Zugriffsgruppen).

**Task:** Erstellen Sie vier Zugriffsgruppen mit den folgenden Namen: `test_team_manage_vpcs`, `test_team_view_vpcs`, `production_team_manage_vpcs` und `production_team_view_vpcs`.

Hilfe zum Erstellen von Zugriffsgruppen finden Sie im Abschnitt [Zugriffsgruppen erstellen](/docs/iam?topic=iam-groups#create_ag).

### Schritt 3: IAM-Richtlinien zu den Zugriffsgruppen hinzufügen, die Sie gerade erstellt haben

Fügen Sie die nötigen VPC-Zugriffsrichtlinien hinzu, sodass die Zugriffsgruppe `test_team` VPC-Ressourcen verwalten (erstellen, aktualisieren und löschen) kann.  

1. Navigieren Sie zur [Benutzerschnittstelle für IAM-Gruppen ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/iam#/groups){: new_window} in der IBM Cloud-Konsole.
2. Wählen Sie die gewünschte Zugriffsgruppe aus (beginnen Sie mit `test_team_manage_vpcs`).
3. Klicken Sie auf der Registerkarte **Zugriffsrichtlinien** auf **Zugriff zuweisen**.
4. Wählen Sie **Zugriff in einer Ressourcengruppe zuweisen** aus.
5. Wählen Sie die gewünschte Ressourcengruppe aus (beginnen Sie mit `test_team`).
6. Stellen Sie sicher, dass die Option **Zugriff für eine Ressourcengruppe zuweisen** weiterhin auf **Anzeigeberechtigter** gesetzt ist.
7. Wählen Sie als Service **Infrastrukturservice** aus.
8. Stellen Sie sicher, dass der Wert für **Ressourcentyp** auf **Alle Ressourcentypen** gesetzt bleibt.
9. Wählen Sie die Rolle **Editor** aus.
10. Wählen Sie **Zuweisen** aus.

Bei diesen Schritten wird auch der Zugriff für die Rolle **Anzeigeberechtigter** auf die Ressourcengruppe `test_team` festgelegt. Dieser Zugriff wird zum Erstellen, Aktualisieren und Löschen von Ressourcen innerhalb der Gruppe benötigt.
{: tip}

Wiederholen Sie die vorherigen Schritte für die verbleibenden drei Zugriffsgruppen. Sie können diese Tasks für die Zuordnung von Zugriffsgruppen zu Ressourcengruppen ausführen:

* Weisen Sie der Zugriffsgruppe `test_team_view_vpcs` die Rolle **Anzeigeberechtigter** für Infrastrukturserviceressourcen innerhalb der Ressourcengruppe `test_team` zu.
* Weisen Sie die Rolle **Editor** der Zugriffsgruppe `production_team_manage_vpcs` zu den Infrastrukturserviceressourcen innerhalb der Ressourcengruppe `production_team` zu.
* Weisen Sie die Rolle **Anzeigeberechtigter** der Zugriffsgruppe `production_team_view_vpcs` zu den Infrastrukturserviceressourcen innerhalb der Ressourcengruppe `production_team` zu.

Benutzer mit dem **Editor**-Zugriff auf VPC-Ressourcen können diese auch anzeigen. Es ist nicht erforderlich, Mitglieder zu den Zugriffsgruppen **Editor** UND **Anzeigeberechtigter** hinzuzufügen.

#### Zugriff für Anzeigeberechtigten einrichten

Infrastrukturserviceressourcen des Typs `Variable IP-Adresse` werden in der Standardressourcengruppe des Kontos erstellt. Daher benötigen Benutzer, die `variable IP-Adressen` verwalten müssen, den Zugriff eines **Anzeigeberechtigten** auf die Standardressourcengruppe des Kontos.
{: tip}

Gehen Sie wie folgt vor, um den Zugriff für die Rolle **Anzeigeberechtigter** zu erstellen:

1. Navigieren Sie zur [Benutzerschnittstelle für IAM-Gruppen ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/iam#/groups){: new_window} in der IBM Cloud-Konsole.
2. Wählen Sie die gewünschte Zugriffsgruppe aus (beginnen Sie mit `test_team_manage_vpcs`).
3. Klicken Sie auf der Registerkarte **Zugriffsrichtlinien** auf **Zugriff zuweisen**.
4. Wählen Sie **Zugriff auf Kontoverwaltungsservices zuweisen** aus.
7. Wählen Sie als Service **Alle Kontoverwaltungsservices** aus.
9. Wählen Sie die Rolle **Anzeigeberechtigter** aus.
10. Wählen Sie **Zuweisen** aus.

Wiederholten Sie die vorherigen Schritte, um der Zugriffsgruppe `production_team_manage_vpcs` die Rolle **Anzeigeberechtigter** für **Alle Kontoverwaltungsservices** zuzuordnen.

### Schritt 4: Benutzer zu den Zugriffsgruppen hinzufügen

Nun können Sie Teammitglieder (Benutzer) den entsprechenden Zugriffsgruppen zuordnen. Führen Sie die folgenden Schritte aus, um die einzelnen Mitglieder des Testteams der Zugriffsgruppe hinzuzufügen, die das VPC-Management für Testteams zulässt:

1. Navigieren Sie zur [Benutzerschnittstelle für IAM-Gruppen ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/iam#/groups){: new_window} in der IBM Cloud-Konsole.
2. Wählen Sie die gewünschte Zugriffsgruppe aus (beginnen Sie mit `test_team_manage_vpcs`).
3. Klicken Sie auf der Registerkarte **Benutzer** auf **Benutzer hinzufügen**.
4. Wählen Sie alle Benutzer aus, die Sie zur Zugriffsgruppe hinzufügen möchten.
5. Klicken Sie auf **Zu Gruppe hinzufügen**.

Wiederholen Sie die vorherigen Schritte, um die folgenden Aufgaben auszuführen:
* Ordnen Sie die gewünschten Benutzer der Zugriffsgruppe `test_team_view_vpcs` zu.
* Ordnen Sie die gewünschten Benutzer der Zugriffsgruppe `production_team_manage_vpcs` zu.
* Ordnen Sie die gewünschten Benutzer der Zugriffsgruppe `production_team_view_vpcs` zu.

Es ist nicht erforderlich, Benutzern den Zugriff des **Anzeigeberechtigten** auf VPC-Ressourcen zu erteilen, wenn die Benutzer über Verwaltungszugriff verfügen.
{: tip}

## Nächste Schritte

Die beiden Beispielteams sind jetzt für die Verwendung von VPCs konfiguriert. An diesem Punkt können Mitglieder der Zugriffsgruppen `test_team_manage_vpcs` und `production_team_manage_vpcs` VPCs in den ihnen zugeordneten Ressourcengruppen erstellen.


## Zugehörige Links

* [Identität und Zugriff verwalten](/docs/iam/quickstart.html)
* [Benutzer und Zugriff verwalten](/docs/iam/iamusermanage.html)
* [Was ist IAM?](/docs/iam/index.html)

