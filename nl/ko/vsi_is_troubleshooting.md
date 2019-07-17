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

# VPC용 가상 서버의 문제점 해결
{: #troubleshooting-your-virtual-servers-for-vpc}
{{site.data.keyword.vsi_is_full}} 인스턴스에서 문제가 발생하면 다음의 가능한 원인을 검토하십시오.

## 오류: 409 인스턴스 조치 작성 시에 충돌 발생

인스턴스의 상태가 다른 조치와 충돌하면 특정 인스턴스 조치를 작성할 수 없습니다. 예를 들어, 인스턴스가 `stopped` 상태인데 `reboot` 조치의 작성을 시도하면 시스템에서 409 오류를 리턴합니다.

| 상태      | 조치     | 충돌 |
| ----------- | ---------- | -------- |
| 실행 중     | 시작      | 예      |
| 중지됨     | 시작 안함  | 예      |
| 실행 중이 아님 | 재부팅     | 예      |

## 인스턴스의 상태가 `deleting` 상태에 머무름

인스턴스를 나열하며 인스턴스의 상태가 `deleting` 상태에 머물러 있는 경우 인스턴스 표시 api `/instances/{instance_id}`를 사용하여 특정 가상 서버 인스턴스의 인스턴스 상태를 업데이트하십시오. 나열 api `/instances`를 사용하여 모든 인스턴스를 표시하는 경우 최신 상태가 표시되지 않을 수 있습니다.
