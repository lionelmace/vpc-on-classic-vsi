---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# 設定檔
{: #profiles}

當您佈建 {{site.data.keyword.vsi_is_full}} 時，可以從三個設定檔系列中選取：平衡、運算及記憶體。設定檔是 vCPU 和 RAM 的組合，可快速實例化以啟動虛擬伺服器實例。在 {{site.data.keyword.Bluemix_notm}} 主控台中，您可以從熱門設定檔配置中進行選擇，或是從最符合您需求的設定檔清單中進行選取。
{: shortdesc}

以下是可用的系列：

| 系列 | 說明 |
| -------- | ----------- |
| [平衡](#balanced) | 最適合用於需要平衡效能和可擴充性的一般雲端工作負載。平衡設定檔（具有網路連接的儲存空間）提供高效能，因為不會超額訂閱資源。|
|[運算](#compute)  |最適合用於中到高 Web 資料流量的工作負載。運算設定檔最適合用於 CPU 需求密集的工作負載，例如高 Web 資料流量工作負載、正式作業批次處理及前端系統 Web 伺服器。|
| [記憶體](#memory) | 最適合用於記憶體快取和即時分析工作負載。記憶體設定檔最適合用於記憶體密集型的工作負載，例如大型快取工作負載、密集型資料庫應用程式或記憶體內分析工作負載。|
{: caption="表 1. 虛擬伺服器系列選擇" caption-side="top"}

## 平衡
{: #balanced}

平衡設定檔提供高效能，因為不會超額訂閱資源。網路效能範圍從標準到超值。

此供應項目提供於下列設定檔：

| 設定檔 | vCPU | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="表 2. 虛擬伺服器平衡設定檔選項" caption-side="top"}

**儲存空間附註：**

* 當您佈建實例時，會自動建立並連接 SAN 主要開機磁區 (100GB)。
* 選擇性地建立次要資料磁區。磁區設定檔以三個預先定義的 IOPS 層級或自訂 IOPS 提供。[3 IOPS 一般用途層級設定檔](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)提供適用於 VSI 平衡設定檔的 IOPS/GB 效能。
* 使用 SAN 儲存空間的公用虛擬伺服器定價包括虛擬 CPU、記憶體及主要開機磁區。次要資料磁區是個別定價。

此供應項目提供所有支援的作業系統（例如 CentOS、Debian、Ubuntu 及 Windows）。

## 運算
{: #compute}

運算設定檔最適合用於 CPU 需求密集的工作負載，例如高 Web 資料流量的工作負載、正式作業批次處理及前端系統 Web 伺服器。

此供應項目提供於下列設定檔：

| 設定檔 | vCPU | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="表 3. 虛擬伺服器實例運算設定檔選項" caption-side="top"}

**儲存空間附註：** 

* 當您佈建實例時，會自動建立並連接 SAN 主要開機磁區 (100GB)。
* 選擇性地建立次要資料磁區。磁區設定檔以三個預先定義的 IOPS 層級或自訂 IOPS 提供。[5-IOPS 層級](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)設定檔提供適用於 VSI 運算設定檔的 IOPS/GB 效能。
* 使用 SAN 儲存空間的公用虛擬伺服器定價包括虛擬 CPU、記憶體及主要開機磁區。次要資料磁區是個別定價。

此供應項目提供所有支援的作業系統（例如 CentOS、Debian、Ubuntu 及 Windows）。 

## 記憶體 
{: #memory}

記憶體設定檔最適合用於記憶體密集型工作負載，例如大型快取工作負載、密集型資料庫應用程式或記憶體內分析工作負載。

此供應項目提供於下列設定檔：

| 設定檔 | vCPU | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="表 4. 虛擬伺服器實例記憶體設定檔選項" caption-side="top"}

**儲存空間附註：** 

* 當您佈建實例時，會自動建立並連接 SAN 主要開機磁區 (100GB)。
* 選擇性地建立次要資料磁區。磁區設定檔以三個預先定義的 IOPS 層級或自訂 IOPS 提供。[10-IOPS 層級](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers)設定檔提供適用於 VSI 記憶體設定檔的 IOPS/GB 效能。
* 使用 SAN 儲存空間的公用虛擬伺服器定價包括虛擬 CPU、記憶體及主要開機磁區。次要資料磁區是個別定價。

此供應項目提供所有支援的作業系統（例如 CentOS、Debian、Ubuntu 及 Windows）。 

## 檢視設定檔配置
{: #popularprofiles}

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或 CLI 來檢視可用的設定檔配置。在 {{site.data.keyword.cloud_notm}} 主控台中，您可以從熱門設定檔配置中進行選取，以支援一般使用案例。

### 使用 IBM Cloud 主控台
1. 在 {{site.data.keyword.cloud_notm}} 主控台中，導覽至**功能表圖示 ![「功能表」圖示](../icons/icon_hamburger.svg) > VPC 基礎架構 > 運算 > 虛擬伺服器實例**。
2. 從此頁面，按一下**新建實例**。
3. 您可以從**熱門設定檔**中選取設定檔配置，或按一下**所有設定檔**來檢視其他配置。

### 使用 CLI
若要使用 CLI 檢視可用設定檔清單，請執行下列指令：
```
$ ibmcloud is instance-profiles
```
{:codeblock}

使用指令行時，下列資訊說明輸出所代表的內容。設定檔大小具有不同的 CPU 與記憶體比例，專為不同工作負載而設計：

*  "b" 是平衡，這是 1:2 或 1:4 的比例
*  "c" 是運算（在 CPU 方面提高），這是 1:1 的比例
*  "m" 是記憶體（在記憶體方面提高），這是 1:8 的比例
