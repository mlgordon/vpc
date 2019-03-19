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


# VPC 的定價
{: #pricing-for-vpc}

下表彙總使用 {{site.data.keyword.cloud}} Virtual Private Cloud 進行網際網路資料傳送的定價。請記住，VPC 與 Classic IBM Cloud 服務之間的資料流量免費。此外，對於 PayGo 服務，服務層也會連結至您的帳戶，而不是連結至任何特定的 VPC 實例。「金額」會以美元為單位顯示。

個別定價適用於 IBM Cloud VPC 內所使用的[虛擬伺服器實例](/docs/infrastructure/vpc?topic=vpc-pricing-for-virtual-servers-for-vpc)。

## 網際網路資料傳送的免費額度

| 資料傳送 | 所有 IBM Cloud VPC 客戶的成本 |
|---------------|------------------|
| 區域內 | 免費 |
| 相同地區的各區域之間 | 免費 |
| 使用公用閘道 | 免費（只有針對 PGW 所使用的浮動 IP 才需要收費）|

## 浮動 IP 定價

浮動 IP 的收費費率是每個月 $1（美國），從保留時開始。即使浮動 IP 未與 VSI 相關聯或未使用中，還是會收取費用。即使浮動 IP 僅保留幾天，還是會收取每個月 $1 的費用。


## 網際網路資料傳送的基本 PayGo 定價

| 資料傳送 | 資料量 | PayGo 定價 |
|-----------|-----------|------------------|
| 輸出至網際網路 | 0 到 5 GB | 免費 |
|  | 6 到 10,000 GB | 每 GB $0.087 |
|  | 10,001 到 50,000 GB | 每 GB $0.083 |
|  | 50,001 到 150,000 GB | 每 GB $0.07 |
|  | 150,001 GB 及以上 | 每 GB $0.05 |


當您建立新的 VPC 時，起始計費費用最多可能需要一小時才會出現在「主控台使用者介面」或 API 中。
{: tip}

如果您有公用閘道或「浮動 IP」，則可能仍然會看到一些最少輸出費用，即使您在該期間未送出任何輸出資料流量。這些費用用於 ARP 資料流量，這是操作帳戶的必要項目。
{: important}


