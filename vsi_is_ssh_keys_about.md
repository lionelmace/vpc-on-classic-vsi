---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-08"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:external: target="_blank" .external}

# SSH keys
{: #ssh-keys}
[comment]: # (linked help topic)

When you provision {{site.data.keyword.vsi_is_full}}, you must select an existing SSH key or add a new SSH key to use before you can create the instance. SSH keys are used by servers to identify a user or instance through public-key cryptography. SSH keys are made up of an alpha-numeric combination and are unique to the instance to which they are assigned. You can add, edit, or delete SSH keys by using the {{site.data.keyword.cloud_notm}} console.
{:shortdesc}

SSH keys allow access to an instance without using a password from corresponding clients for each public key that is implemented on the instance. By adding an SSH key to an instance, which you can do during provisioning, the instance can be accessed with the corresponding key instead of a password. You can add SSH keys to an instance only when you initially create the instance. After a Linux instance is created, you can edit keys directly in the `~/.ssh/` directory of the instance.

Logging in to your instance with a password isn't supported. If you have a Windows instance, the SSH key is used to decrypt your password. For more information, see [Connecting to your Windows instance](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-windows-instance). 
{:note}

## Locating or generating your SSH key
{: #locating-or-generating-your-ssh-key}

Before you can add a key in the {{site.data.keyword.cloud_notm}} console, you must have your SSH key available. To locate your SSH key or generate an SSH key, complete one of the following steps.

 * Locate an SSH key: Look for a file called `id_rsa.pub` under an `.ssh` directory under your home directory, for example, `/Users/<USERNAME>/.ssh/id_rsa.pub`. The file starts with `ssh-rsa` and ends with your email address.

* Generate an SSH key: If you do not have a public SSH key or if you forgot the password of an existing one, generate a new one by running the `ssh-keygen` command and following the prompts. For example, you can generate an SSH key on your Linux or Mac system by running the command `ssh-keygen -t rsa -C "user_ID"`. That command generates two files. The generated public key is in the `<your key>.pub` file. For Windows systems, you can use [PuTTYgen](https://www.ssh.com/ssh/putty/windows/puttygen){: external} to generate an SSH key.
  
  If you are using OpenSSH version 7.8 or higher and plan to use the SSH key to access a Windows instance, you must use the following command to generate the key in PEM format. `$ssh-keygen -m PEM -t rsa -f "user_ID"`
  {:important}
  
## Adding your SSH key
{: #adding-your-ssh-key}

After you locate or generate an SSH key, you must add the key in the {{site.data.keyword.cloud_notm}} console. For more information about adding, editing, or deleting SSH keys, see [Managing SSH keys](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-ssh-keys#managing-ssh-keys).

