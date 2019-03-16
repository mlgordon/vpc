---

copyright:

  years: 2018, 2019

lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}

# Messages d'erreur des API d'IBM Cloud Virtual Private Cloud 
{: #rias-error-messages}

Lorsque vous recevez un message d'erreur des API {{site.data.keyword.cloud}}
Virtual Private Cloud, vous pouvez vous servir de l'ID de message pour savoir comment
résoudre le problème.
{:shortdesc}

## acl_in_use
**Message** : The network ACL cannot be deleted because it is attached to resources.

La liste de contrôle d'accès au réseau ne peut pas être supprimée car elle est associée à des ressources. Vérifiez vos sous-réseaux. 

## address_prefix_conflict
**Message** : The address prefix with this CIDR is in use.

Le bloc CIDR pour le préfixe d'adresse demandé est en conflit avec un préfixe d'adresse existant. 

## address_prefix_in_use
**Message** : Cannot delete an address prefix in use.

Un ou plusieurs sous-réseaux utilisent le préfixe d'adresse. Vous devez détacher tous les sous-réseaux pour pouvoir supprimer un préfixe. 

## backend_service_unavailable
**Message** : The backend service is unavailable.

Un service de cloud de back end ne répond pas. Il est possible qu'un jeton IAM manque ou ait expiré. Réessayez dans quelques minutes. Si le problème persiste, contactez le support. 

## bad_field
**Message** : Correct instance UUID should be provided

Vous devez indiquer un nouveau nom de volume. 

Réessayez en fournissant un identificateur unique universel ou un volume valide dans votre demande.  

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## bad_request                                   
**Message** : The information given was invalid, malformed, or missing a required field.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## classic_access_vpc_conflict_duplicate_res
**Message** : Only one Classic Access VPC can be created.

Vous ne pouvez pas créer plusieurs clouds privés virtuels à accès classique pour un compte. 

## default_address_prefix_not_found
**Message** : Default address prefix not found.

Ce message d'erreur s'affiche si le préfixe d'adresse par défaut est introuvable. 

## duplicate_error
**Message** : The input provided already exists.

La ressource que vous avez spécifiée existe déjà. Pour résoudre ce problème, utilisez un autre nom pour la ressource à créer. Par exemple, lorsque vous créez un cloud privé virtuel, vous pouvez consulter la liste des noms des clouds privés virtuels déjà créés et choisir un nom qui n'entre pas en conflit avec eux, si vous appelez d'abord `get VPC` à l'aide d'un ID, par exemple `GET "/v1/vpcs/{id}” -H  "accept: application/json"`.  

## floating_ip_in_use
**Message** : The floating IP is in use.

Cette adresse IP flottante est déjà associée à une interface réseau ou à une passerelle publique. 

## floating_ip_not_empty
**Message** : Cannot delete a server with a floating IP associated.

Veillez à dissocier l'adresse IP flottante avant de supprimer le serveur.  

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## gateway_too_many
**Message** : Can only have one public gateway per zone in a VPC.

Une passerelle publique et une seule est autorisée dans un cloud privé virtuel, mais elle doit être attachée à plusieurs sous-réseaux dans la zone. Afin de rechercher la passerelle publique pour une zone, exécutez l'API GET public_gateways et consultez les valeurs de "vpc" et "zone". Si vous utilisez l'interface de ligne de commande, vous pouvez exécuter la commande `ibmcloud is public-gateways` et consulter les valeurs de "VPC" et "Zone". 

Utilisez l'ID de la passerelle publique pour attacher la passerelle publique à un sous-réseau ; vous trouverez un exemple dans les [exemples d'API](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis#step-13-attach-the-public-gateway-to-the-subnet-). Si vous utilisez l'interface de ligne de commande, vous pouvez utiliser la commande de mise à jour du sous-réseau pour attacher le sous-réseau à une passerelle publique, par exemple `ibmcloud is subnet-update SUBNET_ID --public-gateway-id PUBLIC_GATEWAY_ID`. 


## http_request_size_exceeded                    
**Message** : The HTTP request is too large.

Ce problème survient lorsque le contenu que vous avez envoyé dans votre demande comporte un nombre trop élevé de caractères. Réessayez avec un contenu plus petit. Par exemple, au lieu de tout effectuer dans une seule demande, essayez de créer une ressource minimale dans une demande, puis ajoutez l'état progressivement dans plusieurs demandes consécutives.  

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## iam_failure
**Message** : None

Ce message peut s'afficher en cas d'erreur liée au service IAM lors de l'authentification ou de l'autorisation. Cette indisponibilité du service IAM peut être temporaire. Relancez la demande après quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policies_quota_exceeded
**Message** : The quota for IKE policies is exceeded for the account.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les stratégies IKE appliquées, utilisez l'API `GET /ike_policies`. 

## ike_policy_duplicate_name
**Message** : The name `<ike_policy_name>` is in use already by IKE policy `<ike_policy_id>`.

Indiquez un autre nom de stratégie IKE. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policy_in_use
**Message** : The IKE policy `<ike_policy_id>` is in use by one or more connections.

Une stratégie IKE ne peut pas être supprimée si elle est en cours d'utilisation par une ou plusieurs connexions. 

## ike_policy_invalid_name
**Message** : The name `<ike_policy_name>` is not a valid IKE policy name.

Un nom de stratégie IKE valide commence par une lettre, suivie d'autres lettres, de chiffres, de traits de soulignement ou de traits d'union. 

## ike_policy_not_found
**Message** : The IKE policy `<ike_policy_id>` could not be found.

Vous avez référencé une stratégie IKE qui n'existe pas. Vérifiez votre demande pour vous assurer que vous avez spécifié l'ID de stratégie IKE approprié. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## insufficient_space_for_subnet
**Message** : Insufficient space for subnet in address prefix

Cette erreur peut s'afficher si vous tentez de créer un sous-réseau et que le sous-réseau ne peut pas être créé car le nombre d'adresses demandé ne peut pas être alloué. 

## internal_error
**Message** : An internal error occurred.

Réessayez. Si l'erreur persiste, contactez le support. 

## internal_server_error
**Message** : None

Ce message s'affiche lorsque le service rencontre une erreur inattendue. Ce problème peut être temporaire. Relancez la demande dans quelques minutes. 

Si le problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## internal_solution
**Message** : Please contact your administrator.

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_id_format
**Message** : Bad ID format. Ensure format is correct.

Assurez-vous que l'ID que vous avez fourni ne contient pas de données incorrectement formées. 

Ce message peut s'afficher si une requête de démarrage incorrectement formée est utilisée lors d'une demande de pagination. Par exemple,
`GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` contient deux points d'interrogation `?`. Corrigez la requête et réessayez. 

## invalid_state
**Message** : None

La commande RIAS (service des API d'infrastructure régionales) `ibmcloud is in-reboot Instance_uuid` peut renvoyer le code de message "invalid_state". 

Le message peut être émis lorsqu'une opération de réamorçage est tentée alors que l'instance de serveur virtuel a déjà été réamorcée. Ce message peut également s'afficher lorsque plusieurs réamorçages n'ont pas lieu simultanément. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_version
**Message** : The `version` parameter is invalid, it must be of the form `YYYY-MM-DD`.

Le format de la version doit être _AAAA-MM-JJ_. Pour les mois ou les dates à un seul chiffre, comme le 1er janvier, la version est similaire à `2019-01-01`. Le paramètre de version doit être présent dans l'adresse URL. La date indiquée dans le paramètre de version doit être ultérieure à la date 2019-01-01 et antérieure à la date en cours. Par exemple, pour obtenir la liste des clouds privés virtuels, ajoutez la version à la fin de la demande `GET "/v1/vpcs?version=2019-01-01”`.

## invalid_version_range
**Message** : The `version` value cannot be set at a future date nor before `2019-01-01`.

Le format de la version doit être _AAAA-MM-JJ_. Pour les mois ou les dates à un seul chiffre, comme le 1er janvier, la version est similaire à `2019-01-01`. Le paramètre de version doit être présent dans l'adresse URL. La date indiquée dans le paramètre de version doit être ultérieure à la date 2019-01-01 et antérieure à la date en cours. Par exemple, pour obtenir la liste des clouds privés virtuels, ajoutez la version à la fin de la demande `GET "/v1/vpcs?version=2019-01-01”`.

## invalid_zone
**Message** : Please check whether the resources you are requesting are in the same zone.

Ce message s'affiche si la ressource que vous avez demandée ne se trouve pas dans une zone valide. 

## ipsec_policies_quota_exceeded
**Message** : The quota for IPsec policies is exceeded for the account.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les stratégies IPSec appliquées, utilisez l'API `GET /ipsec_policies`. 

## ipsec_policy_duplicate_name
**Message** : The name `<ipsec_policy_name>` is in use already by IPsec policy `<ipsec_policy_id>`.

Indiquez un autre nom de stratégie IPSec. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ipsec_policy_in_use
**Message** : The IPsec policy `<ipsec_policy_id>` is in use by one or more connections.

Une stratégie IPSec ne peut pas être supprimée si elle est en cours d'utilisation par une ou plusieurs connexions. 

## ipsec_policy_invalid_name
**Message** : The name `<ipsec_policy_name>` is not a valid IPsec policy name.

Un nom de stratégie IPSec valide commence par une lettre, suivie d'autres lettres, de chiffres, de traits de soulignement ou de traits d'union. 

## ipsec_policy_not_found
**Message** : The IPsec policy `<ipsec_policy_id>` could not be found.

Vous avez référencé une stratégie IPSec qui n'existe pas. Vérifiez votre demande et assurez-vous d'avoir spécifié l'ID de stratégie IPSec approprié. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## key_exists
**Message** : The same key content already exists.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## listener_certificate_not_found
**Message** : Certificate instance with CRN `<listener_certificate_crn>` cannot be found or no permission to access the certificate instance.

Indiquez un nom de ressource de cloud d'instance de certificat existant ou demandez à votre administrateur de compte de vous accorder des droits d'accès à l'instance de certificat indiquée. 

## listener_duplicate_port
**Message** : Port `<listener_port>` is used by another listener instance. Please choose a different port.

Choisissez un autre port. 

## listener_invalid_certificate
**Message** : CRN of certificate instance for the HTTPS listener is invalid.

Indiquez un nom de ressource de cloud d'instance de certificat valide. 

## listener_invalid_connection_limit
**Message** : Listener connection limit `<listener_connection_limit>` in invalid.

Indiquez un nombre maximal de connexions valide. Il doit s'agir d'un entier compris entre 1 et 15000. 

## listener_invalid_port
**Message** : Listener port `<listener_port>` is invalid.

Choisissez un autre port. 

## listener_invalid_protocol
**Message** : Listener protocol `<listener_protocol>` is invalid.

Indiquez un protocole d'écouteur valide. Les valeurs admises pour le protocole d'écouteur sont `http`, `https` et `tcp`.

## listener_missing_certificate_crn
**Message** : CRN of the certificate instance for the `https` listener is missing.

La zone de nom de ressource de cloud de l'instance de certificat est requise. 

## listener_missing_port
**Message** : Listener port is missing.

La zone de port d'écoute est requise. 

## listener_missing_protocol
**Message** : Listener protocol is missing.

La zone de protocole d'écouteur est requise. Indiquez le protocole d'écouteur dans votre demande. Les valeurs admises sont `http`, `https` et `tcp`.

## listener_not_found
**Message** : The listener with ID `<listener_id>` cannot be found.

Indiquez un ID d'écouteur existant. 

## listener_over_quota
**Message** : Listener cannot be created. Quota of listeners for the load balancer resource has reached the maximum limit.

Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}. 

## listener_pool_protocols_conflict
**Message** : Listener protocol(`<listener_protocol>`) and pool protocol(`<pool_protocol>`) are in conflict.

Un écouteur dont le protocole est `https` ou `http` ne peut être associé qu'à un pool dont le protocole est `http`. De même, un écouteur `tcp` ne peut être associé qu'à un pool `tcp`. 

## listener_reserved_port_conflict
**Message** : Listener port `<listener_port>` is one of the reserved ports. The port range of 56500 to 56520 is reserved for management purposes. Please choose a different port.

Choisissez un autre port. 

## load_balancer_duplicate_name
**Message** : Name `<load_balancer_name>` is used by another load balancer instance. Please choose a different name.

Indiquez un autre nom pour l'instance d'équilibreur de charge. 

## load_balancer_invalid_description
**Message** : Load balancer description `<load_balancer_description>` is invalid.

La description de l'équilibreur de charge ne peut pas comporter plus de 255 caractères. 

## load_balancer_invalid_is_public
**Message** : Value of is_public `<load_balancer_is_public>` is invalid.

La valeur du paramètre is_public de l'équilibreur de charge doit être true ou false. 

## load_balancer_invalid_is_public_value
**Message** : Only public load balancers are supported.

Les équilibreurs de charge privés ne sont pas encore pris en charge. 

## load_balancer_invalid_name
**Message** : Name `<load_balancer_name>` is invalid.

Le nom ne doit pas être vide. Le nom ne doit pas comporter plus de 40 caractères. Un nom d'équilibreur de charge valide commence par une lettre, suivie d'autres lettres, de chiffres et de traits de soulignement. 

## load_balancer_missing_is_public
**Message** : 'is_public' field is missing.

La zone 'is_public' est requise. Indiquez une valeur dans la zone is_public de l'équilibreur de charge. 

## load_balancer_missing_name
**Message** : Load balancer name is missing.

Indiquez le nom de l'équilibreur de charge. La zone de nom d'équilibreur de charge est requise. 

## load_balancer_missing_subnets
**Message** : Load balancer subnets is missing.

La zone 'subnets' est requise. Indiquez les sous-réseaux sur lesquels créer l'équilibreur de charge dans votre demande. 

## load_balancer_not_found
**Message** : The load balancer with ID `<load_balancer_id>` cannot be found.

Indiquez un ID d'équilibreur de charge existant. 

## load_balancer_over_quota
**Message** : Load balancer cannot be created. Quota of load balancer instances under your account has reached maximum limit.

Supprimez un équilibreur de charge existant ou contactez le support pour augmenter le quota d'équilibreurs de charge sur votre compte. 

Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}. 

## load_balancer_unchanged_update
**Message** : There is nothing to update the load balancer with ID `<load_balancer_id>`.

Il n'existe aucun élément pour la mise à jour de l'instance d'équilibreur de charge. 

## member_invalid_port
**Message** : The specified member port `<member_port>` is invalid.

Indiquez un numéro de port valide. Les numéros de port valides sont compris entre 1 et 65535.

## member_invalid_weight
**Message** : The specified member weight `<member_weight>` is invalid.

Indiquez un poids de membre valide. Il doit s'agir d'un entier compris entre 0 et 100. 

## member_missing_address
**Message** : Member address is missing.

La zone d'adresse de membre est requise. Indiquez une adresse de membre dans votre demande. 

## member_missing_protocol_port
**Message** : Member port is missing.

La zone de port de membre est requise. Indiquez un port de membre dans votre demande. 

## member_over_quota
**Message** : Member cannot be created. Quota of member instances under the pool has reached maximum limit.

Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}. 

## missing_ims_account_id
**Message** : None

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## missing_version
**Message** : The `version` parameter is required, and it must be of the form `YYYY-MM-DD`.

Le format de la version doit être _AAAA-MM-JJ_. Pour les mois ou les dates à un seul chiffre, comme le 1er janvier, la version est similaire à `2019-01-01`. Le paramètre de version doit être présent dans l'adresse URL. La date indiquée dans le paramètre de version doit être ultérieure à la date 2019-01-01 et antérieure à la date en cours. Par exemple, pour obtenir la liste des clouds privés virtuels, ajoutez la version à la fin de la demande `GET "/v1/vpcs?version=2019-01-01”` 

## network_conflict
**Message** : CIDR conflicts with existing Address Prefix in VPC

Ce message peut s'afficher si vous indiquez un bloc CIDR de réseau qui entre en conflit avec un bloc CIDR de réseau existant dans le même espace d'IP. 

## not_authorized                               
**Message** : The request is not authorized.

En général, cette erreur s'affiche si votre jeton IAM manque ou a expiré. Pour des instructions de génération d'un jeton, voir [Création d'un cloud privé virtuel à l'aides des API REST](/docs/infrastructure/vpc/example-code.html#creating-a-vpc-using-the-rest-apis). Si le jeton n'a pas expiré, vérifiez vos droits et contactez votre administrateur.  

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_found
**Message** : Please check whether the resource you are requesting exists.

Vous avez référencé une ressource qui n'existe pas ou à laquelle vous n'avez pas accès. Vérifiez votre demande pour vous assurer que vous avez spécifié les références et les ID appropriés. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_implemented
**Message** : None

La méthode n'est pas implémentée. 

## not_in_address_prefix
**Message** : The provided CIDR does not fit in any of the address prefixes in the provided zone.

Cette erreur survient si un utilisateur tente de créer un sous-réseau avec un bloc CIDR qui ne correspond à aucun des préfixes d'adresse de la zone indiquée. 

Exécutez GET /vpcs/{vpc_id}/address_prefixes afin d'obtenir la liste des préfixes d'adresse pour le cloud privé virtuel. Consultez les valeurs de `cidr` et `zone` de la réponse et assurez-vous que la valeur `cidr` du sous-réseau correspond à un sous-ensemble de la valeur `cidr` du préfixe d'adresse pour la zone pour laquelle vous tentez de créer le sous-réseau. 

## over_quota                                    
**Message** : The request would exceed the quota for a resource type.

Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}. 

## password_not_ready
**Message** : None

Votre instance doit être en cours d'exécution pour que vous puissiez extraire le mot de passe. Réessayez dans quelques minutes. Si le problème persiste, contactez le support. 

## pool_delete_conflict
**Message** : Pool cannot be deleted because it is still associated with one or more listeners.

Assurez-vous que le pool est dissocié de tout écouteur et réessayez. 

## pool_duplicate_name
**Message** : Pool name `<pool_name>` is already used by another pool. Please choose a different name.

Choisissez un autre nom de pool. 

## pool_missing_algorithm
**Message** : Load balancing algorithm is missing.

La zone d'algorithme d'équilibrage de charge est requise. Indiquez l'algorithme d'équilibrage de charge dans votre demande. Les valeurs admises sont `round_robin`, `weighted_round_robin` et `least_connections`.

## pool_missing_health_monitor
**Message** : Pool health monitor is missing.

La zone de moniteur de santé du pool est requise. 

## pool_missing_name
**Message** : Pool name is missing.

La zone de nom du pool est requise. 

## pool_missing_protocol
**Message** : Pool protocol is missing.

La zone de protocole du pool est requise. Indiquez le protocole du pool dans votre demande. Les valeurs admises sont `http` et `tcp`.

## pool_not_found
**Message** : The pool with ID `<pool_id>` cannot be found.

Indiquez un ID de pool existant. 

## pool_over_quota
**Message** : Pool cannot be created. Quota of pools for the load balancer resource has reached maximum limit.

Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}. 

## public_gateway_in_use
**Message** : Cannot delete a public gateway when it is in use.

Actuellement, la passerelle publique est connectée à un ou plusieurs sous-réseaux. Vous devez déconnecter la passerelle publique de tous les sous-réseaux pour pouvoir la supprimer. 

## rate_limit_exceeded
**Message** : Too many requests within a short time.

Ce message d'erreur est renvoyé si un nombre trop élevé de demandes est reçu dans un intervalle de temps spécifié. Attendez un peu, puis réessayez.  

## security_group_active_transactions
**Message** : The interface cannot be attached or detached until the instance appears in Active state.

L'instance doit être active pour que ses interfaces réseau puissent être associées à un groupe de sécurité. Utilisez `GET /v1/instances/{id}?version=2019-01-01` ou `ibmcloud is instance` pour vérifier le statut de l'instance. Une fois que le statut est `en fonctionnement`, réessayez. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_already_attached
**Message** : The interface is already attached to the security group.


L'interface est déjà associée au groupe de sécurité. Utilisez `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` ou `ibmcloud is security-group-network-interfaces` pour afficher les interfaces associées. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_exists
**Message** : The security group already exists.


Les noms de groupe de sécurité doivent être uniques. Un groupe de sécurité de ce nom existe déjà. Utilisez `GET /v1/security_groups?version=2019-01-01` ou `ibmcloud is security-groups` pour afficher les groupes de sécurité en cours. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias) ou le document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_attached
**Message** : Cannot delete the security group while interfaces are attached.


Détachez toutes les interfaces avant de supprimer les groupes de sécurité. Utilisez `DELETE /v1/security_groups/{id}/network_interfaces/{id}?version=2019-01-01` ou `ibmcloud is security-group-network-interface-remove` pour détacher une interface. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias) ou le
document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_per_sg_exceeded
**Message** : Exceeded limit of interfaces per security group.

L'association d'une autre interface au groupe de sécurité entraînerait un dépassement du nombre maximal d'interfaces par groupe de sécurité. Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas). {: new_window}. Evaluez votre stratégie et envisagez de créer un autre groupe de sécurité avec des règles similaires. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias) ou le
document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_last_security_group_is_default
**Message** : The default security group cannot be removed when it is the only security group attached.

Une interface réseau doit être associée à un groupe de sécurité au moins.
Elle est associée au groupe de sécurité par défaut du cloud privé virtuel si aucun groupe de sécurité n'est spécifié.
Associez l'interface à un autre groupe de sécurité, puis essayez à nouveau de la dissocier du groupe de sécurité par défaut.
Pour des informations sur le groupe de sécurité par défaut, voir le document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_limit_exceeded
**Message** : Exceeded security group limit.

Vous avez tenté de créer un groupe de sécurité, mais vous avez déjà atteint le quota défini pour votre compte. Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Evaluez votre stratégie d'affectation d'instances à des groupes de sécurité. Souvent, il est possible de réduire le nombre global de groupes de sécurité en affectant plusieurs instances à un même groupe de sécurité. Cette stratégie permet de réduire le nombre de groupes de sécurité et de passer sous le quota défini pour votre compte. Rarement, en général pour les grandes organisations, il est nécessaire d'augmenter le quota. Dans ce cas, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) pour savoir si l'opération est possible. 

## security_group_network_interface_not_active
**Message** : The interface cannot be attached because it is not active.

Les interfaces réseau doivent être actives pour pouvoir être associées à des groupes de sécurité. Utilisez `GET /v1/instances/{id}/network_interfaces/{id}?version=2019-01-01` ou `ibmcloud is instance-network-interface` pour afficher le statut d'une interface. Une fois que le statut est 'disponible', réessayez. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_not_attached
**Message** : The interface is not attached.

L'interface n'est pas associée à un groupe de sécurité. Utilisez `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` ou `ibmcloud is security-group-network-interfaces` pour afficher les interfaces associées. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias) ou le document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group-using-the-cli){: new_window}. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_not_in_vpc
**Message** : The interface and security group are in different VPCs.

Pour que vous puissiez associer une interface réseau à un groupe de sécurité, l'instance doit se trouver dans le même cloud privé virtuel que le groupe de sécurité. Utilisez `GET /v1/security_groups/{id}?version=2019-01-01` ou `ibmcloud is security-group` pour afficher les détails des groupes de sécurité et le cloud privé virtuel. Utilisez `GET /v1/instances/{id}?version=2019-01-01` ou `ibmcloud is instance` pour afficher les détails de l'instance et le cloud privé virtuel. 

## security_group_order_bindings
**Message** : Cannot delete the security group while it has pending instance orders.

Si une instance a été créée avec un ou plusieurs groupes de sécurité spécifiés pour les interfaces réseau, l'instance et les interfaces réseau doivent être actives pour que le groupe de sécurité puisse être supprimé. Utilisez `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` ou `ibmcloud is security-group-network-interfaces` pour afficher les interfaces réseau associées et leur statut. Une fois que le statut des interfaces est 'disponible', réessayez. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_port_max_less_than_port_min
**Message** : TCP/UDP max port cannot be less than min port.

La valeur de port maximale ne peut pas être inférieure à la valeur de port minimale. Spécifiez une valeur de port maximale supérieure à la valeur de port minimale. 

## security_group_port_range_both_or_neither
**Message** : Port range must be unset, or both a minimum and maximum port must be set for 'tcp' and 'udp'.

Les règles associées à un protocole 'tcp' ou 'udp' peuvent ne pas avoir de plage de ports définie (pour qu'elles puissent être appliquées à l'intégralité du trafic) ou spécifier une plage de ports. Pour restreindre le trafic à un seul port, définissez la valeur de port comme valeur de port minimale et valeur de port maximale. Par exemple, la commande suivante crée une règle qui permet l'exécution de SSH sur le port 22 : `ibmcloud is security-group-rule-add <id> inbound tcp --port-min 22 --port-max 22`.

Pour plus d'informations sur les configurations de règles de groupe de sécurité, voir la [documentation d'API](https://{DomainName}/apidocs/rias). 


## security_group_port_range_invalid_protocol
**Message** : A port range was specified with a protocol of 'icmp'. A port range is only valid for a protocol of 'tcp' or 'udp'.

Les règles associées au protocole 'icmp' possèdent un type et un code. Les règles associées au protocole 'tcp' ou 'udp' possèdent une plage de ports. Pour plus d'informations sur les configurations de règles de groupe de sécurité, voir la [documentation d'API](https://{DomainName}/apidocs/rias). 

## security_group_remote_group_not_in_vpc
**Message** : The remote group is not in the same VPC as this security group.

Les règles de groupe de sécurité peuvent faire référence à un groupe de sécurité distant et permettre le trafic entre les interfaces associées des deux groupes. Les groupes de sécurité distants doivent se trouver dans le même cloud privé virtuel. Utilisez `GET /v1/security_groups?2019-01-01` ou `ibmcloud is security-groups` pour afficher les groupes de sécurité en cours et leurs clouds privés virtuels. 

Pour plus d'instructions relatives à la résolution de ce problème, voir le document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}. 


## security_group_remoting_rules
**Message** : Cannot delete the security group while remoting rules are attached.

Le groupe de sécurité contient une ou plusieurs règles qui référencent un groupe de sécurité distant. Utilisez `GET /v1/security_groups/{id}/rules?version=2019-01-01` ou `ibmcloud is security-group-rules` pour afficher les règles. La zone 'remote' spécifie les groupes de sécurité distants. Réessayez après avoir supprimé ou édité la règle d'accès distant. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias) ou le document [Utilisation de groupes de sécurité](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}. 


## security_group_remoting_rules_per_sg_exceeded
**Message** : Exceeded limit of remoting rules per security group.


L'ajout d'une autre règle faisant référence à un groupe de sécurité distant entraînerait le dépassement du nombre maximal de règles d'accès distant par groupe de sécurité. Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. 


## security_group_rules_per_sg_exceeded
**Message** : Exceeded limit of rules per security group.

L'ajout d'une règle entraînerait le dépassement du nombre maximal de règles par groupe de sécurité. Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Evaluez votre stratégie et envisagez de créer un autre groupe de sécurité. 


## security_group_sgs_per_interface_exceeded
**Message** : Exceeded limit of security groups per interface.

L'association de cette interface à un autre groupe de sécurité entraînerait le dépassement du nombre maximal de groupes de sécurité par interface. Les quotas par ressource sont indiqués dans la page des [quotas et des limites pour les clouds privés virtuels](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Evaluez votre stratégie et envisagez d'ajouter des règles à un groupe de sécurité existant. 


## security_group_type_code_invalid_protocol
**Message** : An 'icmp' type/code was given, but the requested protocol was not 'icmp'. Set the protocol to 'icmp' or specify a port range.

Seules les règles associées au protocole 'icmp' possèdent un type et un code. Les règles associées au protocole 'tcp' ou 'udp' possèdent une plage de ports. Pour plus d'informations sur les configurations de règles de groupe de sécurité, voir la [documentation d'API](https://{DomainName}/apidocs/rias). 

## security_group_vpc_default
**Message** : Cannot delete the default security group for a VPC.

Le groupe de sécurité par défaut ne peut pas être supprimé. Pour des informations sur le groupe de sécurité par défaut, voir le guide relatif à la [mise à jour du groupe de sécurité par défaut](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group).

## service_manager_service_failure
**Message** : None

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_acl_conflict
**Message** : Cannot delete the network ACL, it is attached to a subnet.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_conflict
**Message** : CIDR conflicts with existing Subnet in VPC.

Exécutez l'API GET /subnets pour extraire tous les sous-réseaux du cloud privé virtuel. Assurez-vous que le bloc CIDR que vous avez fourni n'est pas utilisé pas d'autres sous-réseaux en vérifiant la valeur de `ipv4_cidr_block`.

Si vous utilisez l'interface de ligne de commande, vous pouvez exécuter `ibmcloud is subnets` et consulter la valeur de "Subnet CIDR" pour déterminer s'il existe des conflits. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty
**Message** : The subnet is not empty, please contact your administrator.

Une demande de suppression d'un sous-réseau a été émise, mais des ressources existent encore sur le sous-réseau en question. Les sous-réseaux peuvent héberger des instances, des réseaux privés locaux, des équilibreurs de charge ou des passerelles publiques. Vous devez supprimer les ressources qui se trouvent sur le sous-réseau pour pouvoir supprimer le sous-réseau.  

Dans certains cas, cette erreur peut survenir même si la console indique qu'il n'existe pas d'instance de serveur virtuel ni d'équilibreur de charge, car la suppression est asynchrone et le changement du statut interne peut prendre quelques minutes. Attendez quelques minutes et essayez à nouveau de supprimer votre sous-réseau. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_pgway_exists
**Message** : Cannot delete the subnet while it is attached to a public gateway. Please detach the public gateway and retry.

Une demande de suppression d'un sous-réseau a été émise, mais une passerelle publique est encore associée au sous-réseau. Vous devez supprimer ou détacher la passerelle publique pour pouvoir supprimer le sous-réseau.  

Si vous utilisez l'interface de ligne de commande, vous pouvez exécuter `ibmcloud is public-gateways` pour répertorier les passerelles publiques et `ibmcloud is subnet-public-gateway-detach` pour détacher la passerelle publique d'un sous-réseau.  

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_ipaddr_exists
**Message** : Cannot delete the subnet while it contains IP addresses. Please delete any server instance associated with the IP address and retry.

Une demande de suppression d'un sous-réseau a été émise, mais il existe encore des adresses IP sur le sous-réseau en question. Vous devez supprimer l'instance de serveur associée à l'adresse IP pour pouvoir supprimer le sous-réseau. 

Si vous utilisez l'interface de ligne de commande, vous pouvez exécuter `ibmcloud is instances` pour répertorier les instances de serveur et consulter la valeur de "Address" afin de déterminer leur statut. Exécutez `ibmcloud is instance-delete` pour supprimer une instance de serveur dont le statut n'est pas déjà "suppression".  

Dans certains cas, cette erreur peut survenir même si la console indique qu'il n'existe pas d'instance de serveur virtuel, car la suppression est asynchrone et le changement du statut interne peut prendre quelques minutes. Attendez quelques minutes et essayez à nouveau de supprimer votre sous-réseau. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_loadbalancer_exists
**Message** : Cannot delete the subnet while it contains a load balancer. Please delete the load balancer and retry.

Une demande de suppression d'un sous-réseau a été émise, mais il existe encore un équilibreur de charge sur le sous-réseau en question. Vous devez supprimer l'équilibreur de charge pour pouvoir supprimer le sous-réseau. 

Si vous utilisez l'interface de ligne de commande, vous pouvez exécuter `ibmcloud is load-balancers` pour répertorier les équilibreurs de charge et consulter la valeur "Subnets" pour déterminer leur sous-réseau et la valeur de "Status" pour déterminer leur statut. Exécutez `ibmcloud is load-balancer-delete` pour supprimer un équilibreur de charge dont le statut n'est pas déjà "suppression".  

Dans certains cas, cette erreur peut survenir même si la console indique qu'il n'existe pas d'équilibreur de charge, car la suppression est asynchrone et le changement du statut interne peut prendre quelques minutes. Attendez quelques minutes et essayez à nouveau de supprimer votre sous-réseau. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_vpn_gway_exists
**Message** : Cannot delete the subnet while it contains a VPN gateway. Please delete the VPN gateway and retry.

Une demande de suppression d'un sous-réseau a été émise, mais une passerelle VPN est encore associée au sous-réseau. Vous devez supprimer la passerelle VPN pour pouvoir supprimer le sous-réseau.  

Si vous utilisez l'interface de ligne de commande, vous pouvez exécuter `ibmcloud is vpn-gateways` pour répertorier les équilibreurs de charge et consulter la valeur "Subnets" pour déterminer leur sous-réseau et la valeur de "Status" pour déterminer leur statut. Exécutez `ibmcloud is vpn-gateway-delete` pour supprimer une passerelle VPN dont le statut n'est pas déjà "suppression".  

Dans certains cas, cette erreur peut survenir même si la console indique qu'il n'existe pas de passerelle VPN, car la suppression est asynchrone et le changement du statut interne peut prendre quelques minutes. Attendez quelques minutes et essayez à nouveau de supprimer votre sous-réseau. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_unknown_state
**Message** : None

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## system_limit_exceeded
**Message** : This operation would exceed a system limit

Il se peut que vous receviez ce message d'erreur si vous essayez de créer un préfixe d'adresse alors que le nombre maximal de préfixes d'adresse a déjà été atteint. 

## target_in_use
**Message** : The target already has floating IP attached.

## token_invalid
**Message** : The service token was expired or invalid.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## token_missing
**Message** : The service token was empty or did not exist in the request.

Recréez un jeton et réessayez. 

## validation_enum
**Message** : The value supplied was not a valid option.

L'une des zones fournies possède une valeur qui doit provenir d'une énumération de valeurs possibles. 

Pour les règles de liste de contrôle d'accès au réseau, vous pouvez spécifier une direction : 

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum:
[ inbound, outbound ]
```

Par exemple, la valeur suivante n'est pas valide car `northbound` n'est pas une option valide dans l'énumération `[ inbound, outbound ]`. 

```json
{
    "direction":"northbound"
}
```

## validation_failure                            
**Message** : The JSON provided did not match the expected structure.

Pour résoudre ce problème, assurez-vous que le contenu de votre demande est au format JSON et que votre demande est conforme à la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_invalid_cidr                       
**Message** : The value is not a valid CIDR.

La valeur doit être un bloc CIDR interne valide avec une partie hôte 0. 

Certaines plages d'adresses IP sont réservées. Vous trouverez plus d'informations sur les plages d'IP réservées dans la présentation de l'[utilisation de votre cloud privé virtuel avec des régions et des sous-réseaux](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}. 

## validation_invalid_ipv4_cidr        
**Message** : The value is not a valid IPv4 CIDR.

Il doit s'agir d'un bloc CIDR interne IPv4 avec une partie hôte 0. 

Certaines plages d'adresses IP sont réservées. Vous trouverez plus d'informations sur les plages d'IP réservées dans la présentation de l'[utilisation de votre cloud privé virtuel avec des régions et des sous-réseaux](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}. 

## validation_invalid_ipv6_cidr
**Message** : The value is not a valid IPv6 CIDR.

Actuellement, IPv6 n'est pas pris en charge. Utilisez une adresse IPv4.

## validation_invalid_address
**Message** : The value is not a valid address.

Il doit s'agir d'une adresse IP valide. 

La liste des adresses IP réservées individuellement est indiquée dans le document relatif aux [aux régions et aux sous-réseaux](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets). 

## validation_invalid_ipv4_address
**Message** : The value is not a valid IPv4 address.

Indiquez une adresse IPv4 valide. 

## validation_invalid_ipv6_address
**Message** : The value is not a valid IPv6 address.

Indiquez une adresse IPv6 valide. Actuellement, IPv6 n'est pas pris en charge ; utilisez une adresse IPv4. 

## validation_invalid_field_type
**Message** : The value type does not match the field type.

Pour résoudre ce problème, assurez-vous que le contenu de votre demande est conforme à la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_max_value
**Message** : The value supplied was too large.

Indiquez une valeur plus petite qui ne dépasse pas la valeur maximale telle qu'indiquée par la spécification. Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_min_value
**Message** : The value supplied was too small.

Indiquez une valeur plus grande supérieure à la valeur minimale telle qu'indiquée par la spécification. Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_not_null
**Message** : The field supplied must be null.

Assurez-vous que la valeur est nulle. Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

Exemple non valide : 

```json
{
    "name": null
}
```

## validation_only_one
**Message** : The value must match one of the subschemas.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## validation_discriminator_forbidden
**Message** : The discriminator field forbids this substructure.

Par exemple, si vous spécifiez 
```
{
protocol: icmp
port_min: 5
port_max: 100
}
```

le protocole est `icmp`, et _port_min_ est une zone `tcp` ; par conséquent, une erreur est générée. 
1. validation_discriminator_required pour les règles `icmp` manquantes 
2. validation_discriminator_forbidden pour les zones `tcp` avec `icmp` spécifié 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_internal_error
**Message** : None

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_invalid_name
**Message** : The value is not a valid name.


## validation_invalid_ref
**Message** : The value is not a valid HREF.


## validation_non_empty_uuid
**Message** : None

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_required_field
**Message** : Missing a required field.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_unique_failed
**Message** : The field supplied must be unique.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

Il se peut que le nom que vous avez spécifié soit déjà utilisé. Essayez une autre valeur. 

## vpc_acl_conflict                           
**Message** : Cannot delete the default network ACL, it is attached to a VPC.

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias) ou le document relatif à l'[utilisation de listes de contrôle d'accès au réseau](/docs/infrastructure/vpc-network?topic=vpc-network-setting-up-network-acls-using-the-cli){: new_window}. 

Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_not_empty
**Message** : The VPC cannot be deleted because it is not empty.

Toutes les ressources doivent être retirées d'un cloud privé virtuel pour que celui-ci puisse être supprimé. 

Ce message d'erreur peut s'afficher s'il existe encore une passerelle dans votre cloud privé virtuel, même si tous les sous-réseaux ont été supprimés, car la passerelle peut exister dans le cloud privé virtuel sans sous-réseau. Il peut être nécessaire d'utiliser l'interface de ligne de commande pour rechercher les ressources orphelines. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_resource_separation
**Message** : The resources are in different VPCs

## vpn_connection_cidr_not_created
**Message** : A CIDR block could not be added to the VPN connection `<vpn_connection_id>`.

Indiquez un bloc CIDR valide qui répond aux exigences imposées par la spécification.  

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_cidr_not_deleted
**Message** : A CIDR block could not be deleted from the VPN connection `<vpn_connection_id>`.

Indiquez un bloc CIDR valide qui existe dans la connexion. Une connexion doit posséder au moins un bloc CIDR local et un bloc CIDR homologue. 

Pour afficher les blocs CIDR de la connexion, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` et consultez les zones `local_cidrs` et `peer_cidrs`. 

## vpn_connection_cidr_not_found
**Message** : The CIDR block was not found in the VPN connection `<vpn_connection_id>`.

Indiquez un bloc CIDR valide qui se trouve dans la connexion. 

Pour afficher les blocs CIDR de la connexion, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` et consultez les zones `local_cidrs` et `peer_cidrs`. 

## vpn_connection_cidr_not_valid
**Message** : The CIDR block `<cidr_block>` does not represent a valid address.

La valeur doit être un bloc CIDR interne valide sans ensemble de bits hôte. 

Pour afficher les blocs CIDR de la connexion, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` et consultez les zones `local_cidrs` et `peer_cidrs`. 

## vpn_connection_cidr_overlap
**Message** : The CIDR block `<cidr_block_1>` overlaps with `<cidr_block_2>`. Two peer CIDR blocks cannot overlap on the same VPC and two local CIDR blocks cannot overlap on the same connection.

Indiquez une valeur de bloc CIDR valide qui répond aux exigences imposées par la spécification. 

Pour afficher les blocs CIDR de la connexion, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` et consultez les zones `local_cidrs` et `peer_cidrs`. 

## vpn_connection_duplicate_name
**Message** : The name `<vpn_connection_name>` is already in use by VPN connection `<vpn_connection_id>`.

Indiquez un autre nom de connexion. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_invalid_name
**Message** : The name `<vpn_connection_name>` is not a valid VPN connection name.

Un nom de connexion valide commence par une lettre, suivie d'autres lettres, de chiffres, de traits de soulignement ou de traits d'union. 

## vpn_connection_invalid_psk_format
**Message** : The pre-shared key (PSK) `<psk>` is not in the valid format.

Une clé pré-partagée valide contient entre 6 et 128 caractères, qui peuvent être des lettres, des chiffres, et les signes `-`,`+`,`&`,`!`,`@`,`#`,`$`,`%`,`^`,`*`,`(`,`)`,`,`,`.`,`:`,`_`.

## vpn_connection_local_cidrs_required
**Message** : At least one local CIDR block is required when creating a VPN connection.

Indiquez une valeur de bloc CIDR local valide qui répond aux exigences imposées par la spécification. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_connection_local_subnets_quota_exceeded
**Message** : The quota for local subnets across VPN connections exceeded for VPN gateway `<vpn_gateway_id>`.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les sous-réseaux locaux en cours des connexions VPN, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections` et consultez la zone `local_cidrs` pour chaque connexion. 

## vpn_connection_local_subnets_quota_exceeded_for_connection
**Message** : The quota of '<quota_limit>' local subnets for VPN connection is exceeded.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vp?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les sous-réseaux locaux en cours pour une connexion VPN, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` et consultez la zone `local_cidrs`. 

## vpn_connection_not_found
**Message** : The VPN connection `<vpn_connection_id>` could not be found.

Indiquez si l'ID de connexion est correct. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_peer_cidrs_required
**Message** : At least one peer CIDR block is required when creating a VPN connection.

Indiquez une valeur de bloc CIDR homologue valide qui répond aux exigences imposées par la spécification. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_connection_peer_subnets_quota_exceeded
**Message** : The quota for peer subnets across VPN connections is exceeded for the VPN gateway `<vpn_gateway_id>`.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les sous-réseaux homologues en cours des connexions VPN, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections` et consultez la zone `peer_cidrs` pour chaque connexion. 

## vpn_connection_peer_subnets_quota_exceeded_for_connection
**Message** : The quota of `<quota_limit>` peer subnets for VPN connection is exceeded.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les sous-réseaux homologues en cours pour une connexion VPN, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` et consultez la zone `peer_cidrs`. 

## vpn_connections_quota_exceeded
**Message** : The quota for VPN connections is exceeded for the VPN gateway `<vpn_gateway_id>`.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les connexions VPN en cours pour une passerelle VPN, utilisez l'API `GET /vpn_gateways/<vpn_gateway_id>/connections`. 

## vpn_connection_static_route_not_created
**Message** : Failed to add a static route for the CIDR block `<peer_cidr>`.

Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_static_route_not_deleted
**Message** : Failed to remove a static route for the CIDR block `<peer_cidr>`.

Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_update_cidrs_not_permitted
**Message** : CIDR blocks cannot be changed when updating a connection. Please use the correct API when creating or deleting CIDRs.

Indiquez une valeur de demande valide qui répond aux exigences imposées par la spécification. 

Pour plus d'instructions relatives à la résolution de ce problème, voir la [documentation d'API](https://{DomainName}/apidocs/rias){: new_window}. 

## vpn_gateway_duplicate_name
**Message** : The name `<vpn_gateway_name>` is already in use by VPN gateway `<vpn_gateway_id>`.

Indiquez un autre nom de passerelle VPN. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_initialization_error
**Message** : The VPN gateway could not be initialized.

Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_invalid_name
**Message** : The name `<vpn_gateway_name>` is not a valid VPN gateway name.

Un nom de passerelle VPN valide commence par une lettre, suivie d'autres lettres, de chiffres, de traits de soulignement ou de traits d'union. 

## vpn_gateway_invalid_state
**Message** : The VPN gateway `<vpn_gateway_id>` is in an invalid state for the requested operation.

La passerelle VPN doit être associée au statut `disponible` pour que vous puissiez vous en servir. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_ip_create_error
**Message** : Unable to create an IP address for the VPN gateway.

Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_not_found
**Message** : The VPN gateway `<vpn_gateway_id>` could not be found.

Vérifiez que l'ID de passerelle VPN est correct. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_not_found
**Message** : Could not find the subnet `<subnet_id>` for the given VPN gateway.

Vous avez référencé un sous-réseau qui n'existe pas. Vérifiez votre demande pour vous assurer que vous avez spécifié l'ID de sous-réseau approprié. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_status_error
**Message** : The VPN gateway could not be created due to subnet status.

Indiquez un sous-réseau dont le statut est `disponible`. Réessayez dans quelques minutes. Si ce problème persiste, [contactez le support](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateways_quota_exceeded
**Message** : Quota for VPN gateways exceeded for the account and/or the region.

Les quotas par ressource sont indiqués dans la page [Quotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}. 

Pour afficher les passerelles VPN en cours, utilisez l'API `GET /vpn_gateways`. 
