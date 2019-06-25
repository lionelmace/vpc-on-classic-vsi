---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 疑難排解 Virtual Servers for VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
如果您在使用 {{site.data.keyword.vsi_is_full}} 實例時遇到困難，請檢閱下列可能的原因。

## 錯誤：409 建立實例動作時發生衝突

如果您的實例狀態與另一個動作衝突，則無法建立特定實例動作。例如，如果您的實例狀態為 `stopped`，而您嘗試建立 `reboot` 動作，則系統會傳回 409 錯誤。

|狀態|動作|衝突|
| ----------- | ---------- | -------- |
| Running     | start      |是|
| Stopped     | not start  |是|
| Not running | reboot     |是|

## 實例的狀態停留在 `deleting` 狀態

當您列出實例，並發現實例的狀態停留在 `deleting` 狀態時，請使用 show instance api `/instances/{instance_id}` 來更新特定虛擬伺服器實例的實例狀態。使用 list api `/instances` 來顯示所有實例時，可能未顯示最新狀態。
