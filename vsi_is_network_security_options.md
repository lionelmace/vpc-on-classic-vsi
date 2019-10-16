---

copyright:
  years: 2018, 2019
lastupdated: "2019-10-16"

keywords: virtual network interface card, vNIC, virtual private cloud, virtual server, instance, security, multiple IP addresses, security group, ACL, access control list

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Using instance vNICs
{: #network-security-options}

A virtual network interface card (vNIC) is used to connect a virtual server to a network. When you create a virtual server instance, you can use a vNIC to assign multiple IP addresses. 
{:shortdesc}

## Using instance vNICs
{: #using-instance-vnics}

The following list highlights how vNICs work with your instance.

* You can create and assign up to 5 vNICs to each instance. Each vNIC is assigned a private IP from the connected subnet and you can optionally attach a floating IP and security groups.
* You can attach each vNIC to a subnet in the same zone.
* Each vNIC receives a private IP from the subnet range.
* You can associate and unassociate floating IPs to and from each vNIC.
* You can assign security groups to each vNIC.
* You can change the name of any existing vNIC.

The profile that is selected when an instance is created determines the network performance cap for the instance, 1 - 16 Gbps. Bandwidth is distributed across the vNICs that are attached to the virtual server instance. For more information, see 
[Configuring virtual server settings for improved network performance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-configuring-network-performance).
