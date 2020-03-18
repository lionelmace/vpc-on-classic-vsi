---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-07"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Troubleshooting your Virtual Servers for VPC
{: #troubleshooting-your-virtual-servers-for-vpc}
If you experience difficulties with your {{site.data.keyword.vsi_is_full}} instances, review the following possible causes.

## Error: 409 Conflict when creating an instance action
{: #tbs-1}

You can't create certain instance actions if the status of your instance is in conflict with another action. For example, if your instance status is `stopped`, and you try to create a `reboot` action, the system returns a 409 error.

| Status      | Action     | Conflict |
| ----------- | ---------- | -------- |
| Running     | start      | yes      |
| Stopped     | not start  | yes      |
| Not running | reboot     | yes      |

## Instance's status stuck in `deleting` status
{: #tbs-2}

When you list instances and find the status of an instance stuck in `deleting` status, use the show instance api `/instances/{instance_id}` to update the instance status for your specific virtual server instance. The lastest status might not display when using the list api `/instances` to display all instances.
