---
copyright:
  years: 2018-2019
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

# 從 VPC 連接至 IBM Cloud Object Storage
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

本文件說明如何從 Virtual Private Cloud 連接至 IBM® Cloud Object Storage。

## 何謂 IBM Cloud Object Storage (COS)？

IBM Cloud Object Storage (COS) 是一種可儲存非結構化資料的 Web 規模平台。它提供可靠性、安全、可用性及災難回復，而不進行手動抄寫。儲存在 IBM Cloud Object Storage 內的資訊已加密，並分散在多個地理位置。可透過 S3 API 的實作來存取它。本服務利用 IBM Cloud Object Storage 服務所提供的分散式儲存技術。

IBM COS 有三種配置：**跨地區**、**地區**及**單一站台**。
 * **跨地區**服務提供的延續性及可用性高於使用單一地區，但代價是延遲稍高。
 * **地區**服務剛好相反：它會將物件分散在單一地區內的多個可用性區域。如果無法存取給定的地區或可用性區域，則物件儲存庫會繼續順利運作。當無法存取的資料中心恢復上線時，會套用任何遺漏的變更。
 * **單一站台**服務提供所選取資料中心內 Cloud Object Storage 的存取權。
 
### 與 VPC 搭配使用的 COS 直接端點

端點是應用程式用來發出 COS 指令並與 COS 交換資料的 URL。每個端點使用相同的「應用程式設計介面 (API)」來與 COS 互動。IBM Cloud 內佈建的伺服器會將 API 端點用於服務（包括 COS）。直接端點可讓客戶的 IBM Cloud 伺服器具有高速且直接的服務連線，但不會增加頻寬成本。
 
## 如何從 VPC 連接至 IBM Cloud Object Storage (COS)
 1. 從[型錄 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window} 佈建 COS。
 2. 在下一節所列的其中一個「地區」中，建立 COS 儲存區。
 3. 使用 VPC 的「直接端點」來建立與 COS 儲存區的介面。
 
## 美國跨地區端點
 
| **美國跨地區** | **VPC 的直接端點** |
|------------|-------------------------------|
| 美國跨地區 | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| 達拉斯存取點 | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| 聖荷西存取點 | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| 華盛頓特區存取點 | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## 美國地區端點
 
| **地區** | **VPC 的直接端點** |
|------------|-------------------------------|
| 美國南部 | `s3.direct.us-south.cloud-object-storage.appdomain.cloud`|
| 美國東部 | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`|

 ## 單一資料中心端點
 
| **地區** | **VPC 的直接端點** |
|------------|-------------------------------|
| 加拿大多倫多 | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| 加拿大蒙特婁 | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
