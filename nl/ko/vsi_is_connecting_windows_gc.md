---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

keywords: Windows instance, encrypt password, decrypt password, retrieve password

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

# Windows 인스턴스에 연결
{: #connecting-to-your-windows-instance}

{{site.data.keyword.vsi_is_full}} Windows 인스턴스를 작성한 이후 다음 단계를 완료하여 이에 연결할 수 있습니다.
{:shortdesc}

## 시작하기 전에
{: #prereqs-connect-windows}

시작하려면 반드시 다음의 선행조건을 충족해야 합니다.

1. 계정 관리자에게 요청하여 가상 서버 인스턴스에서 비밀번호 검색을 위한 액세스 권한을 부여받으십시오. 자세한 정보는 [사용자 권한](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources)을 검토하십시오.
2. 새 보안 그룹을 작성하거나 규칙을 기본 보안 그룹에 추가하여 원격 데스크탑 기본 포트 3389에 대한 인바운드 액세스를 사용으로 설정하십시오. 자세한 정보는 [보안 그룹 사용](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups)을 참조하십시오.
3. TCP/IP 포트 3389에서의 인바운드 트래픽이 VPC의 기본 ACL에서 허용되는지 확인하십시오. 자세한 정보는 [네트워크 ACL 설정](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls)을 참조하십시오.
4. OpenSSL을 설치했는지 확인하십시오. 비밀번호를 제대로 복호화하려면 LibreSSL이 아닌 OpenSSL을 실행해야 합니다. 자세한 정보는 [OpenSSL 다운로드 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.openssl.org/source/){: new_window}를 참조하십시오.

LibreSSL은 비밀번호 복호화의 경우 호환 가능하지 않습니다. 비밀번호를 복호화하려면 OpenSSL을 실행해야 합니다.
{:important}

## 연결하기
{: #getting-connected-windows}

Windows 인스턴스를 작성하고 선행조건을 충족한 후에는 다음 단계를 완료하여 Windows 인스턴스에 연결하십시오.

1. 다음 명령을 실행하여 인스턴스의 상태를 조회하십시오.
  ```
  $ ibmcloud is instance <instance id>
  ```
  {:codeblock}
  
  인스턴스가 `running`을 표시하면 비밀번호를 가져오기 위한 초기화 값을 검색할 준비가 되었습니다. 

2. 다음 명령을 실행하여 인스턴스를 초기화하십시오.

  ```
  $ ibmcloud is instance-initialization-values <instance id>
  ```
  {:codeblock}
  
  이 명령은 Windows 이미지를 사용한 인스턴스 작성 시에 자동으로 생성되는 암호화된 비밀번호를 표시합니다.

3. 이제 수동 복호화 프로세스를 통해 비밀번호를 복호화해야 합니다. 비밀번호를 복호화하려면 다음 명령을 실행하십시오.

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  여기서 `~/examplepwd`는 2단계에서 언급한 암호화된 비밀번호가 저장된 파일입니다.  
  
  macOS에 포함된 LibreSSL이 비밀번호 복호화에 필요한 SHA2 해시 알고리즘을 지원하지 않으므로 결과적으로 `Public Key operation error` 오류가 발생합니다. 패키지 관리 도구를 사용하거나 이를 수동으로 설치하여 표준 OpenSSL 라이브러리를 가져올 수 있습니다. 
  {:note}

4. (선택사항) 비밀번호를 복호화한 후에는 인터넷 위치에서 연결이 가능하도록 유동 IP 주소를 Windows 인스턴스와 연관시킬 수 있습니다. 다음 명령을 실행하여 유동 IP 주소를 인스턴스와 연관시키십시오.

  ```
  ibmcloud is fipc --nic <instance nic id>
  ```
  {:codeblock}

5. 이제 Windows 인스턴스에 연결하는 데 필요한 복호화된 비밀번호와 유동 IP 주소를 보유 중입니다. 선호하는 원격 데스크탑 클라이언트를 사용하여 인스턴스에 연결하십시오. 인스턴스에 연결하려면 유동 IP 주소와 복호화된 비밀번호를 제공하십시오. 사용자 이름은 기본적으로 `Administrator`입니다.

## 다음 단계
{: #next-manage-instances}

인스턴스에 연결된 후에는 [{{site.data.keyword.cloud_notm}} 콘솔을 사용한 인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) 또는 [CLI를 사용한 인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)를 수행할 수 있습니다. 
