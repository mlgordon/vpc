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

# 使用 REST API 建立 VPC
{: #creating-a-vpc-using-the-rest-apis}

本手冊顯示如何使用 IBM Cloud Regional API (RIAS) 來建立 {{site.data.keyword.cloud}} Virtual Private Cloud 資源。

## 必要條件：

1. 安裝 [IBM Cloud CLI](https://cloud.ibm.com/docs/cli/index.html#overview)。

## 步驟 1：登入 IBM Cloud，以取得 API 呼叫中使用的 IAM 記號。

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

此指令會傳回 URL，並提示輸入密碼。在瀏覽器中移至該 URL，然後登入。如果成功，您將會取得一次性密碼。複製此密碼，將它貼為提示上的回應。在鑑別步驟之後，系統會提示您選擇帳戶。回應任何剩餘提示以完成登入。

## 步驟 2：取得 IBM Identity and Access Management (IAM) 記號

下列指令會呼叫 IBM Cloud CLI，剖析 IAM 記號及 `Bearer` 記號 ID，然後將其儲存至您可在稍後指令中使用的變數。

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 若要檢視 IAM 記號，請執行 ``echo $iam_token`` 指令。

結果應該看起來如下：

```
Bearer <your token>
```
{: screen}

Authorization 標頭預期記號以 "Bearer" 開頭。如果上述結果未包括 "Bearer"，請更新 `iam_token` 變數予以併入。這些範例假設 "Bearer" 內含在 `iam_token` 中。

您必須重複之前的步驟，每小時重新整理 IAM 記號，因為記號到期。
{: important}

## 步驟 3：將 API 端點儲存為變數

請將 API 端點儲存在變數中，以供稍後重複使用。API 端點是根據地區，並遵循慣例 `https://<region>.iaas.cloud.ibm.com`。例如，`us-south` API 端點是 `https://us-south.iaas.cloud.ibm.com`。

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

若要驗證已儲存此變數，請執行 `echo $rias_endpoint`，並確定回應不是空的。

## 步驟 4：執行 GET 地區 API

如果您執行非預期的結果，請在 `curl` 指令之後新增 `--verbose`（除錯）旗標，以取得詳細的記載資訊。您也可以在[疑難排解頁面](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc)中查看常見的錯誤。
{: tip}

下列指令會以 JSON 格式傳回 VPC 可用的地區。應該傳回至少一個物件。

請記下每個 API 指令的必要 `version` 查詢參數。
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 步驟 5：執行 GET 區域 API

下列指令會以 JSON 格式傳回地區 `us-south` 中 VPC 可用的所有區域。應該傳回至少三個物件。

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 步驟 6：執行 GET 設定檔 API

下列指令會以 JSON 格式傳回您實例可用的設定檔。應該傳回至少一個物件。

在 curl 指令後面新增 ` | json_pp `，以取得可讀取的 JSON 字串
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

如果 API 輸出受限於分頁，請將限制設為高於 `total_count`，例如：

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## 步驟 7：執行 GET 映像檔 API

下列指令會以 JSON 格式傳回您實例可用的映像檔。應該傳回至少一個物件。

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## 步驟 8：執行 GET VPC API

下列指令會以 JSON 格式傳回已在您的帳戶（如果有的話）下建立的 VPC。

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## 步驟 9：建立虛擬專用雲端

建立稱為 `my-vpc` 的 IBM Cloud VPC。

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

對於其餘呼叫，您將需要知道新建立 IBM Cloud VPC 的 ID。將其 ID 貼入變數中，如下所示：

內容看起來如下：`vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## 步驟 10：建立子網路

在 IBM Cloud VPC 中建立子網路。例如，將它放在 `us-south-2` 區域中。

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

與 Virtual Private Cloud 一樣，將子網路的 ID 儲存在變數中。

```bash
subnet="<YOUR_SUBNET_ID>"
```
{: pre}

## 步驟 11：檢查子網路的狀態

若要佈建子網路中的資源，子網路必須處於 `available` 狀態。查詢子網路資源，並在繼續之前確定狀態為 `available`。如果狀態為 `failed`，請與[支援中心](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)聯絡，以取得詳細資料。您可以嘗試佈建另一個子網路以試著繼續進行。

```bash
curl $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 步驟 12：建立公用閘道

若要容許子網路中的虛擬伺服器實例存取公用網際網路，請將公用閘道 (PGW) 新增至子網路。  

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

與使用 Virtual Private Cloud 及子網路執行的作業一樣，將公用閘道的 ID 儲存在變數中。

```bash
gateway="<YOUR_GATEWAY_ID>"
```
{: pre}

## 步驟 13：將公用閘道連接至子網路。

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## 步驟 14：建立 SSH 金鑰

使用公開 SSH 金鑰來建立金鑰。建立虛擬伺服器實例時會使用此金鑰，而且需要有它才能登入虛擬伺服器實例。

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

將金鑰的 ID 儲存在變數中。

```bash
key="<YOUR_KEY_ID>"
```
{: pre}

## 步驟 15：選擇虛擬伺服器實例的設定檔及映像檔

執行這些 API，以列出可供虛擬伺服器實例使用的所有設定檔及映像檔，並選擇一個組合。

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

若要取得設定檔的其他詳細資料，您可以使用 IBM Cloud CLI 指令 `ibmcloud catalog entry <profile-name> --json` 來查詢全球型錄。例如，

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

下列指令會列出可用的映像檔。

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

將設定檔的「名稱」及映像檔的 ID 儲存在變數中，稍後將用來佈建虛擬伺服器實例。

```bash
profile_name="<CHOSEN_PROFILE_NAME>"
image_id="<CHOSEN_IMAGE_ID>"
```
{: pre}

## 步驟 16：佈建虛擬伺服器實例

在新建立的子網路中佈建虛擬伺服器實例。傳入公開 SSH 金鑰，以在佈建實例之後登入。

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

與使用其他資源執行的作業一樣，將虛擬伺服器實例的 ID 儲存在變數中。

```bash
server="<YOUR_INSTANCE_ID>"
```
{: pre}

## 步驟 17：檢查虛擬伺服器實例的狀態

佈建「虛擬伺服器實例」可能需要數秒到幾分鐘的時間。繼續之前，請先查詢伺服器的狀態，並確定它處於 `running` 狀態。

```bash
curl $rias_endpoint/v1/instances/$server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

也請儲存在上述 API 呼叫中所傳回虛擬伺服器實例的主要網路介面 ID。  

```bash
network_interface="<YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

除非您查詢特定實例，否則無法取得主要網路介面。
{: note}

## 步驟 18：建立浮動 IP

建立虛擬伺服器實例的浮動 IP，方法是使用實例的主要網路介面作為新浮動 IP 位址的目標。

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


儲存浮動 IP 的 ID。

```bash
floating_ip="<YOUR_FLOATING_IP_ID>"
```
{: pre}

## 步驟 19：以 SSH 方式登入虛擬伺服器實例

若要以 SSH 方式登入伺服器，請使用您所建立的「浮動 IP」的 `address`。若要取得「浮動 IP」的 `address`，請執行下列指令：

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

使用「浮動 IP」的 `address`，以使用 SSH 連接至虛擬伺服器實例：

```bash
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

安全群組可以防止以 SSH 方式存取虛擬伺服器。如果需要 SSH 存取，您必須使用[適當的安全群組](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups)。
{: note}

如需如何連接至實例的相關資訊，請參閱[使用 Linux 連接至實例](/docs/vsi-is/vsi_is_connecting_linux_gc.html)。


## 步驟 20（選用）：刪除資源

必要的話，請刪除資源。如果資源包含其他資源，則無法予以刪除。例如，如果 Virtual Private Cloud 包含子網路，則無法予以刪除，而且，如果子網路包含虛擬伺服器實例，則無法予以刪除。刪除時，API 可能會很快回復，但可能仍在進行資源刪除。建議查詢資源，以確定在刪除其他資源之前已將其刪除。

### 刪除浮動 IP。

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 刪除虛擬伺服器實例。

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 刪除金鑰。

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### 刪除公用閘道。

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 刪除子網路。

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 刪除 VPC。

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

無法從 VSI 刪除 vNIC，因此不需要執行步驟來刪除 vNIC。
{: note}

## 恭喜！

您已順利使用 REST API 佈建 Virtual Private Cloud 實例。若要嘗試其他 API 指令，請探索完整參考資料：

* [VPC 的 API 參考資料](https://{DomainName}/apidocs/rias)
