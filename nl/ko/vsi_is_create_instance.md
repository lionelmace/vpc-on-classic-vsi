---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: virtual server instances, virtual private cloud, boot volume, location select

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# 가상 서버 인스턴스 작성
{: #creating-virtual-servers}
[comment]: # (링크된 도움말 항목)

{{site.data.keyword.cloud_notm}} 콘솔의 *가상 서버 인스턴스* 페이지에서 {{site.data.keyword.vsi_is_full}}를 작성할 수 있습니다.
{:shortdesc}

시작하기 전에 [IBM Cloud VPC를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)했는지 확인하십시오.
{:important}

인스턴스를 작성하려면 다음의 인스턴스 세부사항을 선택하십시오.
1. [{{site.data.keyword.cloud_notm}} 콘솔 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.cloud.ibm.com/vpc)에서 **메뉴 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg) > VPC 인프라 > 컴퓨팅 > 가상 서버 인스턴스**로 이동하십시오.
2. **새 인스턴스**를 클릭하고 다음 정보를 입력하십시오.

    <table>
    <CAPTION>표 1. 인스턴스 프로비저닝 선택사항</CAPTION>
    <THEAD>
    <TR>
    <th>필드</th>
    <th>값</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>이름 </td>
    <td>가상 서버 인스턴스에 대한 이름이 필요합니다.</td>
    </tr>
    <tr>
    <td>VPC(Virtual Private Cloud)</td>
    <td>인스턴스가 작성될 IBM Cloud VPC를 지정하십시오.</td>
    </tr>
    <tr>
    <td>위치</td>
    <td>위치는 지역(특정 지리적 영역) 및 구역(지역 내의 결함 허용 데이터 센터)으로 구성되어 있습니다. 가상 서버 인스턴스가 작성될 위치를 선택하십시오.</td>
    </tr>
    <tr>
    <td>프로파일</td>
    <td><p>
    널리 사용되는 프로파일 또는 사용 가능한 모든 vCPU 및 RAM 조합에서 선택하십시오. 다음과 같은 제품군이 지원됩니다.
    <ul>
    <li>밸런스</li>
    <li>컴퓨팅</li>
    <li>메모리</li>
    </ul>
    </p>
    <p>서버의 각 실제 코어는 하이퍼스레딩 처리가 되어 있으며 두 개의 가상 CPU(vCPU)로 제공됩니다. 가상 서버 오퍼링은 vCPU당 2.0GHz 이상을 제공하며, 하나의 가상 서버에서 최대 48개의 vCPU가 사용될 수 있습니다.</p>

    <p>메모리의 경우 인스턴스는 최대 256GB의 완전 전용된 RAM을 보유할 수 있습니다.</p>
    <p><note>참고: 최대값은 제품군마다 다를 수 있습니다.</note></p>
    <p>자세한 정보는 [프로파일](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles)을 참조하십시오.</p>
    </td>
    </tr>
    <tr>
    <td>이미지</td>
    <td><p>모든 이미지는 cloud-init를 사용하며, 이를 통해 사후 프로비저닝 스크립트의 인스턴스와 연관된 사용자 메타데이터를 입력할 수 있습니다.</p>
    <p>자세한 정보는 [이미지](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images)를 참조하십시오.</p>
    </td>
    </tr>
    <td>SSH 키</td>
    <td>
    <p>인스턴스를 작성하기 전에 사용할 새 SSH 키를 업로드하거나 기존 SSH 키를 선택해야 합니다. SSH 키는 인스턴스의 실행 이후 이에 안전하게 연결하는 데 사용됩니다. 인스턴스를 처음 작성할 때만 인스턴스에 SSH 키를 추가할 수 있습니다.</p>
    <p>참고: 영숫자 조합은 100자로 제한됩니다.</p>
    <p>자세한 정보는 [SSH 키](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)를 참조하십시오.</p></td>
    </tr>
    <tr>
    <td>사용자 데이터</td>
    <td>
    <p>자동으로 공통 구성 태스크를 수행하거나 스크립트를 실행하는 사용자 데이터를 추가할 수 있습니다. <p>자세한 정보는 [사용자 데이터](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)를 참조하십시오.</p>
    </td>
    </tr>
    <tr>
    <td>부트 볼륨</td>
    <td><p>모든 프로파일의 기본 부트 볼륨 크기는 100GB입니다. 기본적으로 부트 볼륨에는 제공자 관리 암호화가 포함됩니다. 고객 관리 암호화를 사용하려는 경우 부트 볼륨의 세부사항을 편집할 수 있습니다. 자세한 정보는 [스토리지](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage)를 참조하십시오.</p>
    </td>
    </tr>
    <tr>
    <td>연결된 블록 스토리지 볼륨</td>
    <td><p>인스턴스를 프로비저닝할 때 포함될 하나 이상의 2차 데이터 볼륨을 추가할 수 있습니다. 볼륨을 추가하려면 **새 블록 스토리지 볼륨**을 클릭하십시오. 자세한 정보는 [블록 스토리지 볼륨 작성](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage)을 참조하십시오.</p>
    </td>
    </tr>
    <tr>
    <td>네트워크 인터페이스</td>
    <td>IBM Cloud VPC에 연결하기 위한 네트워크 옵션을 지정하십시오. 최대 5개의 네트워크 인터페이스 카드를 작성하여 각 인스턴스에 지정할 수 있습니다. 자세한 정보는 [다중 IP 주소](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options)를 참조하십시오.</td>
    </tr>
    </TBODY>
    </table>

    *비용 요약*이 *새 가상 서버 인스턴스* 페이지의 오른쪽에 표시됩니다.

3. 프로비저닝 준비가 완료되면 **가상 서버 인스턴스 작성**을 클릭하십시오. 일련의 이메일(가상 서버 인스턴스 주문의 수신확인, 주문 승인 및 처리, 인스턴스 작성 완료를 알리는 메시지)이 관리자에게 발송됩니다.

CLI를 사용한 인스턴스 작성을 원하십니까? 자세한 정보는 [CLI를 사용하여 인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)을 참조하십시오.
{: tip}

## 유동 IP 주소 예약
{: #reserving-a-floating-ip-address}

인터넷 위치에서 연결이 가능하도록 유동 IP 주소를 예약하고 이를 인스턴스와 연관시킬 수 있습니다.

유동 IP 주소를 연관시키려면 우선 인스턴스가 실행 중이어야 합니다. 인스턴스가 구동되어 실행되려면 수 분이 소요될 수 있습니다.
{: note} 

유동 IP 주소를 예약하고 연관시키려면 다음 단계를 완료하십시오.
1. **가상 서버 인스턴스** 페이지에서 해당 세부사항을 보고자 하는 인스턴스를 클릭하십시오.
2. **네트워크 인터페이스** 섹션에서 **예약 +**를 클릭하여 유동 IP 주소를 인스턴스와 연관시키십시오.

## 다음 단계
{: #next-connecting-to-instance}

이제 인스턴스에 연결할 준비가 되었습니다. 자세한 정보는 [Linux 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) 또는 [Windows 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)을 참조하십시오.
