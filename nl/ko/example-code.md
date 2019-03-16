---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# REST API를 사용하여 VPC 작성
{: #creating-a-vpc-using-the-rest-apis}

이 안내서는 IBM Cloud 지역 API(RIAS)를 사용하여 {{site.data.keyword.cloud}} Virtual Private Cloud 리소스를 작성하는 방법을 보여줍니다. 

## 전제조건:

1. [IBM Cloud CLI](https://cloud.ibm.com/docs/cli/index.html#overview)를 설치하십시오. 

## 1단계: IBM Cloud에 로그인하여 API 호출에 사용할 IAM 토큰 얻기

연합 계정이 있는 경우에는 다음 명령을 실행하십시오. 
```
ibmcloud login -sso
```
{: pre}

그렇지 않은 경우에는 다음 명령을 실행하십시오. 

```
ibmcloud login
```
{: pre}

이 명령은 URL을 리턴하고 패스코드에 대한 프롬프트를 표시합니다. 브라우저에서 해당 URL로 이동한 후 로그인하십시오. 성공하면 일회성 패스코드를 얻습니다. 이 패스코드를 복사하여 프롬프트에 응답으로 붙여넣으십시오. 인증 단계가 완료되면 계정을 선택하라는 프롬프트가 표시됩니다. 나머지 프롬프트에 응답하여 로그인을 완료하십시오. 

## 2단계: IBM Identity and Access Management(IAM) 토큰 얻기

다음 명령은 IBM Cloud CLI를 호출하고, IAM 토큰 및 `Bearer` 토큰 ID를 구문 분석하여 나중에 다른 명령에 사용할 수 있는 변수에 저장합니다. 

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 IAM 토큰을 보려면 명령 ``echo $iam_token``을 실행하십시오. 

결과는 다음과 같이 표시되어야 합니다. 

```
Bearer <your token>
```
{: screen}

권한 부여 헤더는 토큰이 "Bearer"로 시작될 것으로 예상합니다. 위 결과가 "Bearer"를 포함하지 않는 경우에는 `iam_token` 변수를 업데이트하여 이를 포함시키십시오. 이 문서의 예에서는 "Bearer"가 `iam_token`에 포함되어 있다고 가정합니다. 

IAM 토큰은 만료되므로 각 시간마다 이전 단계를 반복하여 토큰을 새로 고쳐야 합니다.
{: important}

## 3단계: API 엔드포인트를 변수로 저장

나중에 다시 사용할 수 있도록 API 엔드포인트를 변수에 저장하십시오. API 엔드포인트는 지역에 따라 다르며
규칙 `https://<region>.iaas.cloud.ibm.com`을 따릅니다. 예를 들어, `us-south` API 엔드포인트는 `https://us-south.iaas.cloud.ibm.com`입니다. 

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

이 변수가 저장되었는지 확인하려면 `echo $rias_endpoint`를 실행하고 응답이 비어 있지 않은지 확인하십시오. 

## 4단계: GET Regions API 실행

예상치 않은 결과가 발생하는 경우에는 `curl` 명령 뒤에 `--verbose`(디버그) 플래그를 추가하여 자세한 로깅 정보를 얻으십시오. [문제점 해결 페이지](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc)에서 흔히 발생하는 오류를 확인해 볼 수도 있습니다.
{: tip}

다음 명령은 VPC에 대해 사용할 수 있는 지역을 JSON 형식으로 리턴합니다. 하나 이상의 오브젝트가 리턴되어야 합니다. 

각 API 명령에 대해 필요한 `version` 조회 매개변수를 확인하십시오.
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 5단계: GET Zones API 실행

다음 명령은 지역 `us-south`에서 VPC에 대해 사용할 수 있는 모든 구역을 JSON 형식으로 리턴합니다. 셋 이상의 오브젝트가 리턴되어야 합니다. 

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 6단계: GET Profiles API 실행

다음 명령은 인스턴스에 대해 사용할 수 있는 프로파일을 JSON 형식으로 리턴합니다. 하나 이상의 오브젝트가 리턴되어야 합니다. 

읽을 수 있는 JSON 문자열을 얻으려면 curl 명령 뒤에 ` | json_pp `를 추가하십시오.
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

페이지네이션으로 인해 API 출력이 제한되는 경우에는 한계를 `total_count`보다 더 높게 설정하십시오. 예를 들면 다음과 같습니다. 

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## 7단계: GET Images API 실행

다음 명령은 인스턴스에 대해 사용할 수 있는 이미지를 JSON 형식으로 리턴합니다. 하나 이상의 오브젝트가 리턴되어야 합니다. 

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## 8단계: GET VPCs API 실행

다음 명령은 사용자의 계정에서 작성된 VPC를 JSON 형식으로 리턴합니다. 

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## 9단계: Virtual Private Cloud 작성

`my-vpc`라는 IBM Cloud VPC를 작성하십시오. 

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

나머지 호출을 위해서는 새로 작성된 IBM Cloud VPC의 ID를 알아야 합니다. 해당 ID를 다음과 같이 변수에 붙여넣으십시오. 

예: `vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## 10단계: 서브넷 작성

IBM Cloud VPC에 서브넷을 작성하십시오. 예를 들어, `us-south-2` 구역을 삽입하는 경우는 다음과 같습니다. 

```bash
curl -X POST $rias_endpoint/v1/subnets?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-subnet",
        "ipv4_cidr_block": "10.0.1.0/24",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Virtual Private Cloud의 경우와 마찬가지로, 서브넷의 ID를 변수에 저장하십시오. 

```bash
subnet="<YOUR_SUBNET_ID>"
```
{: pre}

## 11단계: 서브넷의 상태 확인

서브넷에 리소스를 프로비저닝하려면 서브넷이 `available` 상태여야 합니다. 진행하기 전에 서브넷 리소스를 조회하여 상태가 `available`인지 확인하십시오. 상태가 `failed`인 경우에는 세부사항을 [지원](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)에 전달하여 문의하십시오. 다른 서브넷을 프로비저닝하여 진행할 수도 있습니다. 

```bash
curl $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## 12단계: 공용 게이트웨이 작성

서브넷의 가상 서버 인스턴스가 공용 인터넷에 액세스할 수 있도록 하려면 서브넷에 공용 게이트웨이(PGW)를 추가하십시오.   

```bash
curl -X POST $rias_endpoint/v1/public_gateways?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-gateway",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Virtual Private Cloud 및 서브넷의 경우와 마찬가지로, 공용 게이트웨이의 ID를 변수에 저장하십시오. 

```bash
gateway="<YOUR_GATEWAY_ID>"
```
{: pre}

## 13단계: 공용 게이트웨이를 서브넷에 연결

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## 14단계: SSH 키 작성

공개 SSH 키로 키를 작성하십시오. 이 키는 가상 서버 인스턴스를 작성하는 데 사용되며 가상 서버 인스턴스에 로그인하는 데 필요합니다. 

```bash
curl -X POST $rias_endpoint/v1/keys?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-key",
        "public_key": "ssh-rsa AAA....n",
        "type": "rsa"
      }'
```
{: pre}

키의 ID를 변수에 저장하십시오. 

```bash
key="<YOUR_KEY_ID>"
```
{: pre}

## 15단계: 가상 서버 인스턴스의 프로파일 및 이미지 선택

API를 실행하여 가상 서버 인스턴스에 대해 사용할 수 있는 모든 프로파일 및 이미지를 나열하고 조합을 선택하십시오. 

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

프로파일에 대한 추가 세부사항을 얻으려는 경우에는 IBM Cloud CLI 명령 `ibmcloud catalog entry <profile-name> --json`을 사용하여 글로벌 카탈로그를 조회할 수 있습니다. 예를 들면 다음과 같습니다. 

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

다음 명령은 사용 가능한 이미지를 나열합니다. 

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization:$iam_token"
```
{: pre}

나중에 가상 서버 인스턴스를 프로비저닝하는 데 사용되는 변수에 프로파일의 이름 및 이미지의 ID를 저장하십시오. 

```bash
profile_name="<CHOSEN_PROFILE_NAME>"
image_id="<CHOSEN_IMAGE_ID>"
```
{: pre}

## 16단계: 가상 서버 인스턴스 프로비저닝

새로 작성된 서브넷에서 가상 서버 인스턴스를 프로비저닝하십시오. 인스턴스가 프로비저닝된 후 로그인할 수 있도록 공개 SSH 키를 전달하십시오. 

```bash
curl -X POST $rias_endpoint/v1/instances?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "server-1",
        "type": "virtual",
        "zone": {
          "name": "us-south-2"
        },
        "vpc": {
          "id": "'$vpc'"
        },
        "primary_network_interface": {
          "port_speed": 1000,
          "subnet": {
            "id": "'$subnet'"
          }
        },
        "keys":[{"id": "'$key'"}],
        "flavor": {
          "name": "'$profile_name'"
         },
        "image": {
          "id": "'$image_id'"
         },
        "userdata": ""
      }'
```
{: pre}

다른 리소스의 경우와 마찬가지로, 가상 서버 인스턴스의 ID를 변수에 저장하십시오. 

```bash
server="<YOUR_INSTANCE_ID>"
```
{: pre}

## 17단계: 가상 서버 인스턴스의 상태 확인

가상 서버 인스턴스 프로비저닝에는 몇 초에서 몇 분 정도 소요될 수 있습니다. 진행하기 전에 서버의 상태를 조회하여 `running`인지 확인하십시오. 

```bash
curl $rias_endpoint/v1/instances/$server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

위 API 호출에서 리턴된 가상 서버 인스턴스의 기본 네트워크 인터페이스 ID 또한 저장하십시오.   

```bash
network_interface="<YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

특정 인스턴스를 조회하기 전까지는 기본 네트워크 인터페이스를 가져올 수 없습니다.
{: note}

## 18단계: 유동 IP 작성

가상 서버 인스턴스의 기본 네트워크 인터페이스를 새 유동 IP 주소의 대상으로 사용하여 인스턴스의 유동 IP를 작성하십시오. 

```bash
curl -X POST $rias_endpoint/v1/floating_ips?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-server-floatingip",
        "target": {
            "id":"'$network_interface'"
        }
      }
'
```
{: pre}


유동 IP의 ID를 저장하십시오. 

```bash
floating_ip="<YOUR_FLOATING_IP_ID>"
```
{: pre}

## 19단계: 가상 서버 인스턴스에 SSH로 연결

서버에 SSH로 연결하려면 작성한 유동 IP의 `address`를 사용하십시오. 유동 IP의 `address`를 가져오려면 다음 명령을 실행하십시오. 

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

유동 IP의 `address`를 사용하여 SSH로 가상 서버 인스턴스에 연결하십시오. 

```bash
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

Virtual Server에 대한 SSH 액세스는 보안 그룹에 의해 차단될 수 있습니다. SSH 액세스가 필요한 경우에는 [적절한 보안 그룹](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups)을 사용해야 합니다.
{: note}

인스턴스에 연결하는 방법에 대한 자세한 정보는 [Linux를 사용하는 인스턴스에 연결](/docs/vsi-is/vsi_is_connecting_linux_gc.html)을 참조하십시오. 


## 20단계(선택사항): 리소스 삭제

원하는 경우에는 리소스를 삭제하십시오. 다른 리소스를 포함하는 리소스는 삭제할 수 없습니다. 예를 들어, 서브넷을 포함하는 Virtual Private Cloud는 삭제할 수 없으며, 가상 서버 인스턴스를 포함하는 서브넷은 삭제할 수 없습니다. 삭제 시, API는 빠르게 리턴될 수 있지만 리소스 삭제는 계속 진행 중일 수 있습니다. 다른 리소스를 삭제하기 전에 해당 리소스를 조회하여 삭제되었는지 확인하는 것이 좋습니다. 

### 유동 IP를 삭제하십시오. 

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 가상 서버 인스턴스를 삭제하십시오. 

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 키를 삭제하십시오. 

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### 공용 게이트웨이를 삭제하십시오. 

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### 서브넷을 삭제하십시오. 

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### VPC를 삭제하십시오. 

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

VSI에서 vNIC는 삭제할 수 없으므로 vNIC 삭제 단계는 수행할 필요가 없습니다.
{: note}

## 축하합니다!

REST API를 사용하여 Virtual Private Cloud 인스턴스를 프로비저닝했습니다. 더 많은 API 명령을 사용해 보려면 전체 참조를 살펴보십시오. 

* [VPC에 대한 API 참조](https://{DomainName}/apidocs/rias)
