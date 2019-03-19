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
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# 已知限制
{: #known-limitations}

本文件包含現行版本已知錯誤的簡短說明、不受支援之特性及 API 的說明，以及現在僅提供為「測試版」服務之特性的指示。已知限制可能會在我們將功能新增至 {{site.data.keyword.cloud}} Virtual Private Cloud 時變更，因此請隨時檢查本文件。 

## 已知錯誤

* 如果您重新命名子網路，則基於快取計時，可能需要 1 小時才能在伺服器詳細資料頁面中看到您子網路的新名稱。(#758)

## 不受支援特性的摘要

* 只有透過[**標準存取**](/docs/infrastructure/vpc/classic-access.html)才支援對 Virtual Private Cloud 的 Direct Link 存取。
* 「專用服務端點」的子集可用於 Virtual Private Cloud，並非所有端點都可以使用。 
* 不支援儲存及還原映像檔。

## API 不受支援

如需支援項目的詳細資料，請參閱 [API 規格](https://{DomainName}/apidocs/rias)。

本版不支援下列 API。

| 元件 | 功能 | 註解 |
|------|------|--------|
| **計算：** |   |   |
| 映像檔 | 不支援建立/刪除 | Ubuntu 16.04、CentOS 7.X、Windows 08、Debian|
| Network_Interfaces | 取得（無建立、刪除、更新）| |
| Volume_Interfaces | 不支援 |   |
| Port_Speed | | 僅限 100 及 1000 |
| **儲存空間：** |   |   |
| 磁區 | 不支援 |   |
| Snapshot | 不支援 |  |

## 尚未支援的特性及使用案例

本節提供不受支援特性及使用案例的詳細清單。 

* Virtual Private Cloud 無法與其他 Virtual Private Cloud 配對。
* 現有 IBM Cloud VSI 或裸機伺服器無法移轉至 Virtual Private Cloud。
* 無法將自訂路徑新增至 Virtual Private Cloud。依預設，Virtual Private Cloud 中的所有子網路都可以彼此通訊。
* IBM Cloud VPC 不支援多重播送或廣播網域。
* IBM Cloud VPC 無法提供端對端加密。 
* 以下是可從 Virtual Private Cloud 使用的核心 IBM Cloud 服務。無法存取其他服務。 
  * NTP
  * 記載
  * DNS 解析器
* 子網路不能位於多個區域上。
* 子網路無法從某個區域移至另一個區域。
* 子網路在建立之後即無法調整大小。
* 裸機伺服器無法佈建於 Virtual Private Cloud 中。
* IBM Cloud Classic 資源不能位於 Virtual Private Cloud 的相同子網路中。使用[**標準存取**](/docs/infrastructure/vpc/classic-access.html)，可以建立標準資源與帳戶中某個 Virtual Private Cloud 之間的連線功能。
* 不支援 IPv6。
* 您不能使用自己的公用 IP 作為「浮動 IP」。「浮動 IP」儲存區由 IBM 提供。
* 「浮動 IP」已連結至區域。例如，無法將「區域 1」中儲存區內所保留的「浮動 IP」指派給相同 VPC 中「區域 2」內的 VSI。
* 無法在 VSI 之間移動專用 IP 位址。
* 無法在 VSI 之間移動網路介面。
* 您無法指定 VSI 的特定 IP 位址。您只能指定子網路的 IP 範圍。將 VSI 連接至子網路之後，系統會指派來自該子網路的專用 IP。
* IBM Cloud VPC 隨附自己的「網路即服務」工具，例如 LBaaS、ACL 及安全群組。您無法使用自己的網路應用裝置（例如，Vyatta Gateway 或其他負載平衡器），來控制 Virtual Private Cloud 中的任何資源。同樣地，您無法在「IBM Cloud 標準基礎架構」中使用您自己的負載平衡器或安全群組服務，來控制 IBM Cloud VPC 中的資源。
* 公用閘道不允許將資料流量從網際網路起始至 IBM Cloud VPC 中的 VSI。基於該目的，必須使用「浮動 IP」。
* ACL 是無狀態的，因此必須在 ACL 規則中明確容許傳回的資料流量。

## 可作為測試版服務使用的元件或特性

* **適用於 IBM Cloud VPC 的 VPN** 僅作為測試版服務提供。
* **適用於 IBM Cloud VPC 的 LBaaS** 僅作為測試版服務提供。
