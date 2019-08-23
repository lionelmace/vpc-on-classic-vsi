---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-23"

keywords: IBM Cloud Virtual Private Cloud, popular profile options, necessary resources, planning, virtual servers

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

After you have an {{site.data.keyword.vpc_short}} available, use the following information to start planning, creating, and connecting to your instances.

<table>
   <CAPTION>Table 1. Quick start steps</CAPTION>
   <THEAD>
   <TR>
   <th>Task</th>
   <th>Details</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Log in to your IBM Cloud account</td>
   <td>Access the {{site.data.keyword.vsi_is_short}} Order Form from the <a href="https://console.bluemix.net/catalog/">IBM Cloud catalog</a>. You will need an <a href="docs/account?topic=account-signup">IBMid and password</a>.
   </td>
   </tr>
   <tr>
   <td>2. Verify your account has the required user permissions</td>
   <td>For more information, see <a href="/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions">user permissions</a>. If you have authorization as an editor or admin on an IBM Cloud VPC resource, then you also inherit authorization to create, delete, and modify virtual server instances within that virtual private cloud.</td>
   </tr>
   <tr>
   <td>3. Determine your workload specifications</td>
   <td>Before you create your instance, determine how it will be used and the instance size you need to be successful. For example, do you intend to use it for development and testing, or production? Are you testing a user experience, processing lengthy algorithms, backing up and restoring data, or increasing latency speed?</td>
   </tr>
   <tr>
   <td>4. Size and price your instance</td>
   <td>You have three family options when it comes to creating your instances: Balanced, Compute, and Memory. The families contain pre-configured vCPU and RAM combinations, called Profiles. Profiles meet the needs of most workloads and can be ready to configure in as little as 5 minutes. It's important to ensure your instances will have the necessary resources to keep your workloads and your environment up and running.
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Balanced</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Compute</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Memory</a></li>
     </ul>
  <p>Use the <a href="/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc">pricing</a> information to help you size and price your instance.</p></td>
   </tr>
   <tr>
   <td>5. Generate an SSH key</td>
   <td> For instructions, see <a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys">SSH keys</a>.</td>
   </tr>
   <tr>
   <td>6. Planning for your instance</td>
   <td><ul><li>Check your <a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-faqs#faqs">account limits</a> for concurrent instances.</li>
  <li>Determine what instance location to select.</li>
  <li>Determine what operating system image you'll select for your instance. You can choose among the current stock <a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-images#images">images</a>.</li>
  <li>Make sure you have a unique name for the instance. If you have a method to naming virtual server instances, it's much easier to filter and search on them later.</li>
   </ul>
   </td>
   </tr>
   <tr>
   <td>7. Creating your instance</td>
   <td>To start creating an instance, see <a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers">Creating a virtual server instance</a>.</td>
   </tr>
   <tr>
   <td>8. Connecting to your instance</td>
   <td>Your instance is now ready! See the following topics under <b>Connecting</b> to verify the instance was successfully created.
    <p>
    <ul>
   <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance">Connecting to your Linux instance</a></li>
   <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance">Connecting to your Windows instance</a></li>
   </ul>
   </p>  
   </td>
   </tr>
   <tr>
   <td>9. Cleaning up your instance</td>
   <td>When you no longer need your instance, you can delete it. </td>
   </tr>
   </TBODY>
   </table>
