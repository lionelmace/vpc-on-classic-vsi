---

copyright:
  years: 2019
lastupdated: "2019-07-23"

keywords: 

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:external: target="_blank" .external}

# Creating virtual server instances with customer-managed encryption
{: #creating-instances-byok}

You can create {{site.data.keyword.vsi_is_full}} that use customer-managed encryption for block storage volumes when you have a key management service provisioned that includes your own data encryption key. By default instances are provisioned with a boot volume that includes provider-managed encryption. You can provision instances that use customer-managed encryption for the block storage volumes from {{site.data.keyword.cloud_notm}} console or by using the command line interface (CLI).
{:shortdesc}

## Supported key management services for customer-managed encryption
{: #kms-for-byok}

You can use the key management service that works best for your needs. {{site.data.keyword.keymanagementserviceshort}} and {{site.data.keyword.hscrypto}} (available in certain [regions](/docs/services/hs-crypto?topic=hs-crypto-regions#regions)) use a common key provider API to provide a consistent approach for managing encryption keys.  Behind the scenes, {{site.data.keyword.cloud_notm}} data centers provide a dedicated hardware security module (HSM) to protect your keys.  The following key management services are supported by customer-managed encryption for block storage volumes: 

| Key Management Service | HSM Encryption Certification |
| ----- | ----- |
| [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/concepts?topic=key-protect-getting-started-tutorial#getting-started-tutorial) | FIPS 140-2 *Level 3* compliance |
| [{{site.data.keyword.hscrypto}}](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) | FIPS 140-2 *Level 4* compliance |
{: caption="Table 1. Available key management service options" caption-side="top"}

## Prerequisites
{: #byok-vsi-prereqs}

To create a virtual server instance that uses customer-managed encryption for the block storage volumes, you must have a key management service that is provisioned and a customer root key added. You must also authorize access between Cloud Block Storage and the key management service. When these prerequisites are complete, you can start creating instances that use customer-managed encryption for the block storage volumes. 

The following example steps are specific to {{site.data.keyword.keymanagementserviceshort}}, but the general flow also applies to {{site.data.keyword.hscrypto}}. If you're using {{site.data.keyword.hscrypto}}, see the [{{site.data.keyword.hscrypto}} information](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) for corresponding instructions.
{:note}

1. Provision the [{{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-provision#provision) service. 
   
   Provisioning a new {{site.data.keyword.keymanagementserviceshort}} service instance ensures that it includes the most recent updates that are required for customer managed encryption of block storage volumes. 
   {: tip}
   
2. [Create](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) or 
[import](/docs/services/key-protect?topic=key-protect-import-root-keys#import-root-keys) a root key (CRK) in 
{{site.data.keyword.keymanagementservicelong_notm}}.
3. From IBM {{site.data.keyword.iamshort}} (IAM), [authorize access](/docs/iam?topic=iam-serviceauth#serviceauth) between **Cloud 
Block Storage** (source service) and **{{site.data.keyword.keymanagementserviceshort}}** (target service).

## Provisioning virtual server instances with volumes that use customer-managed encryption
{: #provision-byok-ui}

When you provision a virtual server instance, you can specify customer-managed encryption for your boot volume and any data volumes that you want to add at provision time. If you want, you can use a combination of provider-managed encryption and customer-managed encryption for the volumes that are associated with your instance.

1. In [{{site.data.keyword.cloud_notm}} console](https://console.cloud.ibm.com/vpc){: external}, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > Virtual server instances**. Click **New instance** and complete the required fields. (For more information about creating instances, see [Creating virtual server instances](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers#creating-virtual-servers).) 
2. In the **Boot volume** section, the default mode of encryption is _Provider managed_ encryption. To specify customer-managed encryption, click the pencil icon in the boot volume row. On the **Edit boot volume** page, update the fields in the **Encryption** section. See the following table for more information. When your changes are complete, click **Apply**.
3. In the **Attached block storage volume** section, you can click **New block storage volume** to add a data volume and specify customer-managed encryption if you choose. On the **New block storage volume** page, update the fields in the **Encryption** section. See the following table for more information. When your changes are complete, click **Attach**.

| Field | Value |
| ----- | ----- |
| Encryption | _Provider managed_ is the default encryption mode. To use customer-managed encryption, select a key management service from the drop-down list. The key management service instance must include the customer root key that you want to use for customer-managed encryption. |
| Encryption service instance | If you have multiple key management service instances that are provisioned in your account, select the one that includes the customer root key that you want to use for customer-managed encryption. |
| Key name | Select the data encryption key within the key management service instance that you want to use for encrypting the volume. | 
| Key ID | Displays the key ID that is associated with the data encryption key that you selected. | 
{: caption="Table 1. Values for specifying customer-managed encryption of volumes" caption-side="top"}

## Using the CLI to provision instances and volumes with customer-managed encryption
{: #provision-byok-cli}

To use the CLI to create a virtual server instance with volumes that use customer-managed encryption, you can use the `ibmcloud is instance-create` command and reference a JSON to attach volumes that use customer-managed encryption. 

1. Obtain the CRN of the root key in your desired key management service instance. The following example is specific to {{site.data.keyword.keymanagementserviceshort}}. 
    
    1. If you need to install the {{site.data.keyword.keymanagementserviceshort}} CLI plug-in, run the following command: 
       ```
       ibmcloud plugin install key-protect -r 'IBM Cloud'
       ```
       {: pre}
    
    2. List the {{site.data.keyword.keymanagementserviceshort}} service instances for your account by running the following command:
       ```
       ibmcloud resource service-instances
       ```
       {: pre}
    
       For this example, you'd see a response similar to the following output:
       ```
       Retrieving all instances of all services in resource group Default and all locations
       under account MyCompany as myuserid@mycompany.com...
       OK
       Name             Location   State    Type   
       Key Protect-17   us-south   active   service_instance
       Key Protect-60   us-south   active   service_instance
       ```
       {:screen}
         
    3. Retrieve the instance ID for the {{site.data.keyword.keymanagementserviceshort}} service instance where your customer root keys are stored by running the following command.  
       ```
       ibmcloud resource service-instance "Key Protect-17" --id
       ```
       {: pre}
    
       where _Key Protect-17_ is your desired {{site.data.keyword.keymanagementserviceshort}} service instance.
    
       For this example, you'd see a response similar to the following output:
       ```
       Retrieving service instance Key Protect-17 in resource group Default under account 
       MyCompany as myuserid@mycompany.com...
       crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-
       ixxx-3jkl4xxxx567::7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7  
       ```
       {:screen}
       
       where the instance ID is the string that follows the final `::` in the CRN, `7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7`. 
    
    4. List the available keys and their associated CRNs within your desired {{site.data.keyword.keymanagementserviceshort}} service instance by running the following command:
       ```
       ibmcloud kp list -c --instance-id 7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7
       ```
       {: pre}
       
       where _7mnxxxo8-91xx-23px-q4rs-xxtuv5w6xxx7_ is the instance ID of your desired {{site.data.keyword.keymanagementserviceshort}} service instance.
       
       For this example, you'd see a response similar to the following output:
       ```
       Retrieving keys...
              
       SUCCESS
               
       Key ID                                 Key Name               CRN   
       ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   test-key               crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:ef1gxxxh-ijxx-234x-56k7-xxxxlmnoxxp8   
       cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   vsi_encrypt_root_key   crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12   
       c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   vsi_encrypt_key        crn:v1:bluemix:public:
       kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:
       key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h   
       ```
       {:screen}
       
2. Use the [ibmcloud is instance-create](/docs/vpc-on-classic?topic=vpc-on-classic-vpc-reference#instance-create) command and attach the necessary JSON files that specify customer-managed encryption for the boot volume and any secondary data volumes that you want to include. The `encryption_key` parameter must include a valid CRN for the root key in the Key Protect service. See the following [JSON file examples](#vsi-vol-attachment-json) of a boot volume JSON and secondary volume JSON. (For more information about creating instances, see [Creating virtual server instances (CLI)](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-creating-virtual-servers-cli).)

## Creating a volume attachment in JSON format
{: #vsi-vol-attachment-json}

When you create either a boot volume or data volume during VSI provisioning, you must specify a JSON file to define the volume parameters. See the following JSON file examples.

### Example boot volume JSON file
{: #boot-volume-byok-json}

The following example defines a general-purpose boot volume and specifies the `encryption key` parameter for customer-managed encryption.

```
{  
   "name":"volume-attachment-1",
   "volume":{  
      "name":"volume-1",
      "capacity":100,
      "profile":{  
         "name":"general-purpose"
      },
      "encryption_key":{  
         "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
         xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:cdex12ef-xxxg-3hxx-i456-7xxx8jk9xl12"
      }
   },
   "delete_volume_on_instance_delete":true
}
```
{:codeblock}

### Example secondary volume JSON file
{: #secondary-volume-byok-json}

The following example defines a general-purpose secondary (data) volume and specifies the `encryption key` parameter for customer-managed encryption.

```
[  
   {  
      "name":"volume-attachment-2",
      "volume":{  
         "name":"volume-2",
         "capacity":200,
         "profile":{  
            "name":"general-purpose"
         },
         "encryption_key":{  
            "crn":"crn:v1:bluemix:public:kms:us-south:a/abxx1c2xxxx34x567xxdex891xxx23fx:
            xxx4g5xx-6789-x1h2-ixxx-3jkl4xxxx567:key:c12xxxx3-45d6-7efg-xxx8-9xxx12345x6h"
         }
      }
   }
]
```
{:codeblock}

