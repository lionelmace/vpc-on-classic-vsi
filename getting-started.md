---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-23"

keywords: "virtual servers, {{site.data.keyword.vsi_is_short}}, getting started, virtual private cloud, virtual machines"

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
{:external: target="_blank" .external}

# Getting started with Virtual Servers for VPC
{: #getting-started}

Use {{site.data.keyword.vsi_is_full}} (VPC) on Classic to create compute instances in the {{site.data.keyword.cloud_notm}}.
{:shortdesc}

You can create virtual server instances on demand, configure network and security, and manage storage. All of these features are available in an improved {{site.data.keyword.cloud_notm}} console. The console is built to provide you with quick and easy access to adjust your environment with your changing workload demands. 

Bet you're anxious to start, so let's get to work creating a Linux instance from {{site.data.keyword.cloud_notm}} console.

## Before you begin
{: #vsi-for-vpc-before-you-begin}

Are you new to {{site.data.keyword.cloud_notm}} and {{site.data.keyword.vsi_is_short}}? The following information might help:

* Make sure that you sign up for an {{site.data.keyword.cloud_notm}} account. For more information, see [Signing up for {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/account?topic=account-signup#signup){: external}.
* {{site.data.keyword.vsi_is_short}} are not compatible with the classic virtual server offerings. If you are interested in any of the classic virtual server offerings, see [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Before you begin, make sure that you [created an IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started) on Classic.
{:important}

## Step 1. Log in to your {{site.data.keyword.cloud_notm}} account
{: #vsi-for-vpc-log-in-gs}

Access the {{site.data.keyword.vsi_is_short}} Order Form from the [{{site.data.keyword.cloud_notm}} catalog](https://{DomainName}/catalog){: external}. Use your IBMid and password.

## Step 2. Generate an SSH key
{: #vsi-for-vpc-generate-ssh-key-gs}

1. Run the `ssh-keygen` command and follow the prompts. The command generates two files. The generated public key is in the `<your key>.pub` file.
2. After you generate an SSH key, you must add the key in {{site.data.keyword.cloud_notm}} console. In [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc){: external}, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > SSH keys**. Then, click **Add SSH key** and complete the required information.

## Step 3. Create a {{site.data.keyword.vsi_is_short}} instance
{: #vsi-for-vpc-create-instance-gs}

1. Navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. Click **New instance** and complete the required fields. For more information, see [Creating virtual server instances](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers).
 
## Step 4. Reserving a floating IP address
{: #vsi-for-vpc-reserve-floating-ip-gs} 

When your instance is running, you can associate a floating IP address to it so that you can connect to it from an internet location. The instance start-up process can take a few minutes.
 
1. On the **Virtual server instances** page, click your instance to view its details.
2. In the **Network interfaces** section, click **Reserve +** to associate a floating IP address to your instance. 

## Step 5. Connecting to your instance
{: #vsi-for-vpc-connect-to-instance-gs} 

To connect to your instance, use your private key and run the following command:

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   You receive a response similar to the following example. When prompted to continue connecting, type `yes`.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   You are now accessing your server!

## Next steps
After your instance is provisioned, explore your options.
* [Managing your instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [{{site.data.keyword.vsi_is_short}} permissions](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Security in your IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* More about [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
