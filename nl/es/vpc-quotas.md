---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---
# Cuotas
{: #quotas}

En este documento se describen las cuotas y los límites de su {{site.data.keyword.cloud}} Virtual Private Cloud y los recursos disponibles en la misma.

## Cuotas de VPC

Las cuentas tienen las cuotas siguientes:

|   Recurso     | Número máximo |
| ------- | :------: |
| Nubes privadas virtuales | 5 por cuenta|
| VPC con acceso clásico | 1 por región, por cuenta |
| Pasarelas públicas (PGW) | 1 por zona |
| Prefijos de dirección | 5 por VPC por zona |

## Cuotas de subred

|   Recurso     | Número máximo |
| ------- | :------: |
| Subredes | 15 por nube privada virtual |


## Cuotas de VSI
|   Recurso     | Número máximo |
| ------- | :------: |
| Instancias de servidor virtual (VSI) | 100 por cuenta de forma predeterminada |
| vNICs por VSI | 5 por VSI |
| Direcciones IP flotantes | 1 por VSI |
| Claves SSH | 100 por cuenta |


## Cuotas de grupos de seguridad

Existen cuotas basadas en cuenta (límites) para los grupos de seguridad y las reglas asociadas.

|Recurso|Cuota|
|--------|-----|
|Grupos de seguridad|5 por interfaz de red|
|Grupos de seguridad|500 por cuenta|
|Reglas|50 por grupo de seguridad|
|Reglas remotas |5 por grupo de seguridad|
|Interfaces de red|100 por grupo de seguridad|

## Cuotas de ACL

|Recurso|Cuota|
|--------|-----|
|ACL| 30 por cuenta|
|ACL |200 por región |
|Reglas de entrada|20 por ACL |
|Reglas de salida |20 por ACL |

## Cuotas de VPN

Estas son las limitaciones actuales de recursos de VPN por cuenta:

|Recurso|Cuota|
|--------|-----|
| Pasarelas VPN| 7 por cuenta |
| Pasarelas VPN | 3 por zona |
| Conexiones de VPN | 10 por pasarela VPN |
| Políticas de IKE | 20 por cuenta |
| Políticas de IPSec | 20 por cuenta |
| Subredes iguales en una sola pasarela VPN | 50 entre todas las conexiones VPN|
| Subredes iguales  | 15 en una sola conexión VPN|
| Subredes locales en una sola pasarela VPN | 50 entre todas las conexiones VPN|
| Subredes locales |  15 en una sola conexión VPN |


## Cuotas de equilibrador de carga

Estas son las cuotas actuales de recursos del equilibrador de carga:

|Recurso|Cuota|
|--------|-----|
| Equilibrador de carga | 50 por cuenta |
| Escucha | 10 por equilibrador de carga |
| Agrupación | 10 por equilibrador de carga |
| Miembro | 50 por agrupación |
