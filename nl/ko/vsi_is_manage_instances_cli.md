---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 가상 서버 인스턴스 관리(CLI)
{: #managing-virtual-servers-cli}

명령행 인터페이스(CLI)를 사용하여 {{site.data.keyword.vsi_is_full}} 인스턴스를 보고 관리할 수 있습니다.
{:shortdesc}

## 시작하기 전에
{: #prereq-managing-instances}

1. 다음의 CLI 플러그인을 다운로드, 설치 및 초기화했는지 확인하십시오.
    * {{site.data.keyword.cloud_notm}} CLI
    * infrastructure-service 플러그인

   자세한 정보는 [IBM Cloud VPC용 CLI 참조서](/docs/vpc-infrastructure-cli-plugin?topic=vpc-infrastructure-cli-plugin-vpc-reference)를 참조하십시오.
   
   vpc-infrastructure 플러그인을 처음 설치하는 경우에는 대상 생성을 gen 1로 설정해야 합니다(`ibmcloud is target --gen 1`).
   {:important}
   
2. 사전에 [{{site.data.keyword.vpc_short}}가 작성](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started)되었는지 확인하십시오.

## 인스턴스 조치 보기
{: #viewing-instance-actions}

인스턴스에서 수행되는 관리 조치를 보려면 다음 명령을 실행하십시오.

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

다음 출력과 유사한 목록이 나타납니다.

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## 인스턴스 관리
{: #managing-your-instances}

약간의 도움이 필요하십니까? `ibmcloud is help` 명령을 실행하여 언제든지 명령을 볼 수 있습니다.

### 재설정  

```
ibmcloud is instance-reset
```
{:codeblock}

인스턴스의 전원을 차단한 후 다시 공급합니다.  

### 다시 시작

```
ibmcloud is instance-reboot
```
{:codeblock}

인스턴스의 운영 체제가 다시 시작됩니다.  

### 중지 및 시작

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

디바이스가 중지되면 해당 디바이스는 중지됨 상태를 유지하며 수동으로 시작되어야 합니다. 인스턴스가 중지되면 이와 상호작용할 수 없습니다. 디바이스가 시작되면 상호작용이 정상적으로 계속됩니다. 

### 업데이트

```
ibmcloud is instance-update
```
{:codeblock}

디바이스 이름을 변경하면 이름이 자동으로 업데이트됩니다. 검색을 수행할 때 연관된 컨텐츠를 찾으려면 새 인스턴스 이름을 사용하십시오. 

### 삭제

```
ibmcloud is instance-delete
```
{:codeblock}

삭제 조치를 확인하면 인스턴스 및 이와 연결된 vNIC, 부트 볼륨 및 데이터를 삭제하는 프로세스가 시작됩니다. 삭제 조치는 수 분이 소요될 수 있지만, 프로세스가 완료되면 인스턴스가 더 이상 가상 서버 인스턴스 페이지에 나타나지 않습니다. 가상 서버 인스턴스와 연관된 유동 IP 주소는 연관 해제 상태이지만 계정에서 계속 유지됩니다.

{{site.data.keyword.cloud}} 콘솔을 사용한 인스턴스 관리를 원하는 경우에는 [인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)를 참조하십시오.
{: tip}
