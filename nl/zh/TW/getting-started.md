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

# 開始使用 IBM Cloud Virtual Private Cloud 基礎架構
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

IBM 將接受限量客戶參與 2019 年 4 月初開辦的 VPC「搶先體驗」計劃，並在接下來幾個月開放擴大使用。如果您的組織希望體驗 IBM Virtual Private Cloud，請填寫此[申請表](https://cloud.ibm.com/vpc){: new_window}，IBM 業務代表將聯絡您進行下一步。
{: important}

若要開始使用「{{site.data.keyword.cloud}} Virtual Private Cloud 基礎架構」，請執行下列動作：

1. 建立 Virtual Private Cloud。
2. 在一個以上區域的 Virtual Private Cloud 中建立一個以上的子網路。
3. 如果您希望子網路上的資源可以存取網際網路，請在子網路上建立公用閘道 (PGW)，反之亦然。
4. 選取您要執行的虛擬伺服器實例 (VSI) 的設定檔，並將它們實例化。
5. 保留浮動 IP 位址，如果您要從網際網路連接虛擬伺服器實例，請建立浮動 IP 位址與虛擬伺服器實例的關聯。
5. 將服務或應用程式部署至虛擬伺服器實例。

## 必要條件

 * **使用者許可權**：確保您的使用者具有足夠的許可權可在 VPC 中建立及管理資源。如需必要許可權的清單，請參閱[授與 VPC 使用者所需的許可權](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources)。

 * **備妥 SSH 金鑰**：您將使用 SSH 金鑰來連接至虛擬伺服器實例。

   * 在起始目錄的 `.ssh` 目錄下尋找稱為 `id_rsa.pub` 的檔案，例如，`/Users/<USERNAME>/.ssh/id_rsa.pub`。檔案的開頭為 `ssh-rsa`，結尾為電子郵件位址。

   * 或者，「產生 SSH 金鑰」：如果您沒有公開 SSH 金鑰，或忘記現有 SSH 金鑰的密碼，請執行 `ssh-keygen` 指令並遵循提示來產生新的 SSH 金鑰。例如，您可以透過執行 `ssh-keygen -t rsa -C "user_ID"` 指令，在 Linux 伺服器上產生 SSH 金鑰。該指令會產生兩個檔案。產生的公開金鑰位於 `<your key>.pub` 檔案中。
   
## 使用使用者介面、CLI 或 REST API

您可以透過使用者介面、CLI 或 REST API 來佈建及管理所有 VPC 資源。

如果您不熟悉 IBM Cloud Virtual Private Cloud，請一律選擇下面的任何鏈結，以引導您完成建立 IBM Cloud VPC 及其資源的處理程序。您可以選擇是從「主控台使用者介面」、指令行 (CLI) 還是地區基礎架構服務 (RIAS) API 開始。

* 若要透過使用者介面存取，請登入 [IBM Cloud 主控台 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]( https://{DomainName}/vpc){: new_window}。如需協助，請遵循[使用者介面手冊](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console)。
* 若要使用指令行介面，請使用 [IBM Cloud CLI](https://console.bluemix.net/docs/cli/index.html#overview) 的 [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) 外掛程式，並遵循 [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli) 範例。
* 若為更高階的使用者，您可以直接呼叫 [REST API](https://{DomainName}/apidocs/rias)。請遵循[程式碼範例](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis)指導教學，開始使用 REST API。

## 後續步驟
如果您準備好深入探討，請直接移至 **VPC 網路**及 **VSI for VPC** 的詳細文件：

* [**IBM Virtual Private Cloud 網路**](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**IBM Virtual Servers for Virtual Private Cloud**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

