---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-09"

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

# Profiles
{: #profiles}

When you provision {{site.data.keyword.vsi_is_full}}, you can select from three families of profiles: Balanced, Compute, and Memory. A profile is a combination of vCPU and RAM that can be instantiated quickly to start a virtual server instance. In the {{site.data.keyword.Bluemix_notm}} console, you can choose from popular profile configurations or select from a list of profiles that best fit your needs.
{: shortdesc}

The following families are available:

| Families | Description |
| -------- | ----------- |
| [Balanced](#balanced) | Best for common cloud workloads that require a balance of performance and scalability. The balanced profiles (with network-attached storage) provide higher performance, since resources are not oversubscribed. |
| [Compute](#compute)  | Best for moderate to high web traffic workloads. Compute profiles are best for workloads with intensive CPU demands, such as high web traffic workloads, production batch processing, and front-end web servers. |
| [Memory](#memory) | Best for memory caching and real-time analytics workloads. Memory profiles are best for memory intensive workloads, such as large caching workloads, intensive database applications, or in-memory analytics workloads. |
{: caption="Table 1. Virtual server family selections" caption-side="top"}

## Balanced
{: #balanced}

The balanced profiles provide higher performance, since resources are not oversubscribed. Network performance ranges from standard to premium.

The offering is available in the following profiles:

| Profile | vCPU | RAM | Network Performance Cap (Gbps) |
|---------|---------|---------|---------|
| bc1-2x8 | 2 | 8 | 1 |
| bc1-4x16 | 4 | 16 | 2 |
| bc1-8x32 | 8 | 32 | 4 |
| bc1-16x64 | 16 | 64 | 8 |
| bc1-32x128 | 32  | 128 | 12 |
| bc1-48x192 | 48 | 192 | 16 |
| bc1-62x248 | 62 | 248 | 16 |
{: caption="Table 2. Virtual server balanced profile options" caption-side="top"}

All supported operating systems (such as CentOS, Debian, Red Hat Enterprise Linux, Ubuntu, and Windows) are available with this offering. For more information about storage, see [Storage notes for profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#storage-notes-for-profiles). For more information about network performance, see [Network performance notes for profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#network-perf-notes-for-profiles).


## Compute
{: #compute}

Compute profiles are best for workloads with intensive CPU demands, such as high web traffic workloads, production batch processing, and 
front-end web servers.

The offering is available in the following profiles:

| Profile | vCPU | RAM | Network Performance Cap (Gbps) |
|---------|---------|---------|---------|
| cc1-2x4 | 2 | 4 | 1 |
| cc1-4x8 | 4 | 8 | 2 |
| cc1-8x16 | 8 | 16 | 4 |
| cc1-16x32 | 16 | 32 | 8 |
| cc1-32x64 | 32  | 64 | 12 |
{: caption="Table 3. Virtual server instance compute profile options" caption-side="top"}

All supported operating systems (such as CentOS, Debian, Red Hat Enterprise Linux, Ubuntu, and Windows) are available with this offering. For more information about storage, see [Storage notes for profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#storage-notes-for-profiles). For more information about network performance, see [Network performance notes for profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#network-perf-notes-for-profiles).

## Memory 
{: #memory}

Memory profiles are best for memory intensive workloads, such as large caching workloads, intensive database applications, or in-memory 
analytics workloads.

The offering is available in the following profiles:

| Profile | vCPU | RAM | Network Performance Cap (Gbps) |
|---------|---------|---------|---------|
| mc1-2x16 | 2 | 16 | 1 |
| mc1-4x32 | 4 | 32 | 2 |
| mc1-8x64 | 8 | 64 | 4 |
| mc1-16x128 | 16 | 128 | 8 |
| mc1-32x256 | 32 | 256 | 12 |
{: caption="Table 4. Virtual server instance memory profile options" caption-side="top"}

All supported operating systems (such as CentOS, Debian, Red Hat Enterprise Linux, Ubuntu, and Windows) are available with this offering. For more information about storage, see [Storage notes for profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#storage-notes-for-profiles). For more information about network performance, see [Network performance notes for profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#network-perf-notes-for-profiles).

## Storage notes for profiles
{: #storage-notes-for-profiles}

* A SAN primary boot volume (100 GB) is automatically created and attached when you provision an instance.
* Optionally, create a secondary data volume. Volume profiles are available as three predefined IOPS tiers or as custom IOPS. 
    * A [3 IOPS general-purpose tier profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) provides IOPS/GB performance suitable for a virtual server instance Balanced profile.
    * A [5-IOPS tier](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) profile provides IOPS/GB performance suitable for a virtual server instance Compute profile.
    * A [10-IOPS tier](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) profile provides IOPS/GB performance suitable for a virtual server instance Memory profile.
* Pricing for public virtual servers that use SAN storage includes virtual CPU, memory, and primary boot volume. Secondary data volumes are priced separately.

## Network performance notes for profiles
{: #network-perf-notes-for-profiles}

Network performance is distributed across the virtual network interface cards (vNICs) that are attached to the virtual server instance. For example, if you provision a virtual server instance with a 62 vCPU profile that has a network performance cap of 16 Gbps and 4 vNICs attached, each vNIC is capped at 4 Gbps. The network performance distribution setting across vNICs cannot be modified.

The network performance cap applies for both egress (upload) and ingress (download) traffic. For example, if you have a 62 vCPU profile the network performance cap is 16 Gbps egress and 16 Gbps ingress. 

The network performance cap is not a guaranteed performance throughput statement, but an "up-to" performance statement. 

When you select a profile that has a network performance cap that is higher than 5 Gbps, you must enable Jumbo Frames in the networking configuration of your virtual server instance. Changing the network configuration of your virtual server instance  ensures that you can achieve network throughput at speeds greater than 5 Gbps. 
{:important}

If you select a profile that indicates network performance greater than 5 Gbps, complete the following steps for your operating system to enable Jumbo Frames. 

### Configuring jumbo frames for Debian and Ubuntu
{: #jumbo-frames-debian-ubuntu}

To increase the maximum transmission unit (MTU) to support ethernet jumbo frames if you are running Debian or Ubuntu, complete the following steps:

1. Check the current setting by running the command, `- ifconfig| grep -i MTU`.
2. Change the current setting to support 9000 MTU by running the command, `ifconfig eth0 mtu 9000`.
3. Change the setting to persist after the system is rebooted. Edit the file `/etc/network/interfaces`, and add `MTU=9000`.

### Configuring jumbo frames for CentOS and Red Hat Enterprise Linux
{: #jumbo-frames-centos-rhel}

To increase the maximum transmission unit (MTU) to support ethernet jumbo frames if you are running CentOS or Red Hat Enterprise Linux, complete the following steps:

1. Check the current setting by running the command, `ip link show dev eth0`
2. Change the current setting to support 9000 MTU by running the command, `ip link set mtu 9000 dev eth0`.
3. Change the setting to persist after the system is rebooted. Edit the file `/etc/sysconfig/network-scripts/ifcfg-eth0`,  and add `MTU=9000`.

### Configuring jumbo frames for Windows
{: #jumbo-frames-windows}

To increase the maximum transmission unit (MTU) to support ethernet jumbo frames if you are running Windows, complete the following steps:

1. Check the current setting by running the command, `netsh interface ipv4 show interfaces`
2. Change the current setting to support 9000 MTU by running the command, `netsh interface ipv4 set subinterface “12”  mtu=9000 store=persistent`.

## Viewing profile configurations
{: #popularprofiles}

You can view available profile configurations by using the {{site.data.keyword.cloud_notm}} console or the CLI. In the {{site.data.keyword.cloud_notm}} console, you can select from popular profile configurations that support most common use cases.

### Using the IBM Cloud console
1. In the {{site.data.keyword.cloud_notm}} console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. From the Virtual server instances for VPC page, click **New instance**.
3. You can either select a profile configuration from **Popular profiles** or click **All profiles** to view more configurations.

### Using the CLI
To view the list of available profiles by using the CLI, run the following command:
```
$ ibmcloud is instance-profiles
```
{:codeblock}

When you use the command line, the following information describes what the output represents. The profile sizes have different ratios of CPU to memory, which are designed for different workloads:

*  "b" is balanced, which is a 1:4 ratio
*  "c" is compute (higher on the CPUs), which is a 1:2 ratio
*  “m” is memory (higher on the memory), which is a 1:8 ratio
