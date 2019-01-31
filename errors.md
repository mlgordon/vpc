---

copyright:

  years: 2018, 2019

lastupdated: "2019-01-31"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}

# IBM Cloud Virtual Private Cloud API error messages
{: #rias-error-messages}

When you receive an error message from the {{site.data.keyword.cloud}} Virtual Private Cloud APIs, you can use the message ID to find more information about how to resolve the problem.
{:shortdesc}

## acl_in_use
**Message**: The network ACL cannot be deleted because it is attached to resources.

The network ACL cannot be deleted because it is attached to resources. Try checking your subnets.

## address_prefix_conflict
**Message**: The address prefix with this CIDR is in use.

The CIDR for the requested address prefix conflicts with an existing address prefix.

## address_prefix_in_use
**Message**: Cannot delete an address prefix in use.

One or more subnets are using the address prefix. You must detach all the subnets before you can delete a prefix.

## backend_service_unavailable
**Message**: Backend service unavailable.

A backend cloud service failed to respond. One cause for receiving this error could be a missing or expired IAM token. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## bad_field
**Message**: Correct instance UUID should be provided

New volume name should be provided

Try again, providing a valid UUID or volume in your request. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).


## bad_request                                   
**Message**: The information given was invalid, malformed, or missing a required field.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).


## default_address_prefix_not_found
**Message**: Default address prefix not found.

You may see this error message when the default address prefix is not found.

## duplicate_error
**Message**: The input provided already exists.

The resource you've specified already exists.

## floating_ip_in_use
**Message**: The floating IP is in use.

This floating IP is already associated with a network interface or public gateway.

## floating_ip_not_empty
**Message**: Cannot delete a server with a floating IP associated.

Be sure to disassociate the floating IP before you delete the server. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## gateway_too_many
**Message**: None

Only one public gateway is allowed per subnet at this time.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## http_request_size_exceeded                    
**Message**: The HTTP request is too large.

This problem occurs when the payload you have sent in your request has too many characters. Please try again with a smaller payload. For example, instead of trying to do everything in a single request, try creating a minimal resource in one request, and then appending state to it incrementally in several subsequent requests. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).


## iam_failure
**Message**: None

This message can be displayed when there's been a failure to convert an IAM token to an IMS token.  It may mean that the token you provided is not supported, or there is an invalid key ID. If this problem persists, [contact support](getting-help.html).


## ike_policies_quota_exceeded1
**Message**: The quota for IKE policies is exceeded for the account.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html)

## ike_policy_duplicate_name
**Message**: The name already is in use by another IKE policy.

Supply a different IKE policy name. Try again in a few minutes. If this problem persists, contact support.

## ike_policy_in_use
**Message**: The IKE policy is in use by one or more connections.


## ike_policy_invalid_name
**Message**: The name is not a valid IKE policy name.

A valid IKE policy name starts with a letter, followed by letters, digits, underscores or hyphens.

## ike_policy_not_found
**Message**: The IKE policy could not be found.

You referenced an IKE policy that does not exist. Please review your request to ensure that you specified the proper IKE policy ID. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).


## insufficient_space_for_subnet
**Message**: Insufficient space for subnet in address prefix

You might get this error if you attempt to create a subnet and the subnet cannot be created because the number of addresses requested cannot be allocated.

## internal_server_error
**Message**: None

You might receive this error if the system is unable to provision your VSI, storage volume, or other resources. Try again in a few minutes. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## invalid_id_format
+**Message**: Bad ID format. Ensure format is correct.
+
+Make sure that the ID you provided does not contain any malformed data.
+
+You may get this error message if a malformed start query is used when making a pagination request. For example, 
+`GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` contains two `?`s. Fix the query and try again.

## invalid_state
**Message**: None

RIAS command `ibmcloud is in-reboot Instance_uuid` can return the message code "invalid_state"

In one situation, the message is thrown when a reboot operation is attempted while the VSI is already being rebooted. This message also can be received in a situation where multiple reboots are not happening at the same time.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## invalid_version
**Message**: The `version` is invalid, it must be in the form of `YYYY-MM-DD`.

The version must comply with the format `YYYY-MM-DD`. For single-digit months or dates, such as January 1st, the version should look like `2019-01-01`.

## invalid_version_range
**Message**: The `version` cannot be set at a future date nor before `2019-01-01`.

The version must be after `2019-01-01` and before the current date.

## invalid_zone
**Message**: Please check whether the resources you are requesting are in the same zone.

You may see this message if the resource you're requested is not in a valid zone.

## ipsec_policies_quota_exceeded
**Message**: The quota for IPsec policies is exceeded for the account.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## ipsec_policy_duplicate_name
**Message**: The name already is in use by another IPsec policy.

Supply a different IPsec policy name. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## ipsec_policy_in_use
**Message**: The IPsec policy is in use by one or more connections.



## ipsec_policy_invalid_name
**Message**: The name is not a valid IPsec policy name.

A valid IPsec policy name starts with a letter, followed by letters, digits, underscores or hyphens.

## ipsec_policy_not_found
**Message**: The IPsec policy could not be found.

You referenced an IPsec policy that does not exist. Please review your request and be sure that you've specified the proper IPsec policy ID. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## key_exists
**Message**: The same key content already exists.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## listener_certificate_not_found
**Message**: Certificate instance with CRN `<listener_certificate_crn>` cannot be found or no permission to access the certificate instance.

Please provide an existing certificate instance CRN or ask your account administrator to grant you access permissions to the provided certificate instance.

## listener_duplicate_port
**Message**: Port `<listener_port>` is used by another listener instance. Please choose a different port.

Please choose a different port.

## listener_invalid_certificate
**Message**: CRN of certificate instance for the HTTPS listener is invalid.

Please provide a valid certificate instance CRN.

## listener_invalid_connection_limit
**Message**: Listener connection limit `<listener_connection_limit>` in invalid.

Please provide a valid connection limit. Connection limit has to be an integer between 1 and 15000.

## listener_invalid_port
**Message**: Listener port `<listener_port>` is invalid.

Please choose a different port.

## listener_invalid_protocol
**Message**: Listener protocol `<listener_protocol>` is invalid.

Please provide a valid listener protocol. Acceptable values for listener protocol are `http`, `https`, and `tcp`.

## listener_missing_certificate_crn
**Message**: CRN of the certificate instance for the `https` listener is missing.

CRN of the certificate instance is a required field.

## listener_missing_port
**Message**: Listener port is missing.

Listener port is a required field.

## listener_missing_protocol
**Message**: Listener protocol is missing.

Listener protocol is a required field. Please provide the listener protocol in your request. The acceptable values are `http`, `https` and `tcp`.

## listener_not_found
**Message**: The listener with ID `<listener_id>` cannot be found.

Please provide an existing listener ID.

## listener_over_quota
**Message**: Listener cannot be created. Quota of listeners for the load balancer resource has reached the maximum limit.

The quotas per resource are given in [Quotas and limits for VPC](https://{DomainName}/docs/infrastructure/vpc/vpc-quotas.html#quotas-and-limits-for-vpc){: new_window}.

## listener_pool_protocols_conflict
**Message**: Listener protocol(`<listener_protocol>`) and pool protocol(`<pool_protocol>`) are in conflict.

A listener with `https` or `http` protocol can only be associated with a pool with `http` protocol. Similarly, a `tcp` listener can only be associated with a `tcp` pool.

## listener_reserved_port_conflict
**Message**: Listener port `<listener_port>` is one of the reserved ports. The port range of 56500 to 56520 is reserved for management purposes. Please choose a different port.

Please choose a different port.


## load_balancer_duplicate_name
**Message**: Name `<load_balancer_name>` is used by another load balancer instance. Please choose a different name.

Provide a different name for the load balancer instance.

## load_balancer_invalid_description
**Message**: Load balancer description `<load_balancer_description>` is invalid.

Load balancer description cannot exceed 255 characters.

## load_balancer_invalid_is_public
**Message**: Value of is_public `<load_balancer_is_public>` is invalid.

Load balancer is_public should be either true or false.

## load_balancer_invalid_is_public_value
**Message**: Only public load balancers are supported.

Private load balancers are not yet supported.

## load_balancer_invalid_name
**Message**: Name `<load_balancer_name>` is invalid.

Name should not be empty. Length of the name should not exceed 40 characters. A valid load balancer name starts with a letter followed by letters, digits, underscores.

## load_balancer_missing_is_public
**Message**: `is_public` field is missing.

`is_public` is a required field. Please provide load balancer is_public field.

## load_balancer_missing_name
**Message**: Load balancer name is missing.

Please provide load balancer name. Load balancer name is a required field.

## load_balancer_missing_subnets
**Message**: Load balancer `subnets` is missing.

`subnets` is a required field. Please provide the subnets where to create the load balancer in your request.

## load_balancer_not_found
**Message**: The load balancer with ID `<load_balancer_id>` cannot be found.

Please provide an existing load balancer ID.

## load_balancer_over_quota
**Message**: Load balancer cannot be created. Quota of load balancer instances under your account has reached maximum limit.

Either delete an existing load balancer or contact support to increase loadbalancer quota on your account.

The quotas per resource are given in [Quotas and limits for VPC](https://{DomainName}/docs/infrastructure/vpc/vpc-quotas.html#quotas-and-limits-for-vpc){: new_window}.

## load_balancer_unchanged_update
**Message**: There is nothing to update the load balancer with ID `<load_balancer_id>`.

There is nothing to update the load balancer instance.


## member_invalid_port
**Message**: The specified member port `<member_port>` is invalid.

Please provide a valid port number. A valid port number is in the range from 1 to 65535.

## member_invalid_weight
**Message**: The specified member weight `<member_weight>` is invalid.

Please provide a valid member weight. It has to be an integer between 0 and 100.

## member_missing_address
**Message**: Member address is missing.

Member address is a required field. Please provide member address in your request.

## member_missing_protocol_port
**Message**: Member port is missing.

Member port is a required field. Please provide member port in your request.

## member_over_quota
**Message**: Member cannot be created. Quota of member instances under the pool has reached maximum limit.

The quotas per resource are given in [Quotas and limits for VPC](https://{DomainName}/docs/infrastructure/vpc/vpc-quotas.html#quotas-and-limits-for-vpc){: new_window}.

## missing_ims_account_id
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## missing_version
**Message**: The `version` parameter is required and must be in the form of `YYYY-MM-DD`.

The version parameter must be present in the URL.

## network_conflict
**Message**: None

You might see this message if you supply a network CIDR that conflicts with an existing network CIDR in the same IP space.

## not_authorized                               
**Message**: The request is not authorized.

A common reason you may see this error is if your IAM token is missing or expired. If so, you may need to check your permissions and contact your administrator. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## not_found
**Message**: Please check whether the resource you are requesting exists.

You referenced a resource that does not exist or one to which you do not have access.  Please review your request to ensure that you specified the proper IDs and references.

This error may occur when you've tried to provision your VSI using a profile that is not supported, or tried to allocate another resource that is unavailable. For a list of available profiles, you can use the command `ibmcloud is instance-profiles`. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## not_implemented
**Message**: None

The method is not implemented.

## not_in_address_prefix
**Message**: No applicable address prefix

No valid address prefix can be found.

## over_quota                                    
**Message**: The request would exceed the quota for a resource type.

The quotas per resource are given in [Quotas and limits for VPC](https://{DomainName}/docs/infrastructure/vpc/vpc-quotas.html#quotas-and-limits-for-vpc){: new_window}.

## password_not_ready
**Message**: None

Your instance must be running before you can retrieve the password. Try again in a few minutes. If this problem persists, contact support.

## pool_delete_conflict
**Message**: Pool cannot be deleted because it is still associated with one or more listeners.

Please ensure the pool is disassociate with any listeners and try again.

## pool_duplicate_name
**Message**: Pool name `<pool_name>` is already used by another pool. Please choose a different name.

Please choose a different pool name.

## pool_missing_algorithm
**Message**: Load balancing algorithm is missing.

Load balancing algorithm is a required field. Please provide the load balancing algorithm in your request. The acceptable values are `round_robin`, `weighted_round_robin` and `least_connections`.

## pool_missing_health_monitor
**Message**: Pool health monitor is missing.

Pool health monitor is a required field.

## pool_missing_name
**Message**: Pool name is missing.

Pool name is a required field.

## pool_missing_protocol
**Message**: Pool protocol is missing.

Pool protocol is a required field. Please provide the pool protocol in your request. The acceptable values are `http` and `tcp`.

## pool_not_found
**Message**: The pool with ID `<pool_id>` cannot be found.

Please provide an existing pool ID.

## pool_over_quota
**Message**: Pool cannot be created. Quota of pools for the load balancer resource has reached maximum limit.

The quotas per resource are given in [Quotas and limits for VPC](https://{DomainName}/docs/infrastructure/vpc/vpc-quotas.html#quotas-and-limits-for-vpc){: new_window}.

## public_gateway_in_use
**Message**: Cannot delete a public gateway when it is in use.

The public gateway currently is attached to one or more subnets. You must detach the public gateway from all subnets before you can delete it.

## rate_limit_exceeded
**Message**: Too many requests

This message is returned if there are too many requests within a specified time interval.

## security_group_active_transactions
**Message**: The interface cannot be attached or detached until the instance appears in Active state.

Please try again once the instance becomes Active. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_already_attached
**Message**: The interface is attached already.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_exists
**Message**: The security group already exists.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_interfaces_attached
**Message**: Cannot delete the security group while interfaces are attached.

Be sure all interfaces are deleted. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_interfaces_per_sg_exceeded
**Message**: Exceeded limit of interfaces per security group.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_last_security_group_is_default
**Message**: The default security group cannot be removed when it is the only security group attached.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_limit_exceeded
**Message**: Exceeded security group limit.

You have attempted to create a new security group but are currently at your account quota. Evaluate your strategy for assigning instances to security groups. It is often possible to reduce the overall number of security groups by assigning multiple instances to the same security group. This will reduce the number of security groups, dropping you below your account quota.  In rare cases, generally for large organizations, there is a need for expanding the quota. In this case, please [contact support](getting-help.html) to inquire if this is possible.


## security_group_network_interface_not_active
**Message**: The interface cannot be attached because it is not active.

To apply security groups, the network interface must be active. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_not_attached
**Message**: The interface is not attached.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_not_in_vpc
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_not_supported
**Message**: Security groups are not supported in the target datacenter.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_order_bindings
**Message**: Cannot delete the security group, it has pending orders.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_perm_denied
**Message**: Incorrect permissions to change the security group.

You may need to check your permissions and contact your administrator. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_port_range_both_or_neither
**Message**: Port range must be unset, or both a minimum and maximum port must be set for `tcp` and `udp`.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_port_range_invalid_protocol
**Message**: A port range was specified with a protocol of `icmp`. A port range is only valid for a protocol of `tcp` or `udp`.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_remote_group_not_in_vpc
**Message**: The remote group is not in the same VPC as this security group

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_remoting_rules
**Message**: Cannot delete the security group while remoting rules are attached.

Be sure to remove all remoting rules. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_remoting_rules_per_sg_exceeded
**Message**: Exceeded limit of remoting rules per security group.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_rules_per_sg_exceeded
**Message**: Exceeded limit of rules per security group.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_sgs_per_interface_exceeded
**Message**: Exceeded limit of security groups per interface.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_type_code_invalid_protocol
**Message**: An `icmp` type/code was given, but the requested protocol was not `icmp`. Set the protocol to `icmp` or specify a port range.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## security_group_vpc_default
**Message**: Cannot delete the security group, it is the VPC default.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Security Groups document](https://{DomainName}/docs/infrastructure/vpc-network/security-groups.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## service_manager_service_failure
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## staticroute_conflict
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## staticroute_invalid_CIDR
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## staticroute_invalid_NextHop
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).


## subnet_acl_conflict
**Message**: Cannot delete the network ACL, it is attached to a subnet.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## subnet_conflict
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## subnet_not_empty
**Message**: The subnet is not empty, please contact your administrator.

There was a request to delete a subnet, but the subnet still has resources in it. Subnets may have instances, VPNs, load balancers, or public gateways in them. You must delete your resources in the subnet before you may delete the subnet. 

In some situations, this error can occur even when the console shows 0 VSIs and 0 load balancers, because deletion is asynchronous and it may take a few minutes for the internal status to change. Try your subnet deletion again in a few minutes.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## subnet_unknown_state
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## system_limit_exceeded
**Message**: This operation would exceed a system limit

One possible scenario for receiving this error message is if you try to create an address prefix, but the maximum number of address prefixes already exist.

## target_in_use
**Message**: The target already has floating IP attached.

## token_invalid
**Message**: The service token was expired or invalid.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## token_missing
**Message**: The service token was empty or did not exist in the request.

Recreate a token and try again.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## validation_enum
**Message**: The value supplied was not a valid option.

One of the fields supplied has a value that must come from an enumeration of possible values.

For Network ACL rules, you may specify a direction:

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum:
[ inbound, outbound ]
```

For example, the following value would be invalid because `northbound` is not a valid option in the enmeration `[ inbound, outbound ]`.

```json
{
    "direction":"northbound"
}
```

## validation_failure                            
**Message**: The JSON provided did not match the expected structure.

To fix this problem, be sure the content of your request is valid JSON and that your request conforms to the [API documentation](api-doc-wrapper.html){: new_window}.

## validation_invalid_cidr                       
**Message**: The value is not a valid CIDR.

The value must be a valid internal CIDR block with a 0 host part.

Certain IP address ranges are reserved. More information about reserved IP ranges is available in our overview of [Using your VPC with Regions and Subnets](https://{DomainName}/docs/infrastructure/vpc-network/vpc-regions-and-subnets.html#available-ip-address-ranges-regions-and-subnets){: new_window}.

## validation_invalid_ipv4_cidr        
**Message**: The value is not a valid IPv4 CIDR.

Must be a IPv4 internal CIDR block with a 0 host part.

Certain IP address ranges are reserved. More information about reserved IP ranges is available in our overview of [Using your VPC with Regions and Subnets](https://{DomainName}/docs/infrastructure/vpc-network/vpc-regions-and-subnets.html#available-ip-address-ranges-regions-and-subnets){: new_window}.

## validation_invalid_ipv6_cidr
**Message**: The value is not a valid IPv6 CIDR.

Currently, IPv6 is not supported. Please use an IPv4 address.

## validation_invalid_address
**Message**: The value is not a valid address.

Must be a valid IP address

A list of individually reserved IP addresses is given in the [Regions and Subnets](https://{DomainName}/docs/infrastructure/vpc-network/vpc-regions-and-subnets.html) document.

## validation_invalid_ipv4_address
**Message**: The value is not a valid IPv4 address.

Give a valid IPv4 address.

## validation_invalid_ipv6_address
**Message**: The value is not a valid IPv6 address.

Give a valid IPv6 address. Currently, IPv6 is not supported; use an IPv4 address.

## validation_invalid_field_type
**Message**: The value type does not match the field type.

To fix this problem, be sure the content of your request conforms to the [API documentation](api-doc-wrapper.html){: new_window} for the endpoint you are calling.

## validation_max_value
**Message**: The value supplied was too large.

Supply a smaller value that meets the maximum as given by the specification. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}.

## validation_min_value
**Message**: The value supplied was too small.

Supply a larger value that meets the minimum as given by the specification. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}.

## validation_not_null
**Message**: The field supplied must be null.

Be sure the value is null. For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}.

Here is an invalid example:

```json
{
    "name": null
}
```

## validation_only_one
**Message**: The value must match one of the subschemas.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}.

## validation_discriminator_forbidden
**Message**: The discriminator field forbids this substructure.

For example, if you specify
```
{
protocol: icmp
port_min: 5
port_max: 100
}
```

The protocol is `icmp`, and _port_min_ is a `tcp` field, so you'll get an error.
1. validation_discriminator_required for missing `icmp` rules
2. validation_discriminator_forbidden for `tcp` fields with `icmp` specified

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## validation_internal_error
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## validation_invalid_name
**Message**: The value is not a valid name.


## validation_invalid_ref
**Message**: The value is not a valid HREF.


## validation_non_empty_uuid
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## validation_required_field
**Message**: Missing a required field.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## validation_unique_failed
**Message**: The field supplied must be unique.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

You might have specified a name that is already in use. Please try a different value.

## vpc_acl_conflict                           
**Message**: Cannot delete the default network ACL, it is attached to a VPC.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html) or the [Using Network ACLs document](using-acls.html){: new_window}.

If this problem persists, [contact support](getting-help.html).

## vpc_not_empty
**Message**: The VPC cannot be deleted becuase it is not empty.

All resources must be removed from a VPC before it can be deleted.

You could receive this error if you still have a gateway in your VPC, even when all subnets are deleted, because the gateway can exist in the VPC without a subnet. It may be necessary to use the CLI to check for orphaned resources.

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## vpc_resource_separation
**Message**: The resources are in different VPCs

## vpn_connection_cidr_not_created
**Message**: A CIDR block could not be added to the VPN connection.

Supply a valid CIDR that meets the requirements given by the specification. 

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).

## vpn_connection_cidr_not_deleted
**Message**: A CIDR block could not be deleted from the VPN connection.

Supply a valid CIDR that exists on the connection. A connection must have at least one local and peer CIDR.

## vpn_connection_cidr_not_found
**Message**: The CIDR block was not found in the VPN connection.

Supply a valid CIDR that is in the connection.

## vpn_connection_cidr_not_valid
**Message**: The CIDR block does not represent a valid address.

The value must be a valid internal CIDR block with no host bits set.

## vpn_connection_cidr_overlap
**Message**: The CIDR block overlaps with another one. Two peer CIDR blocks cannot overlap on the same VPC and two local CIDR blocks cannot overlap on the same connection.

Supply a valid CIDR value that meets the requirements given by the specification.

## vpn_connection_duplicate_name
**Message**: The name is already in use by another VPN connection.

Supply a different connection name. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_connection_invalid_name
**Message**: The name is not a valid VPN connection name.

A valid connection name starts with a letter, followed by letters, digits, underscores, or hyphens.

## vpn_connection_invalid_psk_format
**Message**: The pre-shared key (PSK) is not in the valid format.

A valid PSK should only contain 6 to 128 characters which are letters, digits, `-`,`+`,`&`,`!`,`@`,`#`,`$`,`%`,`^`,`*`,`(`,`)`,`,`,`.`,`:`,`_`.

## vpn_connection_local_cidrs_required
**Message**: At least one local CIDR block is required when creating a VPN connection.

Supply a valid local CIDR value that meets the requirements given by the specification.

## vpn_connection_local_subnets_quota_exceeded
**Message**: The quota for local subnets across VPN connections exceeded for the VPN gateway.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## vpn_connection_local_subnets_quota_exceeded_for_connection
**Message**: The quota of local subnets for VPN connection is exceeded.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## vpn_connection_not_found
**Message**: The VPN connection could not be found.

Check whether the connection ID is correct. Try again in a few minutes. If this problem persists, contact support.

## vpn_connection_peer_cidrs_required
**Message**: At least one peer CIDR block is required when creating a VPN connection.

Supply a valid peer CIDR value that meets the requirements given by the specification.

## vpn_connection_peer_subnets_quota_exceeded
**Message**: The quota for peer subnets across VPN connections is exceeded for the VPN gateway.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## vpn_connection_peer_subnets_quota_exceeded_for_connection
**Message**: The quota of peer subnets for VPN connection is exceeded.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## vpn_connections_quota_exceeded
**Message**: The quota for VPN connections is exceeded for the VPN gateway.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## vpn_connection_static_route_not_created
**Message**: Failed to add a static route for a CIDR block.

Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_connection_static_route_not_deleted
**Message**: Failed to remove a static route for a CIDR block.

Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_connection_update_cidrs_not_permitted
**Message**: CIDR blocks cannot be changed when updating a connection. Please use the correct API when creating or deleting CIDRs.

Supply a valid request value that meets the requirements given by the specification.

## vpn_gateway_duplicate_name
**Message**: The name is already in use by another VPN gateway.

Supply a different VPN gateway name. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_gateway_initialization_error
**Message**: The VPN gateway could not be initialized.

Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_gateway_invalid_name
**Message**: The name is not a valid VPN gateway name.

A valid VPN gateway name starts with a letter, followed by letters, digits, underscores, or hyphens.

## vpn_gateway_invalid_state
**Message**: VPN Gateway is in pending status and cannot be deleted at this time.

VPN Gateway must be in `available` status before you can operate it. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_gateway_ip_create_error
**Message**: Unable to create an IP address for the VPN gateway.

Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_gateway_not_found
**Message**: The VPN gateway could not be found.

Check whether the VPN gateway ID is correct. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_gateway_subnet_not_found
**Message**: Could not find the subnet for the given VPN gateway.

You've referenced a subnet that does not exist. Please review your request to ensure that you specified the proper subnet ID. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).

## vpn_gateway_subnet_status_error
**Message**: The VPN gateway could not be created due to subnet status.

Supply a subnet that is in `available` status. Try again in a few minutes. If this problem persists, [contact support](getting-help.html).


## vpn_gateways_quota_exceeded
**Message**: Quota for VPN gateways exceeded for the account.

The quotas per resource are given in [Using VPN with your IBM Cloud VPC](https://{DomainName}/docs/infrastructure/vpc-network/using-vpn.html#using-vpn-with-your-vpc){: new_window}.

## zone_conflict_duplicate_res
**Message**: None

For further instructions to fix this problem, refer to the [API documentation](api-doc-wrapper.html){: new_window}. If this problem persists, [contact support](getting-help.html).
