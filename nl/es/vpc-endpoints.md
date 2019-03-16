---

copyright:
  years: 2017, 2018, 2019

lastupdated: "2019-02-20"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Puntos finales de servicio disponibles para IBM Cloud VPC
{: #service-endpoints-available-for-ibm-cloud-vpc}

Cuando esté listo para ejecutar cargas de trabajo, puede acceder a algunos servicios de infraestructura de IBM Cloud desde una VSI dentro de su {{site.data.keyword.cloud}} VPC utilizando determinados puntos finales de ADN. Hay varios tipos de servicios disponibles a través de puntos finales privados, a los que pueden acceder los clientes de VPC. Mediante estos puntos finales internos, puede evitar los cargos de ancho de banda en que se puede incurrir si accede a los puntos finales desde Internet público.

Los servicios a los que puede acceder incluyen:

* Resoluciones de DNS
* Duplicaciones
* Cloud Object Storage
* NTP

## Punto final de ejemplo para IBM Cloud Object Storage

Por ejemplo, para acceder a un punto final privado correspondiente a un servicio de almacenamiento de objetos en la red privada de IBM Cloud, sustituya la parte de "dominio" del URL por `objectstorage.adn.networklayer.com`.

## Puntos finales para DNS y duplicaciones

El DNS y las duplicaciones utilizan el mismo espacio 161.26/16 en todas partes. Estos puntos finales de IP específicos están disponibles en cada sitio habilitado para VPC:

* `mirrors.adn.networklayer.com` (161.26.0.6)
* Servidores DNS (161.26.0.10 y 161.26.0.11)
