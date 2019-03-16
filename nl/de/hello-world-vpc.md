---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:table: .aria-labeledby="caption"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# VPC über die IBM Cloud-CLI erstellen
{: #creating-a-vpc-using-the-ibm-cloud-cli}

In diesem Leitfaden erfahren Sie, wie Sie {{site.data.keyword.cloud}} Virtual Private Cloud-Ressourcen mithilfe der IBM Cloud-CLI erstellen.

## Voraussetzungen:

1. Installieren Sie die [IBM Cloud-CLI](https://cloud.ibm.com/docs/cli/index.html#overview).

2. Installieren oder aktualisieren Sie das Plug-in `infrastructure-service` für die IBM Cloud-CLI.

  Führen Sie zum Installieren den folgenden Befehl aus:

  ```
  ibmcloud plugin install infrastructure-service
  ```
  {: pre}

  Führen Sie zum Aktualisieren den folgenden Befehl aus:

  ```
  ibmcloud plugin update
  ```
  {: pre}

  Führen Sie zum Anzeigen installierter Plug-ins und Versionen den folgenden Befehl aus:

  ```
  ibmcloud plugin list
  ```
  {: pre}


3. Generieren Sie einen öffentlichen SSH-Schlüssel zum Bereitstellen virtueller Serverinstanzen (Virtual Server Instances, VSIs).

Möglicherweise haben Sie bereits einen öffentlichen SSH-Schlüssel. Suchen Sie nach einer Datei mit dem Namen ``id_rsa.pub`` in einem ``.ssh``-Verzeichnis unter Ihrem Ausgangsverzeichnis, z. B. ``/Users/<USERNAME>/.ssh/id_rsa.pub``. Die Datei beginnt mit ``ssh-rsa`` und endet mit Ihrer E-Mail-Adresse.

Wenn Sie keinen öffentlichen SSH-Schlüssel oder das Kennwort eines vorhandenen Schlüssels vergessen haben, generieren Sie einen neuen, indem Sie den Befehl ``ssh-keygen`` ausführen und den Eingabeaufforderungen folgen.


Informationen zum Erstellen einer VPC in verschiedenen IBM Cloud-Regionen finden Sie im Abschnitt zu den [Regionen](/docs/infrastructure/vpc/vpc-regions.html).
{: tip}


## Schritt 1: Bei IBM Cloud anmelden

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

### Schritt 2: VPC erstellen und die VPC-ID speichern

Verwenden Sie den folgenden Befehl, um eine VPC mit dem Namen _helloworld-vpc_ zu erstellen.

```
ibmcloud is vpc-create helloworld-vpc
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:

```
Creating VPC helloworld-vpc in resource group Default under account <kontoname> as user <benutzer>...

ID        ba9e785a-3e10-418a-811c-56cfe5669676
Name      helloworld-vpc
Default   no
Created   1 second ago
Status    available
```
{:screen}

Speichern Sie die ID in einer Variablen so, dass sie später verwendet werden kann. Beispiel:

```
vpc="ba9e785a-3e10-418a-811c-56cfe5669676"
```
{: pre}

## Schritt 3: Teilnetz erstellen und die Teilnetz-ID speichern

Wählen Sie die Zone `us-south-2` für die Position des Teilnetzes aus und rufen Sie das Teilnetz _helloworld-subnet_ auf.

```
ibmcloud is subnet-create helloworld-subnet $vpc us-south-2 --ipv4-address-count 8
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:

```
Creating Subnet helloworld-subnet in resource group Default under account <kontoname> as user <benutzer>...

ID               50ba0da9-279a-4791-b7cb-cd3d7b2bc14d
Name             helloworld-subnet
IPv*             ipv4
IPv4 CIDR        10.240.64.0/29
IPv6 CIDR        -
Addr available   3
Addr Total       8
Gen              -
ACL              allow-all-network-acl-ba9e785a-3e10-418a-811c-56cfe5669676(e9c2790b-cee2-465a-8539-d8cd90d33621)
Gateway          -   
Created          now   
Status           pending   
Zone             us-south-2   
VPC              helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)   
```
{:screen}

Speichern Sie die ID in einer Variablen so, dass sie später verwendet werden kann. Beispiel:

```
subnet="50ba0da9-279a-4791-b7cb-cd3d7b2bc14"
```
{: pre}

Beachten Sie, dass der Status des Teilnetzes bei der erstmaligen Erstellung `pending` (anstehend) lautet. Bevor Sie fortfahren können, muss das Teilnetz in den Status `available` (verfügbar) versetzt werden. Dies kann einige Sekunden dauern. Führen Sie den folgenden Befehl aus, um den Status des Teilnetzes zu überprüfen:

```
ibmcloud is subnet $subnet
```
{: pre}

## Schritt 4: SSH-Schlüssel in der IBM Public Cloud erstellen

Sie verwenden den Schlüssel zum Bereitstellen einer virtuellen Serverinstanz. Sie können denselben Schlüssel verwenden, um mehrere virtuelle Serverinstanzen bereitzustellen.

Führen Sie den folgenden Befehl aus, um die verfügbaren Schlüssel in Ihrem IBM Cloud-Konto anzuzeigen:

```
ibmcloud is keys
```
{: pre}

Führen Sie den folgenden Befehl aus, um einen Schlüssel zu erstellen. Ersetzen Sie den Pfad zu der Datei `id_rsa.pub`.

```
ibmcloud is key-create helloworld-key @$HOME/.ssh/id_rsa.pub
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:

```
Creating key helloworld-key in resource group Default under account <kontoname> as user <benutzer>...

ID               859b4e97-7540-4337-9c64-384792b85653
Name             helloworld-key
Type             rsa
Length           2048
FingerPrint      SHA256:hkcAOGB5z7QXqZLHd0kGqhj735qrfMjZLH9PxS/42vA
Key              ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC9i2joQ8eiFVdJ7pOlC6h5+IoBL6wFFygkk9Na3gV8Bi52dv44YOAjSJ2oduguHEtLp5r4eh4+5jiEBkFYkHNUhE0MxlcVZABTYWePXx4QnlmGr99xyOfi6DAHhSRQiSBhmhjcGjbADavDuIgoyKpVXbU9O1If3P0miNpaouaZmr+d68OHt4yPvNnztlluV3JBISJgqJ7pzg6wFF0SrjqtEYKBd8oxwogHu+rmRgT7IF09oSiKpKZRF0VfeLFz+REh9RuKa4Jh63aa2PRIgDKq6HO7MEdfOtGzCzoqqlFKgpl+VgGyT0b5BjQEnWv13cwx02bv5QCwma/GeAOpW0CD user@email.com

Created          now   
```
{:screen}

Speichern Sie die ID in einer Variablen so, dass sie später verwendet werden kann. Beispiel:

```
key="859b4e97-7540-4337-9c64-384792b85653"
```

## Schritt 5: Profil und Image für die virtuelle Serverinstanz auswählen

Führen Sie den folgenden Befehl aus, um alle verfügbaren Instanzprofile aufzulisten:

```
ibmcloud is instance-profiles
```
{: pre}

Führen Sie den folgenden Befehl aus, um alle verfügbaren Images aufzulisten:

```
ibmcloud is images
```
{: pre}

Wählen Sie das Instanzprofil `b-2x8` und das Image `ubuntu-16.04-amd64` aus. Führen Sie den folgenden Befehl aus, um die Image-ID von `ubuntu-16.04-amd64` abzurufen:

```
image=$(ibmcloud is images | grep "ubuntu-16.04-amd64" | cut -d" " -f1)
```
{: pre}

## Schritt 6: Virtuelle Serverinstanz bereitstellen

```
ibmcloud is instance-create helloworld-vsi $vpc us-south-2 b-2x8 $subnet 1000 --image-id $image --key-ids $key
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:

```
Creating instance helloworld-vsi in resource group Default under account <kontoname> as user <benutzer>...

ID                4562c5c0-9cf7-4406-bc90-ab4baea91057
Name              helloworld-vsi
Gen
Profile           b-2x8
CPU Arch          amd64
CPU Cores         2
CPU Frequency     2000
Memory            8
Primary Intf      primary(2e850924-b5d7-4386-a778-03556d5850c1)
Primary Address   10.240.64.4  
Image             ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
Status            pending   
Created           5 seconds ago   
VPC               helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)   
Zone              us-south-2   
```
{:screen}

Speichern Sie die ID der primären Netzschnittstelle `Primary Intf` in einer Variablen so, dass sie später verwendet werden kann. Beispiel:

```
nic="2e850924-b5d7-4386-a778-03556d5850c1"
```
{:pre}

Beachten Sie, dass der Status der Instanz bei der erstmaligen Erstellung `pending` (anstehend) lautet. Bevor Sie fortfahren können, muss die Instanz in den Status `running` (aktiv) versetzt werden, was einige Minuten in Anspruch nimmt. Führen Sie den folgenden Befehl aus, um den Status aller Instanzen zu überprüfen:

```
ibmcloud is instances
```
{: pre}


## Schritt 7: Variable IP-Adresse erstellen

Sie benötigen eine variable IP-Adresse, damit Sie sich über das Internet bei der virtuellen Serverinstanz (VSI) anmelden können.

```
ibmcloud is floating-ip-reserve helloworld-fip --nic-id $nic
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:

```
Creating floating ip helloworld-fip in resource group Default under account <kontoname> as user <benutzer>...

ID               b9d1cc1f-67db-40e3-81de-9228465170a5
Address          169.61.181.53
Name             helloworld-fip
Target           primary(2e850924-.)
Target Type      intf   
Target IP        10.0.1.5   
Created          now   
Status           available   
Zone             us-south-2   
```
{:screen}

Speichern Sie die Adresse (`address`) in einer Variablen so, dass sie später verwendet werden kann:

```
address=169.61.181.53
```
{: pre}

## Schritt 8: Regel zur Standardsicherheitsgruppe für SSH hinzufügen

Suchen Sie die Sicherheitsgruppe für die VPC:

```
ibmcloud is vpc-sg $vpc
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:
```
Getting default security group of vpc ba9e785a-3e10-418a-811c-56cfe5669676 under account <kontoname> as user <benutzer>...

ID               2d364f0a-a870-42c3-a554-000000981149
Name             errand-drastic-imperial-retail-unlocked-jester
Created          1 week ago
VPC              helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)
Resource Group   -
Tags             -

Rules
ID                                     Direction   IPv*   Protocol                  Remote
b597cff2-38e8-4e6e-999d-000002031345   inbound     ipv4   all                       errand-drastic-imperial-retail-unlocked-jester(2d364f0a-.)
b597cff2-38e8-4e6e-999d-000002031527   outbound    ipv4   all                       -

```
{:screen}

Speichern Sie die ID in einer Variablen so, dass sie später verwendet werden kann:

```
sg=2d364f0a-a870-42c3-a554-000000981149
```
{: pre}

Erstellen Sie nun die Regel, um SSH zu ermöglichen:

```
ibmcloud is sg-rulec $sg inbound tcp --port-min=22 --port-max=22
```
{: pre}

Die Ausgabe sollte wie folgt aussehen:

```
Creating rule for security group 2d364f0a-a870-42c3-a554-000000981149 under account <kontoname> as user <benutzer>...

ID          b597cff2-38e8-4e6e-999d-000001949921
Direction   inbound
IPv*        ipv4
Protocol    tcp
Min Port    22
Max Port    22
Remote      -
```
{:screen}

## Schritt 9: Mit dem privaten SSH-Schlüssel bei der virtuellen Serverinstanz anmelden

Sie können z. B. einen Befehl in diesem Format verwenden:

```
ssh -i $HOME/.ssh/id_rsa root@$address
```
{:pre}

Sie erhalten eine ähnliche Antwort wie das folgende Beispiel. Wenn Sie aufgefordert werden, die Verbindung fortzusetzen, geben Sie `yes` ein.

```
The authenticity of host '169.61.181.53 (169.61.181.53)' can't be established.
ECDSA key fingerprint is SHA256:9MczXIwJq892DYwu0sZpQZOXORdvNXeP1aFioZpQDsM.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '169.61.181.53' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-133-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

root@helloworld-vsi:~#
```
{:screen}

## Schritt 10: Hello, World!

Führen Sie den folgenden Befehl im Terminalfenster aus:

```
echo `hostname` says "Hello, World!"
```
{:pre}

Sie sollten die folgende Ausgabe sehen:

```
helloworld-vsi says Hello, World!
```
{:screen}

## Herzlichen Glückwunsch!

Sie haben Ihre VPC-Instanz mithilfe der IBM Cloud-CLI erfolgreich bereitgestellt und eine entsprechende Verbindung hergestellt. Wenn Sie weitere CLI-Befehle testen möchten, sollten Sie sich die vollständige Referenz ansehen:

* [CLI-Referenz für VPC](/docs/cli/reference/ibmcloud?topic=infrastructure-service-cli-vpc-reference#vpc-reference)
