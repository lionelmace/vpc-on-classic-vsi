---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-16"

keywords: user data, virtual private cloud, virtual server, instance, configuration task, script

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# User data
{: #user-data}
[comment]: # (linked help topic)

When you create an {{site.data.keyword.vsi_is_full}} instance, you can add user data that automatically performs common configuration tasks or runs scripts. In the **User Data** field on the order form, you can enter optional cloud-init user data for the server.
{:shortdesc}

## User data examples for Linux 
{: #user-data-examples-for-linux}

The following example shows how a Linux user can add a new user and provide the user with an authorized SSH key. The **Name** field will have the public key added to `~/.ssh/authorized_keys`. 

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

Here's another example of a shell script that shows how a Linux user can add an SSH key for the current user.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}

You can paste one of these examples directly into the **User Data** field. The user data is then available to the virtual server instance during provisioning. 

For more Linux user data examples and information, see [Cloud config examples ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloudinit.readthedocs.io/en/18.5/topics/examples.html){:new_window}.

## User data example for Windows
{: #user-data-example-for-windows}

The following example shows how user data can be passed to a Windows instance. You can copy and paste this example directly into the **User Data** field.

```
#ps1_sysnative
Set-Content -Path "C:\\test.txt" -Value "Hello IBM Cloud Instance"
```
{:codeblock}

For more Windows user data examples and information, see [Cloudbase-init 1.0 documentation ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloudbase-init.readthedocs.io/en/latest/userdata.html){:new_window}.
