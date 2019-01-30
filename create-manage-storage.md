---

copyright:
  years: 2017, 2018

lastupdated: "2018-12-13"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Creating and managing storage in VPC

Currently, your {{site.data.keyword.cloud}} Virtual Private Cloud allows boot storage volumes only.

When you provision a virtual server instance, a 100 GB block storage volume is created as a primary boot volume and attached to the instance, automatically. The boot volume provides 3 IOPS/GB performance and it exists during the VSI lifecycle. 

When you delete the instance, the boot volume is deleted.

## Best practices for creating and naming your VPC storage volumes:

* Ensure that you are naming ALL of your volumes at provision time, including the boot volume.
* Ensure that you are naming ALL of your volume attachments at attachment time
* Each volume must have a distinct name within a region within an account. 


