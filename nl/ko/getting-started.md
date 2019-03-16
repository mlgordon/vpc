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
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# IBM Cloud Virtual Private Cloud 인프라 시작하기
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

IBM은 2019년 4월 초부터 VPC에 대한 얼리 액세스 프로그램에 참여할 제한된 수의 고객을 선발하며, 시간이 지남에 따라 사용자를 늘릴 계획입니다. IBM Virtual Private Cloud에 액세스하려는 조직에서는 이 [지원 양식](https://cloud.ibm.com/vpc){: new_window}을 완료하십시오. 이렇게 하면 IBM 담당자가 연락하여 다음 단계에 대해 안내합니다.
{: important}

{{site.data.keyword.cloud}} Virtual Private Cloud 인프라를 시작하려면 다음 작업을 수행하십시오. 

1. Virtual Private Cloud를 작성하십시오. 
2. 한 구역 이상의 Virtual Private Cloud에서 서브넷을 하나 이상 작성하십시오. 
3. 서브넷에 있는 리소스와 인터넷 간의 연결을 가능하게 하려면 서브넷에 공용 게이트웨이(PGW)를 작성하십시오. 
4. 실행하려는 가상 서버 인스턴스(VSI)의 프로파일을 선택하고 이를 인스턴스화하십시오. 
5. 유동 IP 주소를 예약하고, 인터넷에서 가상 서버 인스턴스에 접근할 수 있도록 하려면 해당 주소를 가상 서버 인스턴스와 연관시키십시오. 
5. 가상 서버 인스턴스에 서비스 또는 애플리케이션을 배치하십시오. 

## 전제조건

 * **사용자 권한**: 사용자에게 VPC에서 리소스를 작성하고 관리할 수 있는 권한이 있는지 확인하십시오. 필수 권한의 목록은 [VPC 사용자에게 필요한 권한 부여](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources)를 참조하십시오. 

 * **SSH 키 준비**: 사용자는 가상 서버 인스턴스에 연결하는 데 SSH 키를 사용합니다. 

   * 홈 디렉토리의 `.ssh` 디렉토리에서 `id_rsa.pub`라는 파일을 찾아보십시오(예: `/Users/<USERNAME>/.ssh/id_rsa.pub`). 이 파일은 `ssh-rsa`로 시작하며 사용자의 이메일 주소로 끝납니다. 

   * 또는 SSH 키 생성: 공개 SSH 키가 없거나 기존 키의 비밀번호를 잊어버린 경우에는 `ssh-keygen` 명령을 실행한 후 프롬프트에 따라 새 키를 생성하십시오. 예를 들면, 명령 `ssh-keygen -t rsa -C "user_ID"`를 실행하여 Linux 서버에서 SSH 키를 생성할 수 있습니다. 이 명령은 두 개의 파일을 생성합니다. 생성된 공개 키는 `<your key>.pub` 파일에 있습니다. 
   
## UI, CLI 또는 REST API 사용

모든 VPC 리소스는 UI, CLI 또는 REST API를 통해 프로비저닝하고 관리할 수 있습니다. 

IBM Cloud Virtual Private Cloud를 처음 사용하는 경우에는 IBM Cloud VPC 및 해당 리소스를 작성하는 프로세스를 처음부터 끝까지 안내하는 아래 링크 중 하나를 선택하십시오. 사용자는 콘솔 UI, 명령행(CLI) 또는 지역 인프라 서비스(RIAS) API 중 무엇을 사용하여 작업을 시작할지 선택할 수 있습니다. 

* 사용자 인터페이스를 통한 액세스를 위해서는 [IBM Cloud 콘솔 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")]( https://{DomainName}/vpc){: new_window}에 로그인하십시오. 도움이 필요한 경우에는 [UI 안내서](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console)를 따르십시오. 
* 명령행 인터페이스를 사용하려는 경우에는 [IBM Cloud CLI](https://console.bluemix.net/docs/cli/index.html#overview)의 [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) 플러그인을 사용하고 [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli) 예를 따르십시오. 
* 고급 사용자는 [REST API](https://{DomainName}/apidocs/rias)를 직접 호출할 수 있습니다. [코드 예](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis) 튜토리얼에 따라 REST API 작업을 시작하십시오. 

## 다음 단계
작업을 시작할 준비가 되었으면 **VPC 네트워킹** 및 **VPC용 VSI**에 대한 상세 문서로 바로 이동할 수 있습니다. 

* [**IBM Virtual Private Cloud 네트워킹**](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**Virtual Private Cloud용 IBM Virtual Server**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

