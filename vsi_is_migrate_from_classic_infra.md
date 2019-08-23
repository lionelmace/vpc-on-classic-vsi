---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: migrate virtual server from classic infrastructure, migrate to vpc, migrate image template, image template, import image to vpc infrastructure, migrate virtual server, migrate instance

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

# Migrating a virtual server instance from the classic infrastructure
{: #migrate-vsi-from-classic-infra-to-vpc-on-classic}

You can migrate a vitual server instance from the classic infrastructure by creating an image template, exporting it to {{site.data.keyword.cos_full_notm}}, then importing it to {{site.data.keyword.vpc_short}} infrastructure so that it can be deployed. 
{:shortdesc}

1. In the {{site.data.keyword.cloud_notm}} classic infrastructure, locate an image template that was created from a virtual server that was provisioned with a [cloud-init enabled image](/docs/infrastructure/image-templates?topic=image-templates-provisioning-with-a-cloud-init-enabled-image). For more information about accessing image templates in the classic infrastructure, with either [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com/){: external} or [{{site.data.keyword.slportal}}](https://control.softlayer.com){: external} , see [Managing images](/docs/infrastructure/image-templates?topic=image-templates-managing-images-from-the-image-templates-page).
  
  The virtual server that the image template is created from must be provisioned without add-ons. (Add-ons include additional software, post-provisioning scripts, and advanced monitoring.) If needed, you can [create an image template](/docs/infrastructure/image-templates?topic=image-templates-creating-an-image-template) from a virtual server instance that was provisioned from a cloud-init enabled image. Make sure that you have completed any customization to the virtual server instance before creating the image template.
  {: note}
  
  Only image templates with a single primary boot volume (or disk) and associated file can be imported to {{site.data.keyword.vpc_short}} infrastructure. Secondary disks and their associated files for an image template are not supported.  
  {:important}
  
2. After locating your image template, you can [export it to {{site.data.keyword.cos_full_notm}}](/docs/infrastructure/image-templates?topic=image-templates-exporting-an-image-to-ibm-cloud-object-storage).  
3. Now you can [import](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-images#import-custom-image) your custom image.
