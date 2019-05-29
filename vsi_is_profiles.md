---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

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

| Profile | vCPU | RAM |
|---------|---------|---------|
| bc1-2x8 | 2 | 8 |
| bc1-4x16 | 4 | 16 |
| bc1-8x32 | 8 | 32 |
| bc1-16x64 | 16 | 64 |
| bc1-32x128 | 32  | 128 |
| bc1-48x192 | 48 | 192 |
| bc1-62x248 | 62 | 248 |
{: caption="Table 2. Virtual server balanced profile options" caption-side="top"}

**Storage Notes:**

* SAN primary boot volume (100GB) is automatically created and attached when you provision an instance.
* Optionally, create a secondary data volume. Volume profiles are available as three predefined IOPS tiers or as custom IOPS. A [3 IOPS general-purpose tier profile](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) provides IOPS/GB performance suitable for a VSI Balanced profile.
* Pricing for public virtual servers using SAN storage includes virtual CPU, memory, and primary boot volume. Secondary data volumes are priced separately.

All supported operating systems (such as CentOS, Debian, Ubuntu, and Windows) are available with this offering.

## Compute
{: #compute}

Compute profiles are best for workloads with intensive CPU demands, such as high web traffic workloads, production batch processing, and 
front-end web servers.

The offering is available in the following profiles:

| Profile | vCPU | RAM |
|---------|---------|---------|
| cc1-2x4 | 2 | 4 |
| cc1-4x8 | 4 | 8 | 
| cc1-8x16 | 8 | 16 |
| cc1-16x32 | 16 | 32 |
| cc1-32x64 | 32  | 64 |
{: caption="Table 3. Virtual server instance compute profile options" caption-side="top"}

**Storage Notes:** 

* SAN primary boot volume (100GB) is automatically created and attached when you provision an instance.
* Optionally, create a secondary data volume. Volume profiles are available as three predefined IOPS tiers or as custom IOPS. A [5-IOPS tier](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) profile provides IOPS/GB performance suitable for a VSI Compute profile.
* Pricing for public virtual servers using SAN storage includes virtual CPU, memory, and primary boot volume. Secondary data volumes are priced separately.

All supported operating systems (such as CentOS, Debian, Ubuntu, and Windows) are available with this offering. 

## Memory 
{: #memory}

Memory profiles are best for memory intensive workloads, such as large caching workloads, intensive database applications, or in-memory 
analytics workloads.

The offering is available in the following profiles:

| Profile | vCPU | RAM |
|---------|---------|---------|
| mc1-2x16 | 2 | 16 |
| mc1-4x32 | 4 | 32 |
| mc1-8x64 | 8 | 64 |
| mc1-16x128 | 16 | 128 |
| mc1-32x256 | 32 | 256 |
{: caption="Table 4. Virtual server instance memory profile options" caption-side="top"}

**Storage Notes:** 

* SAN primary boot volume (100GB) is automatically created and attached when you provision an instance.
* Optionally, create a secondary data volume. Volume profiles are available as three predefined IOPS tiers or as custom IOPS. A [10-IOPS tier](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-block-storage-profiles#tiers) profile provides IOPS/GB performance suitable for a VSI Memory profile.
* Pricing for public virtual servers using SAN storage includes virtual CPU, memory, and primary boot volume. Secondary data volumes are priced separately.

All supported operating systems (such as CentOS, Debian, Ubuntu, and Windows) are available with this offering. 

## Viewing profile configurations
{: #popularprofiles}

You can view available profile configurations using the {{site.data.keyword.cloud_notm}} console or the CLI. In the {{site.data.keyword.cloud_notm}} console, you can select from popular profile configurations that support most common use cases.

### Using the IBM Cloud console
1. In the {{site.data.keyword.cloud_notm}} console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. From this page, click **New instance**.
3. You can either select a profile configuration from **Popular profiles** or click **All profiles** to view additional configurations.

### Using the CLI
To view the list of available profiles using the CLI, run the following command:
```
$ ibmcloud is instance-profiles
```
{:codeblock}

When using the command line, the following information describes what the output represents. The profile sizes have different ratios of CPU to memory, designed for different workloads:

*  "b" is balanced, which is a 1:2 or 1:4 ratio
*  "c" is compute (higher on the CPUs) , which is a 1:1 ratio
*  “m” is memory (higher on the memory), which is a 1:8 ratio
