---
copyright:
  years: 2018-2019
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

# Conexión con IBM Cloud Object Storage desde una VPC
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

En este documento se muestra cómo conectarse a IBM® Cloud Object Storage desde su nube privada virtual (VPC).

## ¿Qué es IBM Cloud Object Storage (COS)?

IBM Cloud Object Storage (COS) es una plataforma de escala web que almacena datos no estructurados. Proporciona fiabilidad, seguridad, disponibilidad y recuperación tras desastre sin réplica manual.
La información almacenada en IBM Cloud Object Storage está cifrada y distribuida entre varias ubicaciones geográficas. Se puede acceder a esta información a través de una implementación de la API S3. Este servicio utiliza las tecnologías de almacenamiento distribuido que proporciona el servicio IBM Cloud Object Storage.

IBM COS está disponible en tres configuraciones: **Varias regiones (Cross-Region)**, **Regional** y **Un solo sitio (Single-Site)**.
 * El servicio **Cross Region** proporciona una mayor durabilidad y disponibilidad que el uso de una sola región, pero a costa de una latencia ligeramente superior.
 * El servicio **Regional** proporciona lo contrario: distribuye los objetos en varias zonas de disponibilidad dentro de una sola región. Si no se puede acceder a una determinada región o zona de disponibilidad, el almacén de objetos continúa funcionando correctamente. Los cambios que falten se aplicarán cuando el centro de datos inaccesible vuelva a estar en línea.
 * El servicio **Single Site** ofrece un acceso a Cloud Object Storage en un centro de datos seleccionado.
 
### Puntos finales directos de COS que se utilizan con VPC

Los puntos finales son URL que las aplicaciones utilizan para emitir mandatos de COS y para intercambiar datos con COS. Cada punto final utiliza la misma interfaz de programación de aplicaciones (API) para interactuar con COS.
Los servidores suministrados en IBM Cloud utilizan puntos finales de API para servicios, incluido COS. Los puntos finales directos proporcionan a los servidores IBM Cloud de los clientes conexiones directas de alta velocidad a servicios sin costes adicionales de ancho de banda.
 
## Cómo conectarse a IBM Cloud Object Storage (COS) desde una VPC
 1. Suministre COS desde el [catálogo ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window}.
 2. Cree un grupo de COS en una de las regiones que se muestran en la siguiente sección.
 3. Utilice Direct Endpoint for VPC para crear una interfaz con el grupo de COS.
 
## Puntos finales de varias regiones de EE.UU.
 
| **Varias regiones de EE.UU.** | **Punto final directo para VPC** |
|------------|-------------------------------|
| Varias regiones de EE.UU. | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| Punto de acceso de Dallas | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| Punto de acceso de San José | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| Punto de acceso de Washington, DC | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## Puntos finales regionales de EE.UU.
 
| **Región** | **Punto final directo para VPC** |
|------------|-------------------------------|
| EE.UU. sur | `s3.direct.us-south.cloud-object-storage.appdomain.cloud`|
| EE.UU. este | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`|

 ## Puntos finales de un solo centro de datos
 
| **Región** | **Punto final directo para VPC** |
|------------|-------------------------------|
| Toronto, Canadá | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| Montreal, Canadá | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
