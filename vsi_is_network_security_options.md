---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-23"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Networking and security on virtual servers
{: #network-security-options}

When implementing {{site.data.keyword.vsi_is_full}}, you have access to the latest features for networking and security.  
{:shortdesc}

## Using instance vNICs
{: #using-instance-vnics}

A virtual network interface card (vNIC) is used to connect a virtual server to a network. When you create a virtual server instance, you can use a vNIC to assign multiple IP addresses. The following list highlights how vNICs work with your instance.

* You can create and assign up to 5 vNICs to each instance. Each vNIC will be assigned a private IP from the connected subnet and you can optionally attach a floating IP and security groups.
* You can attach each vNIC to a subnet in the same zone.
* Each vNIC receives a private IP from the subnet range.
* You can associate and unassociate floating IPs to and from each vNIC.
* You can assign security groups to each vNIC.
* You can change the name of any existing vNIC.

The profile that's selected when an instance is created determines the network performance cap for the instance, from 1 Gbps to 16 Gbps. Bandwidth is distributed across the vNICs that are attached to the virtual server instance. 

## Networking options
{: #networking-options}

For more information about overall networking features in the {{site.data.keyword.vpc_short}} environment, see [About Networking for VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-about-networking-for-vpc).

## Security options
{: #security-options}

{{site.data.keyword.vsi_is_short}} includes built-in security options:
* Access Control Lists (ACLs) can limit traffic to and from a subnet.
* Security groups function as a virtual firewall for virtual server instances.
* SSH keys on your virtual server instance authenticate a secure channel for network communication.

For more information about these security options, see [Security in your IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc) and [Managing SSH keys](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).
