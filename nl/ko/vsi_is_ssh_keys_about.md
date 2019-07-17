---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# SSH 키
{: #ssh-keys}
[comment]: # (링크된 도움말 항목)

{{site.data.keyword.vsi_is_full}}를 프로비저닝하는 경우에는 인스턴스 작성 전에 사용할 새 SSH 키를 업로드하거나 기존 SSH 키를 선택해야 합니다. SSH 키를 사용하여 서버는 공개 키 암호화를 통해 사용자 또는 인스턴스를 식별합니다. SSH 키는 영숫자 조합으로 구성되며 이는 지정된 인스턴스에 고유합니다. {{site.data.keyword.cloud_notm}} 콘솔을 사용하여 SSH 키를 추가, 편집 또는 삭제할 수 있습니다.
{:shortdesc}

SSH 키는 인스턴스에서 구현된 각 공개 키에 해당되는 클라이언트의 비밀번호를 사용하지 않고도 인스턴스에 대한 액세스를 허용합니다. 프로비저닝 중에 실행 가능한 인스턴스에 SSH 키를 추가하면 비밀번호 대신 해당되는 키로 인스턴스에 액세스할 수 있습니다. 인스턴스를 처음 작성할 때만 인스턴스에 SSH 키를 추가할 수 있습니다. Linux 인스턴스가 작성되면 인스턴스의 `~/.ssh/` 디렉토리에서 직접 키를 편집할 수 있습니다.

비밀번호를 사용하여 인스턴스에 로그인할 수는 없습니다. Windows 인스턴스가 있으면 SSH 키를 사용하여 비밀번호가 복호화됩니다. 자세한 정보는 [Windows 인스턴스에 연결](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance)을 참조하십시오.
{:note}

## SSH 키 찾기 또는 생성하기
{: #locating-or-generating-your-ssh-key}

사용 가능한 SSH 키가 있어야 합니다. SSH 키를 찾거나 SSH 키를 생성하려면 다음 단계 중 하나를 완료하십시오.

 * SSH 키 찾기: 홈 디렉토리 아래의 `.ssh` 디렉토리에서 이름이 `id_rsa.pub`인 파일을 찾으십시오(예: `/Users/<USERNAME>/.ssh/id_rsa.pub`). 파일은 `ssh-rsa`로 시작하고 이메일 주소로 끝납니다.

* SSH 키 생성: 공개 SSH 키가 없거나 기존 SSH 키의 비밀번호를 잊은 경우에는 `ssh-keygen` 명령을 실행하고 프롬프트를 따라 새 SSH 키를 생성하십시오. 예를 들어, `ssh-keygen -t rsa -C "user_ID"` 명령을 실행하여 Linux 서버에서 SSH 키를 생성할 수 있습니다. 이 명령은 두 개의 파일을 생성합니다. 생성된 공개 키는 `<your key>.pub` 파일에 있습니다.

  OpenSSH 버전 7.8 이상을 사용 중이며 SSH 키를 사용하여 Windows 인스턴스에 액세스하려면 다음 명령을 사용하여 PEM 형식의 키를 생성해야 합니다. `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}

SSH 키 작성, 편집 또는 삭제에 대한 자세한 정보는 [SSH 키 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys)를 참조하십시오.
