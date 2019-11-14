---

copyright:
  years: 2018, 2019
lastupdated: "2019-10-15"

keywords: virtual server instances, virtual private cloud, create virtual server, provision virtual server, virtual machine, instance, virtual server, deploy virtual server

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Creating virtual server instances
{: #creating-virtual-servers}
[comment]: # (linked help topic)

You can create {{site.data.keyword.vsi_is_full}} from the *Virtual server instances* page in {{site.data.keyword.cloud_notm}} console. Use this information when you're creating generation 1 virtual server instances. 
{:shortdesc}

Before you get started, make sure that you [created an IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

To create an instance, select the following instance details.
1. In [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.cloud.ibm.com/vpc), navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. Click **New instance** and enter the following information:

    <table>
    <CAPTION>Table 1. Instance provisioning selections</CAPTION>
    <THEAD>
    <TR>
    <th>Field</th>
    <th>Value</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Name </td>
    <td>A name is required for your virtual server instance.</td>
    </tr>
    <tr>
    <td>Virtual private cloud</td>
    <td>Specify the IBM Cloud VPC where you want to create your instance.</td>
    </tr>
    <tr>
    <td>Location</td>
    <td>Locations are composed of regions (specific geographic areas) and zones (fault tolerant data centers within a region). Select the location where you want your virtual server instance to be created.</td>
    </tr>
    <tr>
    <td>Image</td>
    <td><p>All images are cloud-init enabled. With cloud-init enabled images, you can associate user metadata with the instance through post provisioning scripts.</p>
    <p>For more information, see [Images](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images).</p>
    </td>
    </tr>
    <tr>
    <td>Profile</td>
    <td><p>
    Select from popular profiles or all available vCPU and RAM combinations. The following families are supported:
    <ul>
    <li>Balanced</li>
    <li>Compute</li>
    <li>Memory</li>
    </ul>
    </p>
    <p>Each physical core on the server is hyper-threaded and presented as two virtual CPUs (vCPUs). The virtual server offering provides 2.0 GHz or better per vCPU with up to 48 vCPU available on a single virtual server.</p>

    <p>For memory, an instance can have up to 256 GB of fully dedicated RAM.</p>
    <p><note>Note: Maximum values vary by family.</note></p>
    <p>For more information, see [Profiles](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-profiles#profiles).</p>
    </td>
    </tr>
    <td>SSH Key</td>
    <td>
    <p>You must select an existing SSH key or upload a new SSH key to use before you can create the instance. SSH keys are used to securely connect to the instance after it's running. You can add SSH keys to your instance only when you initially create the instance.</p>
    <p>Note: Alpha-numeric combinations are limited to 100 characters.</p>
    <p>For more information, see [SSH keys](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</p></td>
    </tr>
    <tr>
    <td>User data</td>
    <td>
    <p>You can add user data that automatically completes common configuration tasks or runs scripts. <p>For more information, see [User data](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data).</p>
    </td>
    </tr>
    <tr>
    <td>Boot volume</td>
    <td><p>The default boot volume size for all profiles is 100 GB. By default the boot volume includes provider-managed encryption. If you want to use customer-managed encryption, you can edit the details of the boot volume. For more information, see [Storage](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-storage#storage).</p>
    </td>
    </tr>
    <tr>
    <td>Attached block storage volume</td>
    <td><p>You can add one or more secondary data volumes to be included when you provision the instance. To add volumes, click **New block storage volume**. For more information, see [Creating block storage volumes](/docs/vpc-on-classic-block-storage?topic=vpc-on-classic-block-storage-creating-block-storage).</p>
    </td>
    </tr>
    <tr>
    <td>Network interfaces</td>
    <td>Assign networking options to connect into the IBM Cloud VPC. You can create and assign up to five network interface cards to each instance. For more information, see [Multiple IP addresses](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-network-security-options#network-security-options).</td>
    </tr>
    </TBODY>
    </table>

    Your *Cost summary* displays on the right side of the *New virtual server instance* page.

3. Click **Create virtual server instance** when you are ready to provision. A series of emails is sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message that states the instance is created.

Do you prefer to create an instance using the CLI? For more information, see [Creating an instance using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli#creating-virtual-servers-cli).
{: tip}

## Reserving a floating IP address
{: #reserving-a-floating-ip-address}

You can reserve and associate a floating IP address to your instance so you can connect to it from an internet location.

Your instance must be running before you can associate a floating IP address. It can take a few minutes for the instance to be up and running.
{: note} 

To reserve and associate a floating IP address, complete the following steps.
1. On the **Virtual server instances** page, click your instance to view its details.
2. In the **Network interfaces** section, click **Reserve +** to associate a floating IP address to your instance.

## Next steps
{: #next-connecting-to-instance}

You are ready to connect to your instance. For more information, see [Connecting to your Linux instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance) or [Connecting to your Windows instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance).
