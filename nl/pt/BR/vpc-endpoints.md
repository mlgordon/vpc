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

# Terminais em serviço disponíveis para o IBM Cloud VPC
{: #service-endpoints-available-for-ibm-cloud-vpc}

Quando você estiver pronto para executar cargas de trabalho, será possível atingir alguns serviços de infraestrutura do IBM Cloud de uma VSI dentro de seu {{site.data.keyword.cloud}} VPC usando determinados terminais ADN. Vários tipos de serviços estão disponíveis por meio de terminais privados, que podem ser atingíveis por clientes VPC. Usando esses terminais internos, é possível evitar os encargos de largura da banda que poderiam ser incorridos se você acessasse os terminais por meio da Internet pública.

Os serviços que podem ser incluídos incluem:

* Resolvedores de DNS
* Espelhos
* Cloud Object Storage
* NTP

## Terminal de exemplo para o IBM Cloud Object Storage

Por exemplo, para atingir um terminal privado para um serviço de armazenamento de objeto na rede privada do IBM Cloud, substitua a parte "domínio" da URL por `objectstorage.adn.networklayer.com`.

## Terminais para DNS e espelhos

O DNS e os espelhos usam o mesmo espaço 161.26/16 em todos os lugares. Esses terminais de IP específicos estão disponíveis em cada site ativado para VPC:

* ` mirrors.adn.networklayer.com `  (161.26.0.6)
* Servidores DNS (161.26.0.10 e 161.26.0.11)
