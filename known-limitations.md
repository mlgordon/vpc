---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-01-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Known Limitations

Known limitations may be changing as we add capabilities to {{site.data.keyword.cloud}} Virtual Private Cloud, so feel free to check back with this document from time to time. You'll find an overview at the beginning and a more detailed list near the end of the document.

## Overview 
This document contains short descriptions of known bugs in the current release, descriptions of features and APIs that are not supported, and indications of features in Beta test.

### Known Bugs

A known bug exists so that the metering server will not report usage for a VPC after it has been deleted. (#618)

### Summary of features not supported

* Access to existing {{site.data.keyword.cloud}} Infrastructure Classic resources such as bare metal or Direct Link (that is, there's no peering)
* IBM Cloud VPC Private Services Endpoints (phasing in)
* Saving and restoring images is not supported, currently.

### APIs not supported

For details about what's supported, see the [API Spec](https://{DomainName}/apidocs/rias).

The following APIs are not supported in this release.

| Component | Functions | Comments |
|------|------|--------|
| **Compute:** |   |   |
| Images | Create/Delete not supported | Ubuntu 16.04, CentOS 7.X, Windows 08, Debian|
| Network_Interfaces | Get (no create, delete, update) | Only one network interface per VSI supported |
| Volume_Interfaces | Not supported |   |
| Port_Speed | | Only 100,1000 |
| **Storage:** |   |   |
| Volumes | Not supported |   |
| Snapshots | Not supported |  |
| **Geo:** |   |   |
| Regions | Get | Only two regions |
| Zones | Get | Only three zones per region |

## Details of unsupported features and use cases

This section gives a detailed list of unsupported features and use cases. You might find this list useful when troubleshooting or for some specific questions that might arise.

### Features not yet supported

* A Virtual Private Cloud cannot be peered with other Virtual Private Clouds.

* A Virtual Private Cloud cannot be peered with the IBM Cloud Classic environment. Later, peering will enable the VPC resources to communicate IBM Cloud Classic resources, such as bare metal servers and IBM Cloud Direct Link service.

* You cannot migrate existing IBM Cloud VSI or bare-metal servers into their IBM Cloud VPC.

* You won't be able to set up custom routes in the IBM Cloud VPC. All the subnets in Virtual Private Cloud can communicate with each other by default.

* IBM Cloud VPC won't support multicast or broadcast domains.

* IBM Cloud VPC has nothing to do with the fast provisioning of the VSIs. It's handled by a different work stream.

* IBM Cloud VPC does not provide end-to-end encryption, but it supports it.

* Here are the core IBM Cloud services that customers of IBM Cloud VPC can use. Other services are not accessible. 
  * NTP
  * Logging
  * DNS resolvers. 

* A subnet cannot be on multiple zones.

* You cannot attach or detach a subnet to or from an availability zone (AZ).

* You cannot resize a subnet.

* You cannot provision a bare metal server in IBM Cloud VPC.

* IBM Cloud Classic resources cannot be in the same subnet in the IBM Cloud VPC.

* There's no support for IPv6, neither as bring your own private IP in VPC, nor as Public Floating IP.

* You may not use your own public IP as a Floating IP. The Floating IP pool is provided by IBM.

* A Floating IP is bound to a zone. For example, a Floating IP reserved from a pool in Zone 1 won't be assigned to a VSI in Zone 2 in the same VPC.

* You cannot move private IP addresses between VSIs.

* You cannot move a network interface between VSIs.

* You cannot designate the specific IP address of the VSI, only specify the IP range for the subnet. Once you attach a VSI to a subnet, the system assigns a private IP from that subnet.

* IBM Cloud VPC comes with its own Network as a Service tools such as LBaaS, ACLs, and security groups. You cannot use your own network appliances (for example, a Vyatta Gateway or other load balancer) to control any resource in the IBM Cloud VPC. Similalry, you cannot use your own load balancer or security groups services in IBM Cloud Classic Infrastructure to control their resources in the IBM Cloud VPC.

* The public gateway does not allow the traffic to be initiated from the Internet to a VSI in the IBM Cloud VPC. For that purpose, a Floating IP must be used.

* ACL is stateless, so return traffic must be allowed explicitly in ACL rules.

### Beta test notification

* VPN for IBM Cloud VPC is available only as an external Beta offering.

* LBaaS for IBM CLoud VPC is available only as an external Beta offering.
