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

# IBM Cloud VPC 可用的服務端點
{: #service-endpoints-available-for-ibm-cloud-vpc}

當您準備好執行工作負載時，可以使用特定 ADN 端點，從 {{site.data.keyword.cloud}} VPC 內的 VSI 到達部分 IBM Cloud 基礎架構服務。透過 VPC 客戶可連接的專用端點，有數種類型的服務可供使用。透過使用這些內部端點，您可以避免在達到公用網際網路端點時可能產生的頻寬費用。

您可以連接的服務包括：

* DNS 解析器
* 鏡映
* Cloud Object Storage
* NTP

## IBM Cloud Object Storage 的範例端點

例如，若要連接 IBM Cloud 專用網路上物件儲存空間服務的專用端點，請將 URL 的「網域」部分取代為 `objectstorage.adn.networklayer.com`。

## DNS 及鏡映的端點

DNS 及鏡映在所有位置都使用相同的 161.26/16 空間。每個啟用 VPC 功能的站台都可以使用這些特定 IP 端點：

* `mirrors.adn.networklayer.com` (161.26.0.6)
* DNS 伺服器（161.26.0.10 及 161.26.0.11）
