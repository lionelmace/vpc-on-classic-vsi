---

copyright:
  years: 2018, 2019
lastupdated: "2019-10-09"

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
5. Verify that you have OpenSSL installed. To successfully decrypt your password, you must run OpenSSL and not LibreSSL. For more information, see [OpenSSL Downloads ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.openssl.org/source/){: new_window}.

LibreSSL isn't compatible for the decryption of your password. You must run OpenSSL to decrypt your password.
{:important}

## Getting connected
{: #getting-connected-windows}

After you create your Windows instance and complete the prerequisites, complete the following steps to connect to your Windows instance.

1. Query the status of your instance by running the following command:
  ```
  $ ibmcloud is instance <INSTANCE_ID>
  ```
  {:codeblock}
  
  When the instance shows that it's `running`, you are ready to retrieve the initialization values to get your password. 

2. Run the following command to initialize your instance:

  ```
  $ ibmcloud is instance-initialization-values <INSTANCE_ID>
  ```
  {:codeblock}
  
  This command displays your encrypted password, which is automatically generated when you create an instance by using a Windows image.

3. You now need to decrypt your password through a manual decryption process. To decrypt your password, run the following command:

  ```
  # Decode the encrypted password
  cat ~/examplepwd | base64 --decode > ~/examplepwd64
  # Decrypt the decoded password using the RSA private key
  openssl pkeyutl -in ~/examplepwd64 -decrypt -inkey private.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256
  -pkeyopt rsa_mgf1_md:sha256
  ```
  {:codeblock}
  
  where `~/examplepwd` is the file where you saved your encrypted password as referenced in step 2.  
  
  LibreSSL, which is included with macOS, doesn't support SHA2 hashing algorithms that are needed to decrypt the password, resulting in `Public Key operation error` errors. You can obtain standard OpenSSL libraries by using a package management tool or by installing them manually. 
  {:note}

4. After you decrypt your password, you can optionally associate a floating IP address to your Windows instance so you can connect to it from an internet location. Run the following command to associate a floating IP address to your instance:

  ```
  ibmcloud is floating-ip-reserve <FLOATING_IP_NAME> --nic-id <NIC_ID>
  ```
  {:codeblock}

5. You now have what you need in order to connect to your Windows instance: decrypted password and floating IP address. Use your preferred Remote Desktop client to connect to your instance. To connect to your instance, provide the floating IP address and the decrypted password. The username is `Administrator` by default. (If you are connecting from a client that is running the Windows Administrator account, use `.\Administrator` as the user ID to log on to RDP.)

In [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc){: external} on the **Instance Details** page of your virtual server instance, you can click **Download RDP file** to get a file with connection values pre-filled. You must add your decrypted password to connect. 
{: tip}

## Next steps
{: #next-manage-instances}

After you are connected to your instance, you can [manage your instances by using the {{site.data.keyword.cloud_notm}} console](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) or [manage your instances by using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli). 
