---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-27"


keywords: create, VPC, API, IAM, token, permissions, endpoint, region, zone, profile, status, subnet, gateway, floating IP, delete, resource, provision

subcollection: vpc

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Creating a VPC using the REST APIs
{: #creating-a-vpc-using-the-rest-apis}

This guide shows you how to create {{site.data.keyword.cloud}} Virtual Private Cloud resources using the {{site.data.keyword.cloud_notm}} Regional APIs (RIAS).

## Prerequisites

Install the [IBM Cloud CLI](https://cloud.ibm.com/docs/cli/index.html#overview).

## Step 1: Log in to IBM Cloud 

If you have a federated account, run this command:

```
ibmcloud login -sso
```
{: pre}

If you don't have a federated account, run this command:

```
ibmcloud login
```
{: pre}


The `ibmcloud login` command returns a URL and prompts for a passcode. Paste the URL in your browser and log in. If successful, you receive a one-time passcode. Copy the passcode and paste it as a response on the prompt. After the authentication steps, you are prompted to choose an account. 

Respond to any remaining prompts to finish logging in.

## Step 2: Get an IBM Identity and Access Management (IAM) token

The following command calls the {{site.data.keyword.cloud_notm}} CLI, parses out the IAM token and the `Bearer` token identifier, and stores the value in a variable that you can use in later commands.

```bash
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

To view your IAM token, run the command ``echo $iam_token``.

The result should look like this:

```
Bearer <your token>
```
{: screen}

The Authorization header expects the token to begin with "Bearer". If the result above does not include "Bearer", update the `iam_token` variable to include it. These examples assume that "Bearer" is included in the `iam_token`.

You must repeat the preceding step to refresh your IAM token every hour, because the token expires.
{: important}

## Step 3: Store the API endpoint as a variable

The API endpoints are per region and follow the convention `https://<region>.iaas.cloud.ibm.com`. Endpoints by region are:

* US-SOUTH: `https://us-south.iaas.cloud.ibm.com`
* EU-DE: `https://eu-de.iaas.cloud.ibm.com`

Store the API endpoint in a variable so you can use it in API requests without having to type the full URL. For example, to store the us-south endpoint in a variable, run this command:

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

To verify that this variable was saved, run `echo $rias_endpoint` and make sure the response is not empty.

## Step 4: Run the GET regions API

The following command returns the regions available for VPC, in JSON format. At least one object should be returned.

A `version` and `generation` query parameter is required in each API request. For details, see the [Regional API for VPC](https://{DomainName}/apidocs/rias).
{: note}

```bash
curl "$rias_endpoint/v1/regions?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}

If you encounter unexpected results, add the `--verbose` (debug) flag after the `curl` command to obtain detailed logging information. Also see commonly-encountered errors in our [troubleshooting page](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc).
{: tip}


## Step 5: Run the GET zones API

The following command returns the all zones available for VPC in region `us-south`, in JSON format. At least three objects should be returned.

```bash
curl "$rias_endpoint/v1/regions/us-south/zones?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}


## Step 6: Run the GET profiles API

The following command returns the profiles available for your instances, in JSON format. At least one object should be returned.

Add ` | json_pp ` after curl command to get readable JSON string
{: tip}


```bash
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}

If the API output is limited by pagination, set the limit higher than the `total_count`, for example:

```bash
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&generation=1&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## Step 7: Run the GET images API

The following command returns the images available for your instances, in JSON format. At least one object should be returned.

```bash
curl "$rias_endpoint/v1/images?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}

## Step 8: Run the GET vpcs API

The following command returns any VPCs that have been created under your account, in JSON format.

```bash
curl "$rias_endpoint/v1/vpcs?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}

## Step 9: Create a virtual private cloud

Create an {{site.data.keyword.cloud_notm}} VPC called `my-vpc`.

```bash
curl -X POST "$rias_endpoint/v1/vpcs?version=2019-01-01&generation=1" \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

For the rest of the calls, you'll need to know the ID of the newly-created {{site.data.keyword.cloud_notm}} VPC. Store its ID in a variable. The command will look something like this: `vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## Step 10: Create a subnet

Create a subnet in your {{site.data.keyword.cloud_notm}} VPC. The following example creates a VPC in the `us-south-2` zone.

```bash
curl -X POST "$rias_endpoint/v1/subnets?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-subnet",
        "ipv4_cidr_block": "10.0.1.0/24",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Store the subnet ID in a variable.

```bash
subnet="<YOUR_SUBNET_ID>"
```
{: pre}

## Step 11: Check the status of your subnet

To provision resources in your subnet, the subnet must be in `available` status. Before you continue, query the subnet resource and make sure the status is `available`. If the status is `failed`, contact [Support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) with the details. You can attempt to continue by trying to provision another subnet.

```bash
curl "$rias_endpoint/v1/subnets/$subnet?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}


## Step 12: Create a public gateway

To allow virtual server instances in the subnet to have access to the public internet, add a public gateway (PGW) to the subnet.  

```bash
curl -X POST "$rias_endpoint/v1/public_gateways?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-gateway",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Store the public gateway ID in a variable.

```bash
gateway="<YOUR_GATEWAY_ID>"
```
{: pre}

## Step 13: Attach the public gateway to the subnet

```bash
curl -X PUT "$rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## Step 14: Create an SSH key

Create a key with your public SSH key. This key is used when you create the virtual server instance. The key is also needed to log in to the virtual server instance.

Keys can be added when you first create the VPC in the UI or CLI. No tooling exists to add keys later.
{:tip}

```bash
curl -X POST "$rias_endpoint/v1/keys?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-key",
        "public_key": "ssh-rsa AAA....n",
        "type": "rsa"
      }'
```
{: pre}

Store the key ID in a variable.

```bash
key="<YOUR_KEY_ID>"
```
{: pre}

## Step 15: Choose a profile and image for your virtual server instance

Run the APIs to list all profiles and images available for your virtual server instance, and choose a combination.

```bash
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&generation=1" -H "Authorization:$iam_token"
```
{: pre}

To get additional details about the profiles, you can query the global catalog using the {{site.data.keyword.cloud_notm}} CLI command `ibmcloud catalog entry <profile-name> --json`. For example:

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

The following command lists the images available.

```bash
curl "$rias_endpoint/v1/images?version=2019-01-01&generation=1" -H "Authorization:$iam_token"
```
{: pre}

Store the profile name and the image ID in variables, which you'll use to provision a virtual server instance.

```bash
profile_name="<CHOSEN_PROFILE_NAME>"
image_id="<CHOSEN_IMAGE_ID>"
```
{: pre}

## Step 16: Provision a virtual server instance

Provision a virtual server instance (VSI) in the newly-created subnet. Pass in your public SSH key so that you can log in after the instance is provisioned.

```bash
curl -X POST "$rias_endpoint/v1/instances?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "server-1",
        "type": "virtual",
        "zone": {
          "name": "us-south-2"
        },
        "vpc": {
          "id": "'$vpc'"
        },
        "primary_network_interface": {
          "port_speed": 1000,
          "subnet": {
            "id": "'$subnet'"
          }
        },
        "keys":[{"id": "'$key'"}],
        "flavor": {
          "name": "'$profile_name'"
         },
        "image": {
          "id": "'$image_id'"
         },
        "userdata": ""
      }'
```
{: pre}

Store the virtual server instance ID in a variable.

```bash
server="<YOUR_INSTANCE_ID>"
```
{: pre}

## Step 17: Check the status of your virtual server instance

Provisioning a virtual server instance can take up to a few minutes. Before you continue, query the status of the server and make sure it is `running`.

```bash
curl "$rias_endpoint/v1/instances/$server?version=2019-01-01&generation=1" -H "Authorization: $iam_token"
```
{: pre}

Store the primary network interface ID of the virtual server instance (returned in the previous API call) in a variable.  

```bash
network_interface="<YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

You can't get the primary network interface until you query the specific instance.
{: note}

## Step 18: Create a floating IP

To create a floating IP for the virtual server instance, use the instance's primary network interface as the target for the new floating IP address.

```bash
curl -X POST "$rias_endpoint/v1/floating_ips?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-server-floatingip",
        "target": {
            "id":"'$network_interface'"
        }
      }
'
```
{: pre}


Store the floating IP ID in a variable.

```bash
floating_ip="<YOUR_FLOATING_IP_ID>"
```
{: pre}

## Step 19: Add a rule to the default security group to allow SSH traffic

Configure the security group to define the inbound and outbound traffic that is allowed for the instance.

Find the security group for the VPC:

```bash
curl "$rias_endpoint/v1/vpcs/$vpc/default_security_group?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

Store the security group ID in a variable.

```bash
sg=2d364f0a-a870-42c3-a554-000000981149
```
{: pre}

Now create a rule to allow inbound SSH traffic:

```bash
curl -X POST "$rias_endpoint/v1/security_groups/$sg/rules?version=2019-01-01&generation=1" \
  -H "Authorization: $iam_token" \
  -d '{
        "direction": "inbound",
        "protocol": "tcp",
        "port_min": 22,
        "port_max": 22
      }'
```
{: pre}

## Step 20: SSH into your virtual server instance

To SSH to the server, use the `address` of the floating IP you created earlier. To get the `address` of the floating IP, run the following command:

```bash
curl -X GET "$rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

Use the `address` of the floating IP to connect to the virtual server instance with SSH:

```
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

SSH access into the virtual server may be prevented by security groups. If SSH access is required, you must use an [appropriate security group](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups).
{: note}

See [Connecting to your instance using Linux](/docs/vsi-is/vsi_is_connecting_linux_gc.html) for more information on how to connect to your instance.

## Step 21: Create and attach a block storage volume

Create a block storage volume with a request similar to this example and specify a volume name, zone, and profile.

To see a list of volume profiles, provide this request:

```
curl -X GET $rias_endpoint/v1/volumes/profiles?version=2019-01-01 \
  -H "Authorization: $iam_token" \
```
{: pre}

Profiles can be general-purpose (3 IOPS/GB), 5iops-tier, 10iops-tier, and custom. See [About Block Storage for VPC](/docs/infrastructure/block-storage-is?topic=block-storage-is-block-storage-about#capacity-performance)
for information about volume capacity and IOPS ranges based on the volume profile you select.

You don't have to provide a volume name in the request, the system creates one by default.  This example specifies a volume name, `helloworld-vol`.  All volume names must be unique.

```
curl -X POST $rias_endpoint/v1/volumes?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "helloworld-vol",
        "iops": 1000,
        "capacity": 100,
        "zone": {
            "name": "us-south-2"
            },
        "profile": {
            "name": "custom"
            }
      }'
```
{: pre}

Your response will look like this:

```
{
    "id": "640774d7-2adc-4609-add9-6dfd96167a8f",
    "crn": crn:v1:public:is:us-south-2:a/78a00cc28d454fba469cdd8a8e4f1618::volume:640444d7-2adc-2309-adc9-6dfd965557a8f",
    "name": "helloworld-vol",
    "href": "https://us-south-int01.iaasdev.cloud.ibm.com/v1/volumes/640444d7-2adc-2309-adc9-6dfd965557a8f",
    "capacity": 50,
    "iops": 100,
    "encryption": "provider_managed",
    "status": "pending",
    "zone": {
        "name": "us-south-2",
        "href": "https://us-south.iaas.cloud.ibm.com/v1/regions/us-south/zones/us-south-2"
    },
    "profile": {
        "name": "custom",
        "crn": "crn:v1:public:globalcatalog::::volume.profile:custom",
        "href": "https://us-south.iaas.cloud.ibm.com/v1/volume/profiles/custom"
    },
    "resource_group": {
        "id": "d2253bafe7f32dbe94aba5d1dca5ef72",
        "href": "https://resource-manager.bluemix.net/v1/resource_groups/d2253bafe7f32dbe94aba5d1dca5ef72",
        "name": ""
    },
    "created_at": "2019-03-28T23:16:53.000Z"
}
```
{: screen}

Note that the status of the volume is pending when it first is created. Before you can proceed, the volume needs to move to available status, which takes a few minutes. 

For the rest of the calls, you'll need to know the ID of the newly created volume. Save the ID of the volume as a variable, for example:

`vol=640774d7-2adc-4609-add9-6dfd96167a8f`

```bash
volume="<YOUR_VOLUME_ID>"
```
{: pre}


To check the status of the volume, provide this request:

```
curl -X GET $rias_endpoint/v1/volumes/$volume?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}

Create a volume attachment to attach the new volume to the virtual server instance. Use the instance ID variable that you created earlier in the request.  Use the volume ID, CRN of the volume, or URL to specify the volume in the data parameter.  This example uses the variable we created for the volume ID.

```
curl -X POST $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "helloworld-vol-attachment",
        "volume": {
            "id": "$volume"
            }
      }'
```
{: pre}

After creating the volume attachment, get the volume attachment ID.

```
curl GET /v1/instances/$server/volume_attachments?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}

Save the attachment ID as a variable.

```bash
attachment="<YOUR_VOLUME_ATTACHMENT_ID>"
```
{: pre}

Specify the volume attachment ID to attach the new volume to a virtual server instance.

```
curl -X PATCH $rias_endpointv1/instances/$server/volume_attachments/$attachment?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d {
	  "name": "helloworld-vsi-volattachment"
    }
```
{: pre}


## Step 22 (Optional): Delete the Resources

Optionally delete the resources. A resource cannot be deleted if it contains other resources. For example, a virtual private cloud cannot be deleted if it contains subnets, and a subnet cannot be deleted if it contains virtual server instances. On a delete operation, the API may return quickly but the resource deletion might still be in progress. IBM recommends that you query the resource to make sure it is deleted before you delete other resources.

### Delete the floating IP

```bash
curl -X DELETE "$rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

### Delete the virtual server instance

```bash
curl -X DELETE "$rias_endpoint/v1/instances/$server?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

### Delete the key

```bash
curl -X DELETE "$rias_endpoint/v1/keys/$key?version=2019-01-01&generation=1" \
  -H "Authorization: $iam_token"
```
{: pre}


### Delete the public gateway

```bash
curl -X DELETE "$rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

### Delete the subnet

```bash
curl -X DELETE "$rias_endpoint/v1/subnets/$subnet?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

### Delete the VPC

```bash
curl -X DELETE "$rias_endpoint/v1/vpcs/$vpc?version=2019-01-01&generation=1" \
  -H "Authorization:$iam_token"
```
{: pre}

Because a vNIC cannot be deleted from a VSI, we do not include steps to delete vNICs in this tutorial.
{: note}

## Congratulations!

You've successfully provisioned a virtual private cloud instance using the REST APIs. To try out more API commands, explore the full reference:

* [Regional API for VPC](https://{DomainName}/apidocs/rias)
