---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Linux 인스턴스에 연결
{: #connecting-to-your-linux-instance}

{{site.data.keyword.vsi_is_full}} Linux 인스턴스를 작성한 이후 다음 단계를 완료하여 이에 연결할 수 있습니다.
{:shortdesc}

## 유동 IP 주소 찾기
{: #locating-floating-ip-address}

연결할 인스턴스에 대한 유동 IP 주소를 찾아야 하는 경우에는 다음 단계를 완료하십시오. 유동 IP 주소를 이미 알고 있는 경우에는 [연결하기](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected)로 건너뛸 수 있습니다. 

1. 유동 IP 주소를 찾으려면 우선 유동 IP ID를 식별해야 합니다. 다음 명령을 실행하여 유동 IP ID를 식별하십시오.

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   이 예제의 경우 다음 출력과 유사한 응답이 나타납니다(예제 용도로만 일반 x 및 123 값 사용).

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. 이제 유동 IP ID를 보유 중이므로 다음 명령을 실행하여 유동 IP 주소를 찾을 수 있습니다.

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   이 예제의 경우 다음 출력과 유사한 응답이 나타납니다(예제 용도로만 일반 x 및 123 값 사용).

   ```
   ID               12345x67-8901-234x-5678-9xx01xx23x4x   
   Address          123.45.678.90   
   Name             my-instance   
   Target           primary(1xx2x34x-.)   
   Target Type      intf   
   Target IP        12.345.6.78   
   Created          1 week ago   
   Status           available   
   Zone             us-south-1   
   Resource Group   -   
   Tags             -   
   ```
   {:screen}

(선택사항) {{site.data.keyword.cloud_notm}} 콘솔을 통해 연결할 인스턴스와 연관된 유동 IP 주소를 찾을 수 있습니다.
{:tip}

## 연결하기
{: #getting-connected}

아래의 리턴된 값은 예제 용도로만 사용됩니다.

1. 인스턴스에 연결하려면 개인 키를 사용하고 다음 명령을 실행하십시오.

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   다음 예제와 유사한 응답이 수신됩니다. 연결을 계속할 것인지를 묻는 프롬프트가 나타나면 `yes`를 입력하십시오.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   이제 서버에 액세스 중입니다.

2. 연결을 종료할 준비가 되면 다음 명령을 실행하십시오.

   ```
   # exit
   ```
   {:codeblock}

## 다음 단계
{: #next-managing-instances}

인스턴스에 연결된 후에는 [{{site.data.keyword.cloud_notm}} 콘솔을 사용한 인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) 또는 [CLI를 사용한 인스턴스 관리](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli)를 수행할 수 있습니다.
