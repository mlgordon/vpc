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

# 알려진 제한사항
{: #known-limitations}

이 문서는 현재 릴리스의 알려진 버그에 대한 간단한 설명, 지원되지 않는 기능 및 API에 대한 설명, 그리고 베타 서비스로만 제공되는 기능에 대한 표시를 포함하고 있습니다. 알려진 제한사항은 {{site.data.keyword.cloud}} Virtual Private Cloud에 기능이 추가됨에 따라 변경될 수 있으므로, 가끔씩 이 문서를 다시 확인하는 것이 좋습니다.  

## 알려진 버그

* 서브넷의 이름을 바꾸는 경우, 캐시 타이밍으로 인해 서버 세부사항 페이지에 서브넷의 새 이름이 표시되는 데 최대 1시간이 소요될 수 있습니다. (#758)

## 지원되지 않는 기능에 대한 요약

* Virtual Private Cloud에 대한 Direct Link 액세스는 [**클래식 액세스**](/docs/infrastructure/vpc/classic-access.html)를 통해서만 지원됩니다. 
* Virtual Private Cloud는 개인 서비스 엔드포인트의 서브세트만 사용할 수 있으며, 모든 엔드포인트가 사용 가능한 것은 아닙니다.  
* 이미지 저장 및 복원은 지원되지 않습니다. 

## 지원되지 않는 API

지원되는 항목에 대한 세부사항은 [API 스펙](https://{DomainName}/apidocs/rias)을 참조하십시오. 

다음 API는 이 릴리스에서 지원되지 않습니다. 

| 컴포넌트 | 기능 | 주석 |
|------|------|--------|
| **컴퓨팅:** |   |   |
| 이미지 | 작성/삭제는 지원되지 않음 | Ubuntu 16.04, CentOS 7.X, Windows 8, Debian|
| Network_Interfaces | 가져오기(작성, 삭제, 업데이트 없음) | |
| Volume_Interfaces |지원되지 않음 |   |
| Port_Speed | | 100 및 1000 한정 |
| **스토리지:** |   |   |
| 볼륨 |지원되지 않음 |   |
| 스냅샷 |지원되지 않음 |  |

## 아직 지원되지 않는 기능 및 유스 케이스

이 절에서는 지원되지 않는 기능 및 유스 케이스의 자세한 목록을 제공합니다.  

* Virtual Private Cloud는 다른 Virtual Private Cloud와 피어 관계가 될 수 없습니다. 
* 기존 IBM Cloud VSI 또는 Bare Metal Server는 Virtual Private Cloud로 마이그레이션할 수 없습니다. 
* 사용자 정의 라우트는 Virtual Private Cloud에 추가할 수 없습니다. Virtual Private Cloud의 모든 서브넷은 기본적으로 서로 통신할 수 있습니다. 
* IBM Cloud VPC는 멀티캐스트 또는 브로드캐스트 도메인을 지원하지 않습니다. 
* IBM Cloud VPC는 엔드-투-엔드 암호화를 제공하지 않습니다.  
* Virtual Private Cloud에서 사용할 수 있는 핵심 IBM Cloud 서비스는 다음과 같습니다. 다른 서비스에는 액세스할 수 없습니다.  
  * NTP
  * 로깅
  * DNS 분석기
* 하나의 서브넷은 여러 구역에 있을 수 없습니다. 
* 서브넷을 한 구역에서 다른 구역으로 이동할 수는 없습니다. 
* 서브넷을 작성한 후에는 해당 크기를 조정할 수 없습니다. 
* Bare Metal Server는 Virtual Private Cloud에서 프로비저닝할 수 없습니다. 
* IBM Cloud 클래식 리소스는 Virtual Private Cloud와 동일한 서브넷에 있을 수 없습니다. [**클래식 액세스**](/docs/infrastructure/vpc/classic-access.html)를 사용하면 클래스 리소스와 사용자 계정에 있는 한 Virtual Private Cloud를 연결할 수 있습니다. 
* IPv6은 지원되지 않습니다. 
* 사용자가 자신이 소유한 공인 IP를 유동 IP로 사용할 수는 없습니다. 유동 IP 풀은 IBM에서 제공합니다. 
* 하나의 유동 IP는 하나의 구역에 바인드됩니다. 예를 들어, 구역 1에서 예약된 유동 IP는 동일한 VPC의 구역 2에 있는 VSI에 지정될 수 없습니다. 
* 사설 IP 주소는 VSI 간에 이동할 수 없습니다. 
* 네트워크 인터페이스는 VSI 간에 이동할 수 없습니다. 
* VSI의 특정 IP 주소를 지정할 수는 없습니다. 서브넷의 IP 범위만 지정할 수 있습니다. VSI를 서브넷에 연결하고 나면 시스템이 해당 서브넷으로부터 사설 IP를 지정합니다. 
* IBM Cloud VPC는 LBaaS, ACL 및 보안 그룹과 같은 고유 NaaS(Network as a Service) 도구와 함께 제공됩니다. 자신이 소유한 네트워크 어플라이언스(예: Vyatta Gateway 또는 기타 로드 밸런서)를 사용하여 Virtual Private Cloud에 있는 리소스를 제어할 수는 없습니다. 마찬가지로, IBM Cloud 클래식 인프라에 있는 자기 소유의 로드 밸런서 또는 보안 그룹을 사용하여 IBM Cloud VPC에 있는 리소스를 제어할 수는 없습니다. 
* 공용 게이트웨이는 인터넷에서 IBM Cloud VPC에 있는 VSI로 트래픽 전송을 시작하는 것을 허용하지 않습니다. 이를 위해서는 유동 IP를 사용해야 합니다. 
* ACL은 Stateless이므로 리턴 트래픽은 ACL 규칙에서 명시적으로 허용되어야 합니다. 

## 베타 서비스로 사용할 수 있는 컴포넌트 또는 기능

* **IBM Cloud VPC용 VPN**은 베타 서비스로만 사용할 수 있습니다. 
* **IBM Cloud VPC용 LBaaS**는 베타 서비스로만 사용할 수 있습니다. 
