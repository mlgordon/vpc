---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---
# Cotas
{: #quotas}

Este documento abrange cotas e limites para seu {{site.data.keyword.cloud}} Virtual Private Cloud e os recursos disponíveis dentro dele.

## Cotas VPC

As contas têm as cotas a seguir:

|   Recurso     | Número Máximo |
| ------- | :------: |
| Nuvens Virtuais Privadas | 5 por conta|
| VPCs com Acesso Clássico | 1 por região, por conta |
| Gateways Públicos (PGWs) | 1 por zona |
| Prefixos de endereço | 5 por VPC por zona |

## Cotas de sub-

|   Recurso     | Número Máximo |
| ------- | :------: |
| Subnets | 15 por Nuvem Virtual Virtual |


## Cotas VSI
|   Recurso     | Número Máximo |
| ------- | :------: |
| Instâncias de Servidor Virtual (VSIs) | 100 por conta, por padrão |
| vNICs por VSI | 5 por VSI |
| Endereços IP flutuantes | 1 por VSI |
| Chaves SSH | 100 por conta |


## Cotas de grupos de

Algumas cotas baseadas em conta (limites) existem para grupos de segurança e suas regras associadas.

|Recurso|Cota|
|--------|-----|
|Grupos de segurança|5 por interface de rede|
|Grupos de segurança|500 por conta|
|Regras|50 por grupo de segurança|
|Regras remotas |5 por grupo de segurança|
|Interfaces de Rede|100 por grupo de segurança|

## cotas da ACL

|Recurso|Cota|
|--------|-----|
|ACLs| 30 por conta|
|ACLs |200 por região |
|Regras de Ingresso|20 por ACL |
|Regras de Egresso |20 por ACL |

## cotas VPN

Aqui estão as limitações de recurso VPN atual por conta:

|Recurso|Cota|
|--------|-----|
| Gateways VPN| 7 por conta |
| Gateways VPN | 3 por zona |
| Conexões VPN | 10 por gateway VPN |
| Políticas IKE | 20 por conta |
| Políticas IPSec | 20 por conta |
| Sub-redes de peer em qualquer gateway VPN único | 50 em todas as conexões VPN|
| Sub-redes de Peer  | 15 em qualquer conexão VPN única|
| Sub-redes locais em qualquer gateway VPN único | 50 em todas as conexões VPN|
| Sub-redes locais |  15 em qualquer conexão VPN única |


## Cotas do balanceador de carga

Aqui estão as cotas de recurso do balanceador de carga atual:

|Recurso|Cota|
|--------|-----|
| Balanceador de carga | 50 por conta |
| Listener | 10 por Balanceador de Carga |
| Conjunto | 10 por Balanceador de Carga |
| Membro | 50 por Conjunto |
