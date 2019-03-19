---
copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# 從 VPC 設定對標準基礎架構的存取權
{: #setting-up-access-to-your-classic-infrastructure-from-vpc}

您可以為任何帳戶，設定從每個地區中的某個 VPC 對「{{site.data.keyword.cloud}} 標準基礎架構」的存取權（包括「直接鏈結」連線功能）。這些特殊「標準存取 VPC」使用與 {{site.data.keyword.cloud}} 標準基礎架構相同的隱含路由器。

當您設定 VPC 進行標準存取時，標準帳戶中的每個計算主機（VSI 或裸機）都可以傳送及接收與標準存取 VPC 之間的封包。不過，請記住，防火牆、閘道、「網路 ACL」或安全群組可以過濾此資料流量。最佳作法是建議您僅容許應用程式正常運作所需的資料流量。

## 必要條件：
1. 標準帳戶必須鏈結至 IBM Cloud 帳戶。如需這項作業作法的指示，請參閱[鏈結 IBM ID 帳戶](/docs/account/softlayerlink.html)。
1. 必須對 VRF 啟用標準帳戶。
    * 如果您的帳戶已有「直接鏈結」，表示您已準備就緒。
    * 如果您的帳戶未啟用 VRF 功能，請開立問題單以針對您的帳戶要求「VRF 移轉」。請參閱「直接鏈結」文件中的[如何起始轉換](/docs/infrastructure/direct-link?topic=direct-link-how-you-can-initiate-the-conversion)，以進一步瞭解轉換處理程序。

防火牆、閘道、「網路 ACL」或安全群組可以過濾「標準」與 VPC 資源之間的部分或所有網路資料流量。
{: important}

## 建立標準存取 VPC
您可以使用「使用者介面」、「指令行介面 (CLI)」或「應用程式設計介面 (API)」，來建立具有「標準存取」功能的 VPC。

VPC 在建立時必須設定進行「標準存取」：您無法更新 VPC 來新增或移除「標準存取」功能。
{: note}

### 從使用者介面建立標準存取 VPC

從**建立 VPC** 頁面建立「標準存取 VPC」，方法是按一下**標準存取**標籤下標題為**啟用對標準資源的存取權**的勾選框。

![classic-access-ui](/images/classic-access-ui.png)

### 使用 CLI 建立標準存取 VPC

建立 VPC 時，請使用 `--classic-access` 旗標。例如，

```
ibmcloud is vpc-create my-access-vpc --classic-access
```
{: pre}


### 使用 API 建立標準存取 VPC

建立 VPC 時，傳入 `classic_access` 參數。例如，

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "my-access-vpc",
        "classic_access": true
      }'
```
{: pre}


## 限制

* 只有專用（後端）網路，才會連接至您帳戶的專用隱含路由器。
* 只有配置標準 API 的子網路，才會連接至專用隱含路由器的標準端。標準 VLAN 上的子網路不是由隱含路由器遞送。
* 只可以啟用每個帳戶每個地區 1 個 VPC 進行「標準存取」。
