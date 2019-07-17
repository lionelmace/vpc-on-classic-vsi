---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 가상 서버 인스턴스 관리
{: #managing-virtual-server-instances}
[comment]: # (링크된 도움말 항목)

{{site.data.keyword.cloud_notm}} 콘솔의 *가상 서버 인스턴스* 페이지에서 {{site.data.keyword.vsi_is_full}} 인스턴스를 보고 관리할 수 있습니다.
{:shortdesc}

인스턴스를 관리하려면 다음 단계를 완료하십시오.
1. [{{site.data.keyword.cloud_notm}} 콘솔 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.cloud.ibm.com/vpc)에서 **메뉴 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg) > VPC 인프라 > 컴퓨팅 > 가상 서버 인스턴스**로 이동하십시오.
2. 여기에서 특정 인스턴스에 대한 태스크를 관리하거나 인스턴스를 클릭하여 해당 특성을 보고 편집할 수 있습니다.

## 재부팅

재부팅 조치는 인스턴스의 전원을 즉시 차단한 후 이에 다시 전원을 공급합니다.

## 중지 및 시작

중지 및 시작 조치는 인스턴스를 원격으로 켜거나 끕니다. 인스턴스가 중지되면 해당 인스턴스는 중지됨 상태를 유지하며 수동으로 시작되어야 합니다. 인스턴스가 중지된 동안에는 일부 컴퓨팅 리소스에 대해 비용 청구가 [일시중단](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing)됩니다. 인스턴스가 중지되면 이와 상호작용할 수 없습니다. 디바이스가 시작되면 상호작용이 정상적으로 계속됩니다.

## 삭제

삭제 조치는 계정에서 인스턴스 및 이와 연결된 vNIC, 부트 볼륨 및 데이터를 영구적으로 제거합니다. 삭제 조치를 확인하면 인스턴스 및 이와 연결된 vNIC, 부트 볼륨 및 데이터를 삭제하는 프로세스가 시작됩니다. 삭제 조치는 최대 30분까지 소요될 수 있지만, 프로세스가 완료되면 인스턴스가 더 이상 가상 서버 인스턴스 페이지에 나타나지 않습니다. 가상 서버 인스턴스와 연관된 유동 IP 주소는 연관 해제 상태이지만 계정에서 계속 유지됩니다.

## 인스턴스 세부사항 보기
*가상 서버 인스턴스* 페이지에서 모든 인스턴스의 요약을 보거나 개별 인스턴스를 클릭하여 세부사항을 보고 변경을 수행함으로써 인스턴스와 상호작용할 수 있습니다. 인스턴스 세부사항 페이지에서 연관된 네트워크 인터페이스를 보고 해당 서브넷에 액세스하며 유동 IP 주소를 예약 또는 삭제할 수도 있습니다.

CLI를 사용한 인스턴스 관리를 원하는 경우에는 [CLI를 사용하여 인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)를 참조하십시오.
{: tip}
