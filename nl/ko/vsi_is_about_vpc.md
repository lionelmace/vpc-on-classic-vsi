---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# VPC용 가상 서버 정보
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}}를 사용하면 네트워크 격리, 보안 및 유연성을 포함한 {{site.data.keyword.vpc_short}}의 모든 이점을 활용할 수 있습니다. 
{:shortdesc}

## {{site.data.keyword.vpc_short}} 개념
{{site.data.keyword.vpc_short}}는 고객 계정에 연계된 가상 네트워크입니다. 이는 성장과 함께 동적으로 확장하는 기능과 클라우드 보안을 제공하는 비용 효율적인 시작점을 제공합니다. 이는 가상 인프라와 네트워크 트래픽 세그먼트화에 대한 세분화된 제어를 제공합니다.
{: shortdesc}

{{site.data.keyword.vpc_short}}에 대한 자세한 정보는 [IBM Cloud VPC 정보](/docs/vpc-on-classic?topic=vpc-on-classic-about)를 참조하십시오.

## {{site.data.keyword.vsi_is_short}} 개념
{{site.data.keyword.vsi_is_short}}를 사용하면 {{site.data.keyword.vpc_short}} 내에서 가상 컴퓨팅 리소스와 결과 용량으로 구성된 인스턴스를 작성할 수 있습니다. 인스턴스를 프로비저닝하는 경우 인스턴스에서 실행할 애플리케이션이나 소프트웨어에 필요한 컴퓨팅 능력과 메모리의 양에 합당한 인스턴스 프로파일을 선택합니다. 인스턴스를 프로비저닝한 후에는 해당 인프라 리소스를 제어하고 관리합니다. 각 계정에서는 서버에서 실행 중인 인스턴스의 수가 제한됩니다. 이러한 한계에 대한 자세한 정보는 [FAQ](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)를 참조하십시오. 

## {{site.data.keyword.vpc_short}}용 가상 서버 인스턴스와 기타 IBM 가상 서버 오퍼링 간의 차이점은 무엇입니까?

오늘날의 IBM Cloud Virtual Server 오퍼링에서 인스턴스는 기본 서브넷과 VLAN 네트워킹을 사용하여 데이터 센터(및 단일 팟(Pod)) 내에서 서로 간에 통신합니다. 하나의 팟(Pod)에서 서브넷과 VLAN 네트워킹을 사용하는 경우에는 팟(Pod) 간에 리소스의 작성이 필요한 대규모 가상 리소스 수요의 보유나 확장이 필요할 때까지 문제 없이 작동합니다. (VLAN Spanning을 위한 어플라이언스 추가는 비용이 많이 들고 복잡할 수 있습니다!) 

{{site.data.keyword.vpc_short}}는 팟(Pod) 경계를 허무는 네트워크 오케스트레이션 계층을 추가하며, 인스턴스의 스케일링을 위한 무제한 용량을 생성합니다. 네트워크 오케스트레이션 계층은 지역과 구역 간의 {{site.data.keyword.vpc_short}} 내에 있는 모든 가상 서버 인스턴스와 관련된 모든 네트워킹을 처리합니다. {{site.data.keyword.vpc_short}}에서 제공하는 소프트웨어 정의 네트워킹 기능을 사용하면 [VPN](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-load-balancers-in-ibm-cloud-vpc), 다중 vNIC 인스턴스 및 대규모 [서브넷](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets) 크기에 대해 추가적인 옵션이 있습니다. 자세한 정보는 [VPC용 네트워킹 정보](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc)를 참조하십시오. 

{{site.data.keyword.vsi_is_short}}에는 보다 심플한 사용자 경험과 비용 절감을 제공하는 다음의 기능도 있습니다.
* 새 {{site.data.keyword.cloud_notm}} 콘솔
* 새 Virtual Private Cloud API 및 CLI
* [가격](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)에서 설명하는 지속적 사용 할인 티어의 새 비용 청구 모델

{{site.data.keyword.vsi_is_short}}는 클래식 가상 서버 오퍼링과 호환되지 않습니다. 클래식 인프라의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} 오퍼링에 관심이 있으면 [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial#getting-started-tutorial)를 참조하십시오.
{:note}




