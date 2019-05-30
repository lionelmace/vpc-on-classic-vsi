---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: IBM Cloud VPC, virtual private cloud, virtual servers 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# About Virtual Servers for VPC
{: #virtual-private-cloud}

{{site.data.keyword.vsi_is_full}} give you access to all of the benefits of {{site.data.keyword.vpc_short}}, including network isolation, security, and flexibility. 
{:shortdesc}

## What is {{site.data.keyword.vpc_short}}?
An {{site.data.keyword.vpc_short}} is a virtual network that is tied to your customer account. It offers you a cost-effective entry point that provides cloud security and the ability to scale dynamically with growth. It gives you fine-grained control over your virtual infrastructure and your network traffic segmentation.
{: shortdesc}

For more information about {{site.data.keyword.vpc_short}}, see [About IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-about).

## What are {{site.data.keyword.vsi_is_short}}?
With {{site.data.keyword.vsi_is_short}}, you can create an instance that consists of your virtual compute resources and resulting capacity within an {{site.data.keyword.vpc_short}}. When you provision an instance, you select an instance profile that matches the amount of memory and compute power that you need for the application or software that you plan to run on the instance. After you provision an instance, you control and manage those infrastructure resources. Each account has a limit on the number of running instances across servers. For more information about this limit, see [FAQs](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs). 

## How are virtual server instances for {{site.data.keyword.vpc_short}} different from other IBM virtual server offerings?

In today's IBM Cloud Virtual Server offering, instances use native subnet and VLAN networking to communicate to each other within a data center (and single pod). Using subnet and VLAN networking in one pod works well until you must scale up or have large virtual resource demands that require resources to be created between pods. (Adding appliances for VLAN spanning can get expensive and complicated!) 

{{site.data.keyword.vpc_short}} adds a network orchestration layer that eliminates the pod boundary, creating infinite capacity for scaling instances. The network orchestration layer handles all of the networking for all virtual server instances that are within an {{site.data.keyword.vpc_short}} across regions and zones. With the software defined networking capabilities that {{site.data.keyword.vpc_short}} provides, you have more options for [VPNs](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---beta-using-vpn-with-your-vpc), [LBaaS](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---beta-using-load-balancers-in-ibm-cloud-vpc), multi-vNIC instances, and larger [subnet](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets#ibm-cloud-vpc-and-subnets) sizes. For more information, see [About Networking for VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc). 

{{site.data.keyword.vsi_is_short}} also have the following features that provide a simpler user experience and cost savings:
* New {{site.data.keyword.cloud_notm}} console
* New Virtual Private Cloud regional API and CLI
* New billing model with sustained usage discount tiers, as described in [Pricing](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc)

{{site.data.keyword.vsi_is_short}} are not compatible with the classic virtual server offerings. If you are interested in any of the  {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} offerings on the classic infrastructure, see [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers#getting-started-with-virtual-servers).
{:note}




