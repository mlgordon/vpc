---

copyright:
  years: 2017, 2018, 2019

lastupdated: "2019-03-03"

keywords: resource, storage, boot, block, volume, name, naming, best practices

subcollection: vpc


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:download: .download}

# Creating and managing storage in VPC
{: #creating-and-managing-storage-in-vpc}

Currently, your {{site.data.keyword.cloud}} Virtual Private Cloud allows boot storage volumes and additional block storage volumes.

## Boot volume

When you provision a virtual server instance, a 100 GB block storage volume is created as a primary boot volume and attached to the instance, automatically. The boot volume provides 3 IOPS/GB performance and it exists during the VSI lifecycle. 

When you delete the instance, the boot volume is deleted.

## Block storage volumes

For more information about working with block storage volumes, see our [Block Storage for VPC documentation](/docs/infrastructure/block-storage-is?topic=block-storage-is-block-storage-getting-started).


## Best practices for creating and naming your VPC storage volumes:

* Ensure that you are naming ALL of your volumes at provision time, including the boot volume.
* Ensure that you are naming ALL of your volume attachments at attachment time
* Each volume must have a distinct name within a region within an account. 

You can re-use the name of a volume after that volume has been deleted. However, be aware that re-using a volume name could cause confusion for billing purposes.
{:note}
