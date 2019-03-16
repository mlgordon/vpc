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
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Acerca de los recursos de la infraestructura de VPC
{: #about-vpc-infrastructure-resources}

El término _recursos_ hace referencia a las partes de componente de un despliegue de nube privada virtual de {{site.data.keyword.cloud}}. Cada VPC puede contener recursos de los tipos siguientes, que se pueden agrupar según sea necesario:

* **vpc**
* **instancia**
* **clave**
* **imagen**
* **subred**
* **volumen**
* **acl**
* **grupo de seguridad**
* **IP flotante**
* **vnic**
* **pasarela**
* **equilibrador de carga**
* **vpn**

Podría considerar que la mayoría de estos tipos de recursos son "hijos" de su VPC, porque adquieren muchas de sus políticas de autorización, que controlan su uso, de la VPC "padre" (tal como se muestra en la tabla de resumen de la sección siguiente).

La excepción son los tipos de recursos `equilibrador de carga` y `vpn`, que mantienen sus propias políticas de autorización. Más adelante en este documento encontrará más información sobre la autorización de recursos correspondiente a los recursos VPN y equilibrador de carga.
{: note}

## Políticas de recursos

Por lo general, el acceso a los recursos de una VPC se controla mediante _políticas_. Si desea personalizar el acceso a los recursos para su VPC, puede crear políticas personalizadas. Una política de recursos aplicarse a:

* todos los recursos
* todos los recursos de un tipo
* todos los recursos de un grupo
* un recurso individual

## Recursos y grupos de recursos
Un _grupo de recursos_ es una colección de recursos, por ejemplo una VPC entera, o una única subred y su ACL, que están asociadas con el fin de definir la autorización y el uso. Podría considerar que un grupo de recursos es una colección de la infraestructura que puede utilizar un proyecto, un departamento o un equipo.

Las grandes empresas tal vez deseen dividir una VPC en grupos de recursos. Es posible que las empresas pequeñas no necesiten dividir su VPC en grupos de recursos, ya que todo su equipo usaría toda la VPC. Si está familiarizado con _OpenStack_, el concepto de grupo de recursos se parece al concepto de _Proyecto_ de _OpenStack Keystone_.

SOLO se puede asignar un recurso a un grupo de recursos al crear la VPC. Los recursos no pueden cambiar de grupo de recursos una vez creados.
{: .note}

Los grupos de recursos se han diseñado principalmente para las organizaciones grandes. Para la mayoría de las empresas y los equipos, la fuga de recursos constituye un problema de la VPC. Esta regla general puede cambiar si se pueden asignar VSI (instancias) individuales a un grupo de recursos y usuarios individuales a un recurso de VSI (instancia).

Al configurar la VPC de IBM Cloud, si desea utilizar grupos de recursos, se recomienda haber planificado cómo se desea asignar los recursos y los usuarios de la organización a cada grupo de recursos.
{: tip}

## Especificaciones para VPC

Actualmente, VPC asigna roles y acceso en el ámbito de la VPC, para cualquiera de los recursos, o para todos ellos, de esa VPC en concreto. Por ejemplo, no puede asignar acceso a subredes individuales dentro de dicha VPC. Las autorizaciones correspondientes a todos los tipos de recursos de la VPC (subredes, instancias, IP flotante, grupos de seguridad, ACL, etc.) se heredan de la VPC "padre" de dicho recurso. Determinados recursos, como **equilibradores de carga** y **vpn**, mantienen autorizaciones por separado de la VPC a la que están conectados.

### Autorización de recursos de VPC por tipo de recurso

En la tabla se resume la forma en que se autorizan los recursos de VPC de forma predeterminada.

| Tipo de recurso | Dónde obtiene su autorización predeterminada |
|-----------|------------|
| VPC | Comprobación de autorización cuando se crea |
| Equilibrador de carga | Comprobación de autorización cuando se crea |
| VPN | Comprobación de autorización cuando se crea |
| Subred | VPC padre |
| Pasarela pública | VPC padre |
| Instancia | VPC padre |
| Grupo de seguridad | VPC padre |
| Clave | Cuenta |
| Imagen | Cuenta |
| IP flotante | Cuenta |
| ACL | Cuenta|
| Volumen | N/D |

Las IP flotantes y las ACL se pueden crear en el ámbito de nivel de cuenta, si no se ha asignado. Sin embargo, en cuanto se asigna una IP flotante a una instancia o se asigna una ACL a una subred, estos recursos pasan a estar sujetos al ámbito de autorización de la VPC.
{: note}

### Cobertura de roles y acciones autorizadas sobre recursos de VPC

En un caso de ejemplo con 2 VPC, aquí encontrará algunos ejemplos de lo que sucede cuando cualquier usuario con determinados roles intenta realizar determinadas acciones:

* Usuario _admin_, con permiso de **Administrador** sobre todos los recursos
  * Crea `vpc1`: correcto

* Usuario _editor_, con permiso de **Editor** sobre todos los recursos
  * Crea `vpc2`: correcto
  * Actualiza `vpc2`: correcto
  * Suprime `vpc2`: correcto

* Usuario _operator_, con permiso de **Operador** sobre todos los recursos
  * Crea `vpc`: denegado
  * Actualiza `vpc1`: denegado
  * Suprime `vpc1`: denegado

* Usuario _viewer_, con permiso de **Visor** sobre todos los recursos
  * Lista VPC: consulta [vpc1]
  * Lee `vpc1`: correcto

* Usuario _noRole_, sin política
  * Lista VPC: consulta []
  * Lee `vpc1`: denegado

### Tabla de resumen de la cobertura de VPC

Para cualquier política que otorga acceso por rol (Administrador, Editor, Operador, Visor), se otorgan las acciones siguientes (X=denegado, o=correcto)

 rol:      | ninguno | Visor | Operador | Editor | Administrador
-----------:|------|--------|-------|--------|-------
Crear      | X    | X      | X     | o      | o
Listar        | X    | o      | X     | o      | o
Leer        | X    | o      | X     | o      | o
Actualizar      | X    | X      | X     | o      | o
Suprimir      | X    | X      | X     | o      | o


## Autorización de recursos de VPN para VPC

La autorización de recursos de **VPN para VPC** se configura por separado de los otros tipos de autorización de recursos de VPC, pero de manera similar.

Las políticas de VPN para VPC controlan el acceso a los recursos de VPN, específicamente a las pasarelas de VPN. El hecho de tener acceso a una pasarela VPN **no** implica que también se tenga acceso a sus recursos hijo, como conexiones de VPN o CIDR locales e iguales. Las políticas de IKE y de IPsec son independientes de la pasarela de VPN y no están reguladas por la política de la pasarela. Una política de recursos en VPN puede aplicarse a:

* todas las pasarelas de VPN
* una pasarela de VPN individual

Una pasarela de VPN también puede formar parte de un grupo de recursos. Si tiene acceso a un grupo de recursos concreto, también tiene acceso a las pasarelas de VPN que están dentro de ese grupo.

El uso de VPN también se factura por separado.
{: note}

### Cobertura de roles y acciones autorizadas sobre recursos de VPN para VPC

Se da soporte a los mismos roles de usuario que en la autorización de recursos de VPC, pero con distintas acciones habilitadas para cada rol.

Estos son algunos ejemplos de lo que sucede cuando usuarios con determinados roles intentan realizar ciertas acciones relacionadas con VPN:

* Usuario _admin_, con permiso de **Administrador** sobre todos los recursos
  * Crea, actualiza, suprime, lee, lista pasarelas de VPN: correcto
  * Crea, actualiza, suprime, lee, lista conexiones VPN: correcto
  * Crea, actualiza, suprime, lee, lista CIDR iguales y locales de conexión de VPN: correcto
  * Crea, actualiza, suprime, lee, lista políticas de IKE: correcto
  * Crea, actualiza, suprime, lee, lista políticas de IPSec: correcto

* Usuario _editor_, con permiso de **Editor** sobre todos los recursos
  * Igual que los del administrador

* Usuario _operator_, con permiso de **Operador** sobre todos los recursos
  * Crea, actualiza, suprime pasarelas de VPN: denegado
  * Crea, actualiza, suprime conexiones VPN: denegado
  * Crea, actualiza, suprime CIDR iguales y locales de conexión de VPN: denegado
  * Crea, actualiza, suprime políticas de IKE: denegado
  * Crea, actualiza, suprime políticas de IPSec: denegado
  * Lee, lista pasarelas de VPN: correcto - ve datos reales
  * Lee, lista conexiones VPN: correcto - ve datos reales
  * Lee, lista CIDR iguales y locales de conexión de VPN: correcto - ve datos reales
  * Lee, lista políticas de IKE: correcto - ve datos reales
  * Lee, lista políticas de IPSec: correcto - ve datos reales

* Usuario _viewer_, con permiso de **Visor** sobre todos los recursos
  * Igual que los del operador

* Usuario _noRole_, sin política
  * Lee, lista pasarelas de VPN: denegado - ve datos vacíos
  * Lee, lista conexiones VPN: denegado - ve datos vacíos
  * Lee, lista CIDR iguales y locales de conexión de VPN: denegado - ve datos vacíos
  * Lee, lista políticas de IKE: denegado - ve datos vacíos
  * Lee, lista políticas de IPSec: denegado - ve datos vacíos

### Tabla de resumen de la cobertura de VPN para VPC

Puede ver la correlación de roles de acción en VPN para VPC en la tabla siguiente (X=denegado, o=correcto):

rol:       | ninguno | Visor | Operador | Editor | Administrador
-----------:|------|--------|-------|--------|-------
Crear      | X    | X      | X     | o      | o
Listar        | X    | o      | o     | o      | o
Leer        | X    | o      | o     | o      | o
Actualizar      | X    | X      | X     | o      | o
Suprimir      | X    | X      | X     | o      | o

## Autorización de recursos de equilibrador de carga para VPC

La autorización de recursos para del **equilibrador de carga para VPC** se configura por separado de las otras autorizaciones de recursos de la VPC, pero de manera similar.

El uso del equilibrador de carga también se factura por separado.
{: note}

### Cobertura de roles y acciones autorizadas sobre recursos del equilibrador de carga

Estos son algunos ejemplos de lo que sucede cuando usuarios con determinados roles intentan realizar ciertas acciones relacionadas con el equilibrador de carga de VPC:

* Usuario _admin_, con permiso de **Administrador** sobre todos los recursos
  * Crea, actualiza, suprime, lee, lista equilibradores de carga: correcto
  * Crea, actualiza, suprime, lee, lista escuchas: correcto
  * Crea, actualiza, suprime, lee, lista agrupaciones: correcto
  * Crea, actualiza, suprime, lee, lista miembros: correcto
  * Crea, actualiza, suprime, lee, lista estadísticas de equilibrador de carga: correcto

* Usuario _editor_, con permiso de **Editor** sobre todos los recursos
  * Igual que los del administrador

* Usuario _operator_, con permiso de **Operador** sobre todos los recursos
  * Crea, actualiza, suprime, lee, lista equilibradores de carga: denegado
  * Crea, actualiza, suprime, lee, lista escuchas: denegado
  * Crea, actualiza, suprime, lee, lista agrupaciones: denegado
  * Crea, actualiza, suprime, lee, lista miembros: denegado
  * Crea, actualiza, suprime, lee, lista estadísticas de equilibrador de carga: denegado

* Usuario _viewer_, con permiso de **Visor** sobre todos los recursos
  * Lee, lista equilibradores de carga: correcto
  * Lee, lista escuchas: correcto
  * Lee, lista agrupaciones: correcto
  * Lee, lista miembros: correcto
  * Lee estadísticas de equilibrador de carga: correcto

* Usuario _noRole_, sin política
  * Lee, lista equilibradores de carga: denegado - la lista muestra datos vacíos
  * Lee, lista escuchas: denegado
  * Lee, lista agrupaciones: denegado
  * Lee, lista miembros: denegado
  * Lee estadísticas de equilibrador de carga: denegado

### Tabla de resumen de la cobertura del equilibrador de carga

Puede ver la correlación de roles de acción del equilibrador de carga para VPC en la tabla siguiente (X=denegado, o=correcto):

rol:       | ninguno | Visor | Operador | Editor | Administrador
-----------:|------|--------|-------|--------|-------
Crear      | X    | X      | X     | o      | o
Listar        | X    | o      | X     | o      | o
Leer        | X    | o      | X     | o      | o
Actualizar      | X    | X      | X     | o      | o
Suprimir      | X    | X      | X     | o      | o
