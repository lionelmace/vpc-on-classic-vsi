---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Planning for instances
{: #planning-for-instances}
[comment]: # (linked help topic)


When you're planning to provision {{site.data.keyword.vsi_is_full}}, you might find this configuration checklist helpful to get the most out of your virtual server deployment.
{:shortdesc}

Before you get started, make sure you have [created an {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

## Planning for provisioning instances
{: #planning-for-provisioning-instances}

After you have an {{site.data.keyword.vpc_short}} available, consider the following before you provision your instance.

|        Considerations|
|-------------------|
|__ 1. Make sure your account has the required [user permissions](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions). If you have authorization as an editor or admin on an {{site.data.keyword.vpc_short}} resource, then you also inherit authorization to create, delete, and modify virtual server instances within that virtual private cloud.|
|__ 2. Check your [account limits](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) for concurrent instances. |
|__ 3. Make sure your [SSH key](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) is available.
|__ 4. Determine what instance location to select.|
|__ 5. Consider the popular [profile options](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) of vCPU and RAM combinations for your workload. Profiles contain preconfigured instances that are ready to use in a matter of minutes. It's important to ensure your instances will have the necessary resources to keep your workloads and your environment up and running.|
|__ 6. Determine what operating system image you'll select for your instance. You can choose among the current stock [images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images). |
|__ 7. Make sure you have a unique name for the instance. If you have a method to naming virtual server instances, it's much easier to filter and search on them later. |

## Next steps
{: #next-create-instance}

When you're ready to get started, see the following resources to create your instance:
* [Creating an instance using the {{site.data.keyword.cloud_notm}} console](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Creating an instance using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
