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

# 規劃 {{site.data.keyword.vsi_is_short}} 許可權
{: #planning-virtual-servers-for-vpc-permissions}

當您規劃佈建 {{site.data.keyword.vsi_is_full}} 時，必須根據使用者角色來瞭解可用的虛擬伺服器存取權。
{:shortdesc}

使用 VSI 時，會根據佈建實例的 {{site.data.keyword.vpc_short}} 來指派使用者的角色。如果使用者具有 {{site.data.keyword.vpc_short}} 的編輯者或管理者存取權，則會繼承在該 {{site.data.keyword.vpc_short}} 內建立、刪除、修改虛擬伺服器實例的能力。

請檢閱下表，進一步瞭解使用者角色以及每個角色所包含的特定存取層次。

* 作為帳戶的管理者時，您可以定義角色，並對 {{site.data.keyword.vsi_is_short}} 採取任何可用的動作。
* 作為帳戶的編輯者時，您可以修改狀態，以及建立/刪除子資源。
* 作為帳戶的檢視者時，您可以採取不會變更資源狀態的動作。

虛擬伺服器資源*繼承* 來自其母項 VPC 的所有使用者許可權。無法在實例層次設定許可權。
{:note}

<table>
<CAPTION>表 1. 使用者許可權</CAPTION>
<THEAD>
<TR>
<th>VPC 許可權</th>
<th>說明</th>
<th>動作</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>管理者</td>
<td>所有動作，包括可以管理<br>
存取控制。</td>
<td>
存取控制：
<ul>
<li>新增及移除使用者</li>
<li>指派每位使用者的角色</li>
</ul>
<p>
虛擬伺服器：
<ul>
<li>建立虛擬伺服器</li>
<li>停止虛擬伺服器</li>
<li>刪除虛擬伺服器</li>
<li>重新啟動虛擬伺服器</li>
<li>複製虛擬伺服器</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>檢視及列出虛擬伺服器</li>
<li>重新命名虛擬伺服器</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>建立及編輯 SSH 金鑰</li>
<li>刪除 SSH 金鑰</li>
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
<td>編輯者</td>
<td>可以修改狀態的動作，以及<br>
建立及刪除子資源。</td>
<td>
虛擬伺服器：
<ul>
<li>建立虛擬伺服器</li>
<li>停止虛擬伺服器</li>
<li>刪除虛擬伺服器</li>
<li>重新啟動虛擬伺服器</li>
<li>複製虛擬伺服器</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>檢視及列出虛擬伺服器</li>
<li>重新命名虛擬伺服器</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>建立 SSH 金鑰</li>
<li>刪除 SSH 金鑰</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>檢視監視及日誌資料</li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td>檢視者</td>
<td>不會變更狀態的動作</td>
<td>
虛擬伺服器：
<ul>
<li>檢視及列出虛擬伺服器</li>
<!-- <li>View and list image snapshots</li> -->
<li>檢視監視及日誌資料</li>
</ul>
</td>
</tr>
</TBODY>
</table>

## 後續步驟
如需如何變更使用者許可權的相關資訊，請參閱[管理 VPC 資源的使用者許可權](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources)。
