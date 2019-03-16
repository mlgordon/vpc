---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

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

# Creación de una VPC mediante las API REST
{: #creating-a-vpc-using-the-rest-apis}

En esta guía se muestra cómo crear recursos de {{site.data.keyword.cloud}} Virtual Private Cloud mediante las API de IBM Cloud Regional (RIAS).

## Requisitos previos:

1. Instale la [CLI de IBM Cloud](https://cloud.ibm.com/docs/cli/index.html#overview).

## Paso 1: Iniciar una sesión en IBM Cloud para obtener una señal IAM que se utilizará en las llamadas de API.

Si tiene una cuenta federada:
```
ibmcloud login -sso
```
{: pre}

de lo contrario

```
ibmcloud login
```
{: pre}

Este mandato devuelve un URL y solicita un código de acceso. Vaya a ese URL en el navegador e inicie la sesión. Si se ejecuta correctamente, obtendrá un código de acceso de un solo uso. Copie este código de acceso y péguelo como respuesta en la solicitud. Después de los pasos de autenticación, se le solicitará que elija una cuenta. Responda a cualquier solicitud restante para finalizar el inicio de sesión.

## Paso 2: Obtener una señal de IBM Identity and Access Management (IAM)

El mandato siguiente llama a la CLI de IBM Cloud, analiza la señal de IAM y el identificador de señal `Bearer` y lo almacena en una variable que puede utilizar en mandatos posteriores.

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 Para ver la señal de IAM, ejecute el mandato ``echo $iam_token``.

El resultado se parecerá al siguiente:

```
Bearer <su señal>
```
{: screen}

La cabecera de autorización espera que la señal empiece por "Bearer". Si el resultado anterior no incluye "Bearer", actualice la variable `iam_token` para incluirlo. En estos ejemplos se presupone que "Bearer" está incluido en `iam_token`.

Debe repetir el paso anterior para renovar la señal de IAM cada hora, ya que la señal caduca.
{: important}

## Paso 3: Almacenar el punto final de la API como una variable

Almacene el punto final de la API en una variable para que se pueda volver a utilizar posteriormente. Los puntos finales de API son por región y siguen el convenio `https://<region>.iaas.cloud.ibm.com`. Por ejemplo, el punto final de la API `us-south` es `https://us-south.iaas.cloud.ibm.com`.

```
rias_endpoint=https://us-south.iaas.cloud.ibm.com
 ```
{: pre}

Para verificar que esta variable se ha guardado, ejecute `echo $rias_endpoint` y asegúrese de que la respuesta no está vacía.

## Paso 4: Ejecutar la API GET Regions

Si recibe resultados inesperados, añada el distintivo `--verbose` (depuración) después del mandato `curl` para
obtener información de registro detallada. También puede consultar los errores más comunes en nuestra [página de resolución de problemas](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc).
{: tip}

El mandato siguiente devuelve las regiones disponibles para VPC, en formato JSON. Se debe devolver al menos un objeto.

Tenga en cuenta el parámetro de consulta `version` necesario para cada mandato de API.
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Paso 5: Ejecutar la API GET Zones

El mandato siguiente devuelve todas las zonas disponibles para VPC en la región `us-south`, en formato JSON. Se deben devolver al menos tres objetos.

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Paso 6: Ejecutar la API GET Profiles

El mandato siguiente devuelve los perfiles disponibles para sus instancias, en formato JSON. Se debe devolver al menos un objeto.

Añada ` | json_pp ` después del mandato curl para obtener una serie JSON legible
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Si la salida de API está limitada por la paginación, establezca un límite superior a `total_count`, por ejemplo:

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## Paso 7: Ejecutar la API GET Images

El mandato siguiente devuelve las imágenes disponibles para sus instancias, en formato JSON. Se debe devolver al menos un objeto.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Paso 8: Ejecutar la API GET VPCs

El mandato siguiente devuelve las VPC que se han creado bajo su cuenta (si las hay), en formato JSON.

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Paso 9: Crear una nube privada virtual (VPC)

Cree una IBM Cloud VPC llamada `my-vpc`.

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

Para el resto de llamadas, tendrá que conocer el ID de la nueva IBM Cloud VPC que se ha creado. Pegue su ID en la variable, tal como se muestra a continuación:

Algo parecido a esto: `vpc="35fb0489-7105-41b9-99de-033fae723006"`

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## Paso 10: Crear una subred

Cree una subred en IBM Cloud VPC. Por ejemplo, la vamos a colocar en la zona `us-south-2`.

```bash
curl -X POST $rias_endpoint/v1/subnets?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-subnet",
        "ipv4_cidr_block": "10.0.1.0/24",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Al igual que en el caso de la nube privada virtual, guarde el ID de la subred en una variable.

```bash
subnet="<YOUR_SUBNET_ID>"
```
{: pre}

## Paso 11: Comprobar el estado de la subred

Para suministrar recursos en la subred, la subred debe estar en estado `disponible`. Consulte el recurso de subred y asegúrese de que el estado sea `disponible` antes de continuar. Si el estado es `error`, póngase en contacto con el equipo de [soporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) con los detalles. Puede intentar suministrar otra subred.

```bash
curl $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Paso 12: Crear una pasarela pública

Para permitir que las instancias del servidor virtual de la subred tengan acceso a Internet público, añada una pasarela pública (PGW) a la subred.  

```bash
curl -X POST $rias_endpoint/v1/public_gateways?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-gateway",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

AL igual que ha hecho con el nube privada virtual y la subred, guarde el ID de la pasarela pública en una variable.

```bash
gateway="<YOUR_GATEWAY_ID>"
```
{: pre}

## Paso 13: Conectar la pasarela pública a la subred.

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## Paso 14: Crear una clave SSH

Cree una clave con la clave SSH pública. Esta clave se utiliza cuando se crea la instancia de servidor virtual, y es necesaria para iniciar la sesión en la instancia de servidor virtual.

```bash
curl -X POST $rias_endpoint/v1/keys?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-key",
        "public_key": "ssh-rsa AAA....n",
        "type": "rsa"
      }'
```
{: pre}

Guarde el ID de la clave en una variable.

```bash
key="<YOUR_KEY_ID>"
```
{: pre}

## Paso 15: Elegir un perfil y una imagen para la instancia de servidor virtual

Ejecute las API para obtener una lista de todos los perfiles y de todas las imágenes disponibles para la instancia de servidor virtual, y elija una combinación.

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Para obtener detalles adicionales acerca de los perfiles, puede consultar el catálogo global con el mandato de CLI de IBM Cloud
`ibmcloud catalog entry <profile-name> --json`. Por ejemplo:

```
ibmcloud catalog entry b-2x8 --json
```
{: pre}

El mandato siguiente muestra la lista de las imágenes disponibles.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Guarde el nombre del perfil y el ID de la imagen en variables, que se utilizarán posteriormente para suministrar una instancia de servidor virtual.

```bash
profile_name="<CHOSEN_PROFILE_NAME>"
image_id="<CHOSEN_IMAGE_ID>"
```
{: pre}

## Paso 16: Proporcionar una instancia de servidor virtual

Suministre una instancia de servidor virtual en la subred recién creada. Pase la clave SSH pública para que pueda iniciar la sesión después de que se suministre la instancia.

```bash
curl -X POST $rias_endpoint/v1/instances?version=2019-01-01 \
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

Al igual que ha hecho con los otros recursos, guarde el ID de la instancia de servidor virtual en una variable.

```bash
server="<YOUR_INSTANCE_ID>"
```
{: pre}

## Paso 17: Comprobar el estado de la instancia de servidor virtual

El suministro de una instancia de servidor virtual puede tardar entre varios segundos y unos minutos. Antes de continuar, consulte el estado del servidor y asegúrese de que esté `en ejecución`.

```bash
curl $rias_endpoint/v1/instances/$server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Guarde también el ID de la interfaz de red primaria de la instancia de servidor virtual que se ha devuelto en la llamada de API anterior.  

```bash
network_interface="<YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

No puede obtener la interfaz de red primaria hasta que consulte la instancia específica.
{: note}

## Paso 18: Crear una IP flotante

Cree una IP flotante para la instancia de servidor virtual utilizando la interfaz de red primaria de la instancia como destino para la nueva dirección IP flotante.

```bash
curl -X POST $rias_endpoint/v1/floating_ips?version=2019-01-01 \
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


Guarde el ID de la IP flotante.

```bash
floating_ip="<YOUR_FLOATING_IP_ID>"
```
{: pre}

## Paso 19: SSH en la instancia de servidor virtual

Para ejecutar SSH sobre el servidor, utilice la `dirección` de la IP flotante que ha creado. Para obtener la `dirección`
de la IP flotante, ejecute el mandato siguiente:

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Utilice la `dirección` de la IP flotante para conectarse a la instancia de servidor virtual con SSH:

```bash
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

El acceso SSH al servidor virtual puede estar bloqueado por los grupos de seguridad. Si se necesita el acceso SSH, debe utilizar un [grupo de seguridad adecuado](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups).
{: note}

Consulte [Conexión con la instancia mediante Linux](/docs/vsi-is/vsi_is_connecting_linux_gc.html)
para obtener más información sobre cómo conectarse a su instancia.


## Paso 20 (opcional): Suprimir los recursos

Suprima los recursos si lo desea. No se puede suprimir un recurso si contiene otros recursos. Por ejemplo, una nube privada virtual no se puede suprimir si contiene subredes, y una subred no se puede suprimir si contiene instancias del servidor virtual. Durante una supresión, la API puede volver rápidamente, pero es posible que la supresión de recursos siga en curso. Se recomienda consultar el recurso para asegurarse de que se suprima antes de suprimir otros recursos.

### Suprima la IP flotante.

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Suprima la instancia de servidor virtual.

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Suprima la clave.

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### Suprima la pasarela pública.

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Suprima la subred.

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Suprima la VPC.

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Una vNIC no se puede suprimir de una VSI, por lo que no es necesario realizar el paso de supresión de vNIC.
{: note}

## ¡Enhorabuena!

Ha suministrado correctamente una instancia de nube privada virtual mediante las API REST. Para probar más mandatos de API, consulte el siguiente enlace:

* [Consulta de API para VPC](https://{DomainName}/apidocs/rias)
