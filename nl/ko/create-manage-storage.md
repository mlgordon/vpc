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

# VPC에서의 스토리지 작성 및 관리
{: #creating-and-managing-storage-in-vpc}

현재 {{site.data.keyword.cloud}} Virtual Private Cloud는 부트 스토리지 볼륨만 허용합니다. 

가상 서버 인스턴스를 프로비저닝할 때 자동으로 100GB 블록 스토리지 볼륨이 기본 부트 볼륨으로 작성되어 인스턴스에 연결됩니다. 이 부트 볼륨은 3IOPS/GB의 성능을 제공하며 VSI 라이프사이클 동안 존재합니다.  

인스턴스를 삭제하면 부트 볼륨이 삭제됩니다. 

## VPC 스토리지 볼륨의 작성 및 이름 지정에 대한 우수 사례:

* 부트 볼륨을 포함하여 모든 볼륨은 프로비저닝 시에 이름을 지정해야 합니다. 
* 모든 볼륨 연결 항목은 연결 시에 이름을 지정해야 합니다. 
* 각 볼륨에는 계정 및 지역 내에서 고유한 이름이 있어야 합니다.  

볼륨이 삭제된 후에는 해당 볼륨의 이름을 다시 사용할 수 있습니다. 그러나 볼륨 이름을 다시 사용하면 청구와 관련하여 혼동이 발생할 수 있습니다.
{:note}
