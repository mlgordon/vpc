---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Troubleshooting your IBM Cloud VPC

This document covers common difficulties you might encounter, and offers some helpful tips.

## Turning on `TRACE` mode

You can use the {{site.data.keyword.cloud}} `TRACE` options to turn on `TRACE` mode, by entering any of the following commands:

 * `IBMCLOUD_TRACE=true`
 * `IS_TRACE=true`
 * `BLUEMIX_TRACE=true`

## Using DEBUG mode or `verbose` mode 

When you're having trouble diagnosing a difficulty, you can use the CLI to get into DEBUG mode, by giving the TRACE command before any other call you make to the IBM Cloud CLI. For example, for the command `ibmcloud is pubgws` you'd write:

```
IBMCLOUD_TRACE=true ibmcloud is pubgws
```

The debug information is helpful to you and also to the support team who may be called upon to diagnose your problem.

**Another option is to use verbose mode**

For example, you can add `--verbose` to your `curl` command and send us the `x-request-id:` value so we can troubleshoot the problem. The `--verbose` flag is particularly helpful if you are experiencing connectivity problems.

**Another option is to add the `-i` flag to your `curl` command** so that the support team can see the headers in the response of your request. This flag is helpful in most situations when you need to contact support. Here's an example of what you might see when you use the `-i`flag:

```
curl -i https://${credentials}@rias.wrig.me:5000/v1/vpcs/0ba0c6f1-705a-4e37-9e26-0f2d7e505329 -H X-Auth-Token:$iam_token -H X-Subject-Token:$subject_token
HTTP/2 200
server: nginx/1.13.5
date: Fri, 25 May 2018 14:45:31 GMT
content-type: application/json; charset=utf-8
content-length: 246
x-request-id: 98a977bd-020b-422b-beb5-0843ab500c41
strict-transport-security: max-age=15724800; includeSubDomains;

{"id":"0ba0c6f1-705a-4e37-9e26-0f2d7e505329","crn":"","name":"VPC-a-late-making-modified","href":"https://rias.wrig.me:5000/v1/vpcs/0ba0c6f1-705a-4e37-9e26-0f2d7e505329","status":"available","is_default":false,"created_at":"2018-04-25T03:30:28Z"}
```

### If Trace ID is blank

Usually, when the Trace ID is blank, it is because the JSON returned does not match what is expected from the Swagger. Try `IBMCLOUD_TRACE=true ibmcloud is server-rm 3fb7c1eb-45fd-4c85-962e-617f216e7393` (substitute your correct server ID token) and check the output.


 ## Other Issues

Here are a few difficulties you might encounter:

### Not on the Whitelist

If this is your problem, you'll see a 401 or 403 error. Contact your support team.

### Permissions not set up in IBM Cloud Infrastructure (SoftLayer)

Before you can create Virtual Servers, you need the correct permissions to be set up on the IBM Cloud Infrastructure (SoftLayer) side. If your permissions are not correct, you can create a server and it will show `Pending` status, which quickly turns into `Failed` status. Make sure the master of the account assigns you the correct [permissions](vpc-user-permissions.html).

### Servers are all in Unknown status

Most likely you do not have adequate permissions to view the server status. Make sure you have the correct [permissions](vpc-user-permissions.html). It also could be caused by an expired IMS token. Run `bx sl init` again and rebuild the `ims_subject` with the new token. Make sure you are passing in the `X-Subject-Token:$ims_subject` parameter in the request header.

### IAM token expired

**Problem:** Service is no longer returning any JSON, instead of just giving an HTTP 403 status to all of my requests.  My earlier requests were going through. What happened?

**Answer:** This error will happen after about an hour if your IAM token has expired. Refresh your IAM token by re-running `iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $4; }')`.

### Different instance ID is returned

**Problem:** I post a request to create an instance, and the returned instance ID is `bce0c60d-20ef-42d1-b282-4eabd0c7bdd6`. Then I get the instance, but the instance ID is changed to `2409a6ac-518c-47ff-ac51-ee8783e98f9a`.

**Answer:** Now RIAS compute supports two kinds of ID: `RIAS UUID` and `GUID(softlayer globalIdentifier)`. When you create a server, it returns the `RIAS UUID`. After the instance receives the GUID from Softlayer, RIAS compute updates the instance ID to `GUID`. You can use either  `RIAS UUID`  or `GUID` to manage the instance.

### Error: 409 Conflict when creating an instance action

You can't create certain instance actions if the status of your instance is in conflict with another action. For example, if your instance status is `stopped`, and you try to create a `reboot` action, the system returns a 409 error.

| status      | action     | conflict |
| ----------- | ---------- | -------- |
| Running     | start      | yes      |
| Stopped     | not start  | yes      |
| Not running | pause      | yes      |
| Not running | reboot     | yes      |
| Not paused  | resume     | yes      |
| Paused      | not resume | yes      |


## Instance not responding to `instance-reboot` request

If your instance is not responding to an `instance-reboot` request, you can try an `instance-reset` request. You can think of `instance-reboot` as a soft request and `instance-reset` as a hard request. The `instance-reboot` request sends an OS-reboot request to the instance, but an `instance-reset` request performs a hard reset of the VSI instance. You could think of the difference as typing "ctrl-alt-delete" on your computer's keyboard versus hitting the reset or power button. It is good to remember that the `instance-reset` request takes longer to complete than the `instance-reboot` request.

## Need for Bearer tokens in the API calls

When using the API with a cURL command, you may need to include "Bearer" in the Authorization header, depending on what is in the `$iam_token`. If it includes the word "Bearer" you don't include it again in the header. Most of our examples assume that "Bearer" is included in the header.

## Asynchronous API operations and cleanup

Certain operations -- creating and deleting VSIs, and creating and deleting subnets, for example -- are completed asynchronously through the API. Because of this fact, it is recommended to do polling on the resources you're deleting, to check for deletion before proceeding. Here's some example pseudocode for how to do that polling for VSIs:

```
do { sleep 10; get list of vsi } while (count(vsi in subnet) > 0))
```
Or to combine deletions, here is the repeated pattern for deletion and cleanup:

```
for (get all vsi) { delete vsi }
do { sleep 10; get list of vsi } while (count(vsi in subnet) > 0))
for (get all subnet) { delete subnet }
do { sleep 10; get list of subnet } while (count(subnets) > 0)
delete vpc
```

It can take several minutes for resources to be deleted from the system, due to these asynchronous operations. To facilitate deletion, the best practice is to do things in this order:

1. Delete your instances
2. Delete your public gateways
3. Delete your subnets
4. Delete your VPCs

## Can't delete my VPC, VSI, or other resource

You can use a script to determine whether all of your VPC's asynchronously-deleted resources are deleted so you can delete your VPC--for example, subnets:

```
do { list subnets } while (num subnets > 0)
```

You can use the same logic for all deletion of resources, including VSIs.
