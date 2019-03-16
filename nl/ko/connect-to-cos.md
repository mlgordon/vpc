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

# VPC에서 IBM Cloud Object Storage에 연결
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

이 문서에서는 Virtual Private Cloud에서 IBM® Cloud Object Storage에 연결하는 방법을 설명합니다. 

## IBM Cloud Object Storage(COS) 개념

IBM Cloud Object Storage(COS)는 비정형 데이터를 저장하는 웹 범위 플랫폼입니다. 이는 신뢰성, 보안, 가용성과 수동 복제가 필요없는 재해 복구 기능을 제공합니다.
IBM Cloud Object Storage에 저장되는 정보는 암호화되어 여러 지리적 위치에 분산됩니다. 이는 S3 API를 구현하여 액세스할 수 있습니다. 이 서비스는 IBM Cloud Object Storage 서비스에서 제공하는 분산 스토리지 기술을 사용합니다. 

IBM COS는 세 가지 구성(**다중 지역**, **단일 지역** 및 **단일 사이트**)으로 사용할 수 있습니다. 
 * **다중 지역** 서비스는 단일 지역을 사용하는 경우보다 더 높은 내구성 및 가용성을 제공하지만 대기 시간이 약간 더 깁니다. 
 * **단일 지역** 서비스의 특성은 이와 반대이며, 하나의 지역에 있는 여러 가용성 구역에 오브젝트를 분배합니다. 특정 가용성 구역이 액세스 불가능하게 되어도 오브젝트 저장소는 계속해서 정상 작동합니다. 누락된 변경사항은 액세스 불가능 데이터 센터가 다시 온라인 상태가 되면 적용됩니다. 
 * **단일 사이트** 서비스는 선택된 데이터 센터의 Cloud Object Storage에 대한 액세스를 제공합니다. 
 
### VPC와 함께 사용할 수 있는 직접 엔드포인트

엔드포인트는 애플리케이션이 COS 명령을 실행하고 COS와 데이터를 교환하는 데 사용하는 URL입니다. 모든 엔드포인트는 동일한 API(Application Programming Interface)를 사용하여 COS와 상호작용합니다.
IBM Cloud 내에 프로비저닝된 서버는
서비스(COS 포함)에 API 엔드포인트를 사용합니다. 직접 엔드포인트는 고객의 IBM Cloud 서버에 서비스에 대한 고속 직접 연결을 제공합니다. 
 
## VPC에서 IBM Cloud Object Storage(COS)에 연결하는 방법
 1. [카탈로그 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window}에서 COS를 프로비저닝하십시오. 
 2. 다음 절에 나열된 지역 중 하나에서 COS 버킷을 작성하십시오. 
 3. Direct Endpoint for VPC를 사용하여 COS 버킷에 대한 인터페이스를 작성하십시오. 
 
## 미국 다중 지역 엔드포인트
 
| **미국 다중 지역** | **Direct Endpoint for VPC** |
|------------|-------------------------------|
| US 다중 지역 | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| 댈러스 액세스 지점 | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| 산호세 액세스 지점 | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| 워싱턴 DC 액세스 지점 | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## 미국 단일 지역 엔드포인트
 
| **지역** | **Direct Endpoint for VPC** |
|------------|-------------------------------|
| 미국 남부 | `s3.direct.us-south.cloud-object-storage.appdomain.cloud` |
| 미국 동부 | `s3.direct.us-east.cloud-object-storage.appdomain.cloud` |

 ## 단일 데이터 센터 엔드포인트
 
| **지역** | **Direct Endpoint for VPC** |
|------------|-------------------------------|
| 캐나다 토론토 | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| 캐나다 몬트리올 | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
