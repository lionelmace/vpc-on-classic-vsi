---

copyright:
  years: 2018, 2020
lastupdated: "2020-03-09"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:faq: data-hd-content-type='faq'}

# FAQs
{: #faqs}
## How many servers can I start?
{: #concurrent}
{: faq}

An account has a limit of 20 instances that can run on public virtual servers, dedicated virtual servers, and bare metal servers, at any time.

## What regions are available?
{: faq}

You can create virtual server intances for {{site.data.keyword.vpc_full}} in Dallas (us-south), Frankfurt (eu-de), Tokyo (jp-tok), London (eu-gb), and Sydney (au-syd).

## Can I use existing virtual server instances from my classic infrastructure with an {{site.data.keyword.vpc_short}}?
{: faq}

No. It is currently not supported to move a virtual server from classic infrastructure to {{site.data.keyword.vpc_short}} infrastructure.

## Why doesn't my {{site.data.keyword.vsi_is_short}} instance appear in the Device List in {{site.data.keyword.slportal}}?
{: faq}

{{site.data.keyword.vsi_is_short}} instances appear only in {{site.data.keyword.cloud_notm}} console. For more information about managing {{site.data.keyword.vsi_is_short}}, see [Managing virtual server instances](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).


## What virtual server families are supported with {{site.data.keyword.vpc_short}}?
{: faq}

Currently, only public virtual servers in the balanced, memory, and compute families are supported. For more information, see [Profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).


## When I attempt to update my Ubuntu image with apt, I receive an error about the grub menu.lst file. How do I fix it?
{: #faq-ubuntu}
{: faq}
{: support}

Edit the file "`/boot/grub/menu.lst`" by changing `# groot=LABEL...` into `# groot=(hd0)`. Then, run following command, `sudo update-grub-legacy-ec2`. For more information, see [Error: groot must be grub root device on ubuntu](https://developer.ibm.com/answers/questions/462237/error-groot-must-be-grub-root-device-on-ubuntu/){: external}.

## How do I get support for my {{site.data.keyword.vsi_is_short}}?
{: #betasupport}
{: faq}

For more information about {{site.data.keyword.vpc_short}} support, see [Getting help and support](/docs/vpc-on-classic?topic=vpc-on-classic-getting-help-and-support).
