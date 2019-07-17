---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-24"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 스토리지
{: #storage}

{{site.data.keyword.vsi_is_full}} 인스턴스를 프로비저닝하면 100GB, 범용 IOPS(3 IOPS/GB) 블록 스토리지 볼륨이 1차 부트 볼륨으로 자동 작성되어 인스턴스에 연결됩니다. 또한 인스턴스에 자동으로 연결되는 2차 데이터 볼륨을 작성할 수도 있습니다.
{:shortdesc}

- VPC용 블록 스토리지 볼륨에 대한 자세한 정보는 [VPC용 블록 스토리지 정보](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-about)를 참조하십시오.  
- 가상 서버 인스턴스 프로비저닝과는 별도로 볼륨 작성을 시작하려면 [{{site.data.keyword.block_storage_is_short}} 시작하기](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-getting-started)를 참조하십시오.

기본적으로 부트 및 데이터 볼륨은 IBM 관리 암호화를 사용하여 암호화됩니다. [독립형 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-encryption) 시에 또는 인스턴스 프로비저닝 중에 암호화 키를 사용하여 볼륨을 암호화할 수도 있습니다.  

가상 서버 인스턴스를 삭제하면 부트 볼륨이 삭제됩니다. 기본적으로 데이터 볼륨은 인스턴스에서 분리 시에 그대로 지속되며 나중에 새 인스턴스에 이 볼륨을 연결할 수 있습니다. 또는 인스턴스 삭제 시에 데이터 볼륨을 자동 삭제하도록 지정할 수도 있습니다.  

## 블록 스토리지의 고객 관리 암호화  
{: #customer-managed-encryption-keys}

관리 중인 데이터 암호화 키와 블록 스토리지 암호화로 {{site.data.keyword.vsi_is_full}}를 작성할 수 있습니다. {{site.data.keyword.keymanagementservicelong_notm}} 서비스와 데이터 암호화 키만 있으면 시작할 수 있습니다. 자세한 정보는 [고객 관리 암호화로 가상 서버 인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-instances-byok)을 참조하십시오.
{:shortdesc}

