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

# Conectando-se à sua instância do Linux
{: #connecting-to-your-linux-instance}

Depois de ter criado a sua instância do Linux dos {{site.data.keyword.vsi_is_full}}, é possível conectar-se a ela concluindo estas etapas.
{:shortdesc}

## Localizando o endereço IP flutuante
{: #locating-floating-ip-address}

Se for necessário localizar o seu endereço IP flutuante para a instância para a qual você deseja se conectar, conclua as etapas a seguir. Se você já souber seu endereço IP flutuante, poderá pular para [Conectando-se](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected). 

1. É necessário identificar seu ID de IP flutuante antes de poder localizar seu endereço IP flutuante. Execute o comando a seguir para identificar seu ID de IP flutuante:

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir (usando valores genéricos x e 123 apenas para fins de exemplo):

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

2. Agora que você tem seu ID de IP flutuante, é possível localizar seu endereço IP flutuante executando o comando a seguir.

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   Para esse exemplo, você veria uma resposta semelhante à saída a seguir (usando valores genéricos x e 123 apenas para fins de exemplo):

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

Opcionalmente, é possível localizar o endereço IP flutuante associado à instância para a qual você deseja se conectar por meio do console do {{site.data.keyword.cloud_notm}}.
{:tip}

## Sendo conectado
{: #getting-connected}

Os valores retornados abaixo são apenas para propósitos de exemplo.

1. Para se conectar à sua instância, use a chave privada e execute o comando a seguir:

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   Você recebe uma resposta semelhante ao exemplo a seguir. Quando solicitado a continuar a conexão, digite `yes`.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   Agora você está acessando seu servidor.

2. Quando você estiver pronto para terminar sua conexão, execute o comando a seguir:

   ```
   # exit
   ```
   {:codeblock}

## Próximas Etapas
{: #next-managing-instances}

Depois de estar conectado à sua instância, é possível [gerenciar suas instâncias usando o console do {{site.data.keyword.cloud_notm}}](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) ou [gerenciar suas instâncias usando a CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
