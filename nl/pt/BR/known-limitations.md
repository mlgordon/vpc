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

# Limitações Conhecidas
{: #known-limitations}

Este documento contém descrições simples de erros conhecidos na liberação atual, descrições de recursos e APIs que não são suportados e indicações de quais recursos são agora oferecidos somente como serviços Beta. As limitações conhecidas podem mudar à medida que recursos são incluídos no {{site.data.keyword.cloud}} Virtual Private Cloud, portanto, sinta-se à vontade para verificar novamente este documento de tempos em tempos. 

## Erros conhecidos

* Se você renomear uma sub-rede, poderá levar até 1 hora para ver o novo nome de sua sub-rede na página de detalhes do servidor, devido à sincronização do cache. (#758)

## Resumo dos recursos não suportados

* O acesso do Direct Link ao Virtual Private Cloud é suportado somente por meio de [**Acesso Clássico**](/docs/infrastructure/vpc/classic-access.html).
* Um subconjunto de Terminais de Serviços Privados está disponível para o Virtual Private Cloud, nem todos os terminais estão disponíveis. 
* O salvamento e a restauração de imagens não são suportados.

## APIs não suportadas

Para obter detalhes sobre o que é suportado, veja a [Especificação de API](https://{DomainName}/apidocs/rias).

As APIs a seguir não são suportadas nesta liberação.

| Componente | Funções | Comentários |
|------|------|--------|
| **Cálculo:** |   |   |
| Imagens | Criar / Excluir não suportado | Ubuntu 16.04, CentOS 7.X, Windows 08, Debian|
| Network_Interfaces | Obter (sem criar, excluir, atualizar) | |
| Volume_Interfaces | Não suportado |   |
| Port_Speed | | Somente 100 e 1000 |
| **Armazenamento:** |   |   |
| Volumes | Não suportado |   |
| Instantâneos | Não suportado |  |

## Recursos e casos de uso não suportados ainda

Esta seção fornece uma lista detalhada de recursos e casos de uso não suportados. 

* Um Virtual Private Cloud não pode ser peer de outros Virtual Private Clouds.
* As VSIs do IBM Cloud ou os servidores bare metal não podem ser migrados para um Virtual Private Cloud.
* As rotas customizadas não podem ser incluídas em um Virtual Private Cloud. Todas as sub-redes em um Virtual Private Cloud podem se comunicar umas com as outras por padrão.
* O IBM Cloud VPC não suporta domínios de multicast ou de transmissão.
* O IBM Cloud VPC não fornece criptografia de ponta a ponta. 
* Aqui estão os serviços principais do IBM Cloud que podem ser usados por meio do Virtual Private Cloud. Outros serviços não são acessíveis. 
  * NTP
  * Criação de log
  * Resolvedores de DNS
* Uma sub-rede não pode estar em múltiplas zonas.
* Uma sub-rede não pode ser movida de uma zona para outra.
* As sub-redes não podem ser redimensionadas após serem criadas.
* Os servidores bare metal não podem ser provisionados em um Virtual Private Cloud.
* Os recursos do IBM Cloud Classic não podem estar na mesma sub-rede em um Virtual Private Cloud. A conectividade entre os recursos clássicos e um Virtual Private Cloud em sua conta é possível usando o [**Acesso Clássico**](/docs/infrastructure/vpc/classic-access.html).
* IPv6 não é suportado.
* Não é possível usar seu próprio IP público como um IP Flutuante. O conjunto de IPs Flutuantes é fornecido pela IBM.
* Um IP Flutuante é ligado a uma zona. Por exemplo, um IP Flutuante reservado de um conjunto na Zona 1 não pode ser designado a uma VSI na Zona 2 no mesmo VPC.
* Os endereços IP privados não podem ser movidos entre VSIs.
* As interfaces de rede não podem ser movidas entre VSIs.
* Não é possível designar o endereço IP específico da VSI. É possível especificar somente o intervalo de IP para a sub-rede. Quando você anexa uma VSI a uma sub-rede, o sistema designa um IP privado dessa sub-rede.
* O IBM Cloud VPC é fornecido com suas próprias ferramentas de Rede como Serviço, como LBaaS, ACLs e grupos de segurança. Não é possível usar seus próprios dispositivos de rede (por exemplo, um Gateway Vyatta ou outro balanceador de carga) para controlar qualquer recurso no Virtual Private Cloud. Da mesma forma, não é possível usar seus próprios serviços de balanceador de carga ou de grupos de segurança no IBM Cloud Classic Infrastructure para controlar recursos no IBM Cloud VPC.
* O gateway público não permite que o tráfego seja iniciado da Internet para uma VSI no IBM Cloud VPC. Para esse propósito, um IP Flutuante deve ser usado.
* A ACL é stateless, portanto, o tráfego de retorno deve ser permitido explicitamente nas regras de ACL.

## Componentes ou recursos disponíveis como serviços Beta

* A **VPN para IBM Cloud VPC** está disponível somente como um serviço Beta.
* O **LBaaS para IBM Cloud VPC** está disponível somente como um serviço Beta.
