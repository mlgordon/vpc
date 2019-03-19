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

# 在 VPC 中建立及管理儲存空間
{: #creating-and-managing-storage-in-vpc}

目前，{{site.data.keyword.cloud}} Virtual Private Cloud 只容許啟動儲存空間磁區。

當您佈建虛擬伺服器實例時，會將 100 GB 區塊儲存空間磁區建立為主要啟動磁區，並自動連接至實例。啟動磁區會提供 3 IOPS/GB 效能，並存在於 VSI 生命週期期間。 

當您刪除實例時，即會刪除啟動磁區。

## 建立及命名 VPC 儲存空間磁區的最佳作法：

* 確定您在佈建時為所有磁區命名（包括啟動磁區）。
* 確定您在連接時間為所有磁區連接命名
* 在帳戶的地區內，每個磁區都必須具有一個不同的名稱。 

刪除磁區之後，即可重新使用磁區的名稱。不過，請注意，重複使用磁區名稱可能會導致計費的混淆。
{:note}
