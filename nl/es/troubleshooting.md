---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Resolución de problemas de IBM Cloud VPC
{: #troubleshooting-your-ibm-cloud-vpc}

En este documento se explican algunas dificultades comunes con las que se puede encontrar y se ofrecen consejos útiles.

## Activación de la modalidad de rastreo (`TRACE`) mediante la CLI

Para activar la modalidad `TRACE` (depuración) mediante CLI, establezca `IBMCLOUD_TRACE=true` antes del mandato de la CLI.

Por ejemplo:

 ```
IBMCLOUD_TRACE=true ibmcloud is pubgws
```

## Utilización de la modalidad DEBUG o `verbose` cuando se utiliza la API

Por ejemplo, puede añadir `--verbose` al mandato `curl` y enviarnos el valor de `X-Request-Id:` para que podamos resolver el problema. El distintivo `--verbose` resulta especialmente útil si tiene problemas de conectividad.

Otra opción es añadir el distintivo `-i` al mandato `curl` para que el equipo de soporte pueda ver las cabeceras de la respuesta de su solicitud. Este distintivo resulta útil en la mayoría de las situaciones cuando necesita ponerse en contacto con el servicio de soporte.

## Las llamadas de API necesitan una señal Bearer

Cuando utilice la API con un mandato cURL, es posible que tenga que incluir "Bearer" en la cabecera de autorización, en función del contenido de `$iam_token`. Si incluye la palabra "Bearer", no la vuelva a incluir en la cabecera. La mayoría de nuestros ejemplos se presupone que "Bearer" está incluido en la cabecera.

## Utilización de otro punto final para la CLI

Para cambiar el punto final que utiliza la CLI de {{site.data.keyword.cloud}} para RIAS de forma predeterminada, establezca la variable `IBMCLOUD_IS_API_ENDPOINT` antes de utilizar la CLI. Por ejemplo:

```
export IBMCLOUD_IS_API_ENDPOINT=api.dev.domain.com
```
{: pre}


## Problemas comunes

Estas son algunas de las dificultades con las que se puede encontrar.

### No autorizado (error 401 o 403)

Es posible que su cuenta no tenga autorización sobre la VPC. Asegúrese de utilizar una cuenta que se haya incorporado.

### No se pueden crear recursos

Si no puede crear una VPC u otros recursos, asegúrese de que el propietario de la cuenta le haya otorgado los [permisos](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) correctos.
### Todas las instancias están en estado Desconocido

Asegúrese de que el propietario de la cuenta le haya otorgado los [permisos](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) adecuados para ver y gestionar instancias.

### No hay respuesta de la API

Si la API deja de devolver JSON, es probable que la señal de IAM haya caducado y se tenga que renovar. Vuelva a iniciar una sesión en IBM Cloud o renueve la señal con el mandato `iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $4; }')`.

### Error: 409 conflicto al invocar una acción sobre una instancia

No se pueden invocar determinadas acciones de la instancia si el estado de la instancia está en conflicto con la acción. Por ejemplo, si el estado de la instancia es `detenido` e intenta ejecutar una acción `reiniciar`, el sistema devuelve un error 409.

| estado          | acción                         | conflicto|
| --------------- | ------------------------------ | -------- |
| En ejecución    | iniciar                        | sí       |
| Detenida        | cualquier acción menos iniciar | sí       |
| No en ejecución | pausar                         | sí       |
| No en ejecución | reiniciar                      | sí       |
| No en pausa     | reanudar                       | sí       |
| En pausa        | cualquier acción menos reanudar| sí       |


### La instancia no responde a la solicitud `instance-reboot`

Si la instancia no responde a una solicitud `instance-reboot`, puede intentar una solicitud `instance-reset`. Se puede considerar que `instance-reboot` es una solicitud suave e `instance-reset` es una completa. La solicitud `instance-reboot` envía una solicitud de reinicio del sistema operativo a la instancia, pero una solicitud `instance-reset` realiza un restablecimiento completo de la instancia de VSI. Se podría comparar con la diferencia entre pulsar "ctrl-alt-supr" en el teclado del sistema frente a pulsar el botón restablecer o el botón de alimentación. Conviene recordar que la solicitud `instance-reset` tarda más en completarse que la solicitud `instance-reboot`.

### No se pueden suprimir recursos

Ciertas operaciones, como por ejemplo la creación y supresión de VSI y la creación y eliminación de subredes, se realizan de forma asíncrona a través de la API. Por este motivo se recomienda sondear los recursos que va a suprimir para comprobar la supresión antes de continuar. 

Se puede tardar varios minutos en suprimir recursos del sistema debido a estas operaciones asíncronas. Para facilitar la supresión, la práctica recomendada es hacer las cosas en este orden:

1. Suprimir las instancias
2. Suprimir las pasarelas públicas
3. Suprimir las subredes
4. Suprimir las VPC
