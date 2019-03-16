---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.vsi_is_short}} 권한 계획
{: #planning-virtual-servers-for-vpc-permissions}

{{site.data.keyword.vsi_is_full}}를 프로비저닝하려는 경우에는 사용자 역할에 따라 가능한 Virtual Server 액세스를 알아야 합니다.
{:shortdesc}

VSI에 대해 작업할 때, 사용자에게는 인스턴스가 프로비저닝된 {{site.data.keyword.vpc_short}}를 기반으로 역할이 지정됩니다. 사용자에게 {{site.data.keyword.vpc_short}}에 대한 편집자 또는 관리자 권한이 있는 경우 이들은 해당 {{site.data.keyword.vpc_short}} 내에서 가상 서버 인스턴스를 작성하고, 삭제하고 수정할 수 있는 권한을 상속합니다. 

다음 표를 검토하여 사용자 역할과 각 역할이 포함하는 특정 액세스 레벨에 대해 더 자세히 알아보십시오. 

* 계정의 관리자는 역할을 정의하고 {{site.data.keyword.vsi_is_short}}에 대해 사용 가능한 조치를 수행할 수 있습니다. 
* 계정의 편집자는 상태를 수정하고 하위 리소스를 작성/삭제할 수 있습니다. 
* 계정의 뷰어는 리소스의 상태를 변경하지 않는 조치를 수행할 수 있습니다. 

Virtual Server 리소스는 해당 상위 VPC로부터 모든 사용자 권한을 *상속*합니다. 인스턴스 레벨에서는 권한을 설정할 수 없습니다.
{:note}

<table>
<CAPTION>표 1. 사용자 권한</CAPTION>
<THEAD>
<TR>
<th>VPC 권한</th>
<th>설명</th>
<th>조치</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>관리자</td>
<td>액세스 제어 관리 권한을 포함한 <br>
모든 조치</td>
<td>
액세스 제어:
<ul>
<li>사용자 추가 및 제거</li>
<li>각 사용자의 역할 지정</li>
</ul>
<p>
Virtual Server:
<ul>
<li>Virtual Server 작성</li>
<li>Virtual Server 중지</li>
<li>Virtual Server 삭제</li>
<li>Virtual Server 다시 시작</li>
<li>Virtual Server 복제</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>Virtual Server 보기 및 나열</li>
<li>Virtual Server 이름 바꾸기</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>SSH 키 작성 및 편집</li>
<li>SSH 키 삭제</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<!-- <li>View monitoring and log data</li> -->
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>
</p>
</td>
</tr>
<tr>
<td>편집자</td>
<td>상태를 수정할 수 있는 조치, 그리고 <br>
하위 리소스를 작성하고 삭제할 수 있는 조치</td>
<td>
Virtual Server:
<ul>
<li>Virtual Server 작성</li>
<li>Virtual Server 중지</li>
<li>Virtual Server 삭제</li>
<li>Virtual Server 다시 시작</li>
<li>Virtual Server 복제</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>Virtual Server 보기 및 나열</li>
<li>Virtual Server 이름 바꾸기</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>SSH 키 작성</li>
<li>SSH 키 삭제</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>모니터링 및 로그 데이터 보기</li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td>뷰어</td>
<td>상태를 변경하지 않는 조치</td>
<td>
Virtual Server:
<ul>
<li>Virtual Server 보기 및 나열</li>
<!-- <li>View and list image snapshots</li> -->
<li>모니터링 및 로그 데이터 보기</li>
</ul>
</td>
</tr>
</TBODY>
</table>

## 다음 단계
사용자 권한을 변경하는 방법에 대한 자세한 정보는 [VPC 리소스에 대한 사용자 권한 관리](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources)를 참조하십시오. 
