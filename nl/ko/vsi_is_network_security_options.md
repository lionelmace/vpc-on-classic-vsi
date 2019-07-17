---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# 가상 서버의 네트워킹 및 보안
{: #network-security-options}

{{site.data.keyword.vsi_is_full}}를 구현하는 경우 네트워킹 및 보안을 위한 최신 기능에 액세스할 수 있습니다.  
{:shortdesc}

## 인스턴스 vNIC 사용
{: #using-instance-vnics}

가상 네트워크 인터페이스 카드(vNIC)는 가상 서버를 네트워크에 연결하는 데 사용됩니다. VSI 인스턴스를 작성하는 경우 vNIC를 사용하여 다중 IP 주소를 지정할 수 있습니다. 다음 목록에는 인스턴스에서 vNIC가 작동하는 방법이 강조되어 있습니다.

* 최대 5개의 vNIC를 작성하여 각 인스턴스에 지정할 수 있습니다. 각 vNIC에는 연결된 서브넷의 사설 IP가 지정되며 사용자는 선택적으로 유동 IP 및 보안 그룹을 연결할 수 있습니다.
* 동일한 구역의 서브넷에 각 vNIC를 연결할 수 있습니다.
* 각 vNIC는 서브넷 범위의 사설 IP를 수신합니다.
* 각 vNIC에 유동 IP를 연관시키거나 각 vNIC에서 유동 IP를 연관 해제시킬 수 있습니다.
* 각 vNIC에 보안 그룹을 지정할 수 있습니다.
* 기존 NIC의 이름을 변경할 수 있습니다.

대역폭은 인스턴스 자체와 연관되며 개별 vNIC의 구성 가능한 측면이 아닙니다. 인스턴스의 기본 대역폭은 100Mbps이며, 1Gbps로 업그레이드하는 옵션이 있습니다.

## 네트워킹 옵션
{: #networking-options}

{{site.data.keyword.vpc_short}} 환경의 전체 네트워킹 기능에 대한 자세한 정보는 [VPC의 네트워킹 정보](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)를 참조하십시오.

## 보안 옵션
{: #security-options}

{{site.data.keyword.vsi_is_short}}에는 기본 제공되는 보안 옵션이 포함되어 있습니다.
* 액세스 제어 목록(ACL)은 서브넷과의 양방향 트래픽을 제한할 수 있습니다.
* 보안 그룹은 가상 서버 인스턴스의 가상 방화벽 기능을 수행합니다.
* 가상 서버 인스턴스의 SSH 키는 네트워크 통신을 위한 보안 채널을 인증합니다.

이러한 보안 옵션에 대한 자세한 정보는 [IBM Cloud VPC의 보안](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) 및 [SSH 키 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)를 참조하십시오.
