---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-23"

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
|__ 2. Determine your workload specifications. Before you create your instance, determine how it will be used and the instance size you need to be successful. For example, do you intend to use it for development and testing, or production? Are you testing a user experience, processing lengthy algorithms, backing up and restoring data, or increasing latency speed?|
|__ 3. Check your [account limits](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs) for concurrent instances. |
|__ 4. Make sure your [SSH key](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys) is available.
|__ 5. Determine what instance location to select.|
|__ 6. Consider the popular [profile options](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles) of vCPU and RAM combinations for your workload. Profiles contain preconfigured instances that are ready to use in a matter of minutes. It's important to ensure your instances will have the necessary resources to keep your workloads and your environment up and running.|
|__ 7. Use the [Pricing](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-vpc#pricing-for-virtual-servers-for-vpc) information to help you size and price your instance.|
|__ 8. Determine what operating system image you'll select for your instance. You can choose among the current stock [images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images). |
|__ 9. Make sure you have a unique name for the instance. If you have a method to naming virtual server instances, it's much easier to filter and search on them later. |

## Next steps
{: #next-create-instance}

When you're ready to get started, see the following resources to create your instance:
* [Creating an instance using the {{site.data.keyword.cloud_notm}} console](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers)
* [Creating an instance using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli)
