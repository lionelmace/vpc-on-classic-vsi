---

copyright:
  years: 2019
lastupdated: "2019-10-30"

keywords: import custom image, custom image, deploy custom image, use custom image for virtual server, create custom image, custom Windows image, custom Linux image, provision instance with custom image

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}


# Importing and managing images
{: #managing-images}

You can import your own custom image to the {{site.data.keyword.vpc_short}} infrastructure. Then, you can use your custom image to create new generation 1 virtual server instances.
{:shortdesc}

## Before you begin
{: #prereq-custom-images}

To import a custom image to {{site.data.keyword.vpc_full}}, you must have an instance of {{site.data.keyword.cos_full_notm}} available. You must also create a bucket in {{site.data.keyword.cos_full_notm}} to store your images. Finally, you must create an authorization so that the Image Service for VPC can access images in {{site.data.keyword.cos_full_notm}}.

Make sure that your image meets custom image [requirements](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#custom-images). For more information, see [Creating a custom image](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-images#create-deployable-custom-image).
{: important}

### Creating an {{site.data.keyword.cos_full_notm}} service instance
{: #prereq-icos-instance}

1. If you need to create an instance of {{site.data.keyword.cos_full_notm}}, see [Getting started with {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started).
2. If you need to upload an image to {{site.data.keyword.cos_full_notm}}, navigate to your bucket and click **Add Objects** to 
[upload](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) the image. The bucket must be in the same region where you plan to import your image and create new instances. You can use the Aspera 
high-speed transfer plug-in to upload images larger than 200 MB.

### Granting access between services
{: #prereq-create-service-authorization}

From IBM {{site.data.keyword.iamshort}} you must create an authorization so that the Image Service for VPC can access images in {{site.data.keyword.cos_full_notm}}. 

1. From the [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc){: external} menu bar, click **Manage** &gt; **Access (IAM)**, and select **Authorizations**.
2. Click **Create**.
3. Select a source and target service for the authorization. Specify **VPC Infrastructure**  as the source service. Specify **Image Service for VPC** as the resource type. Specify **Cloud Object Storage**  as the target service.
4. Select a role to assign access to the source service that accesses the target service.
5. Click **Authorize**.

For more information, see [Using authorizations to grant access between services](/docs/iam?topic=iam-serviceauth#serviceauth).

## Creating a custom image 
{: #create-deployable-custom-image}

You can create your own custom image, either a Linux-based custom image or a Windows custom image, to deploy a generation 1 virtual server instance in the {{site.data.keyword.vpc_short}} infrastructure. Another option is to use an image template from the classic infrastructure to export to {{site.data.keyword.cos_full_notm}}. Then, you can import the image template as a custom image to the {{site.data.keyword.vpc_short}} infrastructure. 

To use a custom image from the classic infrastructure that can be deployed in the {{site.data.keyword.vpc_short}} infrastructure, see [Migrating a virtual server instance from the classic infrastructure](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-migrate-vsi-from-classic-infra-to-vpc-on-classic). 
{:tip}

### Creating a Linux custom image
{: #create-linux-custom-image}

Complete the following steps to ensure that your own Linux custom image can be successfully deployed in the {{site.data.keyword.vpc_short}} infrastructure environment.

1. Begin with a single image file in VHD format. 

2. Install the latest xe-guest-utilities Xen tools. Complete the following steps:
    1. Download the latest Citrix Hypervisor ISO (version 8.0 and later) from Citrix: [https://www.citrix.com/downloads/citrix-hypervisor/](https://www.citrix.com/downloads/citrix-hypervisor/){: external}.

    2. Mount the ISO by running the following command:

        ```
        mount -o loop xenserver.iso /mnt
        ```
        {: pre}

    3. Locate the RPM for the ISO by running the following command:

        ```
        ls -l /mnt/Packages/xenserver-pv*
        ```
        {: pre}

    4. The output lists an RPM similar to:

        ```
        xenserver-pv-tools-7.1.0-137222c.2185.noarch.rpm
        ```
        {: screen}

    5. You can copy the RPM and then extract the ISO for xentools. Run the following command to create a directory structure that houses the ISO:

        ```
        rpm2cpio <xenserver-pv-tools-7.1.0-137222c.2185.noarch.rpm> | cpio -idv
        ```
        {: pre}

    6. From the resulting directory structure, you can mount the *guest-tools* ISO and locate *rpm/debs* to install xentools. See the following example directory structure:

        ```
        [root@mysystem user1]# rpm2cpio ../xenserver-pv-tools-7.1.0-137222c.2185.noarch.rpm | cpio -idv
        ./opt/xensource/bin/sr_rescan
        ./opt/xensource/libexec/unmount_halted_xstools.sh
        ./opt/xensource/packages/iso/guest-tools-7.1.0-137222c.iso
        139264 blocks
        [root@mysystem user1]#
        ```
        {: pre}
        
3. Make sure that your image is cloud-init enabled. 

    * For more information about configuring images, see
[cloud-init documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloudinit.readthedocs.io/en/latest/).
    * For more information about datasources, see [Datasources ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://cloudinit.readthedocs.io/en/latest/topics/datasources.html). {{site.data.keyword.cloud_notm}} cloud-init images are created for the
environment by using the [Config Drive ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://cloudinit.readthedocs.io/en/latest/topics/datasources/configdrive.html) - Version 2 datasource to supply the metadata.
    * Linux images require Cloud-init version 0.7.7 or greater.
    
4. Upload your image to {{site.data.keyword.cos_full_notm}}. For more information about uploading to {{site.data.keyword.cos_full_notm}}, see [Upload data](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload).    
    
### Creating a Windows custom image
{: #create-windows-custom-image}

Complete the following steps to ensure that your own Windows custom image can be successfully deployed in the {{site.data.keyword.vpc_short}} infrastructure environment.

1. Begin with a single image file in VHD format. 

2. Install the latest xe-guest-utilities Xen tools. Complete the following steps:

    1. Download the latest Citrix Hypervisor ISO (version 8.0 and later) from Citrix: [https://www.citrix.com/downloads/citrix-hypervisor/](https://www.citrix.com/downloads/citrix-hypervisor/){: external}
.
    2. Mount the ISO by right-clicking the .iso file that you downloaded and selecting **Mount**.
    3. Navigate to the Windows Installer, for example, _managementagent64_, and double-click to open the **Citrix XenServer Windows Management Agent Setup** wizard. Complete the installation wizard to install XenServer Tools.

3. Make sure that your image is cloud-init enabled. 
    * For more information, see [cloudbase-init’s documentation](https://cloudbase-init.readthedocs.io/en/latest/index.html){: external}.
    * For more information about datasources, see [Datasources](http://cloudinit.readthedocs.io/en/latest/topics/datasources.html){: external}. {{site.data.keyword.cloud_notm}} cloud-init images are created for the
environment by using the [Config Drive](http://cloudinit.readthedocs.io/en/latest/topics/datasources/configdrive.html){: external} - Version 2 datasource to supply the metadata.

4. Windows images require the Cloudbase-init Metadata Service for public and private network support in {{site.data.keyword.vpc_short}} infrastructure. You can access the service at
[https://github.com/softlayer/bluemix-cloudbase-init](https://github.com/softlayer/bluemix-cloudbase-init){: external}.

5. Upload your image to {{site.data.keyword.cos_full_notm}}. For more information about uploading to {{site.data.keyword.cos_full_notm}}, see [Upload data](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload).

## Importing a custom image
{: #import-custom-image}

When you import a custom image, it's private to the account where you import it. Also, the region where you choose to import the image is the region where you can create virtual server instances from that image.  

When you have an image available in {{site.data.keyword.cos_full_notm}}, you can import it to {{site.data.keyword.vpc_short}} infrastructure by using the {{site.data.keyword.cloud_notm}} console.

When you import an image, the region where your {{site.data.keyword.cos_full_notm}} bucket is created and where your custom image is stored must be the same as the region where you are importing an image and creating new instances.
{: tip}

1. Make sure that your compatible custom image is available in {{site.data.keyword.cos_full_notm}}. For more information, see [Creating a custom image](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-images#create-deployable-custom-image) and [Uploading data](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) to {{site.data.keyword.cos_full_notm}}.
2. In [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc){: external}, 
navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Custom Images**.
3. Click **Import Custom Image**. 
4. Complete the required fields and click **Create Custom Image**.

## Managing custom images
{: #managing-custom images}

After you import custom images, you can deploy and manage them from the Custom images page. 

You can manage an image by using the {{site.data.keyword.cloud_notm}} console.
1. In [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc), 
navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Custom Images**.
2. From your list of custom images, you can click **...** and select from the available options. 
