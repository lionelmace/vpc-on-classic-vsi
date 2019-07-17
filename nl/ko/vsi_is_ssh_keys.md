---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# SSH 키 관리
{: #managing-ssh-keys}

## 시작하기 전에
{: #prereq-ssh-key-available}

{{site.data.keyword.vsi_is_full}} 인스턴스에 액세스하려면 사용 가능한 SSH 키가 있어야 한다. {{site.data.keyword.cloud_notm}} 콘솔에서 또는 CLI를 사용하여 SSH 키를 관리할 수 있습니다. 

{{site.data.keyword.cloud_notm}} 콘솔 또는 CLI를 사용한 키 관리는 이미 작성된 인스턴스의 키에 영향을 주지 않습니다. (기존 Linux 인스턴스의 경우 인스턴스의 `~/.ssh/` 디렉토리에서 직접 키를 편집할 수 있습니다.)

SSH 키 찾기 또는 생성에 대한 자세한 정보는 [SSH 키](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)를 참조하십시오.
{: tip}

## IBM Cloud 콘솔에서 SSH 키 관리
{: #managing-ssh-keys-with-ibm-cloud-console}

가상 서버를 프로비저닝하는 경우 사용 가능한 SSH 키에서 선택하거나 새 SSH 키를 업로드할 수 있습니다. {{site.data.keyword.cloud_notm}} 콘솔에서는 SSH 키를 생성할 수 없습니다.
{:shortdesc}

{{site.data.keyword.cloud_notm}} 콘솔을 사용하여 SSH 키를 관리 및 삭제할 수 있습니다.
1. [{{site.data.keyword.cloud_notm}} 콘솔 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.cloud.ibm.com/vpc)에서 **메뉴 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg) > VPC 인프라 > 컴퓨팅 > SSH 키**로 이동하십시오.
2. 여기에서 SSH 키를 추가 또는 삭제할 수 있습니다.

## CLI를 사용하여 SSH 키 관리
{: #managing-ssh-keys-by-using-the-cli}

CLI를 사용하여 SSH 키를 관리할 수도 있습니다.

| 조치           | 명령                     | 실행 결과 |
| ---------------- | --------------------------- | ----------------- |
| SSH 키 작성   | `ibmcloud is key-create`    | 작성된 이후 SSH 키가 키 목록에 추가됩니다. |
| 키 세부사항 보기 | `ibmcloud is key`           | 키의 이름과 키의 ID를 볼 수 있습니다. |
| 키 나열        | `ibmcloud is keys`          | 기존 SSH 키를 모두 볼 수 있습니다. |
| 키 업데이트       | `ibmcloud is key-update`    | 기존 키를 업데이트하면 키의 이름이 즉시 변경됩니다. |
| 키 삭제       | `ibmcloud is key-delete`    | SSH 키를 제거하면 새 인스턴스를 프로비저닝하거나 기존 인스턴스에서 OS 재로드를 수행할 때 더 이상 이를 사용할 수 없습니다. 그러나 키는 이를 사용하여 프로비저닝된 인스턴스에서 여전히 사용 가능하며 이를 사용하여 로그인할 수 있습니다. |
{: caption="표 1. SSH 키 조치" caption-side="top"}
