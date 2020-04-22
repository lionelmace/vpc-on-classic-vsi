---

copyright:
  years: 2019
lastupdated: "2019-09-16"

keywords: 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:important: .important}

# Configuring virtual server settings for improved network performance
{: #configuring-network-performance}

The network performance cap for your virtual server is determined by the profile that you select when you create the virtual 
server instance. If you select a profile that has a network performance cap that is higher than 5 Gbps, you must enable Jumbo 
Frames in the networking configuration to achieve the higher network throughput.
{: shortdesc}

Network performance is distributed across the virtual network interface cards (vNICs) that are attached to the virtual server 
instance. For example, if you provision a virtual server instance with a 62 vCPU profile that has a network performance cap of 
16 Gbps and 4 vNICs attached, each vNIC is capped at 4 Gbps. The network performance distribution setting across vNICs cannot 
be modified.

The network performance cap applies for both egress (upload) and ingress (download) traffic. For example, if you have a 62 
vCPU profile the network performance cap is 16 Gbps egress and 16 Gbps ingress. 

The network performance cap is not a guaranteed performance throughput statement, but an "up-to" performance statement. For more 
information about the network performance cap for profiles, see [Profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles).

When you select a profile that has a network performance cap that is higher than 5 Gbps, you must enable Jumbo Frames in the networking configuration of your virtual server instance. Changing the network configuration of your virtual server instance ensures that you can achieve network throughput at speeds greater than 5 Gbps.  
{:important}

In addition to configuring jumbo frames, you can also use multiple TCP connections to help achieve higher network performance on your workloads. Support for multiple TCP connections is application-dependent, so you can refer to your application documentation to determine whether you can use multiple TCP connections.

If you select a profile that indicates network performance greater than 5 Gbps, complete the following steps for your 
operating system to enable Jumbo Frames. 

## Configuring jumbo frames for Debian and Ubuntu
{: #jumbo-frames-debian-ubuntu}

To increase the maximum transmission unit (MTU) to support ethernet jumbo frames if you are running Debian or Ubuntu, complete the following steps:

1. Check the current setting by running the command, `- ifconfig| grep -i MTU`.
2. Change the current setting to support 9000 MTU by running the command, `ifconfig eth0 mtu 9000`.
3. Change the setting to persist after the system is rebooted. Edit the file `/etc/network/interfaces`, and add `MTU=9000`.

## Configuring jumbo frames for CentOS and Red Hat Enterprise Linux
{: #jumbo-frames-centos-rhel}

To increase the maximum transmission unit (MTU) to support ethernet jumbo frames if you are running CentOS or Red Hat Enterprise Linux, complete the following steps:

1. Check the current setting by running the command, `ip link show dev eth0`
2. Change the current setting to support 9000 MTU by running the command, `ip link set mtu 9000 dev eth0`.
3. Change the setting to persist after the system is rebooted. Edit the file `/etc/sysconfig/network-scripts/ifcfg-eth0`,  and add `MTU=9000`.

## Configuring jumbo frames for Windows
{: #jumbo-frames-windows}

To increase the maximum transmission unit (MTU) to support ethernet jumbo frames if you are running Windows, complete the following steps:

1. Check the current setting by running the command, `netsh interface ipv4 show interfaces`
2. Change the current setting to support 9000 MTU by running the command, `netsh interface ipv4 set subinterface “12”  mtu=9000 store=persistent`.
