---
copyright:
  years: 2018-2019
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

# Conectando-se ao IBM Cloud Object Storage por meio de um VPC
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

Este documento descreve como se conectar ao IBM® Cloud Object Storage por meio de seu Virtual Private Cloud.

## O que é o IBM Cloud Object Storage (COS)?

O IBM Cloud Object Storage (COS) é uma plataforma de escala da web que armazena dados não estruturados. Ele fornece confiabilidade, segurança, disponibilidade e recuperação de desastre sem replicação manual.
As informações armazenadas no IBM Cloud Object Storage são criptografadas e dispersas em várias localizações geográficas. Ele é acessível por meio de uma implementação da API do S3. Esse serviço faz uso das tecnologias de armazenamento distribuído fornecidas pelo serviço IBM Cloud Object Storage.

O IBM COS está disponível em três configurações: **Região cruzada**, **Regional** e **Site único**.
 * O serviço **Região cruzada** fornece durabilidade e disponibilidade mais altas do que usar uma única região, mas ao custo de latência um pouco mais alta.
 * O serviço **Regional** fornece o inverso: ele distribui objetos em múltiplas zonas de disponibilidade dentro de uma única região. Se uma determinada região ou zona de disponibilidade estiver inacessível, o armazenamento de objeto continuará a funcionar normalmente. Qualquer mudança ausente será aplicada quando o data center inacessível voltar a ficar on-line.
 * O serviço **Site único** oferece acesso ao Cloud Object Storage em um data center selecionado.
 
### Terminais diretos do COS para uso com VPC

Terminais são URLs que os aplicativos usam para emitir comandos do COS e trocar dados com o COS. Cada terminal usa a mesma Interface de Programação de Aplicativos (API) para interagir com o COS.
Os servidores provisionados no IBM Cloud usam
terminais de API para serviços, incluindo o COS. Os terminais diretos fornecem aos servidores IBM Cloud dos clientes as conexões diretas de alta velocidade para serviços sem nenhum custo de largura da banda incluído.
 
## Como se conectar ao IBM Cloud Object Storage (COS) por meio de um VPC
 1. Provisione o COS por meio do [catálogo ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/cloud-object-storage){: new_window}.
 2. Crie um depósito COS em uma das Regiões listadas na seção a seguir.
 3. Use o Terminal Direto para VPC para criar uma interface com seu depósito COS.
 
## EUA Terminais de região cruzada
 
| **Região cruzada dos EUA** | **Terminal Direto para VPC** |
|------------|-------------------------------|
| Região cruzada dos EUA | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| Ponto de Acesso de Dallas | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud`
| Ponto de acesso de San Jose | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud`
| Washington, Ponto de Acesso DC | `s3.direct.wdc.us.cloud-object-storage.appdomain.cloud` |

 ## EUA Terminais regionais
 
| **Região** | **Terminal Direto para VPC** |
|------------|-------------------------------|
| Sul dos EUA | ` s3.direct.us-south.cloud-object-storage.appdomain.cloud `|
| Leste dos EUA | ` s3.direct.us-east.cloud-object-storage.appdomain.cloud `|

 ## Terminais de Datacenter Únicos
 
| **Região** | **Terminal Direto para VPC** |
|------------|-------------------------------|
| Toronto, Canadá | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
| Montreal, Canadá | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
