---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-01-15"

---
# Quotas

This document covers quotas and limits for your {{site.data.keyword.cloud}} Virtual Private Cloud and the resources available within it.

## VPC quotas

Accounts have the following quotas:

|   Resource     | Maximum Number |
| ------- | :------: |
| Virtual Private Clouds | 5 per account|
| Subnets | 15 per Virtual Private Cloud |
| Virtual Server Instances (VSIs) | 100 per account by default |
| Floating IP addresses | 1 per VSI |


## Security groups quotas

Some account-based quotas (limits) exist for security groups and their associated rules.

|Resource|Quota|
|--------|-----|
|Security groups per network interface|5|
|Security groups per account|500|
|Rules per security group|50|
|Remote rules per security group|5|
|Network interfaces per security group|100|

## ACL quotas

|Resource|Quota|
|--------|-----|
|ACLs per account | 30 |
|ACLs per region |200|
|Ingress rules per ACL |20|
|Egress rules per ACL |20|

## VPN quotas

Here are the current VPN resource limitations per account:

|Resource|Quota|
|--------|-----|
| VPN gateways | Maximum 7 |
| VPN connections per VPN gateway | Maximum 10 |
| peer subnets across VPN connections on a given VPN gateway | Maximum 50 |
| peer subnets on a given VPN connection | Maximum 15 |
| local subnets across VPN connections on a given VPN gateway | Maximum 50 |
| local subnets on a given VPN connection |  Maximum 15 |
| IKE policies | Maximum 20  |
| IPSec policies | *Maximum 20 |

## Load Balancer quotas

Here are the current load balancer resource quotas:

|Resource|Quota|
|--------|-----|
| Load Balancer | 3 per account |
| Listener | 10 per Load Balancer |
| Pool | 10 per Load Balancer |
| Member | 50 per Pool |

## Key pair quotas

A maximum of 100 key pairs across all regions is allowed.
