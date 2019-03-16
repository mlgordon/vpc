---
copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# Configuración del acceso a la infraestructura clásica desde VPC
{: #setting-up-access-to-your-classic-infrastructure-from-vpc}

Puede configurar el acceso a la infraestructura clásica de {{site.data.keyword.cloud}}, incluida la conectividad Direct Link, desde una VPC en cada región, para cualquier cuenta. Estas "VPC de acceso clásico" especiales utilizan el mismo direccionador implícito que la infraestructura clásica de {{site.data.keyword.cloud}}.

Cuando haya configurado una VPC para el acceso clásico, cada host de cálculo (VSI o nativo) de su cuenta clásica puede enviar y recibir paquetes a y desde la VPC de acceso clásico. Sin embargo, recuerde que los cortafuegos, las pasarelas, las ACL de red o los grupos de seguridad pueden filtrar este tráfico. Como práctica recomendada, sugerimos que solo permita el tráfico necesario para que las aplicaciones funcionen correctamente.

## Requisitos previos:
1. La cuenta clásica debe estar enlazada a su cuenta de IBM Cloud. Consulte [Enlace de cuentas de IBMid](/docs/account/softlayerlink.html) para ver instrucciones sobre cómo hacerlo.
1. La cuenta clásica debe estar habilitada para VRF.
    * Si ya tiene Direct Link en su cuenta, estará listo.
    * Si su cuenta no está habilitada para VRF, abra una incidencia para solicitar "Migración de VRF" para su cuenta. Consulte [Cómo puede iniciar la conversión](/docs/infrastructure/direct-link?topic=direct-link-how-you-can-initiate-the-conversion) en la documentación de Direct Link para obtener más información sobre el proceso de conversión.

Los cortafuegos, las pasarelas, las ACL de red o los grupos de seguridad pueden filtrar todo el tráfico de red o parte del mismo entre los recursos de la infraestructura clásica y de VPC.
{: important}

## Creación de una VPC de acceso clásico
Puede crear una VPC con la función de acceso clásico utilizando la interfaz de usuario (IU), la interfaz de línea de mandatos (CLI) o la interfaz de programación de aplicaciones (API).

Se debe configurar una VPC para el acceso clásico cuando se cree; no puede actualizar una VPC para añadir o eliminar la función de acceso clásico.
{: note}

### Creación de una VPC de acceso clásico desde la interfaz de usuario

Cree una VPC de acceso clásico desde la página **Crear VPC**, pulsando en el recuadro de selección **Habilitar acceso a recurso clásico**, bajo la etiqueta **Acceso clásico**.

![classic-access-ui](/images/classic-access-ui.png)

### Creación de una VPC de acceso clásico mediante la CLI

Utilice el distintivo `--classic-access` cuando cree la VPC. Por ejemplo:

```
ibmcloud is vpc-create my-access-vpc --classic-access
```
{: pre}


### Creación de una VPC de acceso clásico mediante la API

Pase el parámetro `classic_access` cuando cree la VPC. Por ejemplo:

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "my-access-vpc",
        "classic_access": true
      }'
```
{: pre}


## Limitaciones

* Solo las redes privadas (internas) se conectarán al direccionador implícito privado de la cuenta.
* Únicamente las subredes asignadas con API clásicas se conectan a la parte clásica del direccionador implícito privado. El direccionador implícito no direcciona las subredes en las VLAN clásicas.
* Solo se puede habilitar una VPC por región y por cuenta para el acceso clásico.
