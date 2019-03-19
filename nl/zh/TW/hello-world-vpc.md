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

# 使用 IBM Cloud CLI 建立 VPC
{: #creating-a-vpc-using-the-ibm-cloud-cli}

本手冊顯示如何使用 IBM Cloud CLI 來建立 {{site.data.keyword.cloud}} Virtual Private Cloud 資源。

## 必要條件：

1. 安裝 [IBM Cloud CLI](https://cloud.ibm.com/docs/cli/index.html#overview)。

2. 安裝或更新 IBM Cloud CLI 的 `infrastructure-service` 外掛程式。

  若要安裝，請執行下列指令：

  ```
  ibmcloud plugin install infrastructure-service
  ```
  {: pre}

  若要更新，請執行下列指令：

  ```
  ibmcloud plugin update
  ```
  {: pre}

  若要檢視已安裝的外掛程式及版本，請執行下列指令：

  ```
  ibmcloud plugin list
  ```
  {: pre}


3. 產生用來佈建「虛擬伺服器實例 (VSI)」的公開 SSH 金鑰。

您可能已有公開 SSH 金鑰。在起始目錄的 ``.ssh`` 目錄下尋找稱為 ``id_rsa.pub`` 的檔案，例如，``/Users/<USERNAME>/.ssh/id_rsa.pub``。檔案的開頭為 ``ssh-rsa``，結尾為電子郵件位址。

如果您沒有公開 SSH 金鑰，或忘記現有 SSH 金鑰的密碼，請執行 ``ssh-keygen`` 指令並遵循提示來產生新的 SSH 金鑰。


若要瞭解如何在不同的 IBM Cloud 地區中建立 Virtual Private Cloud，請參閱[地區](/docs/infrastructure/vpc/vpc-regions.html)主題。
{: tip}


## 步驟 1：登入 IBM Cloud。

如果您具有聯合帳戶，請執行下列指令：
```
ibmcloud login -sso
```
{: pre}

否則，請執行下列指令：

```
ibmcloud login
```
{: pre}

### 步驟 2：建立 VPC 並儲存 VPC ID。

使用下列指令，以建立名為 _helloworld-vpc_ 的 VPC。

```
ibmcloud is vpc-create helloworld-vpc
```
{: pre}

您應該會看到如下的輸出：

```
Creating VPC helloworld-vpc in resource group Default under account <Account Name> as user <User>...

ID        ba9e785a-3e10-418a-811c-56cfe5669676   
Name      helloworld-vpc   
Default   no   
Created   1 second ago   
Status    available   
```
{:screen}

將 ID 儲存在變數中，以供稍後使用，例如：

```
vpc="ba9e785a-3e10-418a-811c-56cfe5669676"
```
{: pre}

## 步驟 3：建立子網路並儲存子網路 ID。

請挑選子網路位置的 `us-south-2` 區域，並將子網路稱為 _helloworld-subnet_。

```
ibmcloud is subnet-create helloworld-subnet $vpc us-south-2 --ipv4-address-count 8
```
{: pre}

您應該會看到如下的輸出：

```
Creating Subnet helloworld-subnet in resource group Default under account <Account Name> as user <User>...

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

將 ID 儲存在變數中，以供稍後使用，例如：

```
subnet="50ba0da9-279a-4791-b7cb-cd3d7b2bc14"
```
{: pre}

請注意，第一次建立子網路時，其狀態為 `pending`。在您繼續之前，子網路需要移至 `available` 狀態，這需要幾秒鐘。若要檢查子網路的狀態，請執行以下指令：

```
ibmcloud is subnet $subnet
```
{: pre}

## 步驟 4：在 IBM Public Cloud 中建立 SSH 金鑰。

您將使用金鑰來佈建虛擬伺服器實例。您可以使用相同的金鑰來佈建多個虛擬伺服器實例。

若要查看 IBM Cloud 帳戶中的可用金鑰，請執行此指令：

```
ibmcloud is keys
```
{: pre}

若要建立金鑰，請執行下列指令。替換 `id_rsa.pub` 檔案的路徑。

```
ibmcloud is key-create helloworld-key @$HOME/.ssh/id_rsa.pub
```
{: pre}

您應該會看到如下的輸出：

```
Creating key helloworld-key in resource group Default under account <Account Name> as user <User>...

ID               859b4e97-7540-4337-9c64-384792b85653   
Name             helloworld-key   
Type             rsa   
Length           2048   
FingerPrint      SHA256:hkcAOGB5z7QXqZLHd0kGqhj735qrfMjZLH9PxS/42vA   
Key              ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC9i2joQ8eiFVdJ7pOlC6h5+IoBL6wFFygkk9Na3gV8Bi52dv44YOAjSJ2oduguHEtLp5r4eh4+5jiEBkFYkHNUhE0MxlcVZABTYWePXx4QnlmGr99xyOfi6DAHhSRQiSBhmhjcGjbADavDuIgoyKpVXbU9O1If3P0miNpaouaZmr+d68OHt4yPvNnztlluV3JBISJgqJ7pzg6wFF0SrjqtEYKBd8oxwogHu+rmRgT7IF09oSiKpKZRF0VfeLFz+REh9RuKa4Jh63aa2PRIgDKq6HO7MEdfOtGzCzoqqlFKgpl+VgGyT0b5BjQEnWv13cwx02bv5QCwma/GeAOpW0CD user@email.com   

Created          now   
```
{:screen}

將 ID 儲存在變數中，以供稍後使用，例如：

```
key="859b4e97-7540-4337-9c64-384792b85653"
```

## 步驟 5：選取虛擬伺服器實例的設定檔及映像檔。

若要列出所有可用的實例設定檔，請執行下列指令：

```
ibmcloud is instance-profiles
```
{: pre}

若要列出所有可用的映像檔，請執行下列指令：

```
ibmcloud is images
```
{: pre}

請挑選實例設定檔 `b-2x8` 及映像檔 `ubuntu-16.04-amd64`。若要取得 `ubuntu-16.04-amd64` 的映像檔 ID，請執行下列指令：

```
image=$(ibmcloud is images | grep "ubuntu-16.04-amd64" | cut -d" " -f1)
```
{: pre}

## 步驟 6：佈建虛擬伺服器實例。

```
ibmcloud is instance-create helloworld-vsi $vpc us-south-2 b-2x8 $subnet 1000 --image-id $image --key-ids $key
```
{: pre}

您應該會看到如下的輸出：

```
Creating instance helloworld-vsi in resource group Default under account <Account Name> as user <User>...

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

將主要網路介面 `Primary Intf` 的 ID 儲存在變數中，以供稍後使用，例如：

```
nic="2e850924-b5d7-4386-a778-03556d5850c1"
```
{:pre}

請注意，第一次建立實例時，其狀態為 `pending`。在您繼續之前，實例需要移至 `running` 狀態，這需要幾分鐘。若要檢查所有實例的狀態，請執行以下指令：

```
ibmcloud is instances
```
{: pre}


## 步驟 7：建立浮動 IP 位址。

您需要有「浮動 IP 位址」，才能從網際網路登入虛擬伺服器實例 (VSI)。

```
ibmcloud is floating-ip-reserve helloworld-fip --nic-id $nic
```
{: pre}

您應該會看到如下的輸出：

```
Creating floating ip helloworld-fip in resource group Default under account <Account Name> as user <User>...

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

將 `Address` 儲存在變數中，以供稍後使用：

```
address=169.61.181.53
```
{: pre}

## 步驟 8：將規則新增至 SSH 的預設安全群組

尋找 VPC 的安全群組：

```
ibmcloud is vpc-sg $vpc
```
{: pre}

您應該會看到如下的輸出：
```
Getting default security group of vpc ba9e785a-3e10-418a-811c-56cfe5669676 under account <Account Name> as user <User>...

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

將 ID 儲存在變數中，以供稍後使用：

```
sg=2d364f0a-a870-42c3-a554-000000981149
```
{: pre}

現在，請建立規則來容許 SSH：

```
ibmcloud is sg-rulec $sg inbound tcp --port-min=22 --port-max=22
```
{: pre}

您應該會看到如下的輸出：

```
Creating rule for security group 2d364f0a-a870-42c3-a554-000000981149 under account <Account Name> as user <User>...

ID          b597cff2-38e8-4e6e-999d-000001949921
Direction   inbound
IPv*        ipv4
Protocol    tcp
Min Port    22
Max Port    22
Remote      -
```
{:screen}

## 步驟 9：使用專用 SSH 金鑰登入虛擬伺服器實例。

例如，您可以使用下列形式的指令：

```
ssh -i $HOME/.ssh/id_rsa root@$address
```
{:pre}

您會收到類似下列範例的回應。系統提示您繼續連接時，請鍵入 `yes`。

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

## 步驟 10：Hello, World!

在終端機視窗中，執行下列指令：

```
echo `hostname` says "Hello, World!"
```
{:pre}

您應該會看到下列輸出：

```
helloworld-vsi says Hello, World!
```
{:screen}

## 恭喜！

您已使用 IBM Cloud CLI 順利佈建及連接至 Virtual Private Cloud 實例。若要嘗試其他 CLI 指令，請探索完整參考資料：

* [VPC 的 CLI 參考資料](/docs/cli/reference/ibmcloud?topic=infrastructure-service-cli-vpc-reference#vpc-reference)
