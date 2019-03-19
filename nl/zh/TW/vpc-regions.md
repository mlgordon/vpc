---

copyright:
  years: 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# 在不同地區中建立 VPC
{: #creating-a-vpc-in-a-different-region}

地區是您可以在其中部署應用程式、服務及其他 {{site.data.keyword.cloud}} 資源的特定地理位置。地區包含一個以上的區域，這些區域是管理運算、網路和儲存空間資源，以及管理各項服務和應用程式的相關冷能和電能的實體資料中心。區域彼此隔離，以確保不會共用單一失敗點。


Virtual Private Cloud 將分階段推出至所有 IBM Cloud 地區。

|   位置         | 地區   | API 端點     | 狀態   |
| ------- | :------: | :------: |:------: |
| 達拉斯 | us-south | `us-south.iaas.cloud.ibm.com`| 可用      |
| 法蘭克福  | eu-de | `eu-de.iaas.cloud.ibm.com`| 可用      |
| 華盛頓特區    | us-east | `us-east.iaas.cloud.ibm.com`| 即將推出    |
| 東京  | jp-tok | `jp-tok.iaas.cloud.ibm.com`| 即將推出    |
| 倫敦   | eu-gb | `eu-gb.iaas.cloud.ibm.com`| 即將推出    |
| 雪梨   | au-syd | `au-syd.iaas.cloud.ibm.com`| 即將推出    |

當您登入特定地區時，IBM Cloud CLI 會自動設定「地區 API (VPC)」端點。
{: note}

## 使用 CLI 登入特定地區

當您登入 IBM Cloud 時，可以指定地區，或稍後選擇地區。例如，若要直接登入「達拉斯」(`us-south`) 地區中的廣域 API 端點，請根據您是否有聯合帳戶 (SSO) 直接執行下列指令。

若為聯合帳戶，請執行下列指令：

```
ibmcloud login -a https://cloud.ibm.com -r us-south --sso
```
{: pre}

若為非聯合帳戶，請執行下列指令：

```
ibmcloud login -a https://cloud.ibm.com -r us-south
```
{: pre}

若要稍後選擇地區，請不要指定 `-r <region>` 參數，CLI 將會提示您選擇地區。

輸出範例：

```
API endpoint: cloud.ibm.com

Get One Time Code from https://identity-2.eu-central.iam.cloud.ibm.com/identity/passcode to proceed.
Open the URL in the default browser? [Y/n]> y
One Time Code >
Authenticating...
OK

Select an account:
1. MyAccount (00a11aa1a11aa11a1111a1111aaa11aa) <-> 1234567
2. TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321
Enter a number> 2
Targeted account TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321


Targeted resource group Default

Select a region (or press enter to skip):
1. au-syd
2. jp-tok
3. eu-de
4. eu-gb
5. us-south
6. us-east
Enter a number> 5
Targeted region us-south


API endpoint:      https://cloud.ibm.com   
Region:            us-south   
User:              first.last@email.com   
Account:           TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321  
Resource group:    Default   
CF API endpoint:      
Org:                  
Space:                

...
```
{: screen}

## 使用 CLI 切換地區

若要取得可用 VPC 地區的最新狀態，請執行下列指令：

```
ibmcloud is regions
```
{: pre}

若要切換至不同的地區，請執行 `ibmcloud target -r <region>` 指令。例如，若要切換至「法蘭克福」地區，請執行下列指令：

```
ibmcloud target -r eu-de
```
{: pre}

若要檢查您目前所在的位置，請執行下列指令：

```
ibmcloud target
```
{: pre}

## 使用 API 切換地區  

若要透過 REST 與「地區 API」互動，請將要求導向至您要在其中建立資源之地區的 API 端點。地區的 API 端點會顯示在表格上方。此外，您還可以執行下列指令來尋找不同地區的可用端點：

```
ibmcloud is regions
```
{: pre}


例如，若要取得 `us-south` 地區中的 VPC 清單，請執行下列指令：

```
curl https://us-south.iaas.cloud.ibm.com/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 區域

若要取得每個地區的可用區域清單，請執行 `ibmcloud is zones <region>` 指令。例如，若要取得 `us-south` 地區中的區域清單，請執行下列指令：

```
ibmcloud is zones us-south
```
{: pre}
