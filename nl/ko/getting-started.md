---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# 시작하기 튜토리얼
{: #getting-started}

{{site.data.keyword.vsi_is_full}}(VPC)를 사용하여 IBM Cloud에서 확장형 컴퓨팅 리소스를 프로비저닝할 수 있습니다.
{:shortdesc}

필요한 수만큼의 가상 서버를 작성하고 네트워크와 보안을 구성하며 스토리지를 관리할 수 있습니다. 이 모두를 개선된 IBM Cloud 콘솔에서 사용할 수 있습니다. 이 콘솔은 사용자 환경을 변화하는 워크로드 수요에 맞추기 위해 빠르고 손쉬운 액세스를 제공할 수 있도록 만들어졌습니다. 바로 시작하고 싶으실테니 곧장 본론으로 들어가겠습니다.

시작하기 전에 [IBM Cloud VPC를 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)했는지 확인하십시오.
{:important}

{{site.data.keyword.vsi_is_short}}는 클래식 가상 서버 오퍼링과 호환되지 않습니다. 클래식 인프라의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} 오퍼링에 관심이 있으면 [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial)를 참조하십시오.
{:note}

<p>다음 정보를 사용하여 빠르게 인스턴스를 작성하고 이에 연결하십시오.
<table>
   <CAPTION>표 1. 빠른 시작 단계</CAPTION>
   <THEAD>
   <TR>
   <th>태스크</th>
   <th>세부사항</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. 구현에 도움이 될 수 있는 컨텐츠 검토</td>
   <td>IBM Cloud 및 가상 서버가 처음이십니까? 다음 사이트에서 사용자 환경을 계획하는 데 도움이 되는 유용한 정보를 제공합니다.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">IBM Cloud 개념</a></li>
      <li><a href="https://ibm.com/cloud/get-started">IBM Cloud 시작하기</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. IBM Cloud에 등록</td>
   <td>IBM Cloud 계정을 설정하는 방법에 대한 정보는 <a href="/docs/account?topic=account-signup#signup">IBM Cloud에 등록</a>을 참조하십시오.</td>
 <tr>
   <td>3. 워크로드 스펙 결정</td>
   <td>인스턴스를 작성하려면 우선 이에 대한 사용 방법과 성공에 필요한 인스턴스 크기를 결정하십시오. 예를 들어, 이를 개발 및 테스트에 또는 프로덕션에 사용하시겠습니까? 사용자 경험 테스트, 장황한 알고리즘 처리, 데이터 백업 및 복원 또는 대기 시간 속도 높이기를 수행 중이십니까?</td>  
 <tr>
   <td>4. 인스턴스의 크기 조정 및 가격</td>
   <td>인스턴스 작성과 관련하여 세 가지 제품군 옵션(밸런스, 컴퓨팅 및 메모리)이 있습니다. 제품군에는 대부분의 고객의 요구사항을 충족시키며 단 5분 만에 구성 준비가 가능한 사전 구성된 인스턴스("프로파일"이라고 함)가 포함되어 있습니다.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">밸런스</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">컴퓨팅</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">메모리</a></li>
     </ul>
  <p>[가격](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) 정보를 사용하면 인스턴스의 크기를 조정하고 가격을 책정하는 데 도움이 됩니다.</p></td>
 <tr>
   <td>5. IBM 클라우드 계정에 로그인</td>
   <td><a href="https://console.bluemix.net/catalog/">IBM Cloud 카탈로그</a>에서 {{site.data.keyword.vsi_is_short}} 주문 양식에 액세스하십시오. <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBM ID 및 비밀번호</a>가 필요합니다.
   </td>
 <tr>
   <td>6. {{site.data.keyword.vpc_short}} 환경에 대한 액세스 요청</td>
   <td>아직 액세스를 요청하지 않은 경우에는 {{site.data.keyword.vpc_short}}에 대한 액세스를 요청하십시오.</td>
<tr>
<td>7. SSH 키 생성</td>
<td> 지시사항은 [SSH 키](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys)를 참조하십시오.</td>
<tr>
<td>8. 인스턴스에 대한 계획</td>
<td> 리소스의 성공적인 계획, 프로비저닝 및 구성에 도움이 되는 자세한 정보는 [인스턴스에 대한 계획](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances)을 참조하십시오.</td>
<tr>
<td>9. 인스턴스 작성</td>
<td>
<p>
인스턴스 작성을 시작하려면 [인스턴스 작성](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)을 참조하십시오.
</td>  
<tr>
<td>10. 인스턴스에 연결</td>
<td>인스턴스가 이제 준비되었습니다! *연결* 아래의 다음 주제를 참조하여 인스턴스 작성이 완료되었는지 확인하십시오.
   <ul>
   <li>[Linux 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Windows 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. 인스턴스 정리</td>
<td>인스턴스가 더 이상 필요하지 않으면 이를 삭제할 수 있습니다. </td>
</tr>
</TBODY>
</table>
</p>

## 다음 단계
인스턴스가 프로비저닝된 후에는 옵션을 탐색하십시오.
* [인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [{{site.data.keyword.vsi_is_short}} 권한](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [IBM Cloud VPC의 보안](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about) 관련 추가 정보
