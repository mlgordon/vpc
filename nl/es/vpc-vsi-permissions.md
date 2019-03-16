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
{:table: .aria-labeledby="caption"}

# Planificación de los permisos de {{site.data.keyword.vsi_is_short}}
{: #planning-virtual-servers-for-vpc-permissions}

Cuando planifique el suministro de {{site.data.keyword.vsi_is_full}}, de conocer el acceso al servidor virtual disponible en función de su rol de usuario.
{:shortdesc}

Cuando se trabaja con VSI, se asigna a los usuarios un rol basado en la {{site.data.keyword.vpc_short}} en la que se suministra una instancia. Si un usuario tiene acceso de editor o de administrador a la {{site.data.keyword.vpc_short}}, hereda la posibilidad de crear, suprimir, modificar instancias del servidor virtual de {{site.data.keyword.vpc_short}}.

Revise la tabla siguiente para obtener más información sobre los roles de usuario y el nivel específico de acceso que abarca cada rol.

* Como administrador de una cuenta, puede definir roles y llevar a cabo las acciones disponibles en {{site.data.keyword.vsi_is_short}}.
* Como editor de una cuenta, puede modificar el estado y crear y suprimir subrecursos.
* Como visor de una cuenta, puede llevar a cabo acciones que no cambien el estado de los recursos.

Los recursos del servidor virtual *hereden* todos los permisos de usuario de la VPC padre. Los permisos no se pueden establecer en el nivel de instancia.
{:note}

<table>
<CAPTION>Tabla 1. Permisos de usuario</CAPTION>
<THEAD>
<TR>
<th>Permiso de VPC</th>
<th>Descripción</th>
<th>Acciones</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>Administrador</td>
<td>Todas las acciones, incluida la capacidad de gestionar <br>
el control de acceso.</td>
<td>
Control de acceso:
<ul>
<li>Añadir y eliminar usuarios</li>
<li>Asignar roles a cada usuario</li>
</ul>
<p>
Servidores virtuales:
<ul>
<li>Crear servidores virtuales</li>
<li>Detener servidores virtuales</li>
<li>Suprimir servidores virtuales</li>
<li>Reiniciar servidores virtuales</li>
<li>Duplicar servidores virtuales</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>Ver y listar servidores virtuales</li>
<li>Cambiar el nombre de servidores virtuales</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Crear y editar claves SSH</li>
<li>Suprimir claves SSH</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<!-- <li>View monitoring and log data</li> -->
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>
</p>
</td>
</tr>
<tr>
<td>Editor</td>
<td>Acciones que pueden modificar el estado, así como <br>
crear y suprimir subrecursos.</td>
<td>
Servidores virtuales:
<ul>
<li>Crear servidores virtuales</li>
<li>Detener servidores virtuales</li>
<li>Suprimir servidores virtuales</li>
<li>Reiniciar servidores virtuales</li>
<li>Duplicar servidores virtuales</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>Ver y listar servidores virtuales</li>
<li>Cambiar el nombre de servidores virtuales</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Crear claves SSH</li>
<li>Suprimir claves SSH</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>Ver datos de supervisión y de registro</li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td>Visor</td>
<td>Acciones que no modifiquen el estado</td>
<td>
Servidores virtuales:
<ul>
<li>Ver y listar servidores virtuales</li>
<!-- <li>View and list image snapshots</li> -->
<li>Ver datos de supervisión y de registro</li>
</ul>
</td>
</tr>
</TBODY>
</table>

## Pasos siguientes
Para obtener más información sobre cómo cambiar los permisos de un usuario, consulte [Gestión de permisos de usuario para recursos de VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
