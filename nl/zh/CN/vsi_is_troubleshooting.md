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

# 有关 Virtual Servers for VPC 的故障诊断
{: #troubleshooting-your-virtual-servers-for-vpc}
如果使用 {{site.data.keyword.vsi_is_full}} 实例遇到困难，请查看以下可能的原因。

## 错误：创建实例操作时发生 409 冲突

如果实例的状态与其他操作相冲突，那么无法创建某些实例操作。例如，如果实例状态为 `stopped`，而您尝试创建 `reboot` 操作，那么系统会返回 409 错误。

|状态|操作|冲突|
| ----------- | ---------- | -------- |
|Running|start|是|
|Stopped|非 start|是|
|非 running|reboot|是|

## 实例的状态卡在 `deleting` 状态

列出实例并找到卡在 `deleting` 状态的实例的状态后，使用 show instance api `/instances/{instance_id}` 来更新特定虚拟服务器实例的实例状态。使用 list api `/instances` 显示所有实例时，可能显示的不是最新状态。
