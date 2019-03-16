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

# Limitaciones conocidas
{: #known-limitations}

Este documento contiene breves descripciones de problemas conocidos del release actual, descripciones de las características y API a las que no se da soporte e indicaciones de las características que actualmente se ofrecen únicamente como servicios Beta. Las limitaciones conocidas pueden ir cambiando a medida que añadimos funciones a la nube privada virtual de {{site.data.keyword.cloud}}, así que le recomendamos que consulte este documento de vez en cuando. 

## Problemas conocidos

* Si cambia el nombre de una subred, podría tardar hasta 1 hora en ver el nuevo nombre de la subred en la página de detalles del servidor, debido a la temporización de la memoria caché. (#758)

## Resumen de características a las que no se da soporte

* El acceso mediante Direct Link a la nube privada virtual solo recibe a través del [**acceso clásico**](/docs/infrastructure/vpc/classic-access.html).
* Dispone de un subconjunto de puntos finales de servicios privados disponibles para la nube privada virtual; no todos los puntos finales están disponibles. 
* No se permite guardar y restaurar imágenes.

## API que no reciben soporte

Para obtener detalles sobre lo que recibe soporte, consulte la [Especificación de API](https://{DomainName}/apidocs/rias).

Las siguientes API no reciben soporte en este release.

| Componente | Funciones | Comentarios |
|------|------|--------|
| **Cálculo:** |   |   |
| Imágenes | No se puede crear/suprimir | Ubuntu 16.04, CentOS 7.X, Windows 08, Debian|
| Interfaces de red | Obtener (no crear, suprimir ni actualizar) | |
| Interfaces de volumen | No reciben soporte |   |
| Port_Speed | | Solo 100 y 1000 |
| **Almacenamiento:** |   |   |
| Volúmenes | No reciben soporte |   |
| Instantáneas | No reciben soporte |  |

## Características y casos de uso a los que aún no se da soporte

En esta sección se proporciona una lista detallada de las características y casos de uso que no reciben soporte. 

* Una nube privada virtual no se puede definir como igual (peered) de otras nubes privadas virtuales.
* Las VSI de IBM Cloud o los servidores nativos no se pueden migrar a una nube privada virtual.
* No se pueden añadir rutas personalizadas a una red privada virtual. De forma predeterminada, todas las subredes de una nube privada virtual pueden comunicarse entre sí.
* IBM Cloud VPC no da soporte a dominios de multidifusión ni de difusión.
* IBM Cloud VPC no ofrece cifrado de extremo a extremo. 
* Estos son los servicios principales de IBM Cloud que se pueden utilizar desde la nube privada virtual. No se puede acceder a otros servicios. 
  * NTP
  * Registro
  * Resoluciones de DNS
* Una subred no puede estar en varias zonas.
* Una subred no se puede trasladar de una zona a otra.
* No se puede cambiar el tamaño de las subredes después de que se creen.
* No se pueden suministrar servidores nativos en una nube privada virtual.
* Los recursos de IBM Cloud Classic no pueden estar en la misma subred de una nube privada virtual. La conectividad entre los recursos clásicos y una nube privada virtual en la cuenta se puede establecer mediante el [**Acceso clásico**](/docs/infrastructure/vpc/classic-access.html).
* No se da soporte a IPv6.
* No puede utilizar su propia IP pública como IP flotante. IBM proporciona la agrupación de IP flotante.
* Una IP flotante está enlazada a una zona. Por ejemplo, una IP flotante reservada de una agrupación de la Zona 1 no se puede asignar a una VSI de la Zona 2 en la misma VPC.
* No se pueden mover direcciones IP privadas entre VSI.
* No se pueden mover interfaces de red entre VSI.
* No se puede designar la dirección IP específica de la VSI. Solo puede especificar el rango de IP para la subred. Cuando conecte una VSI a una subred, el sistema asigna una IP privada desde dicha subred.
* IBM Cloud VPC se suministra con sus propias herramientas de red como servicio, como por ejemplo LBaaS, ACL y grupos de seguridad. No puede utilizar sus propios dispositivos de red (por ejemplo, una pasarela Vyatta u otro equilibrador de carga) para controlar ningún recurso de la nube privada virtual. Paralelamente, no puede utilizar su propio equilibrador de carga ni sus servicios de grupos de seguridad en la infraestructura clásica de IBM Cloud para controlar los recursos de IBM Cloud VPC.
* La pasarela pública no permite que el tráfico se inicie desde Internet a una VSI en la misma IBM Cloud VPC. Para tal fin se debe utilizar una IP flotante.
* ACL no tiene estado, de modo que el tráfico de retorno se debe permitir de forma explícita en las reglas de ACL.

## Componentes o características disponibles como servicios Beta

* **VPN para IBM Cloud VPC** solo está disponible como servicio Beta.
* **LBaaS para IBM Cloud VPC** solo está disponible como servicio Beta.
