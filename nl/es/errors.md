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

# Mensajes de error de la API de IBM Cloud Virtual Private Cloud
{: #rias-error-messages}

Cuando reciba un mensaje de error de las API de nube privada virtual de {{site.data.keyword.cloud}}, puede utilizar el ID del mensaje para encontrar más información sobre cómo resolver el problema.
{:shortdesc}

## acl_in_use
**Mensaje**: La ACL de red no se puede suprimir porque está conectada a recursos.

La ACL de red no se puede suprimir porque está conectada a recursos. Compruebe las subredes.

## address_prefix_conflict
**Mensaje**: El prefijo de dirección con este CIDR se está utilizando.

El CIDR correspondiente al prefijo de dirección solicitado está en conflicto con un prefijo de dirección existente.

## address_prefix_in_use
**Mensaje**: No se puede suprimir un prefijo de dirección en uso.

Una o varias subredes están utilizando el prefijo de dirección. Debe desconectar todas las subredes para poder suprimir un prefijo.

## backend_service_unavailable
**Mensaje**: El servicio de fondo no está disponible.

Un servicio de nube de fondo no ha respondido. Una causa para recibir este error podría ser que falta una señal IAM o que está caducada. Vuelva a intentarlo en unos minutos. Si el problema continúa, póngase en contacto con el equipo de soporte.

## bad_field
**Mensaje**: Se debe proporcionar el UUID de instancia correcto

Se debe proporcionar un nuevo nombre de volumen

Vuelva a intentarlo, proporcionando un UUID o un volumen válido en la solicitud. 

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## bad_request                                   
**Mensaje**: La información proporcionada no es válida, está mal formada o falta un campo necesario.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## classic_access_vpc_conflict_duplicate_res
**Mensaje**: Solo se puede crear una VPC de acceso clásico.

No se puede crear más de una VPC de acceso clásico para una cuenta

## default_address_prefix_not_found
**Mensaje**: No se ha encontrado el prefijo de dirección predeterminado.

Es posible que vea este mensaje de error cuando no se encuentre el prefijo de dirección predeterminado.

## duplicate_error
**Mensaje**: La entrada proporcionada ya existe.

El recurso que ha especificado ya existe. Para solucionar este problema, utilice otro nombre para el recurso que desea crear. Por ejemplo, cuando cree una nueva VPC, puede revisar una lista de nombres de las VPC ya creadas y elegir un nombre que no entre en conflicto, si primero llama a `getVPC` utilizando el ID, como en este ejemplo: `GET "/v1/vpcs/{id}" -H  "accept: application/json"`. 

## floating_ip_in_use
**Mensaje**: La IP flotante se está utilizando.

Esta IP flotante ya está asociada a una interfaz de red o a una pasarela pública.

## floating_ip_not_empty
**Mensaje**: No se puede suprimir un servidor con una IP flotante asociada.

Asegúrese de eliminar la asociación de la IP flotante antes de suprimir el servidor. 

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## gateway_too_many
**Mensaje**: Solo se puede tener una pasarela pública por zona en una VPC.

Solo se permite una pasarela pública por zona en una VPC, pero la pasarela pública se puede conectar a varias subredes en la zona. Para encontrar la pasarela pública para una zona, ejecute la API GET public_gateways y examine los valores "vpc" y "zone". Si utiliza la CLI, ejecute el mandato `ibmcloud is public-gateways` y examine el valor de "VPC" y "Zone".

Utilice el ID de la pasarela pública para conectarla a una subred; encontrará un ejemplo en nuestros [ejemplos de API](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis#step-13-attach-the-public-gateway-to-the-subnet-). Si utiliza la CLI, utilice el mandato de actualización de subred para conectarla a una pasarela pública, como en este ejemplo: `ibmcloud is subnet-update SUBNET_ID --public-gateway-id PUBLIC_GATEWAY_ID`.


## http_request_size_exceeded                    
**Mensaje**: La solicitud HTTP es demasiado larga.

Este problema se produce cuando la carga útil que ha enviado en la solicitud tiene demasiados caracteres. Inténtelo de nuevo con una carga útil más corta. Por ejemplo, en lugar de intentar hacer todo en una sola solicitud, intente crear un recurso mínimo en una solicitud y luego añada el estado al mismo de forma incremental en varias solicitudes posteriores. 

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## iam_failure
**Mensaje**: Ninguno

Este mensaje puede aparecer cuando se ha producido una anomalía en el servicio IAM, al verificar la autenticación o la autorización. Esta interrupción del servicio IAM puede ser temporal. Vuelva a intentar la solicitud transcurridos unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policies_quota_exceeded
**Mensaje**: Se ha excedido la cuota de políticas de IKE para la cuenta.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las políticas de IKE actuales, utilice la API `GET /ike_policies`.

## ike_policy_duplicate_name
**Mensaje**: El nombre `<ike_policy_name>` ya está siendo utilizado por la política de IKE `<ike_policy_id>`.

Especifique otro nombre de política de IKE. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policy_in_use
**Mensaje**: La política de IKE `<ike_policy_id>` ya está siendo utilizada por una o varias conexiones.

Una política de IKE no se puede suprimir si hay una o varias conexiones que la están utilizando.

## ike_policy_invalid_name
**Mensaje**: El nombre `<ike_policy_name>` no es un nombre de política de IKE válido.

Un nombre de política de IKE válido comienza por una letra, seguida de letras, dígitos, signos de subrayado o guiones.

## ike_policy_not_found
**Mensaje**: La política de IKE `<ike_policy_id>` no se ha podido encontrar.

Ha hecho referencia a una política de IKE que no existe. Revise su solicitud para asegurarse de que ha especificado el ID de política de IKE adecuado. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## insufficient_space_for_subnet
**Mensaje**: No hay suficiente espacio para la subred en el prefijo de dirección

Es posible que reciba este error si intenta crear una subred y esta no se puede crear porque no se puede asignar el número de direcciones solicitadas.

## internal_error
**Mensaje**: Se ha producido un error interno.

Inténtelo de nuevo. Si este error continúa, póngase en contacto con el equipo de soporte.

## internal_server_error
**Mensaje**: Ninguno

Este error se produce cuando el servicio detecta un error inesperado. Este problema puede ser temporal. Vuelva a intentar la solicitud transcurridos unos minutos.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## internal_solution
**Mensaje**: Póngase en contacto con el administrador.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_id_format
**Mensaje**: Formato de ID incorrecto. Asegúrese de que el formato sea correcto.

Asegúrese de que el ID que ha proporcionado no contiene ningún dato mal formado.

Puede recibir este mensaje de error si se utiliza una consulta de inicio mal formada cuando se realiza una solicitud de paginación. Por ejemplo, `GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` contiene dos signos `?`. Corrija la consulta y vuélvalo a intentar.

## invalid_state
**Mensaje**: Ninguno

El mandato de RIAS `ibmcloud is in-reboot Instance_uuid` puede devolver el código de mensaje "invalid_state"

En una situación, el mensaje se emite cuando se intenta realizar una operación de rearranque mientras la VSI ya se está rearrancado. Este mensaje también se puede recibir en una situación en la que no se están produciendo varios rearranques al mismo tiempo.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_version
**Mensaje**: El parámetro `version` no es válido, debe tener el formato `AAAA-MM-DD`.

La versión debe ajustarse al formato _AAAA-MM-DD_. En el caso de meses o fechas de un solo dígito, como el 1 de enero, la versión debe tener este formato: `2019-01-01`. El parámetro de versión debe aparecer en el URL. La fecha especificada en el parámetro de versión debe ser posterior al 1 de enero de 2019 y anterior a la fecha actual. Por ejemplo, para obtener una lista de VPC, añada la versión al final de la solicitud `GET "/v1/vpcs?version=2019-01-01"`.

## invalid_version_range
**Mensaje**: El valor de `version` no se puede establecer en una fecha futura ni anterior a `2019-01-01`.

La versión debe ajustarse al formato _AAAA-MM-DD_. En el caso de meses o fechas de un solo dígito, como el 1 de enero, la versión debe tener este formato: `2019-01-01`. El parámetro version debe aparecer en el URL. La fecha especificada en el parámetro de versión debe ser posterior al 1 de enero de 2019 y anterior a la fecha actual. Por ejemplo, para obtener una lista de VPC, añada la versión al final de la solicitud `GET "/v1/vpcs?version=2019-01-01"`.

## invalid_zone
**Mensaje**: Compruebe si los recursos que está solicitando se encuentran en la misma zona.

Puede ver este mensaje si el recurso que se ha solicitado no está en una zona válida.

## ipsec_policies_quota_exceeded
**Mensaje**: Se ha excedido la cuota de políticas de IPsec para la cuenta.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las políticas de IPsec actuales, utilice la API `GET /ipsec_policies`.

## ipsec_policy_duplicate_name
**Mensaje**: El nombre `<ipsec_policy_name>` ya está siendo utilizado por la política de IPsec `<ipsec_policy_id>`.

Especifique otro nombre de política de IPsec. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ipsec_policy_in_use
**Mensaje**: La política de IPsec `<ipsec_policy_id>` ya está siendo utilizada por una o varias conexiones.

Una política de IPsec no se puede suprimir si hay una o varias conexiones que la están utilizando.

## ipsec_policy_invalid_name
**Mensaje**: El nombre `<ipsec_policy_name>` no es un nombre de política de IPsec válido.

Un nombre de política de IPsec válido comienza por una letra, seguida de letras, dígitos, signos de subrayado o guiones.

## ipsec_policy_not_found
**Mensaje**: La política de IPsec `<ipsec_policy_id>` no se ha podido encontrar.

Ha hecho referencia a una política de IPsec que no existe. Revise su solicitud y asegúrese de que ha especificado el ID de política de IPsec adecuado. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## key_exists
**Mensaje**: Este contenido de clave ya existe.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## listener_certificate_not_found
**Mensaje**: La instancia de certificado con CRN `<listener_certificate_crn>` no se ha encontrado o no hay permiso para acceder a la instancia de certificado.

Especifique un CRN de instancia de certificado existente o solicite al administrador de la cuenta que le otorgue permiso de acceso a la instancia de certificado proporcionada.

## listener_duplicate_port
**Mensaje**: El puerto `<listener_port>` está siendo utilizado por otra instancia de escucha. Elija otro puerto.

Elija otro puerto.

## listener_invalid_certificate
**Mensaje**: El CRN de la instancia de certificado para el escucha HTTPS no es válido.

Proporcione un CRN de instancia de certificado válido.

## listener_invalid_connection_limit
**Mensaje**: El límite de conexiones de escucha `<listener_connection_limit>` no es válido.

Especifique un límite de conexiones válido. El límite de conexiones debe ser un entero comprendido entre 1 y 15000.

## listener_invalid_port
**Mensaje**: El puerto de escucha `<listener_port>` no es válido.

Elija otro puerto.

## listener_invalid_protocol
**Mensaje**: El protocolo de escucha `<listener_protocol>` no es válido.

Especifique un protocolo de escucha válido. Los valores válidos para el protocolo de escucha son `http`, `https` y `tcp`.

## listener_missing_certificate_crn
**Mensaje**: Falta el CRN de la instancia de certificado para el escucha `https`.

El CRN de la instancia de certificado es un campo obligatorio.

## listener_missing_port
**Mensaje**: Falta el puerto de escucha.

El puerto de escucha es un campo obligatorio.

## listener_missing_protocol
**Mensaje**: Falta el protocolo de escucha.

El protocolo de escucha es un campo obligatorio. Especifique el protocolo de escucha en la solicitud. Los valores válidos son
`http`, `https` y `tcp`.

## listener_not_found
**Mensaje**: El escucha con el ID `<listener_id>` no se ha podido encontrar.

Especifique un ID de escucha existente.

## listener_over_quota
**Mensaje**: No se puede crear el escucha. La cuota de escuchas para el recurso del equilibrador de carga ha alcanzado el límite máximo.

Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## listener_pool_protocols_conflict
**Mensaje**: El protocolo de escucha (`<listener_protocol>`) y el protocolo de agrupación (`<pool_protocol>`) están en conflicto.

Un escucha con el protocolo `https` o `http` solo se puede asociar con una agrupación con el protocolo `http`. Paralelamente, un escucha `tcp` solo se puede asociar a una agrupación `tcp`.

## listener_reserved_port_conflict
**Mensaje**: El puerto de escucha `<listener_port>` es uno de los puertos reservados. El rango de puertos 56500 a 56520 está reservado para fines de gestión y no se puede utilizar. Elija otro puerto.

Elija otro puerto.

## load_balancer_duplicate_name
**Mensaje**: El nombre `<load_balancer_name>` está siendo utilizado por otra instancia del equilibrador de carga. Elija otro nombre.

Especifique otro nombre para la instancia del equilibrador de carga.

## load_balancer_invalid_description
**Mensaje**: La descripción del equilibrador de carga `<load_balancer_description>` no es válida.

La descripción del equilibrador de carga no puede superar los 255 caracteres.

## load_balancer_invalid_is_public
**Mensaje**: El valor de is_public `<load_balancer_is_public>` no es válido.

El valor de is_public del equilibrador de carga debe ser true o false.

## load_balancer_invalid_is_public_value
**Mensaje**: Solo se da soporte a equilibradores de carga públicos.

Los equilibradores de carga privados aún no reciben soporte.

## load_balancer_invalid_name
**Mensaje**: El nombre `<load_balancer_name>` no es válido.

El nombre no debe estar en blanco. La longitud del nombre no debe superar los 40 caracteres. Un nombre de equilibrador de carga válido comienza por una letra, seguida de letras, dígitos y signos de subrayado.

## load_balancer_missing_is_public
**Mensaje**: Falta el campo 'is_public'.

'is_public' es un campo obligatorio. Especifique el campo is_public del equilibrador de carga.

## load_balancer_missing_name
**Mensaje**: Falta el nombre del equilibrador de carga.

Especifique el nombre del equilibrador de carga. El nombre del equilibrador de carga es un campo obligatorio.

## load_balancer_missing_subnets
**Mensaje**: Faltan las subredes del equilibrador de carga.

'subnets' es un campo obligatorio. Especifique las subredes en las que se va a crear el equilibrador de carga en la solicitud.

## load_balancer_not_found
**Mensaje**: El equilibrador de carga con el ID `<load_balancer_id>` no se ha podido encontrar.

Especifique un ID de equilibrador de carga existente.

## load_balancer_over_quota
**Mensaje**: No se puede crear el equilibrador de carga. La cuota de instancias del equilibrador de carga bajo su cuenta ha alcanzado el límite máximo.

Suprima un equilibrador de carga existente o póngase en contacto con el servicio de soporte para aumentar la cuota del equilibrador de carga de la cuenta.

Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## load_balancer_unchanged_update
**Mensaje**: No hay nada que actualizar en el equilibrador de carga con el ID `<load_balancer_id>`.

No hay nada que actualizar en la instancia del equilibrador de carga.

## member_invalid_port
**Mensaje**: El puerto del miembro especificado `<member_port>` no es válido.

Especifique un número de puerto válido. Los números de puerto válidos son los comprendidos entre 1 y 65535.

## member_invalid_weight
**Mensaje**: La ponderación de miembro especificada `<member_weight>` no es válida.

Proporcione una ponderación de miembro válida. Tiene que ser un entero comprendido entre 0 y 100.

## member_missing_address
**Mensaje**: Falta la dirección del miembro.

La dirección del miembro es un campo obligatorio. Especifique una dirección de miembro en la solicitud.

## member_missing_protocol_port
**Mensaje**: Falta el puerto del miembro.

El puerto del miembro es un campo obligatorio. Especifique el puerto del miembro en la solicitud.

## member_over_quota
**Mensaje**: No se puede crear el miembro. La cuota de instancias del miembro bajo la agrupación ha alcanzado el límite máximo.

Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## missing_ims_account_id
**Mensaje**: Ninguno

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## missing_version
**Mensaje**: El parámetro `version` es obligatorio y debe tener el formato `AAAA-MM-DD`.

La versión debe ajustarse al formato _AAAA-MM-DD_. En el caso de meses o fechas de un solo dígito, como el 1 de enero, la versión debe tener este formato: `2019-01-01`. El parámetro version debe aparecer en el URL. La fecha especificada en el parámetro de versión debe ser posterior al 1 de enero de 2019 y anterior a la fecha actual. Por ejemplo, para obtener una lista de las VPC, añada la versión al final de la solicitud `GET "/v1/vpcs?version=2019-01-01”`.cs?version=2019-01-01”`

## network_conflict
**Mensaje**: CIDR está en conflicto con un prefijo de direcciones existente en VPC

Es posible que vea este mensaje si proporciona un CIDR de red que está en conflicto con un CIDR de red existente en el mismo espacio de IP.

## not_authorized                               
**Mensaje**: La solicitud no está autorizada.

Es probable que falte la señal de IAM o que haya caducado. Para ver instrucciones sobre cómo generar una señal, consulte el apartado [Creación de una VPC mediante las API REST](/docs/infrastructure/vpc/example-code.html#creating-a-vpc-using-the-rest-apis). Si la señal no ha caducado, es posible que tenga que comprobar los permisos y ponerse en contacto con el administrador. 

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_found
**Mensaje**: Compruebe si el recurso que está solicitando existe.

Ha hecho referencia a un recurso que no existe o a un recurso al que no tiene acceso. Revise su solicitud para asegurarse de que ha especificado las referencias y los ID adecuados.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_implemented
**Mensaje**: Ninguno

No se ha implementado el método.

## not_in_address_prefix
**Mensaje**: El CIDR proporcionado no encaja en ninguno de los prefijos de direcciones de la zona proporcionada.

Este error se produce si un usuario intenta crear una subred con un CIDR que no se encuentra en ningún prefijo de direcciones para la zona determinada.

Ejecute GET /vpcs/{vpc_id}/address_prefixes para ver la lista de prefijos de direcciones para la VPC. Mire los valores de `cidr` y de `zone` de la respuesta y asegúrese de que el `cidr` de la subred es un subconjunto del `cidr` del prefijo de direcciones correspondiente a la zona en la que lo está intentando crear.

## over_quota                                    
**Mensaje**: La solicitud superará la cuota de un tipo de recurso.

Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## password_not_ready
**Mensaje**: Ninguno

La instancia debe estar en ejecución para poder recuperar la contraseña. Vuelva a intentarlo en unos minutos. Si el problema continúa, póngase en contacto con el equipo de soporte.

## pool_delete_conflict
**Mensaje**: La agrupación no se puede suprimir porque todavía está asociada con uno o más escuchas.

Asegúrese de que la agrupación no está asociada a ningún escucha y vuelva a intentarlo.

## pool_duplicate_name
**Mensaje**: El nombre de agrupación `<pool_name>` ya está siendo utilizado por otra agrupación. Elija otro nombre.

Elija otro nombre de agrupación.

## pool_missing_algorithm
**Mensaje**: Falta el algoritmo de equilibrio de carga.

El algoritmo de equilibrio de carga es un campo obligatorio. Especifique el algoritmo de equilibrio de carga en la solicitud. Los valores válidos son `round_robin`, `weighted_round_robin` y `least_connections`.

## pool_missing_health_monitor
**Mensaje**: Falta el supervisor de estado de la agrupación.

El supervisor de estado de la agrupación es un campo obligatorio.

## pool_missing_name
**Mensaje**: Falta el nombre de la agrupación.

El nombre de la agrupación es un campo obligatorio.

## pool_missing_protocol
**Mensaje**: Falta el protocolo de la agrupación.

El protocolo de la agrupación es un campo obligatorio. Especifique el protocolo de la agrupación en la solicitud. Los valores válidos son `http` y `tcp`.

## pool_not_found
**Mensaje**: La agrupación con el ID `<pool_id>` no se ha podido encontrar.

Especifique un ID de agrupación existente.

## pool_over_quota
**Mensaje**: No se puede crear la agrupación. La cuota de agrupaciones para el recurso del equilibrador de carga ha alcanzado el límite máximo.

Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## public_gateway_in_use
**Mensaje**: No se puede suprimir una pasarela pública cuando se está utilizando.

La pasarela pública está conectada actualmente a una o varias subredes. Debe desconectar la pasarela pública de todas las subredes para poder suprimirla.

## rate_limit_exceeded
**Mensaje**: Demasiadas solicitudes en un breve periodo de tiempo.

Este mensaje de error se devuelve si se reciben demasiadas solicitudes dentro de un intervalo de tiempo especificado. Espere un momento e inténtelo de nuevo. 

## security_group_active_transactions
**Mensaje**: La interfaz no se puede conectar o desconectar hasta que la instancia esté en estado Activo.

La instancia debe estar activa para que sus interfaces de red se puedan conectar a un grupo de seguridad. Utilice `GET /v1/instances/{id}?version=2019-01-01` o `ibmcloud is instance` para comprobar el estado de la instancia. Cuando el estado sea `en ejecución`, inténtelo de nuevo. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_already_attached
**Mensaje**: La interfaz ya está conectada al grupo de seguridad.


La interfaz ya está conectada al grupo de seguridad. Utilice `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` o `ibmcloud is security-group-network-interfaces` para ver las interfaces conectadas.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_exists
**Mensaje**: El grupo de seguridad ya existe.


Los nombres de grupo de seguridad deben ser exclusivos. Ya existe un grupo de seguridad con este nombre. Utilice `GET /v1/security_groups?version=2019-01-01` o `ibmcloud is security-groups` para ver los grupos de seguridad actuales.

Para ver instrucciones sobre cómo solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias) o el [documento sobre cómo utilizar grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_attached
**Mensaje**: No se puede suprimir el grupo de seguridad mientras haya interfaces conectadas.


Desconecte todas las interfaces antes de suprimir el grupo de seguridad. Utilice `DELETE /v1/security_groups/{id}/network_interfaces/{id}?version=2019-01-01` o `ibmcloud is security-group-network-interface-remove` para desconectar una interfaz.

Para ver instrucciones sobre cómo solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias) o el [documento sobre cómo utilizar grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_per_sg_exceeded
**Mensaje**: Se ha superado el límite de interfaces por grupo de seguridad.

Si se conecta otra interfaz al grupo de seguridad, se superará el límite de interfaces por grupo de seguridad. Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas)){: new_window}. Evalúe su estrategia y considere la posibilidad de crear otro grupo de seguridad con reglas similares.

Para ver instrucciones sobre cómo solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias) o el [documento sobre cómo utilizar grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_last_security_group_is_default
**Mensaje**: El grupo de seguridad predeterminado no se puede eliminar si es el único grupo de seguridad conectado.

Una interfaz red debe estar conectada al menos a un grupo de seguridad. 
Se conectará al grupo de seguridad predeterminado de la VPC si no se especifica ninguno. 
Conecte la interfaz a otro grupo de seguridad y luego intente de nuevo desconectarla del grupo de seguridad predeterminado. 
Para obtener información sobre el grupo de seguridad predeterminado, consulte el [documento sobre utilización de grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_limit_exceeded
**Mensaje**: Se ha superado el límite de grupos de seguridad.

Ha intentado crear un nuevo grupo de seguridad, pero actualmente ha alcanzado la cuota de su cuenta. Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Evalúe su estrategia para asignar instancias a grupos de seguridad. Generalmente es posible reducir el número global de grupos de seguridad asignando varias instancias al mismo grupo de seguridad. Esta estrategia reducirá el número de grupos de seguridad y le situará por debajo de la cuota de su cuenta. En casos excepcionales, en general en grandes organizaciones, es necesario ampliar la cuota. En este caso, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) para consultar si esto es posible.

## security_group_network_interface_not_active
**Mensaje**: No se puede conectar la interfaz porque no está activa.

Las interfaces de red deben estar activas para que se puedan conectar a grupos de seguridad. Utilice `GET /v1/instances/{id}/network_interfaces/{id}?version=2019-01-01` o `ibmcloud is instance-network-interface` para ver el estado de una interfaz. Cuando el estado sea 'disponible', inténtelo de nuevo. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_not_attached
**Mensaje**: La interfaz no está conectada.

La interfaz no está conectada al grupo de seguridad. Utilice `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` o `ibmcloud is security-group-network-interfaces` para ver las interfaces conectadas.

Para ver instrucciones sobre cómo solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias) o el [documento sobre cómo utilizar grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group-using-the-cli){: new_window}.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_not_in_vpc
**Mensaje**: La interfaz y el grupo de seguridad están en distintas VPC.

Para conectar una interfaz de red a un grupo de seguridad, la instancia debe estar en la misma VPC que el grupo de seguridad. Utilice `GET /v1/security_groups/{id}?version=2019-01-01` o `ibmcloud is security-group` para ver detalles de los grupos de seguridad y VPC. Utilice `GET /v1/instances/{id}?version=2019-01-01` o `ibmcloud is instance` para ver detalles de la instancia y VPC.

## security_group_order_bindings
**Mensaje**: No se puede suprimir el grupo de seguridad mientras haya pedidos de instancias pendientes.

Si una instancia se ha grado con grupos de seguridad especificados en las interfaces de red, la instancia y las interfaces de red debe estar activas para que se pueda suprimir el grupo de seguridad. Utilice `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` o `ibmcloud is security-group-network-interfaces` para ver las interfaces de red conectadas y su estado. Cuando el estado de las interfaces sea 'disponible', inténtelo de nuevo. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_port_max_less_than_port_min
**Mensaje**: El valor máximo de puertos TCP/UDP no puede ser menor que el valor mínimo de puertos.

El valor máximo de puertos no puede ser menor que el valor mínimo de puertos. Especifique un valor máximo de puertos que sea mayor que el valor mínimo de puerto.

## security_group_port_range_both_or_neither
**Mensaje**: El rango de puertos debe estar sin establecer, o bien deben estar establecidos tanto el valor mínimo como el valor máximo de puertos para 'tcp' y 'udp'.

Las reglas con un protocolo 'tcp' o 'udp' pueden tener un rango de puertos sin establecer (para aplicar la regla a todo el tráfico) o bien deben especificar un rango de puertos. Para restringir el tráfico a un solo puerto, establezca el mismo valor para el mínimo y el máximo de puertos. Por ejemplo, el mandato siguiente crearía una regla para permitir SSH en el puerto 22: `ibmcloud is security-group-rule-add <id> inbound tcp --port-min 22 --port-max 22`.

Para obtener más información sobre configuraciones de reglas de grupos de seguridad, consulte la [documentación de la API](https://{DomainName}/apidocs/rias).


## security_group_port_range_invalid_protocol
**Mensaje**: Se ha especificado un rango de puertos con el protocolo 'icmp'. El rango de puertos solo es válido para los protocolos 'tcp' o 'udp'.

Las reglas con el protocolo 'icmp' tienen un tipo y un código. Las reglas con los protocolos 'tcp' o 'udp' tienen un rango de puertos. Para obtener más información sobre configuraciones de reglas de grupos de seguridad, consulte la [documentación de la API](https://{DomainName}/apidocs/rias).

## security_group_remote_group_not_in_vpc
**Mensaje**: El grupo remoto no está en la misma VPC que este grupo de seguridad.

Las reglas de grupo de seguridad pueden hacer referencia a un grupo de seguridad remoto, lo que permite el tráfico entre las interfaces conectadas de los dos grupos. Los grupos de seguridad remotos deben estar en la misma VPC. Utilice `GET /v1/security_groups?2019-01-01` o `ibmcloud is security-groups` para ver los grupos de seguridad actuales y sus VPC.

Para obtener más instrucciones para solucionar este problema, consulte el [documento sobre utilización de grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules
**Mensaje**: No se puede suprimir el grupo de seguridad mientras haya reglas de referencia remota conectadas.

El grupo de seguridad contiene una o varias reglas que hacen referencia a un grupo de seguridad remoto. Utilice `GET /v1/security_groups/{id}/rules?version=2019-01-01` o `ibmcloud is security-group-rules` para ver las reglas. El campo 'remote' especifica los grupos de seguridad remotos. Vuélvalo a intentar después de suprimir o editar la regla de referencia remota.

Para ver instrucciones sobre cómo solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias) o el [documento sobre cómo utilizar grupos de seguridad](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules_per_sg_exceeded
**Mensaje**: Se ha superado el límite de reglas de referencia remota por grupo de seguridad.


Si se añade otra regla que haga referencia a un grupo de seguridad remoto, se superará el límite de reglas de referencia remota por grupo de seguridad. Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}.


## security_group_rules_per_sg_exceeded
**Mensaje**: Se ha superado el límite de reglas por grupo de seguridad.

Si se añade una regla se superará el límite de reglas por grupo de seguridad. Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Evalúe su estrategia y considere la posibilidad de crear otro grupo de seguridad.


## security_group_sgs_per_interface_exceeded
**Mensaje**: Se ha superado el límite de grupos de seguridad por interfaz.

Si se conecta esta interfaz a otro grupo de seguridad, se superará el límite de grupos de seguridad por interfaz. Las cuotas por recurso se muestran en [Cuotas y límites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Evalúe su estrategia y tenga en cuenta la posibilidad de añadir reglas a un grupo de seguridad existente.


## security_group_type_code_invalid_protocol
**Mensaje**: Se ha especificado un tipo/código 'icmp', pero el protocolo solicitado no era 'icmp'. Establezca el protocolo en 'icmp' o especifique un rango de puertos.

Solo las reglas con el protocolo 'icmp' tienen un tipo y un código. Las reglas con los protocolos 'tcp' o 'udp' tienen un rango de puertos. Para obtener más información sobre configuraciones de reglas de grupos de seguridad, consulte la [documentación de la API](https://{DomainName}/apidocs/rias).

## security_group_vpc_default
**Mensaje**: No se puede suprimir el grupo de seguridad predeterminado para una VPC.

El grupo de seguridad predeterminado no se puede suprimir. Para obtener información sobre el grupo de seguridad predeterminado, consulte la guía sobre [Actualización del grupo de seguridad predeterminado](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group).

## service_manager_service_failure
**Mensaje**: Ninguno

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_acl_conflict
**Mensaje**: No se puede suprimir la ACL de red, está conectada a una subred.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_conflict
**Mensaje**: CIDR está en conflicto con una subred existente en VPC.

Ejecute la API GET /subnets para recuperar todas las subredes de la VPC. Asegúrese de que el CIDR que ha especificado no está siendo utilizado por otras subredes; para ello compruebe el valor de `ipv4_cidr_block`.

Si utiliza la CLI, ejecute `ibmcloud is subnets` y observe el valor de "Subnet CIDR" para resolver los conflictos.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty
**Mensaje**: La subred no está vacía; póngase en contacto con el administrador.

Se ha solicitado suprimir una subred, pero la subred todavía contiene recursos. Las subredes pueden contener instancias, VPN, equilibradores de carga o pasarelas públicas. Debe suprimir los recursos de la subred para poder suprimir la subred. 

En algunas situaciones, este error se puede producir incluso cuando la consola muestra 0 VSI y 0 equilibradores de carga, porque la supresión es asíncrona y el estado interno puede tardar unos minutos en cambiar. Intente de nuevo suprimir la subred en unos minutos.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_pgway_exists
**Mensaje**: No se puede suprimir la subred mientras está conectada a una pasarela pública. Desconecte la pasarela pública y vuelva a intentarlo.

Se ha solicitado suprimir una subred, pero la subred todavía tiene una pasarela pública conectada. Debe suprimir o desconectar la pasarela pública para poder suprimir la subred. 

Si utiliza la CLI, ejecute `ibmcloud is public-gateways` para obtener una lista de las pasarelas públicas e `ibmcloud is subred-public-public-gateway-detach` para desconectar una pasarela pública de una subred. 

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_ipaddr_exists
**Mensaje**: No se puede suprimir la subred mientras contiene direcciones IP. Suprima cualquier instancia de servidor asociada a la dirección IP y vuelva a intentarlo.

Se ha solicitado suprimir una subred, pero la subred todavía contiene direcciones IP. Debe suprimir la instancia de servidor asociada a la dirección IP para poder suprimir la subred.

Si utiliza la CLI, ejecute `ibmcloud is instances` para obtener una lista de las instancias de servidor y examine el valor de "Address" para determinar su dirección IP y el de "Status" para determinar su estado. Ejecute `ibmcloud is instance-delete` para suprimir una instancia de servidor que aún no tenga el estado "deleting". 

En algunas situaciones, este error se puede producir incluso cuando la consola muestra 0 VSI, porque la supresión es asíncrona y el estado interno puede tardar unos minutos en cambiar. Intente de nuevo suprimir la subred en unos minutos.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_loadbalancer_exists
**Mensaje**: No se puede suprimir la subred mientras contiene un equilibrador de carga. Suprima el equilibrador de carga y vuelva a intentarlo.

Se ha solicitado suprimir una subred, pero la subred todavía contiene un equilibrador de carga. Debe suprimir el equilibrador de carga para poder suprimir la subred.

Si utiliza la CLI, puede ejecutar `ibmcloud is load-balancers` para ver una lista de los equilibradores de carga y examinar el valor de "Subredes" para determinar su subred y el valor de "Estado" para determinar su estado. Ejecute `ibmcloud is load-balancer-delete` para suprimir un equilibrador de carga que aún no tenga el estado "suprimiendo". 

En algunas situaciones, este error se puede producir incluso cuando la consola muestra 0 equilibradores de carga, porque la supresión es asíncrona y el estado interno puede tardar unos minutos en cambiar. Intente de nuevo suprimir la subred en unos minutos.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_vpn_gway_exists
**Mensaje**: No se puede suprimir la subred mientras contiene una pasarela VPN. Suprima la pasarela VPN y vuelva a intentarlo.

Se ha solicitado suprimir una subred, pero la subred todavía tiene una pasarela VPN conectada. Debe suprimir la pasarela VPN para poder suprimir la subred. 

Si utiliza la CLI, puede ejecutar `ibmcloud is vpn-gateways` para ver una lista de los equilibradores de carga y examinar el valor de "Subredes" para determinar su subred y el valor de "Estado" para determinar su estado. Ejecute `ibmcloud is vpn-gateway-delete` para suprimir una pasarela VPN que aún no tenga el estado "suprimiendo". 

En algunas situaciones, este error se puede producir incluso cuando la consola muestra 0 pasarelas VPN, porque la supresión es asíncrona y el estado interno puede tardar unos minutos en cambiar. Intente de nuevo suprimir la subred en unos minutos.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_unknown_state
**Mensaje**: Ninguno

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## system_limit_exceeded
**Mensaje**: Esta operación superaría un límite del sistema

Un posible caso en que se recibiría este mensaje de error es si intenta crear un prefijo de dirección, pero ya existe el número máximo de prefijos de dirección.

## target_in_use
**Mensaje**: El destino ya tiene una IP flotante conectada.

## token_invalid
**Mensaje**: La señal de servicio ha caducado o no es válida.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## token_missing
**Mensaje**: La señal de servicio está vacía o no existe en la solicitud.

Vuelva a crear una señal e inténtelo de nuevo.

## validation_enum
**Mensaje**: El valor proporcionado no es una opción válida.

Uno de los campos suministrados tiene un valor que debe proceder de una enumeración de valores posibles.

Para las reglas de ACL de red, puede especificar una dirección:

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum:
[ inbound, outbound ]
```

Por ejemplo, el siguiente valor no sería válido porque `northbound` no es una opción válida en la enumeración `[ inbound, outbound ]`.

```json
{
    "direction":"northbound"
}
```

## validation_failure                            
**Mensaje**: El archivo JSON proporcionado no coincide con la estructura esperada.

Para solucionar este problema, asegúrese de que el contenido de la solicitud es un archivo JSON válido y de que la solicitud se ajusta a la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_invalid_cidr                       
**Mensaje**: El valor no es un CIDR válido.

El valor debe ser un bloque CIDR interno válido con una parte de host 0.

Algunos rangos de direcciones IP están reservados. Encontrará más información acerca de los rangos de IP reservados en nuestra visión general sobre [Utilización de su VPC con regiones y subredes](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv4_cidr        
**Mensaje**: El valor no es un CIDR IPv4 válido.

Debe ser un bloque CIDR interno de IPv4 con una parte de host 0.

Algunos rangos de direcciones IP están reservados. Encontrará más información acerca de los rangos de IP reservados en nuestra visión general sobre [Utilización de su VPC con regiones y subredes](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv6_cidr
**Mensaje**: El valor no es un CIDR IPv6 válido.

Actualmente, IPv6 no recibe soporte. Utilice una dirección IPv4.

## validation_invalid_address
**Mensaje**: El valor no es una dirección válida.

Debe ser una dirección IP válida

Encontrará una lista de direcciones IP reservadas individualmente en el documento sobre [Regiones y subredes](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets).

## validation_invalid_ipv4_address
**Mensaje**: El valor no es una dirección IPv4 válida.

Proporcione una dirección IPv4 válida.

## validation_invalid_ipv6_address
**Mensaje**: El valor no es una dirección IPv6 válida.

Proporcione una dirección IPv6 válida. Actualmente, IPv6 no recibe soporte; utilice una dirección IPv4.

## validation_invalid_field_type
**Mensaje**: El tipo de valor no coincide con el tipo de campo.

Para solucionar este problema, asegúrese de que el contenido de la solicitud cumple con las especificaciones de la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window} para el punto final al que está llamando.

## validation_max_value
**Mensaje**: El valor proporcionado es demasiado grande.

Proporcione un valor menor que cumpla con el máximo mostrado en la especificación. Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_min_value
**Mensaje**: El valor proporcionado es demasiado pequeño.

Proporcione un valor mayor que cumpla con el mínimo mostrado en la especificación. Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_not_null
**Mensaje**: El campo suministrado debe ser nulo.

Asegúrese de que el valor sea nulo. Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

A continuación se muestra un ejemplo no válido:

```json
{
    "name": null
}
```

## validation_only_one
**Mensaje**: El valor proporcionado debe coincidir con uno de los subesquemas.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_discriminator_forbidden
**Mensaje**: El campo de discriminador prohíbe esta subestructura.

Por ejemplo, si especifica
```
{
protocol: icmp
port_min: 5
port_max: 100
}
```

El protocolo es `icmp`, y _port_min_ es un campo `tcp`, de modo que recibirá un error.
1. validation_discriminator_required para reglas `icmp` que faltan
2. validation_discriminator_forbidden para campos `tcp` con `icmp` especificado

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_internal_error
**Mensaje**: Ninguno

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_invalid_name
**Mensaje**: El valor no es un nombre válido.


## validation_invalid_ref
**Mensaje**: El valor no es un HREF válido.


## validation_non_empty_uuid
**Mensaje**: Ninguno

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_required_field
**Mensaje**: Falta un campo obligatorio.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_unique_failed
**Mensaje**: El campo suministrado debe ser exclusivo.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

Es posible que haya especificado un nombre que ya se está utilizando. Inténtelo con otro valor.

## vpc_acl_conflict                           
**Mensaje**: No se puede suprimir la ACL de red predeterminada, está conectada a una VPC.

Para ver instrucciones sobre cómo solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias) o el [documento sobre cómo utilizar ACL de red](/docs/infrastructure/vpc-network?topic=vpc-network-setting-up-network-acls-using-the-cli){: new_window}.

Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_not_empty
**Mensaje**: La VPC no se puede suprimir porque no está vacía.

Se deben eliminar todos los recursos de una VPC para que se pueda suprimir.

Puede recibir este error si todavía tiene una pasarela en la VPC, incluso si se han suprimido todas las subredes, porque la pasarela puede existir en la VPC sin una subred. Es posible que tenga que utilizar la CLI para comprobar si hay recursos huérfanos.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_resource_separation
**Mensaje**: Los recursos se encuentran en diferentes VPC

## vpn_connection_cidr_not_created
**Mensaje**: No se ha podido añadir un bloque CIDR a la conexión de VPN `<vpn_connection_id>`.

Especifique un CIDR válido que cumpla los requisitos que proporciona la especificación. 

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_cidr_not_deleted
**Mensaje**: No se ha podido suprimir un bloque CIDR de la conexión de VPN `<vpn_connection_id>`.

Especifique un CIDR válido que exista en la conexión. Una conexión debe tener al menos un CIDR local e igual.

Para ver los bloques CIDR de la conexión, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` y compruebe los campos `local_cidrs` y `peer_cidrs`.

## vpn_connection_cidr_not_found
**Mensaje**: No se ha encontrado el bloque CIDR en la conexión de VPN `<vpn_connection_id>`.

Especifique un CIDR válido que esté en la conexión.

Para ver los bloques CIDR de la conexión, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` y compruebe los campos `local_cidrs` y `peer_cidrs`.

## vpn_connection_cidr_not_valid
**Mensaje**: El bloque CIDR `<cidr_block>` no representa una dirección válida.

El valor debe ser un bloque CIDR interno válido sin bits de host establecidos.

Para ver los bloques CIDR de la conexión, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` y compruebe los campos `local_cidrs` y `peer_cidrs`.

## vpn_connection_cidr_overlap
**Mensaje**: El bloque CIDR `<cidr_block_1>` se solapa con `<cidr_block_2>`. No se pueden solapar dos bloques CIDR iguales en la misma VPC y dos bloques CIDR locales no se pueden solapar en la misma conexión.

Especifique un valor de CIDR válido que cumpla los requisitos que proporciona la especificación.

Para ver los bloques CIDR de la conexión, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` y compruebe los campos `local_cidrs` y `peer_cidrs`.

## vpn_connection_duplicate_name
**Mensaje**: El nombre `<vpn_connection_name>` ya está siendo utilizado por la conexión de VPN `<vpn_connection_id>`.

Especifique otro nombre de conexión. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_invalid_name
**Mensaje**: El nombre `<vpn_connection_name>` no es un nombre de conexión de VPN válido.

Un nombre de conexión válido comienza por una letra, seguida de letras, dígitos, signos de subrayado o guiones.

## vpn_connection_invalid_psk_format
**Mensaje**: La clave precompartida (PSK) `<psk>` no tiene un formato válido.

Una PSK válida solo puede contener entre 6 y 128 caracteres que sean letras, dígitos, `-`,`+`,`&`,`!`,`@`,`#`,`$`,`%`,`^`,`*`,`(`,`)`,`,`,`.`,`:`,`_`.

## vpn_connection_local_cidrs_required
**Mensaje**: Se necesita al menos un bloque CIDR local para crear una conexión VPN.

Especifique un valor de CIDR local válido que cumpla los requisitos que proporciona la especificación.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## vpn_connection_local_subnets_quota_exceeded
**Mensaje**: Se ha superado la cuota correspondiente a subredes locales entre conexiones VPN para la pasarela de VPN `<vpn_gateway_id>`.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las subredes locales actuales de las conexiones VPN, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections` y compruebe el campo `local_cidrs` de cada conexión.

## vpn_connection_local_subnets_quota_exceeded_for_connection
**Mensaje**: Se ha superado la cuota de '<quota_limit>' subredes locales para la conexión VPN.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vp?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las subredes locales actuales correspondientes a una conexión VPN, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` y compruebe el campo `local_cidrs`.

## vpn_connection_not_found
**Mensaje**: La conexión VPN `<vpn_connection_id>` no se ha podido encontrar.

Compruebe si el ID de conexión es correcto. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_peer_cidrs_required
**Mensaje**: Se necesita al menos un bloque CIDR igual para crear una conexión VPN.

Especifique un valor de CIDR igual válido que cumpla los requisitos que proporciona la especificación.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## vpn_connection_peer_subnets_quota_exceeded
**Mensaje**: Se ha superado la cuota correspondiente a subredes iguales entre conexiones VPN para la pasarela de VPN `<vpn_gateway_id>`.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las subredes iguales actuales de las conexiones VPN, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections` y compruebe el campo `peer_cidrs` de cada conexión.

## vpn_connection_peer_subnets_quota_exceeded_for_connection
**Mensaje**: Se ha superado la cuota de `<quota_limit>` subredes iguales para la conexión VPN.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las subredes iguales actuales correspondientes a una conexión VPN, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` y compruebe el campo `peer_cidrs`.

## vpn_connections_quota_exceeded
**Mensaje**: Se ha superado la cuota correspondiente a conexiones VPN para la pasarela de VPN `<vpn_gateway_id>`.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las conexiones VPN actuales correspondientes a una pasarela VPN, utilice la API `GET /vpn_gateways/<vpn_gateway_id>/connections`.

## vpn_connection_static_route_not_created
**Mensaje**: No se ha podido añadir una ruta estática para el bloque CIDR `<peer_cidr>`.

Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_static_route_not_deleted
**Mensaje**: No se ha podido eliminar una ruta estática para el bloque CIDR `<peer_cidr>`.

Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_update_cidrs_not_permitted
**Mensaje**: Los bloques CIDR no se pueden modificar cuando se actualiza una conexión. Utilice la API correcta cuando cree o suprima CIDR.

Especifique un valor de solicitud válido que cumpla los requisitos que proporciona la especificación.

Para obtener más instrucciones para solucionar este problema, consulte la [documentación de la API](https://{DomainName}/apidocs/rias){: new_window}.

## vpn_gateway_duplicate_name
**Mensaje**: El nombre `<vpn_gateway_name>` ya está siendo utilizado por una pasarela VPN `<vpn_gateway_id>`.

Especifique otro nombre de pasarela VPN. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_initialization_error
**Mensaje**: No se ha podido inicializar la pasarela VPN.

Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_invalid_name
**Mensaje**: El nombre `<vpn_gateway_name>` no es un nombre de pasarela VPN válido.

Un nombre de pasarela VPN válido comienza por una letra, seguida de letras, dígitos, signos de subrayado o guiones.

## vpn_gateway_invalid_state
**Mensaje**: La pasarela VPN `<vpn_gateway_id>` está en un estado no válido para la operación solicitada.

La pasarela VPN debe estar en estado `disponible` para que se pueda trabajar con la misma. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_ip_create_error
**Mensaje**: No se ha podido crear una dirección IP para la pasarela VPN.

Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_not_found
**Mensaje**: La pasarela VPN `<vpn_gateway_id>` no se ha podido encontrar.

Compruebe si el ID de pasarela VPN es correcto. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_not_found
**Mensaje**: No se ha podido encontrar la subred `<subnet_id>` para la pasarela VPN especificada.

Ha hecho referencia a una subred que no existe. Revise su solicitud para asegurarse de que ha especificado el ID de subred adecuado. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_status_error
**Mensaje**: No se ha podido crear la pasarela VPN debido al estado de la subred.

Especifique una subred que esté en estado `disponible`. Vuelva a intentarlo en unos minutos. Si el problema continúa, [póngase en contacto con el equipo de soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateways_quota_exceeded
**Mensaje**: Se ha superado la cuota para las pasarelas VPN para la cuenta y/o la región.

Las cuotas por recurso se muestran en la página [Cuotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para ver las pasarelas de VPN actuales, utilice la API `GET /vpn_gateways`.
