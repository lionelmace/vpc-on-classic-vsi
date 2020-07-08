---

copyright:
  years: 2018, 2019, 2020
lastupdated: "2020-07-08"

keywords: 

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
{:external: target="_blank" .external}

# Connecting to your Windows instance
{: #connecting-to-your-windows-instance}

After you have created your {{site.data.keyword.vsi_is_full}} Windows instance, you must decrypt your password so that you can connect to your instance.
{:shortdesc}

## Before you begin
{: #prereqs-connect-windows}

Make sure to complete the following prerequisites before you begin:

1. Ensure that you downloaded, installed, and initialized the following CLI plug-ins:
    * {{site.data.keyword.cloud_notm}} CLI
    * The vpc-infrastructure plug-in

   For more information, see [IBM Cloud CLI for VPC Reference](/docs/vpc-on-classic?topic=vpc-on-classic-vpc-reference).
   
   When you install the vpc-infrastructure plug-in for the first time, you must set the target generation to gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Ask your account administrator to grant you access to retrieve the password from your virtual server instance. For more information, review [user permissions](/docs/vpc-on-classic?topic=vpc-on-classic-managing-user-permissions-for-vpc-resources).
3. Create a new security group or add a rule to the default security group to enable inbound access for the Remote Desktop default port, 3389. For more information, see [Using security groups](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-using-security-groups).
4. Ensure that inbound traffic over TCP/IP port 3389 is permitted on the VPC's default ACL. For more information, see [Setting up Network ACLs](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-setting-up-network-acls).

## Getting connected
{: #getting-connected-windows}

After you create your Windows instance and complete the prerequisites, complete the following steps to connect to your Windows instance.

1. Query the status of your instance by running the following command:
  ```
  $ ibmcloud is instance <INSTANCE_ID>
  ```
  {:codeblock}
  
  When the instance shows that it's `running`, you are ready to retrieve the initialization values to get your password. 

2. Run the following [CLI command](/docs/vpc-on-classic?topic=vpc-on-classic-vpc-reference#instance-initialization-values) to initialize your instance and obtain your instance password:

  ```
  $ ibmcloud is instance-initialization-values INSTANCE [--private-key (KEY | @KEY_FILE)]
  ```
  {:codeblock}
  
  This command decodes and decrypts your password, which is automatically generated when you create an instance using a Windows image based on the public SSH Key you uploaded and the associated private SSH key file.

3. After you obtain your instance password, you can optionally associate a floating IP address to your Windows instance so you can connect to it from an internet location. Run the following command to associate a floating IP address to your instance:

  ```
  ibmcloud is floating-ip-reserve <FLOATING_IP_NAME> --nic-id <NIC_ID>
  ```
  {:codeblock}

4. You now have what you need in order to connect to your Windows instance: a decrypted password and a floating IP address. Use your preferred Remote Desktop client to connect to your instance. To connect to your instance, provide the floating IP address and the decrypted password. The username is `Administrator` by default. (If you are connecting from a client that is running the Windows Administrator account, use `.\Administrator` as the user ID to log on to RDP.)

In [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc){: external} on the **Instance Details** page of your virtual server instance, you can click **Download RDP file** to get a file with connection values pre-filled. You must add your decrypted password to connect. 
{: tip}

## Next steps
{: #next-manage-instances}

After you are connected to your instance, you can [manage your instances by using the {{site.data.keyword.cloud_notm}} console](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) or [manage your instances by using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
