---

copyright:
  years: 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Criando um VPC e uma região diferente
{: #creating-a-vpc-in-a-different-region}

Uma região é uma localização geográfica específica na qual é possível implementar apps, serviços e outros recursos do {{site.data.keyword.cloud}}}. As regiões consistem em uma ou mais zonas, que são data centers físicos que hospedam os recursos de cálculo, rede e armazenamento e o resfriamento e energia relacionados que hospedam serviços e aplicativos. As zonas são isoladas umas das outras, o que assegura nenhum ponto único de falha compartilhado.

O Virtual Private Cloud está sendo apresentado para todas as regiões do IBM Cloud em fases.

|   Localização     | Região | Terminal de API | Status |
| ------- | :------: | :------: |:------: |
| Dallas | para sul | ` us-south.iaas.cloud.ibm.com `| Disponíveis |
| Frankfurt | eu-de | `eu-de.iaas.cloud.ibm.com`| Disponíveis |
| Washington DC | nós-Leste | ` us-east.iaas.cloud.ibm.com `| Em breve |
| Tóquio | jp-tok | ` jp-tok.iaas.cloud.ibm.com `| Em breve |
| Londres | eu-gb | ` eu-gb.iaas.cloud.ibm.com `| Em breve |
| Sydney | au-syd | ` au-syd.iaas.cloud.ibm.com `| Em breve |

O terminal da API Regional (VPC) é configurado automaticamente pela CLI do IBM Cloud quando você efetua login em uma região específica.
{: note}

## Efetuar login em uma região específica usando a CLI

Ao efetuar login no IBM Cloud, é possível especificar uma região ou escolhê-la posteriormente. Por exemplo, para efetuar login no terminal de API global na região de Dallas (`us-south`) diretamente, execute os comandos a seguir, dependendo se você tiver uma conta federada (SSO) ou não.

Para uma conta federada,

```
ibmcloud login -a https://cloud.ibm.com -r us-south --sso
```
{: pre}

Para uma conta não federada,

```
ibmcloud login -a https://cloud.ibm.com -r us-south
```
{: pre}

Para escolher a região posteriormente, não especifique o parâmetro `-r<region>` e a CLI solicitará que você escolha uma região.

Saída de exemplo:

```
API endpoint: cloud.ibm.com

Get One Time Code from https://identity-2.eu-central.iam.cloud.ibm.com/identity/passcode to proceed.
Open the URL in the default browser? [Y/n]> y
One Time Code >
Authenticating...
OK

Select an account:
1. MyAccount (00a11aa1a11aa11a1111a1111aaa11aa) <-> 1234567 2. TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321
Enter a number> 2
Targeted account TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321


Targeted resource group Default

Select a region (or press enter to skip):
1. au-syd 2. jp-tok
3. eu-de 4. eu-gb 5. us-south 6. us-east
Enter a number> 5
Targeted region us-south


API endpoint:      https://cloud.ibm.com   
Region:            us-south   
User:              first.last@email.com   
Account:           TeamAccount (2bb222bb2b22222bbb2b2222bb2bb222) <-> 7654321  
Resource group:    Default   
CF API endpoint:      
Org:                  
Space:                

...
```
{: screen}

## Alternar regiões usando a CLI

Para obter o status mais recente das regiões VPC disponíveis, execute o comando a seguir:

```
ibmcloud são regiões
```
{: pre}

Para alternar para uma região diferente, execute o comando `ibmcloud target -r <region>`. Por exemplo, para alternar para a região de Frankfurt, execute o comando a seguir:

```
ibmcloud target -r eu-de
```
{: pre}

Para verificar em qual local você está atualmente, execute o comando a seguir:

```
ibmcloud target
```
{: pre}

## Alternar regiões usando a API  

Para interagir com a API Regional via REST, direcione a solicitação para o terminal de API da região na qual você deseja criar recursos. O terminal de API da região é mostrado acima na tabela. Além disso, é possível localizar o terminal disponível para as diferentes regiões, executando o comando a seguir:

```
ibmcloud são regiões
```
{: pre}


Por exemplo, para obter a lista de VPCs na região `us-south`, execute o comando a seguir:

```
curl https://us-south.iaas.cloud.ibm.com/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Zonas

Para obter a lista de zonas disponíveis para cada região, execute o comando `ibmcloud is zones<region>`. Por exemplo, para obter a lista de zonas na região `us-south`, execute o comando a seguir:

```
ibmcloud is zones us-south
```
{: pre}
