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
{:faq: data-hd-content-type='faq'}
{:DomainName: data-hd-keyref="DomainName"}


# Preguntas frecuentes
{: #faqs}

## ¿Cuál es el límite en el número de caracteres en un nombre de VPC?
{:faq}

Actualmente, el límite es de 100. Si se supera este límite, es posible que reciba un mensaje de "error interno".

## ¿Puede empezar alguno de los nombres de mis recursos de VPC por un número?
{:faq}

No; aunque el nombre puede contener números, debe comenzar por una letra.

## ¿Existen restricciones en cuanto a los caracteres que puedo utilizar en un nombre?
{:faq}

Sí, la interfaz de usuario no permite que los dobles guiones duplicados, los signos de subrayado y los puntos formen parte del nombre de una VSI.


## Durante la asignación de IP flotante en una VPC, un cliente debe especificar el vNIC de la VSI, ¿es correcto?
{:faq}

Sí; de hecho, debe ser la interfaz de red primaria de un servidor.

Sin embargo, si añadimos un recurso de "dirección" en la API bajo el área de red, podríamos perfectamente cambiar la asociación de la IP flotante con la dirección en lugar de con la interfaz.

## ¿Puede un vNIC de una instancia de servidor virtual de mi VPC tener una IP flotante y una IP privada?
{:faq}
 
Sí.

## En la interfaz de usuario de la consola de IBM Cloud para VPC, solo hay una ”conmutación" para conectar o desconectar cada subred de la pasarela pública. ¿Quién crea la PGW? ¿Estará la PGW predeterminada preparada cuando un cliente desee conectar la subred a la PGW en la interfaz de usuario?
{:faq}

La PGW se debe crear de forma explícita mediante la API tal como está ahora, ya que la API necesita una asociación explícita de una subred con una pasarela pública determinada.

## Supongamos que VSI1 de una VPC solo tiene vNIC1 y que está conectada a Subnet1. Subnet1 está conectada a una pasarela pública (PGW). ¿Puede un cliente asignar una IP flotante a VSI1?
{:faq}

Sí, un servidor puede estar en una subred conectada a una pasarela pública y también tener una IP flotante. La asignación de la IP flotante a una VSI no está relacionada con si hay una pasarela pública conectada a la subred. Una IP flotante asociada a una VSI prevalecerá sobre la pasarela pública conectada a la subred.

## En mi VPC, VSI1 tiene 2 vNICs, llamadas vNIC1 y vNIC2. ¿Se pueden conectar estas dos vNICs a la misma subred?
{:faq}
 
Sí, no hay limitación en el hecho de tener varias interfaces de red en el mismo servidor conectadas a la misma subred. Sin embargo, actualmente no se da soporte a varias NIC en una VSI.

## ¿Se puede crear una VSI sin una subred, solo con la IP flotante?
{:faq}

No.

## ¿Se puede conectar una VSI a más de una VPC?
{:faq}

No.

## ¿Se puede cambiar el tamaño de una subred después de crearla en una VPC?
{:faq}

No.

## Durante la creación de PGW, ¿tengo que reservar el FIP, o lo reserva el sistema automáticamente? ¿Veré dicha IP flotante cuando consulte todas las IP flotantes?

Según la especificación actual, RIAS crea automáticamente una IP flotante junto con la pasarela pública si no se especifica una IP flotante existente. Y, sí, esa IP flotante se mostrará en la lista.

## ¿Quién impone el hecho de que solo puede haber 1 pasarela pública por zona para una VPC?
{: faq}

El servicio de API de la infraestructura regional (RIAS) impone este límite.

## ¿Cómo afecta VRF a mis otras funciones de red y a mis subredes?
{:faq}

Advertencias sobre las VLAN y VRF:

* No se permite la expansión de VLAN entre cuentas en el entorno VRF.
* El servicio VPN IPSec está limitado.

**Nota:** VRF no impide el acceso VPN de PPTP o SSL, pero su comportamiento cambia. Sin VRF, una conexión VPN es suficiente para ver todos los servidores de la cuenta. Con VRF, solo puede acceder a los recursos del mercado asociados a su VPN. Así, si se conecta al VPN DAL, solo puede conectarse a servidores DAL.

## ¿Cuál es la forma correcta de utilizar el submandato `instance-network-interface-floating-ip-add` en VPC? ¿Se crea o se asigna de antemano una dirección IP flotante?
{:faq}

 Primero tiene que asignar una IP flotante y luego debe proporcionar la dirección FIP en el mandato `add` de IP flotante de la interfaz.

 Por ejemplo: `ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE | --nic NIC_ID)`. Especifique la zona.

 ## ¿Por qué tengo que especificar una subred al configurar mi VPN para VPC y qué debo especificar?
 {:faq}

Cuando esté configurando una pasarela VPN, debe especificar una subred, de modo que la pasarela VPN pueda obtener las direcciones IP que necesita para el servicio de la VPN. Al especificar la subred, mantiene el control sobre cómo se maneja el tráfico de VPN y tiene la flexibilidad de especificar una ubicación que esté cerca de los recursos que utilizan la VPN. De este modo, puede reducir la latencia y mejorar el rendimiento. 

## ¿Existen cargos de ancho de banda de salida para el tráfico entre VPC y COS?
{:faq}

No hay cargos de ancho de banda de salida siempre que se utilice el punto final de ADN para establecer una conexión entre VPC y COS, pero es posible que se apliquen cargos de llamada a la API.

## ¿Cómo puedo saber dónde se desplegarán las instancias del equilibrador de carga?
{:faq}

Las subredes elegidas determinan dónde se va a desplegar el equilibrador de carga de VPC. El equilibrador de carga de VPC es un recurso regional. Se recomienda elegir subredes de diferentes zonas bajo una región determinada para aumentar la redundancia.
