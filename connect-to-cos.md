---
copyright:
  years: 2018
lastupdated: "2018-08-28"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Connecting to IBM Cloud Object Storage from a VPC

This document tells how to connect to IBM® Cloud Object Storage from your Virtual Private Cloud.

## What is IBM Cloud Object Storage (COS)?

IBM Cloud Object Storage (COS) is a web-scale platform that stores unstructured data. It provides reliability, security, availability, and disaster recovery without manual replication.
Information stored within IBM Cloud Object Storage is encrypted and dispersed across multiple geographic locations. It is accessible through an implementation of the S3 API. This service makes use of the distributed storage technologies provided by the IBM Cloud Object Storage service.

IBM COS is available in three configurations: **Cross-Region**, **Regional** and **Single-Site**.
 * **Cross Region** service provides higher durability and availability than using a single region, but at the cost of slightly higher latency.
 * **Regional** service provides the reverse: It distributes objects across multiple availability zones within a single region. If a given region or availability zone is inaccessible, the object store continues to function smoothly. Any missed changes are applied when the inaccessible datacenter comes back online.
 * **Single Site** service offers affordable access to Cloud Object Storage in a selected datacenter.
 
### COS Private Endpoints for use with VPC

Endpoints are URLs that applications use to issue COS commands and exchange data with COS. Every endpoint uses the same Application Programming Interface (API) to interact with COS.
Servers provisioned within IBM Cloud use private API endpoints for services, including COS. Private endpoints provide customers' IBM Cloud servers with high-speed, direct connections to services with no added bandwidth costs.
 
## How to connect to IBM Cloud Object Storage (COS) from a VPC
 1. Provision COS from the [catalog ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window}.
 2. Create a COS bucket in one of the Regions listed in the following section.
 3. Use the Private Endpoint for VPC to create an interface with your COS bucket.
 
## U.S. Cross-region Endpoints
 
| **Region** | **Private Endpoint for VPC** |
|------------|-------------------------------|
| US Cross Region | `s3-api.us-geo.objectstorage.adn.networklayer.com` |
| Dallas Access Point | `s3-api.dal-us-geo.objectstorage.adn.networklayer.com`
| San Jose Access Point | `s3-api.sjc-us-geo.objectstorage.adn.networklayer.com`
| Washington, DC Access Point | `s3-api.wdc-us-geo.objectstorage.adn.networklayer.com` |
  
 ## U.S. Regional Endpoints
 
| **Region** | **Private Endpoint for VPC** |
|------------|-------------------------------|
| US South | `s3.us-south.objectstorage.adn.networklayer.com`|
| US East | `s3.us-east.objectstorage.adn.networklayer.com`|

 ## Single Datacenter Endpoints
 
| **Region** | **Private Endpoint for VPC** |
|------------|-------------------------------|
| Toronto, Canada | `s3.tor01.objectstorage.adn.networklayer.com` |
