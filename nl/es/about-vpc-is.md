---
copyright:
  years: 2017, 2019
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

# Acerca de la infraestructura de IBM Cloud Virtual Private Cloud (VPC)
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

{{site.data.keyword.cloud}} VPC forma parte de la próxima generación de la plataforma IBM One Cloud, que redefine los estándares de la industria tradicional en cuanto a rendimiento, crecimiento de servicios, flexibilidad y libertad de despliegue.

Una red privada virtual (VPC) le ofrece el punto de partida rentable que proporciona seguridad en la nube y la posibilidad de escalar de forma dinámica en una nube pública. Ofrece un control detallado sobre la infraestructura virtual y sobre la segmentación del tráfico de la red.

## Espacio privado en una nube pública
IBM Cloud VPC ofrece un entorno aislado y seguro dentro de la nube pública. Le proporciona la seguridad de una nube privada, con la agilidad y la facilidad de una nube pública.

 * Puede gestionar los principales servicios de red e iniciar servidores virtuales según sea necesario para dar soporte a las aplicaciones críticas, tolerantes a la nube y nativas de la nube.
 * Puede definir sus propias políticas de red diseñadas para la seguridad y el acceso cómodo.
 * Puede suministrar sus recursos y conectarlos entre sí, o bien puede aislarlos unos de otros.

### Aislamiento lógico
IBM Cloud Virtual Private Cloud (VPC) proporciona a sus aplicaciones aislamiento lógico de otras redes en todas las regiones, al tiempo que proporciona escalabilidad y seguridad.

Para posibilitar este aislamiento lógico, la VPC se divide en subredes, utilizando un rango de direcciones IP privadas. Sin embargo, de forma predeterminada, todos los recursos (como las VSI) dentro de la misma nube privada virtual pueden comunicarse entre sí, independientemente de su subred. Las subredes están contenidas dentro de una única zona y no pueden abarcar varias zonas, lo que ayuda a aumentar la seguridad, a reducir la latencia, y a proporcionar funciones de recuperación en caso de error.

### Seguridad y suministro rápido de instancias

Cree instancias de servidor virtual (VSI) rápidamente utilizando perfiles predefinidos optimizados para sus cargas de trabajo específicas. Proteja sus instancias con grupos de seguridad.

### Funciones de redes
IBM Cloud VPC ofrece completas funciones de red, que incluyen selección de rangos de direcciones IP, cortafuegos virtuales (grupos de seguridad y ACL de red), redes privadas virtuales (VPN) de sitio a sitio y equilibrio de carga (LBaaS) con elasticidad.

 * Puede configurar la topología virtual automáticamente, utilizando rangos de prefijos sugeridos y políticas de red preconfiguradas.
 * Puede personalizar IBM Cloud VPC y adaptarla a sus requisitos cambiantes sin problemas.
 * Puede traer su propio rango de IP.
 * Puede asignar una IP flotante de una agrupación preexistente.
 * El equilibrio de carga y la VPN tienen planos de control de varias regiones, lo que significa que cada región en la que se despliega el plano de control puede dar soporte a todas las regiones para las instancias de servidor virtual de un cliente. Un error en una sola región no afectará al servicio de ninguna otra región.

### Conectividad global
Puede especificar el ámbito de las aplicaciones y los recursos disponibles de modo que abarquen varias regiones. Mediante VPN, puede crear conexiones privadas con otros proyectos y con otras partes de sus despliegues híbridos de nube.

### Seguridad de red
La seguridad está integrada en su IBM Cloud VPC, con grupos de seguridad que actúan como cortafuegos virtuales para la protección a nivel de instancia y con listas de control de acceso de red (ACL) para la protección a nivel de subred.

### Equilibrio de carga
Dentro de su IBM Cloud VPC, utilice el equilibrio de carga para distribuir el tráfico de red a través de un conjunto de destinos para mejorar el rendimiento y la alta disponibilidad. Los equilibradores de carga también supervisan el estado de las aplicaciones y de los servicios. Puede configurar un equilibrador de carga para distribuir el tráfico de aplicaciones de entrada entre instancias en una sola zona o en varias zonas dentro de una región.

### Acceso a Internet
Hay dos opciones disponibles para habilitar las comunicaciones entre las instancias de servidor virtual (VSI) e Internet público:
* Utilice una pasarela pública (PGW) para habilitar la comunicación para todas las instancias de servidor virtual de la subred conectada. No se cobran cargos por utilizar una PGW, excepto por el ancho de banda utilizado.
* Utilice una IP flotante (FIP) para habilitar la comunicación procedente de una sola instancia de servidor virtual (VSI).

![IBM Cloud VPC](images/vpc-experience.png)
**Figura: Ejemplo de configuración de IBM Cloud VPC**

## Soporte de cargas de trabajo nativas de la nube

Una nube privada virtual es ideal para las cargas de trabajo nativas de la nube y para enlazar la infraestructura existente a IBM Cloud. Puede crear la mejor nube para todas las cargas de trabajo importantes como, por ejemplo, los cálculos cognitivo, AI y Machine Learning. Mientras tanto, puede seguir utilizando IBM Cloud Classic para las cargas de trabajo tradicionales.

Estas son algunas de las formas en que VPC da soporte a las cargas de trabajo híbridas, tolerantes a la nube y nativas de la nube:

 * Crear y gestionar entornos de aplicaciones aisladas a través de una API
 * Diseñar topologías de red con BYOIP (traer su propia IP)
 * Utilizar grupos de seguridad y listas de control de acceso (ACL) a la red para permitir topologías flexibles y basadas en API
 * Las zonas de disponibilidad permiten conexiones de alta velocidad y baja latencia entre regiones, con alta disponibilidad
 * Escalado automático
   * Aumentar o reducir en miles de servidores por día
   * Utilizar un equilibrio de carga escalable y fiable con la gestión de certificados
   * Establecer un sistema de supervisión escalable y fiable
   * Mantenga la ilusión de la capacidad infinita para sus clientes
 * Utilizar redes de alta velocidad y dispositivos de almacenamiento
 * Permitir servicios siempre activos (plano de control)
 * Dar cobertura a varias regiones para la recuperación en caso de error y resiliencia
 * Proporcionar y utilizar los servicios principales: IPAM, VPN, cortafuegos, SSH, DNS y equilibrio de carga L4
 * Configurar otros servicios: escalado automático, CDN, NFV de terceros
 * Permitir el suministro rápido de VSI con afinidad y antiafinidad
 * Utilizar una gestión de imágenes flexible con imágenes prealmacenadas
 * Ofrecer soporte para GPU

## Resumen de ventajas

 * Comienzo rápido mediante configuraciones predefinidas, denominadas perfiles, para sus instancias
 * Ámbito geográfico flexible con zonas y regiones disponibles a nivel global
 * Protección desde el primer momento, con ACL y grupos de seguridad
 * Facilidad para escalar y compartir; una red y los recursos de VPC pueden abarcar desde una instalación local hasta la nube
 * Supervisión de cargas de trabajo para un rendimiento y eficiencia óptimos

## Resumen de características

  * Crear subredes y traer su propio rango de IP
  * Crear y gestionar instancias de servidor virtual (VSI) mediante Ubuntu 16.04, CentOS 7.x, Windows o Debian
  * Reservar y asociar una IPv4 flotante
  * Obtener acceso a través de Internet a las subredes mediante la creación de una pasarela pública (PGW), una por zona
  * Crear y asignar grupos de seguridad a las VSI
  * Utilizar listas de control de acceso (ACL) a la red para proporcionar seguridad para las subredes
  * VSI de alojamiento único, utilizando una tarjeta de interfaz de red virtual (vNIC)
  * Instancias de servidor virtual (VSI) de varios alojamientos y varias vNIC
  * Despliegue en la zona, en la región EE. UU. sur o FRA
  * Acceso a Internet por parte de VPN
  * Equilibro de carga (LB) nativo de VPC

## Advertencias sobre BYOIP

Puede utilizar su propio rango de dirección IPv4 público (BYOIP) en su cuenta de VPC de IBM Cloud. Si utiliza BYOIP, IBM Cloud debe configurar estas direcciones IPv4 en los recursos de IBM Cloud, que enviarán paquetes a las direcciones que ha proporcionado y los recibirán de las mismas. Por lo tanto, como resultado de utilizar el rango IPv4 proporcionado en IBM Cloud, las direcciones IP pueden estar expuestas al personal de soporte de IBM y a terceros como parte de su uso de este servicio.
{: important}

Debe utilizar la API o la CLI para poder utilizar BYOIP. Esta función avanzada no está disponible a través de la interfaz de usuario de la consola de IBM Cloud.
{: note}

Para obtener una lista completa de limitaciones y características conocidas que no están soportadas actualmente, consulte el documento [Limitaciones conocidas](/docs/infrastructure/vpc?topic=vpc-known-limitations).

## Más información

* [**Terminología de IBM VPC**](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**Seguridad de IBM VPC**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**Regiones y subredes de IBM VPC disponibles**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**Creación y gestión de recursos de red en VPC**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [**Creación y gestión de instancias de servidor virtual**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
