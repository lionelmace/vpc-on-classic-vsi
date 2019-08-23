---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: view instance details, virtual server instance, restart virtual server, stop virtual server, instance details, delete virtual server, delete instance

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Managing virtual server instances
{: #managing-virtual-server-instances}
[comment]: # (linked help topic)

You can view and manage your {{site.data.keyword.vsi_is_full}} instances from the *Virtual server instances* page in {{site.data.keyword.cloud_notm}} console.
{:shortdesc}

To manage your instances, complete the following steps.
1. In [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.cloud.ibm.com/vpc), navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**.
2. From here, you can manage tasks for a specific instance, or click an instance to view and edit its properties.

## Reboot

The reboot action immediately powers off an instance and then powers it back on again.

## Stop and start

The stop and start action remotely turns an instance off or on. If the instance is stopped, the instance remains in the stopped state and must be started manually. Billing is [suspended](/docs/vpc-on-classic?topic=vpc-on-classic-pricing-for-virtual-servers-for-vpc#suspend-billing) for some compute resources while the instance is stopped. You cannot interact with an instance if it is stopped. If the device is started, normal interaction continues.

## Delete

The delete action permanently removes an instance and its connected vNIC, boot volume, and data from your account. After you confirm the delete action, the process to delete the instance and its associated vNIC, boot volume, and data begins. The delete action can take up to 30  minutes, but when the process is complete, the instance no longer appears on the Virtual server instances page. The floating IP address that is associated to the virtual server instance is unassociated, but remains on your account.

## Viewing instance details
You can interact with instances by viewing the summary of all instances on the *Virtual server instances* page, or by clicking an individual instance to view details and make changes. From the instance details page, you can also view the associated network interface, access its subnet, and reserve or delete a floating IP address.

If you prefer to manage your instances by using the CLI, see [Managing an instance using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
{: tip}
