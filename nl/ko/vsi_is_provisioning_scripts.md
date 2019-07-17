---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-16"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 사용자 데이터
{: #user-data}
[comment]: # (링크된 도움말 항목)

{{site.data.keyword.vsi_is_full}} 인스턴스를 작성하는 경우 스크립트를 실행하거나 공통 구성 태스크를 자동으로 수행하는 사용자 데이터를 추가할 수 있습니다. 주문 양식의 **사용자 데이터** 필드에서 서버에 대한 선택적 cloud-init 사용자 데이터를 입력할 수 있습니다.
{:shortdesc}

## Linux용 사용자 데이터 예제 
{: #user-data-examples-for-linux}

다음 예제는 Linux 사용자가 새 사용자를 추가하고 권한 부여된 SSH 키를 사용자에게 제공하는 방법을 보여줍니다. **이름** 필드는 `~/.ssh/authorized_keys`에 추가된 공개 키를 보유합니다. 

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

다음은 Linux 사용자가 현재 사용자에 대한 SSH 키를 추가하는 방법을 보여주는 쉘 스크립트의 또 다른 예제입니다.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

**사용자 데이터** 필드에 직접 이러한 예제 중 하나를 붙여넣을 수 있습니다. 그러면 프로비저닝 중에 가상 서버 인스턴스가 사용자 데이터를 사용할 수 있습니다. 

추가적인 Linux 사용자 데이터 예제와 정보에 대해서는 [클라우드 구성 예제 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}를 참조하십시오.

## Windows용 사용자 데이터 예제
{: #user-data-example-for-windows}

다음 예제는 사용자 데이터를 Windows 인스턴스에 전달하는 방법을 보여줍니다. 이 예제를 복사하여 **사용자 데이터** 필드에 직접 붙여넣을 수 있습니다.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

추가적인 Windows 사용자 데이터 예제와 정보에 대해서는 [Cloudbase-init 1.0 문서 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}를 참조하십시오.
