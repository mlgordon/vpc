---
copyright:
  years: 2017, 2019
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

# 關於 IBM Cloud Virtual Private Cloud (VPC) 基礎架構
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

{{site.data.keyword.cloud}} VPC 是下一代 IBM One Cloud 平台的一部分，以重新定義效能、服務成長、彈性及部署自由的傳統業界標準。

Virtual Private Cloud (VPC) 提供符合成本效益的進入點，提供雲端安全，以及在公用雲端中動態調整的能力。它提供對虛擬基礎架構及網路資料流量分段的細部控制。

## 公用雲端中的專用空間
IBM Cloud VPC 在公用雲端內提供隔離且絕對安全的環境。它為您提供專用雲端的安全，以及公用雲端的敏捷性和易用性。

 * 您可以管理重要網路服務，以及視需要啟動「虛擬伺服器」，來支援您的關鍵任務、雲端容錯及雲端原生應用程式。
 * 您可以定義針對安全及方便存取所設計的專屬網路原則。
 * 您可以佈建資源並將它們彼此連接，也可以將它們彼此隔離。

### 邏輯隔離
IBM Cloud Virtual Private Cloud (VPC) 可讓您的應用程式與所有地區中的其他網路進行邏輯隔離，同時提供可調整性及安全。

為了讓此邏輯隔離可行，會使用某範圍的專用 IP 位址將該 VPC 分割為數個子網路。不過，依預設，相同 Virtual Private Cloud 內的所有資源（如 VSI）都可以彼此通訊，不論其子網路為何。子網路包含在單一區域內，而且不能跨越多個區域，這有助於安全保護、減少延遲，以及災難回復。

### 快速實例佈建及安全

使用針對特定工作負載最佳化的預先定義設定檔，快速建立虛擬伺服器實例 (VSI)。請使用安全群組來保護實例。

### 網路功能
IBM Cloud VPC 提供綜合性網路功能，包括 IP 位址範圍選擇、虛擬防火牆（安全群組及網路 ACL）、站台對站台虛擬專用網路 (VPN)，以及具備彈性的負載平衡 (LBaaS)。

 * 您可以使用建議的字首範圍及預先配置的網路原則，來自動配置虛擬拓蹼。
 * 您可以自訂 IBM Cloud VPC，並無縫地將它調整為不斷變更的需求。
 * 您可以攜帶自己的 IP 範圍。
 * 您可以從預先存在的儲存區中指派浮動 IP。
 * 負載平衡及 VPN 具有多地區控制平面，這表示每個部署控制平面的地區都可以支援客戶虛擬伺服器實例的所有地區。單一地區的故障將不會影響任何其他地區的服務。

### 廣域連線功能
您可以將應用程式及可用資源限定為跨越多個地區。您可以使用 VPN，為混合式雲端部署的其他專案及其他部分建立專用連線。

### 網路安全
安全已整合到 IBM Cloud VPC，其中的安全群組會充當用於實例層次保護的虛擬防火牆，以及用於子網路層次保護的網路存取控制清單 (ACL)。

### 負載平衡
在 IBM Cloud VPC 內，使用負載平衡，將您的網路資料流量配送到一組目標，以改善效能及 HA。「負載平衡器」也會監視應用程式及服務的性能。您可以設定負載平衡器，以將送入的應用程式資料流量配送到單一區域中的實例，或某個地區內的多個區域。

### 網際網路存取
有兩個選項可用來啟用從虛擬伺服器實例 (VSI) 到公用網際網路的通訊：
* 使用公用閘道 (PGW) 來啟用連接子網路上所有虛擬伺服器實例的通訊。使用 PGW 無需付費，但若使用頻寬則不在此限。
* 使用「浮動 IP (FIP)」來啟用來自單一虛擬伺服器實例 (VSI) 的通訊。

![IBM Cloud VPC](images/vpc-experience.png)
**圖：範例 IBM Cloud VPC 配置**

## 支援雲端原生工作負載

Virtual Private Cloud 適用於雲端原生工作負載，以及將現有基礎架構鏈結至 IBM Cloud。您可以為所有重要工作負載（例如認知、AI 及 Machine Learning 計算）建立最佳雲端。同時，您可以視需要繼續將 IBM Cloud Classic 用於傳統工作負載。

以下是 VPC 支援混合式、雲端容錯及雲端原生工作負載的一些方式：

 * 透過 API 建立及管理隔離的應用程式環境
 * 使用 BYOIP（自帶 IP）來設計網路拓蹼
 * 利用「安全群組」及「網路存取控制清單 (ACL)」來容許彈性且由 API 驅動的拓蹼
 * 「可用性區域」容許跨地區的高速及低延遲連線，並具有 HA
 * 自動調整大小
   * 每天擴增或縮減數千部伺服器
   * 搭配使用可擴充及可靠的負載平衡與憑證管理
   * 建立可擴充及可靠的監視
   * 維護用戶端無限容量的假象
 * 利用高速網路及儲存裝置
 * 容許「一律開啟」服務（控制平面）
 * 涵蓋多個地區以進行災難回復及備援
 * 提供並利用核心服務：IPAM、VPN、防火牆、SSH、DNS 及「L4 負載平衡」
 * 設定其他服務：自動調整大小、CDN、協力廠商 NFV
 * 容許具有親緣性及反親緣性的快速 VSI 佈建
 * 搭配使用彈性映像檔管理與預先儲存的映像檔
 * 提供 GPU 的支援

## 好處摘要

 * 使用您實例的預先定義配置（稱為設定檔）來快速開始使用
 * 廣域提供區域及地區的彈性地理範圍
 * 使用 ACL 及安全群組，從基礎進行安全保護
 * 可輕鬆地擴充及共用 VPC 網路與資源，以從內部部署機能延伸到您的雲端
 * 監視工作負載，以獲得最佳效能及效率

## 特性摘要

  * 建立子網路，並自帶 IP 範圍
  * 使用 Ubuntu 16.04、CentOS 7.x、Windows 或 Debian 來建立及管理「虛擬伺服器實例 (VSI)」
  * 保留並關聯「浮動 IPv4」
  * 建立公用閘道 (PGW) 以取得子網路的網際網路存取，一個區域一個
  * 建立安全群組並將其指派給 VSI
  * 使用網路存取控制清單 (ACL) 來提供子網路的安全
  * 使用一張虛擬網路介面卡 (vNIC) 的單一主目錄 VSI
  * 多重主目錄、多 vNIC 虛擬伺服器實例 (VSI)
  * US-South 地區或 FRA 地區中的區域部署
  * 透過 VPN 的網際網路存取
  * VPC 原生的「負載平衡 (LB)」

## BYOIP 警告

您可以將自己的公用 IPv4 位址範圍 (BYIP) 帶至您的 IBM Cloud VPC 帳戶。當您使用 BYOIP 時，IBM Cloud 必須在 IBM Cloud 資源上配置這些 IPv4 位址，以將封包傳送至您所提供的位址以及傳送來自您所提供位址的封包。因此，在 IBM Cloud 上使用所提供的 IPv4 範圍之後，可以在使用此服務時，向 IBM 支援人員及協力廠商公開這些 IP 位址。
{: important}

您必須使用 API 或 CLI 來使用 BYOIP。此進階功能無法透過 IBM Cloud 主控台使用者介面取得。
{: note}

如需目前不支援的完整已知限制及特性清單，請參閱[已知限制](/docs/infrastructure/vpc?topic=vpc-known-limitations)文件。

## 進一步瞭解

* [**IBM VPC 術語**](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**IBM VPC 安全**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**可用的 IBM VPC 地區及子網路**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**在 VPC 中建立及管理網路資源**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [**建立及管理虛擬伺服器實例**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
