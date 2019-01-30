---

copyright:
  years: 2017, 2018, 2019

lastupdated: "2019-01-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Assigning role-based access to VPC resources

Account Administrators can utilize authorization _policies_, which control access to _resources_ based on an individual user's _role_. Policies also can be applied for:

(1) the authorization of a group of users, called an _access group_,

(2) on the assigned characteristics of a single _resource_, or

(3) on a collection of resources called a _resource group_.

The authorizations for resources and the authorizations for users can be assigned independently of each other.

For more information about creating users, user access groups, resource groups, and policies, please refer to [About resources](about-resources.html).

## IAM-based access control

In general, the {{site.data.keyword.cloud}} Virtual Private Cloud authorization and resource management practices coordinate with the IBM Cloud Identity and Access Management (IAM) services. For more information about IAM, resource groups, and access groups in general, please refer to these IBM Cloud documents:

* [IBM Cloud IAM](/docs/developing/get-coding/policy_examples.html#iam_policy_examples)
* [Resource Groups](/docs/overview/resource-groups.html#whatis)
* [Access Groups](/docs/overview/manageaccess.html#cloudaccess)

Certain features of the IBM Cloud IAM Service have been customized for use in IBM Cloud VPC. The [About resources](about-resources.html) document explains more about IAM authorization policies as they are applied in VPC.

To summarize, you can assign IAM-based authorizations based on:

* individual users
* access groups (groups of users)
* specific types of resources
* resource groups

## Assigning user permissions

For users, access is controlled by assigning system-defined IAM roles:

* Administrator
* Editor
* Operator
* Viewer

Here's a table that shows the correspondence between each user role and the type of control it allows for VPCs:

| Role Name | Type of Access Allowed |
|-----------|-------------------------|
| Viewer | View VPC, List VPCs  |
| Editor | View VPC, List VPCs, Create VPCs, Delete VPCs, Update VPCs |
| Operator  | View VPC, List VPCs |
| Administrator |View VPC, List VPCs, Create VPCs, Delete VPCs, Update VPCs, Assign policies to other users |


## Next steps

For step by step instructions on granting role-based permissions to users for certain tasks, please refer to our [Managing User Permissions for VPC Resources](vpc-user-permissions.html) topic.
