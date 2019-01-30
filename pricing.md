---

copyright:
  years: 2017, 2018

lastupdated: "2018-12-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Pricing for VPC

The table summarizes the pricing for internet data transfer with {{site.data.keyword.cloud}} Virtual Private Cloud. Remember that there is no charge for traffic between VPC and Classic IBM Cloud services. Also, for PayGo services, the service tiers are bound to your account, not to any specific VPC instance. Amounts are shown in U.S. dollars.

Separate pricing applies for [virtual server instances](vpc-vsi-pricing.md) used within your IBM Cloud VPC.

## Free allowances for internet data transfer

| Data transfer |  Cost for all IBM Cloud VPC Customers |
|---------------|------------------|
| Within the zone | Free |
| Between zones in the same region | Free |
| Use of public gateway | Free (Charged only for the floating IP used by the PGW) |

## Floating IP pricing

A floating IP is charged at the rate of $1 (U.S.) per month, starting when it is reserved. The fee is charged even if the floating IP is not associated to a VSI or not in use. The $1 for the monthly fee is charged even if the floating IP is reserved for only a few days.


## Basic PayGo pricing for internet data transfer

| Data transfer | Amount of data | PayGo pricing |
|-----------|-----------|------------------|
| Egress to Internet |  0 to 5 GB | Free |
|  | 6 to 10,000 GB | $0.087 per GB |
|  | 10,001 to 50,000 GB | $0.83 per GB |
|  | 50,001 to 150,000 GB | $0.07 per GB |
|  | 150,001 GB and over | $0.05 per GB |


When you create a new VPC, it may take up to an hour for initial billing charges to appear in the Console UI or API.
{: tip}
