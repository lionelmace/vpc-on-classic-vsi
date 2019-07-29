---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: virtual servers, {{site.data.keyword.vsi_is_short}}, virtual private cloud

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}

# Getting started with IBM Cloud Virtual Servers for VPC
{: #getting-started}

Use {{site.data.keyword.vsi_is_full}} (VPC) to provision scalable compute resources in the IBM Cloud.
{:shortdesc}

You can create as many virtual servers as you need, configure network and security, and manage storage. All of this is available in an improved IBM Cloud console. The console is built to provide you with quick and easy access to adjust your environment with your changing workload demands. Bet you're anxious to get started, so let's get straight to business.

Before you begin, make sure you have [created an IBM Cloud VPC](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).
{:important}

{{site.data.keyword.vsi_is_short}} are not compatible with the classic virtual server offerings. If you are interested in any of the  {{site.data.keyword.cloud_notm}} {{site.data.keyword.BluVirtServers_short}} offerings on the classic infrastructure, see [IBM Cloud Virtual Servers](/docs/vsi?topic=virtual-servers-getting-started-tutorial).
{:note}

<p>Use the following information to start creating and connecting to your instances quickly.
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
   <td>1. Review content that can help with your implementation</td>
   <td>New to IBM Cloud and virtual servers? The following sites provide useful information to help you plan your environment.
      <ul>
      <li><a href="https://ibm.com/cloud-computing/">What is IBM Cloud</a></li>
      <li><a href="https://ibm.com/cloud/get-started">Getting started with IBM Cloud</a></li>
      <!-- <li><a href="https://www.ibm.com/cloud/virtual-servers">Virtual Servers</a></li> -->
      </ul>
      <!-- (Reviewers: This link will go to VSI for VPC section of marketing page when we have the URL) -->
   </td>
 <tr>
   <td>2. Sign up for IBM Cloud</td>
   <td>For information on how to set up your IBM Cloud account, see <a href="/docs/account?topic=account-signup#signup">Signing up for IBM Cloud</a>.</td>
 <tr>
   <td>3. Determine your workload specifications</td>
   <td>Before you create your instance, determine how it will be used and the instance size you need to be successful. For example, do you intend to use it for development and testing, or production? Are you testing a user experience, processing lengthy algorithms, backing up and restoring data, or increasing latency speed?</td>  
 <tr>
   <td>4. Size and price your instance</td>
   <td>You have three family options when it comes to creating your instances: Balanced, Compute, and Memory. The families contain pre-configured instances, called Profiles, that meet the needs of most customers and can be ready to configure in as little as 5 minutes.  
     <ul>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-balanced#balanced">Balanced</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-compute#compute">Compute</a></li>
     <li><a href="/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-memory#memory">Memory</a></li>
     </ul>
  <p>Use the [Pricing](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc) information to help you size and price your instance.</p></td>
 <tr>
   <td>5. Log in to your IBM Cloud account</td>
   <td>Access the {{site.data.keyword.vsi_is_short}} Order Form from the <a href="https://console.bluemix.net/catalog/">IBM Cloud catalog</a>. You will need an <a href="/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBMid and password</a>.
   </td>
 <tr>
   <td>6. Request access to the {{site.data.keyword.vpc_short}} experience</td>
   <td>If you have not requested access already, request access to {{site.data.keyword.vpc_short}}.</td>
<tr>
<td>7. Generate an SSH key</td>
<td> For instructions, see [SSH keys](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).</td>
<tr>
<td>8. Planning for your instance</td>
<td> For more information to help you plan for, provision, and configure your resources successfully, see [Planning for instances](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-planning-for-instances#planning-for-instances).</td>
<tr>
<td>9. Creating your instance</td>
<td>
<p>
To start creating an instance, see [Creating an instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).
</td>  
<tr>
<td>10. Connecting to your instance</td>
<td>Your instance is now ready! See the following topics under *Connecting* to verify the instance was successfully created.
   <ul>
   <li>[Connecting to your Linux instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#connecting-to-your-linux-instance)</li>
   <li>[Connecting to your Windows instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance#connecting-to-your-windows-instance)</li>
   </ul>
</td>
</td>
<tr>
<td>11. Cleaning up your instance</td>
<td>When you no longer need your instance, you can delete it. </td>
</tr>
</TBODY>
</table>
</p>

## Next steps
After your instance is provisioned, explore your options.
* [Managing your instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances)
* [{{site.data.keyword.vsi_is_short}} permissions](/docs/vpc-on-classic?topic=vpc-on-classic-about-vpc-infrastructure-resources#planning-virtual-servers-for-vpc-permissions)
* [Security in your IBM Cloud VPC](/docs/vpc-on-classic-network?topic=vpc-on-classic-network-security-in-your-ibm-cloud-vpc)
* More about [IBM Cloud Virtual Private Cloud](/docs/vpc-on-classic?topic=vpc-on-classic-about)
