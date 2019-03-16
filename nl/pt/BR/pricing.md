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


# Precificação para VPC
{: #pricing-for-vpc}

A tabela resume a precificação para transferência de dados da Internet com o {{site.data.keyword.cloud}} Virtual Private Cloud. Lembre-se de que não há encargo para o tráfego entre os serviços do IBM Cloud VPC e Classic. Além disso, para serviços Pré-pagos, as camadas de serviço são ligadas à sua conta, não a uma instância específica do VPC. Os montantes são mostrados nos EUA dólares.

A precificação separada se aplica às [instâncias de servidor virtual](/docs/infrastructure/vpc?topic=vpc-pricing-for-virtual-servers-for-vpc) usadas dentro de seu IBM Cloud VPC.

## Abonos grátis para transferência de dados da Internet

| Transferência de dados |  Custo para todos os Clientes do IBM Cloud VPC |
|---------------|------------------|
| Dentro da zona | Grátis |
| Entre zonas na mesma região | Grátis |
| Uso de gateway público | Grátis (cobrado somente para o IP flutuante usado pelo PGW) |

## Precificação de IP flutuante

Um IP flutuante é cobrado com a taxa de $1 (EUA) por mês, iniciando quando ele é reservado. A taxa será cobrada mesmo se o IP flutuante não estiver associado a uma VSI ou não estiver em uso. O $1 para a taxa mensal será cobrado mesmo que o IP flutuante seja reservado por somente alguns dias.


## Precificação básica de Pré-pago para transferência de dados da Internet

| Transferência de dados | Quantidade de dados | Precificação PayGo |
|-----------|-----------|------------------|
| Egress para a Internet |  0 a 5 GB | Grátis |
|  | 6 a 10.000 GB | $0,087 por GB |
|  | 10.001 a 50.000 GB | $0,083 por GB |
|  | 50.001 a 150.000 GB | $0,07 por GB |
|  | 150.001 GB e mais | $0,05 por GB |


Ao criar um novo VPC, pode levar até uma hora para os encargos de faturamento iniciais aparecerem na API ou IU do Console.
{: tip}

Se você tiver um gateway público ou IP Flutuante, ainda poderá ver alguns encargos mínimos do egresso, mesmo que não tenha enviado nenhum tráfego de egresso durante esse tempo. Esses encargos são para o tráfego ARP, que é necessário para operar sua conta.
{: important}


