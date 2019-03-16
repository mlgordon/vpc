---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:download: .download}

# Consulta rápida sobre mandatos de la CLI para recursos
{: #quick-reference-to-cli-commands-for-resources}

Esta guía rápida sobre los mandatos de la CLI para recursos resulta útil para trabajar con la CLI de {{site.data.keyword.cloud}} para Virtual Private Cloud.

* **Para iniciar una sesión**

  * `ibmcloud login [-sso]`

* **Para obtener información sobre las VPC**

  * `ibmcloud is vpcs`
  
Utilice el ID del recurso para ver detalles específicos sobre el recurso.
{: tip}

* **Para ver detalles de la VPC** 

  * `ibmcloud is vpc [vpc_id]` 

* **Para obtener información acerca de las subredes** 

  * `ibmcloud is subnets`

* **Para ver detalles sobre una subred**

  * `ibmcloud is subnet [subnet_id]`

* **Para obtener información sobre las instancias**

  * `ibmcloud is instances` 

* **Para ver detalles sobre las instancias** 

  * `ibmcloud is instance [instance_id]`

* **Para obtener información sobre las IP flotantes** 

  * `ibmcloud is floating-ips`  

* **Para ver detalles sobre una IP flotante**

  * `ibmcloud is floating-ip [floating-ips_id]`

* **Para obtener información acerca de sus regiones y puntos finales**

  * `ibmcloud is regions`

* **Para obtener información sobre zonas** 

  * `ibmcloud is zones [region_name]`
