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

# IBM Cloud VPC에서 사용할 수 있는 서비스 엔드포인트
{: #service-endpoints-available-for-ibm-cloud-vpc}

워크로드를 실행할 준비가 되면 특정 ADN 엔드포인트를 사용하여 {{site.data.keyword.cloud}} VPC에 있는 VSI로부터 몇 가지 IBM Cloud 인프라 서비스에 접근할 수 있습니다. VPC 고객이 접근할 수 있는 사설 엔드포인트를 통해 몇 가지 유형의 서비스를 사용할 수 있습니다. 이러한 내부 엔드포인트를 사용하면 공용 인터넷에서 엔드포인트에 접근했을 때 발생할 수 있는 대역폭 비용을 절감할 수 있습니다. 

접근할 수 있는 서비스는 다음 항목을 포함합니다. 

* DNS 분석기
* 미러
* Cloud Object Storage
* NTP

## IBM Cloud Object Storage에 대한 엔드포인트 예

예를 들어, IBM Cloud 사설 네트워크에 있는 Object Storage 서비스에 대한 사설 엔드포인트에 접근하려면 URL의 "도메인" 부분을 `objectstorage.adn.networklayer.com`으로 대체하십시오. 

## DNS 및 미러에 대한 엔드포인트

DNS와 미러는 모든 곳에서 동일한 161.26/16 영역을 사용합니다. 다음 특정 IP 엔드포인트는 각 VPC 사용 사이트에서 사용할 수 있습니다. 

* `mirrors.adn.networklayer.com`(161.26.0.6)
* DNS 서버(161.26.0.10 및 161.26.0.11)
