---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# 인스턴스에 대한 계획
{: #planning-for-instances}
[comment]: # (링크된 도움말 항목)


{{site.data.keyword.vsi_is_full}}를 프로비저닝하려는 경우 이 구성 체크리스트가 가상 서버 배치를 최대한 활용하는 데 유용할 수 있습니다.
{:shortdesc}

시작하려면 우선 [{{site.data.keyword.vpc_short}}가 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)되었는지 확인하십시오.
{:important}

## 인스턴스 프로비저닝에 대한 계획
{: #planning-for-provisioning-instances}

{{site.data.keyword.vpc_short}}가 사용 가능하면 인스턴스를 프로비저닝하기 전에 다음을 고려하십시오.

|        고려사항|
|-------------------|
|__ 1. 계정에 필수 [사용자 권한](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)이 있는지 확인하십시오. {{site.data.keyword.vpc_short}} 리소스에 대한 편집자 또는 관리자로서 권한이 부여된 경우에는 해당 가상 프라이빗 클라우드 내에서 가상 서버 인스턴스를 작성, 삭제 및 수정할 수 있는 권한도 상속됩니다.|
|__ 2. 동시 인스턴스에 대한 [계정 한계](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs)를 확인하십시오. |
|__ 3. [SSH 키](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)가 사용 가능한지 확인하십시오.
|__ 4. 선택할 인스턴스 위치를 결정하십시오.|
|__ 5. 워크로드에 대해 vCPU 및 RAM 조합의 널리 사용되는 [프로파일 옵션](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)을 고려하십시오. 프로파일에는 수 분이면 사용 준비가 완료되는 사전 구성된 인스턴스가 포함되어 있습니다. 워크로드와 사용자 환경의 구동 및 실행을 지속적으로 유지하는 데 필요한 리소스를 인스턴스가 보유할 수 있을지 여부를 확인하는 것이 중요합니다.|
|__ 6. 인스턴스에 대해 선택할 운영 체제 이미지를 판별하십시오. 현재 재고 [이미지](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images) 중에서 선택할 수 있습니다. |
|__ 7. 인스턴스에 대해 고유 이름을 보유 중인지 확인하십시오. 가상 서버 인스턴스의 이름을 지정하는 방법이 있으면 나중에 이를 필터링하여 검색하기가 훨씬 더 쉽습니다. |

## 다음 단계
{: #next-create-instance}

시작할 준비가 되면 다음 리소스를 참조하여 인스턴스를 작성하십시오.
* [{{site.data.keyword.cloud_notm}} 콘솔을 사용하여 인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [CLI를 사용하여 인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
