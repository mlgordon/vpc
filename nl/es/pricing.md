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


# Precios de VPC
{: #pricing-for-vpc}

En esta tabla se resumen los precios de la transferencia de datos de Internet con la nube privada virtual de {{site.data.keyword.cloud}}. Recuerde que el tráfico entre los servicios de VPC y Classic IBM Cloud no se factura. Además, para los servicios PayGo, los niveles de servicio están vinculados a su cuenta, no a una instancia específica de VPC. Los importes se muestran en dólares de EE. UU.

Se aplican distintos precios a las [instancias de servidor virtual](/docs/infrastructure/vpc?topic=vpc-pricing-for-virtual-servers-for-vpc) que se utilizan en IBM Cloud VPC.

## Concesiones gratuitas para la transferencia de datos en Internet

| Transferencia de datos |  Coste para todos los clientes de IBM Cloud VPC |
|---------------|------------------|
| Dentro de la zona | Gratuito |
| Entre zonas de la misma región | Gratuito |
| Uso de pasarela pública | Gratuito (solo se factura la IP flotante que utiliza PGW) |

## Precios de IP flotante

La tasa de facturación de una IP flotante es de 1 $ (EE. UU.) al mes, empezando en el momento en que se reserva. La tarifa se cargará incluso si la IP flotante no está asociada a una VSI o si no se utiliza. El dólar de la tarifa mensual se carga incluso si la IP flotante se reserva solo unos días.


## Precios básicos de PayGo para la transferencia de datos en Internet

| Transferencia de datos | Cantidad de datos | Precios de PayGo |
|-----------|-----------|------------------|
| Salida a Internet |  0 a 5 GB | Gratuito |
|  | 6 a 10.000 GB | 0,087 $ por GB |
|  | 10.001 a 50.000 GB | 0,083 $ por GB |
|  | 50.001 a 150.000 GB | 0,07 $ por GB |
|  | 150.001 GB y superiores | 0,05 $ por GB |


Cuando crea una nueva VPC, los cargos de facturación iniciales pueden tardar hasta una hora en aparecer en la interfaz de usuario de la consola o en la API.
{: tip}

Si tiene una pasarela pública o una IP flotante, es posible que siga viendo algunos cargos mínimos de salida, aunque no haya enviado ningún tráfico de salida durante ese tiempo. Estos cargos corresponden al tráfico de ARP, necesario para trabajar con su cuenta.
{: important}


