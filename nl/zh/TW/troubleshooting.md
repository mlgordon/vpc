---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# IBM Cloud VPC 疑難排解
{: #troubleshooting-your-ibm-cloud-vpc}

本文件涵蓋您可能遇到的常見困難，並提供一些有用的提示。

## 在使用 CLI 時開啟 `TRACE` 模式

若要在使用 CLI 時開啟 `TRACE`（除錯）模式，請在 CLI 指令之前設定 `IBMCLOUD_TRACE=true`。

範例：

 ```
 IBMCLOUD_TRACE=true ibmcloud is pubgws
 ```

## 在使用 API 時使用 DEBUG 模式或 `verbose` 模式

例如，您可以將 `--verbose` 新增至 `curl` 指令，並將 `X-Request-Id:` 值傳送給我們，讓我們可以對問題進行疑難排解。如果您遇到連線問題，`--verbose` 旗標特別有用。

另一個選項是將 `-i` 旗標新增至 `curl` 指令，讓支援團隊可以查看要求回應中的標頭。當您需要與支援中心聯絡時，此旗標通常十分有用。



## API 呼叫需要 Bearer 記號

搭配使用 API 與 cURL 指令時，您可能需要在 Authorization 標頭中包括 "Bearer"（視 `$iam_token` 中的項目而定）。如果它已包括 "Bearer" 這個字，則不需要再次將它包括在標頭中。大部分範例都假設 "Bearer" 內含在標頭中。



## 使用 CLI 的不同端點

若要變更 {{site.data.keyword.cloud}} CLI 依預設用於 RIAS 的端點，請在使用 CLI 之前設定環境變數 `IBMCLOUD_IS_API_ENDPOINT`。例如，

```
export IBMCLOUD_IS_API_ENDPOINT=api.dev.domain.com
```
{: pre}


## 一般問題

以下是您可能遇到的一些困難。



### 未獲授權（401 或 403 錯誤）

您的帳戶可能未獲得 VPC 的授權。請確定您使用已加入的帳戶。



### 無法建立資源

如果您無法建立 VPC 或其他資源，請確定帳戶的擁有者已授與您正確的[許可權](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources)。

### 實例全部都處於「不明」狀態

請確定帳戶的擁有者已授與您正確的[許可權](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources)，以用來檢視及管理實例。

### 沒有來自 API 的回應

如果 API 不再傳回任何 JSON，則您的 IAM 記號可能已過期，並且需要重新整理。請重新登入 IBM Cloud，或執行 `iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $4; }')` 來重新整理記號。

### 錯誤：409 對實例呼叫動作時發生衝突

如果您實例的狀態與動作衝突，則無法呼叫特定實例動作。例如，如果您的實例狀態為「已停止」，而且您嘗試執行「重新啟動」動作，則系統會傳回 409 錯誤。

|狀態|動作|衝突|
| ----------- | ---------- | -------- |
|正在執行|啟動|是|
|已停止|啟動以外的任何動作|是|
|不在執行中|暫停|是|
|不在執行中|重新開機|是|
|未暫停|繼續|是|
|已暫停|繼續以外的任何動作|是|


### 實例未回應 `instance-reboot` 要求

如果您的實例未回應 `instance-reboot` 要求，則可以嘗試 `instance-reset` 要求。您可以將 `instance-reboot` 視為軟性要求，並將 `instance-reset` 視為硬性要求。`instance-reboot` 要求會將 OS 重新開機要求傳送至實例，但 `instance-reset` 要求會執行 VSI 實例的強迫重設。您可以將差異想成在電腦鍵盤按下 "ctrl-alt-delete" 鍵，以及按下重設或電源按鈕。請記住，`instance-reset` 要求完成所需的時間會比 `instance-reboot` 要求久。

### 無法刪除資源

特定作業（例如，建立及刪除 VSI，以及建立及刪除子網路）是透過 API 非同步完成。基於此事實，建議您輪詢所要刪除的資源，先檢查刪除作業，再繼續進行。 

基於這些非同步作業，從系統中刪除資源可能需要數分鐘的時間。為了協助刪除，最佳作法是依下列順序執行作業：

1. 刪除實例
2. 刪除公用閘道
3. 刪除子網路
4. 刪除 VPC
