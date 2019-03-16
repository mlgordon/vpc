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

# IBM Cloud Virtual Private Cloud(VPC) 인프라 정보
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

{{site.data.keyword.cloud}} VPC는 성능, 서비스 성장, 유연성 및 배치 자유도에 대한 기존 산업 표준을 재정의하는 차세대 IBM One Cloud 플랫폼의 일부입니다. 

VPC(Virtual Private Cloud)는 클라우드 보안 및 공용 클라우드에서의 동적 스케일링 기능을 제공하는 비용 효율적인 시작점을 제공합니다. 이는 가상 인프라 및 네트워크 트래픽 세분화를 세밀하게 제어할 수 있게 해 줍니다. 

## 퍼블릭 클라우드 내의 개인용 영역
IBM Cloud VPC는 퍼블릭 클라우드 내에서 보안이 강력하며 격리된 환경을 제공합니다. 이는 사용자에게 프라이빗 클라우드의 보안과 퍼블릭 클라우드의 민첩성 및 사용 용이성을 동시에 제공합니다. 

 * 미션에 있어서 필수적인, 클라우드 허용 애플리케이션 또는 클라우드 네이티브 애플리케이션을 지원하기 위해 주요 네트워크 서비스를 관리하고 필요에 따라 Virtual Server를 시작할 수 있습니다. 
 * 보안 및 간편한 액세스를 위해 디자인된 고유 네트워크 정책을 정의할 수 있습니다. 
 * 리소스를 프로비저닝하고 이를 서로 연결하거나 서로 격리시킬 수 있습니다. 

### 논리적 격리
IBM Cloud Virtual Private Cloud(VPC)는 사용자의 애플리케이션에 확장성 및 보안을 제공하는 동시에 모든 지역의 다른 네트워크로부터 논리적으로 격리시킵니다. 

이 논리적 격리를 가능하게 하기 위해, VPC는 사설 IP 주소 범위를 사용하여 서브넷으로 분할됩니다. 그러나 기본적으로 동일한 Virtual Private Cloud 내의 모든 리소스(VSI 등)는 서브넷에 관계없이 서로 통신할 수 있습니다. 서브넷은 하나의 구역에 포함되고 여러 구역에 걸쳐 존재할 수 없으며, 이는 보안, 대기 시간 감소 및 재해 복구에 도움이 됩니다. 

### 빠른 인스턴스 프로비저닝 및 보안

특정 워크로드에 대해 최적화된, 사전 정의된 프로파일을 사용하여 가상 서버 인스턴스(VSI)를 빠르게 작성하십시오. 보안 그룹을 사용하여 인스턴스를 보호하십시오. 

### 네트워킹 기능
IBM Cloud VPC는 IP 주소 범위 선택, 가상 방화벽(보안 그룹 및 네트워크 ACL), 사이트 대 사이트 가상 사설망(VPN) 및 탄력적 로드 밸런싱(LBaaS)을 포함한 포괄적인 네트워크 기능을 제공합니다. 

 * 제안된 접두부 범위 및 사전 구성된 네트워크 정책을 사용하여 가상 토폴로지를 자동으로 구성할 수 있습니다. 
 * IBM Cloud VPC를 사용자 정의하고 변화하는 요구사항에 맞춰 이를 조정할 수 있습니다. 
 * 자신이 소유한 IP 범위를 사용할 수 있습니다. 
 * 기존 풀의 유동 IP를 지정할 수 있습니다. 
 * 로드 밸런싱 및 VPN에 다중 지역 제어 평면이 있으며, 이는 제어 평면이 배치된 각 지역이 고객의 가상 서버 인스턴스에 대해 모든 지역을 지원할 수 있음을 의미합니다. 하나의 지역에서 발생한 장애는 다른 지역의 서비스에 영향을 주지 않습니다. 

### 글로벌 연결
애플리케이션 및 사용 가능한 리소스를 여러 지역에서 사용할 수 있도록 범위 지정할 수 있습니다. VPN을 사용하면 하이브리드 클라우드 배치의 다른 프로젝트 또는 다른 부분으로의 사설 연결을 작성할 수 있습니다. 

### 네트워크 보안
IBM Cloud VPC에서는 인스턴스 레벨 보호를 위한 가상 방화벽 역할을 하는 보안 그룹과 서브넷 레벨 보호를 위한 네트워크 액세스 제어 목록(ACL)을 사용하여 보안이 통합되어 있습니다. 

### 로드 밸런싱
IBM Cloud VPC 내에서는 로드 밸런싱을 사용하여 특정 대상 집합에 네트워크 트래픽을 분배함으로써 성능 및 HA를 향상시키십시오. Load Balancers는 애플리케이션 및 서비스의 상태 또한 모니터합니다. 한 구역 내의 인스턴스 또는 지역 내 여러 구역의 인스턴스에 수신 애플리케이션 트래픽을 분배하도록 로드 밸런서를 구성할 수 있습니다. 

### 인터넷 액세스
가상 서버 인스턴스(VSI)에서 공용 인터넷과 통신할 수 있도록 하는 데는 두 가지 선택사항이 있습니다. 
* 공용 게이트웨이(PGW)를 사용하여 연결된 서브넷에 있는 모든 가상 서버 인스턴스의 통신을 가능하게 합니다. 사용되는 대역폭을 제외하고 PGW를 사용하여 발생하는 비용은 없습니다. 
* 유동 IP(FIP)를 사용하여 한 가상 서버 인스턴스(VSI)로부터의 통신을 가능하게 합니다. 

![IBM Cloud VPC](images/vpc-experience.png)
**그림: IBM Cloud VPC 구성 예**

## 클라우드 네이티브 워크로드 지원

Virtual Private Cloud는 클라우드 네이티브 워크로드에 대해서, 그리고 기존 인프라를 IBM Cloud와 연결하는 데 있어서 이상적입니다. 코그너티브, AI 및 기계 학습 컴퓨팅과 같은 모든 중요 워크로드를 위한 최상의 클라우드를 작성할 수 있습니다. 한편, 원하는 경우에는 기존 워크로드에 대해 계속해서 기존 IBM Cloud를 이용할 수 있습니다. 

VPC가 하이브리드, 클라우드 허용 및 클라우드 네이티브 워크로드를 지원하는 몇 가지 방법은 다음과 같습니다. 

 * API를 통해 격리된 애플리케이션 환경을 작성하고 관리
 * BYOIP(Bring Your Own IP)를 사용하여 네트워크 토폴로지 디자인
 * 유연한 API 기반 토폴로지를 위한 보안 그룹 및 네트워크 액세스 제어 목록(ACL) 사용
 * 대기 시간이 짧으며 속도가 빠른 연결을 가능하게 하는, HA 제공 가용성 구역
 * Auto-Scaling
   * 1일당 수천 개 서버 단위로 확장하거나 축소
   * 인증서 관리를 통해 확장 가능하며 신뢰할 수 있는 로드 밸런싱 사용
   * 확장 가능하며 신뢰할 수 있는 모니터링 설정
   * 고객에게 무한한 용량을 보유한 것과 같은 느낌을 줌
 * 고속 네트워킹 및 스토리지 디바이스 이용
 * 항상 작동 서비스 사용 가능(제어 평면)
 * 재해 복구 및 복원성을 위해 여러 지역을 활용
 * 주요 서비스 제공 및 이용: IPAM, VPN, 방화벽, SSH, DNS, L4 로드 밸런싱
 * 기타 서비스 설정: Auto-Scaling, CDN, 서드파티 NFV
 * 선호도 및 비선호도를 사용한 빠른 VSI 프로비저닝 가능
 * 사전 저장된 이미지를 통한 유연한 이미지 관리 사용
 * GPU에 대한 지원 제공

## 이점 요약

 * 프로파일이라고 하는, 인스턴스에 대해 사전 정의된 구성을 사용하여 빠르게 시작할 수 있음
 * 전 세계 범위에서 사용 가능한 구역 및 지역으로 인한 유연한 지리적 범위
 * ACL 및 보안 그룹으로 처음부터 보안 확보
 * 쉬운 확장 및 공유를 통해 VPC 네트워크 및 리소스를 온프레미스 설비에서 클라우드로 확장 가능
 * 최적의 성능 및 효율을 위한 워크로드 모니터링

## 기능 요약

  * 서브넷을 작성하고 자신이 소유한 IP 범위를 사용
  * Ubuntu 16.04, CentOS 7.x, Windows 또는 Debian을 사용하는 가상 서버 인스턴스(VSI) 작성 및 관리
  * 유동 IPv4 예약 및 연관
  * 구역당 하나의 공용 게이트웨이(PGW)를 작성하여 서브넷에 대한 인터넷 액세스 확보
  * 보안 그룹을 작성하고 VSI에 할당
  * 네트워크 액세스 제어 목록(ACL)을 사용하여 서브넷에 대한 보안 제공
  * 하나의 가상 네트워크 인터페이스 카드(vNIC)를 사용한 단일 홈 VSI
  * 다중 홈, 다중 vNIC 가상 서버 인스턴스(VSI)
  * 구역 배치(US-South 지역 또는 FRA 지역)
  * VPN에 의한 인터넷 액세스
  * VPC의 네이티브 로드 밸런싱(LB)

## BYOIP 제한사항

IBM Cloud VPC 계정에서 자신이 소유한 공인 IPv4 주소 범위를 사용(BYOIP)할 수 있습니다. BYOIP를 사용하는 경우 IBM Cloud는 이러한 IPv4 주소를 IBM Cloud 리소스에 구성해야 하며, 이렇게 하면 사용자가 제공한 주소에서 패킷이 송수신됩니다. 따라서 사용자가 제공한 IPv4 범위를 IBM Cloud에서 사용하면, 이 서비스를 사용함으로써 이러한 IP 주소가 IBM의 지원 인력 및 서드파티에 노출될 수 있습니다.
{: important}

BYOIP를 사용하려면 API 또는 CLI를 사용해야 합니다. 이 고급 기능은 IBM Cloud 콘솔 UI를 통해 사용할 수 없습니다.
{: note}

알려진 제한사항과 현재 지원되지 않는 기능의 전체 목록은 [알려진 제한사항](/docs/infrastructure/vpc?topic=vpc-known-limitations) 문서를 참조하십시오. 

## 자세히 보기

* [**IBM VPC 용어**](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**IBM VPC 보안**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**사용 가능한 IBM VPC 지역 및 서브넷**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**VPC에서의 네트워크 리소스 작성 및 관리**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [**가상 서버 인스턴스 작성 및 관리**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
