---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 이미지
{: #images}

{{site.data.keyword.vsi_is_full}}를 프로비저닝하는 경우 지원되는 재고 이미지에서 선택할 수 있습니다. 선택하는 이미지에 따라 인스턴스에 대해 프로비저닝되는 운영 체제가 결정됩니다. 
{:shortdesc}

## 재고 이미지
{: #stock-images}

다음의 운영 체제가 가상 서버 작성 시에 재고 이미지로 사용 가능합니다.
* CentOS 7.x
* Debian 8.x, 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04, 18.04
* Windows 2012, 2012 R2, 2016

인스턴스 주문 시에 이미지는 프로비저닝 시간의 최적화를 위해 cloud-init 사용이 설정되어 있습니다. cloud-init 사용이 설정된 이미지에서는 사용자 데이터를 제공할 수 있습니다. 주문 양식의 **사용자 데이터** 필드에서 서버에 대한 선택적 cloud-init 사용자 데이터를 입력할 수 있습니다. 사용자 데이터 및 자동화에 대한 자세한 정보는 [사용자 데이터](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)를 참조하십시오.

## 가상화
{: #virtualization}
인스턴스에서는 HVM(Hardware Virtualization Machine) 부트 모드를 지원하는 이미지가 필요합니다. HVM 가상화 유형은 가상 서버에서 직접 이미지의 실행을 허용하며, 이는 고급 네트워크 및 GPU 기능에 필요합니다.
