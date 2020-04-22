---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Managing virtual server instances (CLI)
{: #managing-virtual-servers-cli}

You can view and manage your {{site.data.keyword.vsi_is_full}} instances by using the command line interface (CLI). Perform tasks such as start, stop, restart, and delete virtual server instances. 
{:shortdesc}

## Before you begin
{: #prereq-managing-instances}

1. Ensure you have downloaded, installed, and initialized the following CLI plug-ins:
    * {{site.data.keyword.cloud_notm}} CLI
    * The infrastructure-service plugin

   For more information, see [IBM Cloud CLI for VPC Reference](/docs/vpc-on-classic?topic=vpc-on-classic-vpc-reference).
   
   When you install the vpc-infrastructure plugin for the first time, you must set the target generation to gen 1, `ibmcloud is target --gen 1`.
   {:important}
   
2. Make sure you have already [created an {{site.data.keyword.vpc_short}}](/docs/vpc-on-classic?topic=vpc-on-classic-getting-started).

## Viewing instance actions
{: #viewing-instance-actions}

To view the management actions that are performed on your instance, run the following command:

```
ibmcloud is instance-actions <server-ID>
```
{:codeblock}

You will see a list similar to the following output:

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## Managing your instances
{: #managing-your-instances}

Need a little help? Run the `ibmcloud is help` command to view commands at anytime.

### Reset  

```
ibmcloud is instance-reset
```
{:codeblock}

The instance is powered off and then powered on.  

### Restart

```
ibmcloud is instance-reboot
```
{:codeblock}

The operating system of the instance is restarted.  

### Stop and start

```
ibmcloud is instance-stop or ibmcloud is instance-start
```
{:codeblock}

If the device has been stopped, the device remains in the stopped state and must be manually started. You cannot interact with an instance if it is stopped. If the device is started, normal interaction continues. 

### Update

```
ibmcloud is instance-update
```
{:codeblock}

After renaming the device, the name is automatically updated. When performing a search, use the new instance name when attempting to locate content associated with it. 

### Delete

```
ibmcloud is instance-delete
```
{:codeblock}

After confirming the delete action, the process to delete the instance and its associated vNIC, boot volume, and data begins. The delete action can take several minutes, but when the process is complete, the instance no longer appears on the Virtual server instances page. The floating IP address that is associated to the virtual server instance is unassociated, but remains on your account.

If you prefer to manage instances by using the {{site.data.keyword.cloud}} console, see [Managing an instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances).
{: tip}
