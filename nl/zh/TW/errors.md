---

copyright:

  years: 2018, 2019

lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}

# IBM Cloud Virtual Private Cloud API 錯誤訊息
{: #rias-error-messages}

當您收到來自 {{site.data.keyword.cloud}} Virtual Private Cloud API 的錯誤訊息時，可以使用訊息 ID 來尋找如何解決問題的相關資訊。
{:shortdesc}

## acl_in_use
**訊息**：無法刪除網路 ACL，因為它連接至資源。

無法刪除網路 ACL，因為它連接至資源。請嘗試檢查子網路。

## address_prefix_conflict
**訊息**：具有此 CIDR 的位址字首正在使用中。

所要求位址字首的 CIDR 與現有位址字首衝突。

## address_prefix_in_use
**訊息**：無法刪除使用中的位址字首。

一個以上的子網路正在使用位址字首。您必須先分離所有子網路，才能刪除字首。

## backend_service_unavailable
**訊息**：後端服務無法使用。

後端雲端服務無法回應。收到此錯誤的一個原因可能是 IAM 記號遺漏或過期。請在幾分鐘之後重試。如果此問題持續發生，請與支援中心聯絡。

## bad_field
**訊息**：應該提供正確的實例 UUID

應該提供新的磁區名稱

請在要求中提供有效的 UUID 或磁區，然後重試。 

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## bad_request                                   
**訊息**：給定的資訊無效、格式錯誤，或遺漏必要欄位。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## classic_access_vpc_conflict_duplicate_res
**訊息**：只能建立一個「標準存取 VPC」。

不能為一個帳戶建立多個「標準存取 VPC」

## default_address_prefix_not_found
**訊息**：找不到預設位址字首。

找不到預設位址字首時，您可能會看到此錯誤訊息。

## duplicate_error
**訊息**：提供的輸入已存在。

您所指定的資源已存在。若要解決此問題，請針對您要建立的資源使用不同的名稱。例如，建立新的 VPC 時，如果您先使用 ID 來呼叫 `get VPC`（如下：`GET "/v1/vpcs/{id}” -H  "accept: application/json"`），則可以檢閱已建立的 VPC 名稱清單，並選擇未衝突的名稱。 

## floating_ip_in_use
**訊息**：浮動 IP 正在使用中。

此浮動 IP 已與網路介面或公用閘道相關聯。

## floating_ip_not_empty
**訊息**：無法刪除與浮動 IP 相關聯的伺服器。

刪除伺服器之前，請務必取消與浮動 IP 的關聯。 

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## gateway_too_many
**訊息**：VPC 中每個區域都只能有一個公用閘道。

VPC 中允許每個區域都只有一個公用閘道，但可以將一個公用閘道連接至區域中的多個子網路。若要尋找區域的公用閘道，請執行 GET public_gateways API，並查看 "vpc" 及 "zone" 值。如果使用 CLI，您可以執行 `ibmcloud is public-gateways` 指令，並查看 "VPC" 及 "Zone" 值。

使用公用閘道 ID 將其連接至子網路，請參閱 [API 範例](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis#step-13-attach-the-public-gateway-to-the-subnet-)中的範例。如果使用 CLI，您可以使用 subnet update 指令將它連接至公用閘道，例如，`ibmcloud is subnet-update SUBNET_ID --public-gateway-id PUBLIC_GATEWAY_ID`。


## http_request_size_exceeded                    
**訊息**：HTTP 要求太大。

您在要求中傳送的有效負載包含太多字元時，會發生此問題。請使用較小的有效負載重試。例如，嘗試在一個要求中建立最少資源，然後在數個後續要求中漸進地附加其狀態，而不是嘗試在單一要求中執行所有作業。 

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## iam_failure
**訊息**：無

IAM 服務中驗證鑑別或授權發生失敗時，可能會顯示此訊息。IAM 服務的這項中斷可能是暫時的。請在幾分鐘之後重試要求。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## ike_policies_quota_exceeded
**訊息**：超出帳戶的 IKE 原則配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視現行 IKE 原則，請使用 `GET /ike_policies` API。

## ike_policy_duplicate_name
**訊息**：IKE 原則 `<ike_policy_id>` 已使用名稱 `<ike_policy_name>`。

請提供不同的 IKE 原則名稱。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## ike_policy_in_use
**訊息**：一個以上的連線正在使用 IKE 原則 `<ike_policy_id>`。

如果一個以上的連線正在使用 IKE 原則，則無法將其刪除。

## ike_policy_invalid_name
**訊息**：名稱 `<ike_policy_name>` 不是有效的 IKE 原則名稱。

有效的 IKE 原則名稱以字母開頭，後面接著字母、數字、底線或連字號。

## ike_policy_not_found
**訊息**：找不到 IKE 原則 `<ike_policy_id>`。

您參照的 IKE 原則不存在。請檢閱您的要求，確定您已指定適當的 IKE 原則 ID。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## insufficient_space_for_subnet
**訊息**：位址字首中子網路的空間不足

如果您嘗試建立子網路，而且因無法配置所要求的位址數目而無法建立子網路，則可能會收到此錯誤。

## internal_error
**訊息**：發生內部錯誤。

請重試。如果此錯誤持續發生，請與支援中心聯絡。

## internal_server_error
**訊息**：無

服務發生非預期的錯誤時，發生此錯誤。此問題可能是暫時的。請在幾分鐘之後重試要求。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## internal_solution
**訊息**：請與管理者聯絡。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## invalid_id_format
**訊息**：不當的 ID 格式。請確定格式正確無誤。

請確定您提供的 ID 未包含任何形態異常的資料。

如果在進行分頁要求時使用形態異常的起始查詢，您可能會收到此錯誤訊息。例如，`GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` 包含兩個 `?`。請修正查詢，然後再試一次。

## invalid_state
**訊息**：無

RIAS 指令 `ibmcloud is in-reboot Instance_uuid` 可以傳回訊息碼 "invalid_state"

在某種狀況下，當 VSI 在已重新開機的情況下嘗試重新開機作業時，即會擲出此訊息。在多次重新開機未同時發生的狀況下，也會收到此訊息。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## invalid_version
**訊息**：`version` 參數無效，其格式必須為 `YYYY-MM-DD`。

版本必須符合格式 _YYYY-MM-DD_。對於 1 月 1 日這類單一位數的月份或日期，版本應該類似於 `2019-01-01`。URL 中必須有版本參數。版本參數中給定的日期必須晚於 2019-01-01 且早於現行日期。例如，若要取得 VPC 清單，請在要求 `GET "/v1/vpcs?version=2019-01-01"` 的尾端加上版本。

## invalid_version_range
**訊息**：`version` 值不能設定在未來日期，也不能早於 `2019-01-01`。

版本必須符合格式 _YYYY-MM-DD_。對於 1 月 1 日這類單一位數的月份或日期，版本應該類似於 `2019-01-01`。URL 中必須有版本參數。版本參數中給定的日期必須晚於 2019-01-01 且早於現行日期。例如，若要取得 VPC 清單，請在要求 `GET "/v1/vpcs?version=2019-01-01"` 的尾端加上版本。

## invalid_zone
**訊息**：請檢查您要求的資源是否位於相同區域中。

如果所要求的資源不在有效的區域中，您可能會看到此訊息。

## ipsec_policies_quota_exceeded
**訊息**：超出帳戶的 IPsec 原則配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視現行 IPsec 原則，請使用 `GET /ipsec_policies` API。

## ipsec_policy_duplicate_name
**訊息**：IPsec 原則 `<ipsec_policy_id>` 已使用名稱 `<ipsec_policy_name>`。

請提供不同的 IPsec 原則名稱。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## ipsec_policy_in_use
**訊息**：一個以上的連線正在使用 IPsec 原則 `<ipsec_policy_id>`。

如果一個以上的連線正在使用 IPsec 原則，則無法將其刪除。

## ipsec_policy_invalid_name
**訊息**：名稱 `<ipsec_policy_name>` 不是有效的 IPsec 原則名稱。

有效的 IPsec 原則名稱以字母開頭，後面接著字母、數字、底線或連字號。

## ipsec_policy_not_found
**訊息**：找不到 IPsec 原則 `<ipsec_policy_id>`。

您參照的 IPsec 原則不存在。請檢閱您的要求，並確定您已指定適當的 IPsec 原則 ID。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## key_exists
**訊息**：相同的金鑰內容已存在。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## listener_certificate_not_found
**訊息**：找不到具有 CRN `<listener_certificate_crn>` 的憑證實例，或沒有可存取憑證實例的許可權。

請提供現有憑證實例 CRN，或要求帳戶管理者授與您對所提供憑證實例的存取權。

## listener_duplicate_port
**訊息**：另一個接聽器實例已使用埠 `<listener_port>`。請選擇不同的埠。

請選擇不同的埠。

## listener_invalid_certificate
**訊息**：HTTPS 接聽器的憑證實例 CRN 無效。

請提供有效的憑證實例 CRN。

## listener_invalid_connection_limit
**訊息**：接聽器連線限制 `<listener_connection_limit>` 無效。

請提供有效的連線限制。連線限制必須是介於 1 與 15000 之間的整數。

## listener_invalid_port
**訊息**：接聽器埠 `<listener_port>` 無效。

請選擇不同的埠。

## listener_invalid_protocol
**訊息**：接聽器通訊協定 `<listener_protocol>` 無效。

請提供有效的接聽器通訊協定。接聽器通訊協定的可接受值為 `http`、`https` 及 `tcp`。

## listener_missing_certificate_crn
**訊息**：遺漏 `https` 接聽器的憑證實例 CRN。

憑證實例的 CRN 是必要欄位。

## listener_missing_port
**訊息**：遺漏接聽器埠。

接聽器埠是必要欄位。

## listener_missing_protocol
**訊息**：遺漏接聽器通訊協定。

接聽器通訊協定是必要欄位。請在您的要求中提供接聽器通訊協定。可接受的值是 `http`、`https` 及 `tcp`。

## listener_not_found
**訊息**：找不到 ID 為 `<listener_id>` 的接聽器。

請提供現有的接聽器 ID。

## listener_over_quota
**訊息**：無法建立接聽器。負載平衡器資源的接聽器配額已達到上限。

[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}中提供每個資源的配額。

## listener_pool_protocols_conflict
**訊息**：接聽器通訊協定 (`<listener_protocol>`) 與儲存區通訊協定 (`<pool_protocol>`) 衝突。

具有 `https` 或 `http` 通訊協定的接聽器只能與具有 `http` 通訊協定的儲存區相關聯。同樣地，`tcp` 接聽器只能與 `tcp` 儲存區相關聯。

## listener_reserved_port_conflict
**訊息**：接聽器埠 `<listener_port>` 是其中一個保留埠。埠範圍 56500 到 56520 保留供管理用途。請選擇不同的埠。

請選擇不同的埠。

## load_balancer_duplicate_name
**訊息**：另一個負載平衡器實例已使用名稱 `<load_balancer_name>`。請選擇不同的名稱。

請為負載平衡器實例提供不同的名稱。

## load_balancer_invalid_description
**訊息**：負載平衡器說明 `<load_balancer_description>` 無效。

負載平衡器說明不得超出 255 個字元。

## load_balancer_invalid_is_public
**訊息**：is_public `<load_balancer_is_public>` 的值無效。

負載平衡器 is_public 應該為 true 或 false。

## load_balancer_invalid_is_public_value
**訊息**：僅支援公用負載平衡器。

尚未支援專用負載平衡器。

## load_balancer_invalid_name
**訊息**：名稱 `<load_balancer_name>` 無效。

名稱不應該是空的。名稱長度不應該超出 40 個字元。有效的負載平衡器名稱以字母開頭，後面接著字母、數字或底線。

## load_balancer_missing_is_public
**訊息**：遺漏 'is_public' 欄位。

'is_public' 是必要欄位。請提供負載平衡器 is_public 欄位。

## load_balancer_missing_name
**訊息**：遺漏負載平衡器名稱。

請提供負載平衡器名稱。負載平衡器名稱是必要欄位。

## load_balancer_missing_subnets
**訊息**：遺漏負載平衡器子網路。

'subnets' 是必要欄位。請在您的要求中提供負載平衡器建立所在的子網路。

## load_balancer_not_found
**訊息**：找不到 ID 為 `<load_balancer_id>` 的負載平衡器。

請提供現有的負載平衡器 ID。

## load_balancer_over_quota
**訊息**：無法建立負載平衡器。您帳戶下的負載平衡器實例配額已達到上限。

刪除現有的負載平衡器，或與支援中心聯絡，以增加您帳戶的負載平衡器配額。

[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}中提供每個資源的配額。

## load_balancer_unchanged_update
**訊息**：沒有任何項目可以更新 ID 為 `<load_balancer_id>` 的負載平衡器。

沒有任何項目可以更新負載平衡器實例。

## member_invalid_port
**訊息**：指定的成員埠 `<member_port>` 無效。

請提供有效的埠號。有效的埠號是在 1 到 65535 的範圍內。

## member_invalid_weight
**訊息**：指定的成員加權 `<member_weight>` 無效。

請提供有效的成員重量。它必須是介於 0 與 100 之間的整數。

## member_missing_address
**訊息**：遺漏成員位址。

成員位址是必要欄位。請在您的要求中提供成員位址。

## member_missing_protocol_port
**訊息**：遺漏成員埠。

成員埠是必要欄位。請在您的要求中提供成員埠。

## member_over_quota
**訊息**：無法建立成員。儲存區下的成員實例配額已達到上限。

[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}中提供每個資源的配額。

## missing_ims_account_id
**訊息**：無

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## missing_version
**訊息**：`version` 是必要參數，且其格式必須為 `YYYY-MM-DD`。

版本必須符合格式 _YYYY-MM-DD_。對於 1 月 1 日這類單一位數的月份或日期，版本應該類似於 `2019-01-01`。URL 中必須有版本參數。版本參數中給定的日期必須晚於 2019-01-01 且早於現行日期。例如，若要取得 VPC 清單，請在要求 `GET "/v1/vpcs?version=2019-01-01"`.cs?version=2019-01-01"` 的尾端加上版本。

## network_conflict
**訊息**：CIDR 與 VPC 中的現有「位址字首」衝突

如果您提供與相同 IP 空間中的現有網路 CIDR 有衝突的網路 CIDR，則可能會看到此訊息。

## not_authorized                               
**訊息**：要求未獲授權。

您看到此錯誤的常見原因是 IAM 記號遺漏或過期。如需如何產生記號的指示，請參閱[使用 REST API 建立 VPC](/docs/infrastructure/vpc/example-code.html#creating-a-vpc-using-the-rest-apis)。如果記號未過期，您可能需要檢查您的許可權，並與管理者聯絡。 

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## not_found
**訊息**：請檢查您要求的資源是否存在。

您參照的資源不存在，或您沒有存取權。請檢閱您的要求，確定您已指定適當的 ID 及參照。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## not_implemented
**訊息**：無

該方法未實作。

## not_in_address_prefix
**訊息**：所提供的 CIDR 不適合所提供區域中的任何位址字首。

如果使用者嘗試以不屬於給定區域的任何位址字首的 CIDR 來建立子網路，則會發生此錯誤。

執行 GET /vpcs/{vpc_id}/address_prefixes，以取得 VPC 的位址字首清單。請查看回應的 `cidr` 及 `zone` 值，確定子網路的 `cidr` 是您嘗試建立之區域的位址字首的 `cidr` 子集。

## over_quota                                    
**訊息**：要求會超出資源類型的配額。

[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}中提供每個資源的配額。

## password_not_ready
**訊息**：無

您的實例必須先執行，您才能擷取密碼。請在幾分鐘之後重試。如果此問題持續發生，請與支援中心聯絡。

## pool_delete_conflict
**訊息**：無法刪除儲存區，因為它仍與一個以上的接聽器相關聯。

請確定取消儲存區與任何接聽器的關聯，然後再試一次。

## pool_duplicate_name
**訊息**：另一個儲存區已使用儲存區名稱 `<pool_name>`。請選擇不同的名稱。

請選擇不同的儲存區名稱。

## pool_missing_algorithm
**訊息**：遺漏負載平衡演算法。

負載平衡演算法是必要欄位。請在您的要求中提供負載平衡演算法。可接受的值是 `round_robin`、`weighted_round_robin` 及 `least_connections`。

## pool_missing_health_monitor
**訊息**：遺漏儲存區性能監視器。

儲存區性能監視器是必要欄位。

## pool_missing_name
**訊息**：遺漏儲存區名稱。

儲存區名稱是必要欄位。

## pool_missing_protocol
**訊息**：遺漏儲存區通訊協定。

儲存區通訊協定是必要欄位。請在您的要求中提供儲存區通訊協定。可接受的值是 `http` 及 `tcp`。

## pool_not_found
**訊息**：找不到 ID 為 `<pool_id>` 的儲存區。

請提供現有的儲存區 ID。

## pool_over_quota
**訊息**：無法建立儲存區。負載平衡器資源的儲存區配額已達到上限。

[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}中提供每個資源的配額。

## public_gateway_in_use
**訊息**：無法刪除使用中的公用閘道。

目前已將公用閘道連接至一個以上子網路。您必須先將公用閘道與所有子網路分離，才能予以刪除。

## rate_limit_exceeded
**訊息**：短時間內的要求太多。

如果在指定的時間間隔內接收到太多要求，則會傳回此錯誤訊息。請等待一段時間，然後再試一次。 

## security_group_active_transactions
**訊息**：除非實例顯示為「作用中」狀態，否則無法連接或分離介面。

實例必須先處於作用中狀態，才能將其網路介面連接至安全群組。使用 `GET /v1/instances/{id}?version=2019-01-01` 或 `ibmcloud is instance` 來檢查實例的狀態。狀態處於 `running` 狀態之後，請重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## security_group_already_attached
**訊息**：介面已連接至安全群組。


介面已連接至安全群組。使用 `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` 或 `ibmcloud is security-group-network-interfaces`，來檢視連接的介面。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。


## security_group_exists
**訊息**：安全群組已存在。


安全群組名稱必須是唯一的。具有該名稱的安全群組已存在。使用 `GET /v1/security_groups?version=2019-01-01` 或 `ibmcloud is security-groups`，來檢視現行安全群組。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias)或[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。


## security_group_interfaces_attached
**訊息**：連接介面時，無法刪除安全群組。


請先分離所有介面，再刪除安全群組。使用 `DELETE /v1/security_groups/{id}/network_interfaces/{id}?version=2019-01-01` 或 `ibmcloud is security-group-network-interface-remove`，來分離介面。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias)或[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。


## security_group_interfaces_per_sg_exceeded
**訊息**：超出每個安全群組的介面限制。

將另一個介面連接至安全群組，會超出每個安全群組的介面限制。[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas)){: new_window}中提供每個資源的配額。請評估您的策略，並考慮建立另一個具有類似規則的安全群組。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias)或[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。


## security_group_last_security_group_is_default
**訊息**：預設安全群組是唯一連接的安全群組時，則無法予以移除。

必須將網路介面至少連接至一個安全群組。
如果未指定安全群組，則會將它連接至 VPC 的預設安全群組。
將介面連接至不同的安全群組，然後重試以將它與預設安全群組分離。
如需預設安全群組的相關資訊，請參閱[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## security_group_limit_exceeded
**訊息**：超出安全群組限制。

您已嘗試建立新的安全群組，但目前位於您的帳戶配額。[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}中提供每個資源的配額。請評估將實例指派給安全群組的策略。藉由將多個實例指派給相同的安全群組，通常可以減少整體安全群組數目。此策略將減少安全群組數目，並降到低於您的帳戶配額。在極少數情況下（通常是針對大型組織），需要擴充配額。在此情況下，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)，以查詢這是否可能。

## security_group_network_interface_not_active
**訊息**：無法連接介面，因為它非作用中。

連接至安全群組之前，網路介面必須處於作用中狀態。使用 `GET /v1/instances/{id}/network_interfaces/{id}?version=2019-01-01` 或 `ibmcloud is instance-network-interface`，來檢視介面的狀態。狀態處於 'available' 狀態之後，請重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## security_group_not_attached
**訊息**：未連接介面。

介面未連接至安全群組。使用 `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` 或 `ibmcloud is security-group-network-interfaces`，來檢視連接的介面。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias)或[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group-using-the-cli){: new_window}。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。


## security_group_not_in_vpc
**訊息**：介面及安全群組位於不同的 VPC 中。

若要將網路介面連接至安全群組，實例必須位於與安全群組相同的 VPC 中。使用 `GET /v1/security_groups/{id}?version=2019-01-01` 或 `ibmcloud is security-group`，來檢視安全群組詳細資料及 VPC。使用 `GET /v1/instances/{id}?version=2019-01-01` 或 `ibmcloud is instance`，來檢視實例詳細資料及 VPC。

## security_group_order_bindings
**訊息**：安全群組擱置實例訂單時，即無法予以刪除。

如果是使用網路介面上指定的安全群組建立實例，則實例及網路介面必須先處於作用中狀態，才能刪除安全群組。使用 `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` 或 `ibmcloud is security-group-network-interfaces`，來檢視連接的網路介面及其狀態。介面的狀態處於 'available' 狀態之後，請重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## security_group_port_max_less_than_port_min
**訊息**：TCP/UDP 最大埠不能小於最小埠。

埠值上限不能小於埠值下限。請指定大於埠值下限的埠值上限。

## security_group_port_range_both_or_neither
**訊息**：必須對 'tcp' 和 'udp' 取消設定埠範圍，或同時設定最小及最大埠。

具有 'tcp' 或 'udp' 通訊協定的規則可能有取消設定的埠範圍（以將規則套用至所有資料流量），或者它們可能指定埠範圍。若要將資料流量限制為單一埠，請同時將最小及最大埠設為埠值。例如，下列指令將建立規則以容許埠 22 上的 SSH：`ibmcloud is security-group-rule-add <id> inbound tcp --port-min 22 --port-max 22`。

如需安全群組規則配置的進一步資訊，請參閱 [API 文件](https://{DomainName}/apidocs/rias)。


## security_group_port_range_invalid_protocol
**訊息**：已指定通訊協定為 'icmp' 的埠範圍。埠範圍僅適用於 'tcp' 或 'udp' 通訊協定。

具有 'icmp' 通訊協定的規則包含類型及代碼。具有 'tcp' 或 'udp' 通訊協定的規則包含埠範圍。如需安全群組規則配置的進一步資訊，請參閱 [API 文件](https://{DomainName}/apidocs/rias)。

## security_group_remote_group_not_in_vpc
**訊息**：遠端群組與此安全群組不在同一個 VPC 中。

安全群組規則可能參照遠端安全群組，以容許在兩個群組的連接介面之間進行傳輸。遠端安全群組必須在同一個 VPC 中。使用 `GET /v1/security_groups?2019-01-01` 或 `ibmcloud is security-groups`，來檢視現行安全群組及其 VPC。

如需修正此問題的進一步指示，請參閱[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}。


## security_group_remoting_rules
**訊息**：連接遠端規則時，無法刪除安全群組。

安全群組包含一個以上參照遠端安全群組的規則。使用 `GET /v1/security_groups/{id}/rules?version=2019-01-01` 或 `ibmcloud is security-group-rules`，來檢視規則。'remote' 欄位將指定任何遠端安全群組。請在刪除或編輯遠端規則之後重試。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias)或[使用安全群組文件](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}。


## security_group_remoting_rules_per_sg_exceeded
**訊息**：超出每個安全群組的遠端規則限制。


新增另一個參照遠端安全群組的規則，會超出每個安全群組的遠端規則限制。[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}中提供每個資源的配額。


## security_group_rules_per_sg_exceeded
**訊息**：超出每個安全群組的規則限制。

新增規則會超出每個安全群組的規則限制。[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}中提供每個資源的配額。請評估您的策略，並考慮建立另一個安全群組。


## security_group_sgs_per_interface_exceeded
**訊息**：超出每個介面的安全群組限制。

將此介面連接至另一個安全群組，會超出每個介面的安全群組限制。[VPC 的配額及限制](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}中提供每個資源的配額。請評估您的策略，並考慮將規則新增至現有安全群組。


## security_group_type_code_invalid_protocol
**訊息**：已給定 'icmp' 類型/代碼，但所要求的通訊協定不是 'icmp'。請將通訊協定設為 'icmp'，或指定埠範圍。

只有具有 'icmp' 通訊協定的規則才包含類型及代碼。具有 'tcp' 或 'udp' 通訊協定的規則包含埠範圍。如需安全群組規則配置的進一步資訊，請參閱 [API 文件](https://{DomainName}/apidocs/rias)。

## security_group_vpc_default
**訊息**：無法刪除 VPC 的預設安全群組。

無法刪除預設安全群組。如需預設安全群組的相關資訊，請參閱[更新預設安全群組](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group)的相關手冊。

## service_manager_service_failure
**訊息**：無

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_acl_conflict
**訊息**：無法刪除網路 ACL，它已連接至子網路。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_conflict
**訊息**：CIDR 與 VPC 中的現有「子網路」衝突。

執行 GET /subnets API，以擷取 VPC 中的所有子網路。檢查 `ipv4_cidr_block` 的值，確定其他子網路未使用您所提供的 CIDR。

如果使用 CLI，您可以執行 `ibmcloud is subnets`，並查看 "Subnet CIDR" 值以尋找衝突。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_not_empty
**訊息**：子網路不是空的，請與管理者聯絡。

已要求刪除子網路，但子網路中仍有資源。子網路中可能有實例、VPN、負載平衡器或公用閘道。您必須先刪除子網路中的資源，才能刪除子網路。 

在某些情況下，即使主控台顯示 0 個 VSI 及 0 個負載平衡器，還是會發生此錯誤，因為刪除是非同步的，而且可能需要幾分鐘的時間，才能變更內部狀態。請在幾分鐘之後重試子網路刪除。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_not_empty_pgway_exists
**訊息**：在子網路連接至公用閘道時，無法予以刪除。請分離公用閘道，然後重試。

已要求刪除子網路，但子網路仍連接公用閘道。您必須先刪除或分離公用閘道，才能刪除子網路。 

如果使用 CLI，您可以執行 `ibmcloud is public-gateways` 來列出公用閘道，以及執行 `ibmcloud is subnet-public-gateway-detach` 來分離公用閘道與子網路。 

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_not_empty_ipaddr_exists
**訊息**：在子網路包含 IP 位址時，無法予以刪除。請刪除與 IP 位址相關聯的任何伺服器實例，然後重試。

已要求刪除子網路，但子網路仍包含 IP 位址。您必須先刪除與 IP 位址相關聯的伺服器實例，才能刪除子網路。

如果使用 CLI，您可以執行 `ibmcloud is instances` 來列出伺服器實例，並查看 "Address" 值來判定其「IP 位址」，以及查看 "Status" 來判定其狀態。執行 `ibmcloud is instance-delete`，以刪除尚未有 "deleting" 狀態的伺服器實例。 

在某些情況下，即使主控台顯示 0 個 VSI，還是會發生此錯誤，因為刪除是非同步的，而且可能需要幾分鐘的時間，才能變更內部狀態。請在幾分鐘之後重試子網路刪除。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_not_empty_loadbalancer_exists
**訊息**：在子網路包含負載平衡器時，無法予以刪除。請刪除負載平衡器，然後重試。

已要求刪除子網路，但子網路仍包含負載平衡器。您必須先刪除負載平衡器，才能刪除子網路。

如果使用 CLI，您可以執行 `ibmcloud is load-balancers` 來列出負載平衡器，並查看 "Subnets" 值來判定其「子網路」，以及查看 "Status" 來判定其狀態。執行 `ibmcloud is load-balancer-delete`，以刪除尚未有 "deleting" 狀態的負載平衡器。 

在某些情況下，即使主控台顯示 0 個負載平衡器，還是會發生此錯誤，因為刪除是非同步的，而且可能需要幾分鐘的時間，才能變更內部狀態。請在幾分鐘之後重試子網路刪除。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_not_empty_vpn_gway_exists
**訊息**：在子網路包含 VPN 閘道時，無法予以刪除。請刪除 VPN 閘道，然後重試。

已要求刪除子網路，但子網路仍連接 VPN 閘道。您必須先刪除 VPN 閘道，才能刪除子網路。 

如果使用 CLI，您可以執行 `ibmcloud is vpn-gateways` 來列出負載平衡器，並查看 "Subnets" 值來判定其「子網路」，以及查看 "Status" 來判定其狀態。執行 `ibmcloud is vpn-gateway-delete`，以刪除尚未有 "deleting" 狀態的 VPN 閘道。 

在某些情況下，即使主控台顯示 0 個 VPN 閘道，還是會發生此錯誤，因為刪除是非同步的，而且可能需要幾分鐘的時間，才能變更內部狀態。請在幾分鐘之後重試子網路刪除。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## subnet_unknown_state
**訊息**：無

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## system_limit_exceeded
**訊息**：此作業會超出系統限制

收到此錯誤訊息的一個可能情境如下：您嘗試建立位址字首，但已達到位址字首數目上限。

## target_in_use
**訊息**：目標已連接浮動 IP。

## token_invalid
**訊息**：服務記號過期或無效。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## token_missing
**訊息**：服務記號是空的，或不存在於要求中。

請重建記號，然後再試一次。

## validation_enum
**訊息**：所提供的值不是有效的選項。

所提供的其中一個欄位具有的值必須來自可能值的列舉。

對於「網路 ACL」規則，您可以指定方向：

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum:
[ inbound, outbound ]
```

例如，下列值無效，因為 `northbound` 不是列舉 `[ inbound, outbound ]` 中的有效選項。

```json
{
    "direction":"northbound"
}
```

## validation_failure                            
**訊息**：提供的 JSON 不符合預期的結構。

若要修正此問題，請確定您的要求內容是有效的 JSON，而且您的要求符合 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## validation_invalid_cidr                       
**訊息**：值不是有效的 CIDR。

值必須是具有 0 個主機組件的有效內部 CIDR 區塊。

特定 IP 位址範圍已保留。如需保留 IP 範圍的相關資訊，請參閱[搭配使用 VPC 與地區及子網路](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}的概觀。

## validation_invalid_ipv4_cidr        
**訊息**：值不是有效的 IPv4 CIDR。

必須是具有 0 個主機組件的 IPv4 內部 CIDR 區塊。

特定 IP 位址範圍已保留。如需保留 IP 範圍的相關資訊，請參閱[搭配使用 VPC 與地區及子網路](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}的概觀。

## validation_invalid_ipv6_cidr
**訊息**：值不是有效的 IPv6 CIDR。

目前不支援 IPv6。請使用 IPv4 位址。

## validation_invalid_address
**訊息**：值不是有效的位址。

必須是有效的 IP 位址

[地區及子網路](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)文件中提供個別保留 IP 位址的清單。

## validation_invalid_ipv4_address
**訊息**：值不是有效的 IPv4 位址。

請提供有效的 IPv4 位址。

## validation_invalid_ipv6_address
**訊息**：值不是有效的 IPv6 位址。

請提供有效的 IPv6 位址。目前不支援 IPv6；請使用 IPv4 位址。

## validation_invalid_field_type
**訊息**：值類型不符合欄位類型。

若要修正此問題，請確定您的要求內容符合所呼叫端點的 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## validation_max_value
**訊息**：所提供的值太大。

請提供較小的值，以符合規格所給定的上限。如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## validation_min_value
**訊息**：所提供的值太小。

請提供較大的值，以符合規格所給定的下限。如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## validation_not_null
**訊息**：所提供的欄位必須是空值。

請確定值是空值。如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

以下是無效的範例：

```json
{
    "name": null
}
```

## validation_only_one
**訊息**：值必須符合其中一個子綱目。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## validation_discriminator_forbidden
**訊息**：鑑別器欄位禁止此結構。

例如，如果您指定：
```
{
protocol: icmp
port_min: 5
port_max: 100
}
```

通訊協定為 `icmp`，且 _port_min_ 是 `tcp` 欄位，因此您將收到錯誤。
1. validation_discriminator_required 適用於遺漏 `icmp` 規則
2. validation_discriminator_forbidden 適用於已指定 `icmp` 的 `tcp` 欄位

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## validation_internal_error
**訊息**：無

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## validation_invalid_name
**訊息**：值不是有效的名稱。


## validation_invalid_ref
**訊息**：值不是有效的 HREF。


## validation_non_empty_uuid
**訊息**：無

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## validation_required_field
**訊息**：遺漏必要欄位。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## validation_unique_failed
**訊息**：所提供的欄位必須是唯一的。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

您可能指定了已在使用中的名稱。請嘗試不同的值。

## vpc_acl_conflict                           
**訊息**：無法刪除預設網路 ACL，它已連接至 VPC。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias)或[使用網路 ACL 文件](/docs/infrastructure/vpc-network?topic=vpc-network-setting-up-network-acls-using-the-cli){: new_window}。

如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpc_not_empty
**訊息**：無法刪除 VPC，因為它不是空的。

必須先移除 VPC 中的所有資源，才能刪除 VPC。

如果您的 VPC 中仍有閘道，則即使已刪除所有子網路，還是會收到此錯誤，因為閘道可以存在於不含子網路的 VPC 中。可能需要使用 CLI 來檢查孤立資源。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpc_resource_separation
**訊息**：資源位於不同的 VPC 中

## vpn_connection_cidr_not_created
**訊息**：無法將 CIDR 區塊新增至 VPN 連線 `<vpn_connection_id>`。

請提供有效的 CIDR，以符合規格所給定的需求。 

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_connection_cidr_not_deleted
**訊息**：無法刪除 VPN 連線 `<vpn_connection_id>` 中的 CIDR 區塊。

請提供存在於連線上的有效 CIDR。連線必須至少有一個本端及對等節點 CIDR。

若要檢視連線的 CIDR 區塊，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` API，並檢查 `local_cidrs` 及 `peer_cidrs` 欄位。

## vpn_connection_cidr_not_found
**訊息**：在 VPN 連線 `<vpn_connection_id>` 中找不到 CIDR 區塊。

請提供位於連線上的有效 CIDR。

若要檢視連線的 CIDR 區塊，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` API，並檢查 `local_cidrs` 及 `peer_cidrs` 欄位。

## vpn_connection_cidr_not_valid
**訊息**：CIDR 區塊 `<cidr_block>` 不代表有效位址。

值必須是未設定主機位元的有效內部 CIDR 區塊。

若要檢視連線的 CIDR 區塊，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` API，並檢查 `local_cidrs` 及 `peer_cidrs` 欄位。

## vpn_connection_cidr_overlap
**訊息**：CIDR 區塊 `<cidr_block_1>` 與 `<cidr_block_2>` 重疊。相同 VPC 上的兩個對等節點 CIDR 區塊不能重疊，而且相同連線上的兩個本端 CIDR 區塊不能重疊。

請提供有效的 CIDR 值，以符合規格所給定的需求。

若要檢視連線的 CIDR 區塊，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` API，並檢查 `local_cidrs` 及 `peer_cidrs` 欄位。

## vpn_connection_duplicate_name
**訊息**：VPN 連線 `<vpn_connection_id>` 已使用名稱 `<vpn_connection_name>`。

請提供不同的連線名稱。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_connection_invalid_name
**訊息**：名稱 `<vpn_connection_name>` 不是有效的 VPN 連線名稱。

有效的連線名稱以字母開頭，後面接著字母、數字、底線或連字號。

## vpn_connection_invalid_psk_format
**訊息**：預先共用金鑰 (PSK) `<psk>` 的格式無效。

有效的 PSK 只應該包含 6 到 128 個字元，它們為字母、數字、`-`、`+`、`&`、`!`、`@`、`#`、`$`、`%`、`^`、`*`、`(`、`)`、`,`、`.`、`:`、`_`。

## vpn_connection_local_cidrs_required
**訊息**：建立 VPN 連線時，至少需要一個本端 CIDR 區塊。

請提供有效的本端 CIDR 值，以符合規格所給定的需求。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## vpn_connection_local_subnets_quota_exceeded
**訊息**：超出 VPN 閘道 `<vpn_gateway_id>` 的跨 VPN 連線的本端子網路配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視跨 VPN 連線的現行本端子網路，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections` API，並檢查每個連線的 `local_cidrs` 欄位。

## vpn_connection_local_subnets_quota_exceeded_for_connection
**訊息**：超出 VPN 連線的 '<quota_limit>' 本端子網路配額。

[配額](https://{DomainName}/docs/infrastructure/vp?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視 VPN 連線的現行本端子網路，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` API，並檢查 `local_cidrs` 欄位。

## vpn_connection_not_found
**訊息**：找不到 VPN 連線 `<vpn_connection_id>`。

請檢查連線 ID 是否正確。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_connection_peer_cidrs_required
**訊息**：建立 VPN 連線時，至少需要一個對等節點 CIDR 區塊。

請提供有效的對等節點 CIDR 值，以符合規格所給定的需求。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## vpn_connection_peer_subnets_quota_exceeded
**訊息**：超出 VPN 閘道 `<vpn_gateway_id>` 的跨 VPN 連線的對等節點子網路配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視跨 VPN 連線的現行對等節點子網路，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections` API，並檢查每個連線的 `peer_cidrs` 欄位。

## vpn_connection_peer_subnets_quota_exceeded_for_connection
**訊息**：超出 VPN 連線的 `<quota_limit>` 對等節點子網路配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視 VPN 連線的現行對等節點子網路，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` API，並檢查 `peer_cidrs` 欄位。

## vpn_connections_quota_exceeded
**訊息**：超出 VPN 閘道 `<vpn_gateway_id>` 的 VPN 連線配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視 VPN 閘道的現行 VPN 連線，請使用 `GET /vpn_gateways/<vpn_gateway_id>/connections` API。

## vpn_connection_static_route_not_created
**訊息**：無法新增 CIDR 區塊 `<peer_cidr>` 的靜態路徑。

請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_connection_static_route_not_deleted
**訊息**：無法移除 CIDR 區塊 `<peer_cidr>` 的靜態路徑。

請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_connection_update_cidrs_not_permitted
**訊息**：更新連線時，無法變更 CIDR 區塊。建立或刪除 CIDR 時，請使用正確的 API。

請提供有效的要求值，以符合規格所給定的需求。

如需修正此問題的進一步指示，請參閱 [API 文件](https://{DomainName}/apidocs/rias){: new_window}。

## vpn_gateway_duplicate_name
**訊息**：VPN 閘道 `<vpn_gateway_id>` 已使用名稱 `<vpn_gateway_name>`。

請提供不同的 VPN 閘道名稱。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateway_initialization_error
**訊息**：無法起始設定 VPN 閘道。

請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateway_invalid_name
**訊息**：名稱 `<vpn_gateway_name>` 不是有效的 VPN 閘道名稱。

有效的 VPN 閘道名稱以字母開頭，後面接著字母、數字、底線或連字號。

## vpn_gateway_invalid_state
**訊息**：所要求作業的 VPN 閘道 `<vpn_gateway_id>` 處於無效狀態。

「VPN 閘道」必須先處於 `available` 狀態，您才能對其進行操作。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateway_ip_create_error
**訊息**：無法建立 VPN 閘道的 IP 位址。

請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateway_not_found
**訊息**：找不到 VPN 閘道 `<vpn_gateway_id>`。

請檢查 VPN 閘道 ID 是否正確。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateway_subnet_not_found
**訊息**：找不到所給定 VPN 閘道的子網路 `<subnet_id>`。

您參照的子網路不存在。請檢閱您的要求，確定您已指定適當的子網路 ID。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateway_subnet_status_error
**訊息**：因子網路狀態，而無法建立 VPN 閘道。

請提供處於 `available` 狀態的子網路。請在幾分鐘之後重試。如果此問題持續發生，請[與支援中心聯絡](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support)。

## vpn_gateways_quota_exceeded
**訊息**：超出帳戶及（或）地區的 VPN 閘道配額。

[配額](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}頁面上提供每個資源的配額。

若要檢視現行 VPN 閘道，請使用 `GET /vpn_gateways` API。
