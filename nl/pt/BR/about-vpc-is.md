---
copyright:
  years: 2017, 2019
lastupdated: "2019-02-20"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# Sobre o IBM Cloud Virtual Private Cloud (VPC) Infrastructure
{: #about-ibm-cloud-virtual-private-cloud-vpc-infrastructure}

A {{site.data.keyword.cloud}} VPC faz parte da próxima geração da plataforma IBM One Cloud, que redefine os padrões de mercado tradicionais para desempenho, crescimento de serviço, flexibilidade e liberdade de implementação.

Um Virtual Private Cloud (VPC) fornece um ponto de entrada com custo reduzido que fornece segurança de nuvem e a capacidade para escalação dinâmica em uma nuvem pública.
Ele oferece controle de baixa granularidade sobre a sua infraestrutura virtual e sua segmentação de tráfego de rede.

## Espaço privado em uma nuvem pública
O IBM Cloud VPC oferece um ambiente isolado, rico em segurança, dentro da nuvem pública. Isso fornece a segurança de uma nuvem particular, com a agilidade e a facilidade de uma nuvem pública.

 * É possível gerenciar os serviços de rede de chaves e ativar Virtual Servers, conforme necessário, para suportar seus aplicativos essenciais, tolerantes à nuvem e nativos de nuvem.
 * É possível definir suas próprias políticas de rede projetadas para segurança e acesso conveniente.
 * É possível provisionar seus recursos e conectá-los uns aos outros ou é possível isolá-los um do outro.

### Isolamento lógico
O IBM Cloud Virtual Private Cloud (VPC) fornece aos seus aplicativos isolamento lógico de outras redes em todas as regiões, enquanto fornece escalabilidade e segurança.

Para tornar esse isolamento lógico possível, o VPC é dividido em sub-redes, usando uma gama de endereços IP privados. No entanto, por padrão, todos os recursos (como VSIs) dentro do mesmo Virtual Private Cloud podem se comunicar uns com os outros, independentemente da sub-rede deles. As sub-redes estão contidas em uma única zona e não podem abranger múltiplas zonas, o que ajuda com a segurança, com a redução da latência e com a recuperação de desastre.

### Provisionamento e segurança de instância rápida

Crie instâncias de servidor virtual (VSIs) rapidamente, usando os perfis predefinidos otimizados para suas cargas de trabalho específicas. Proteja suas instâncias com grupos de segurança.

### Recursos de rede
O IBM Cloud VPC oferece recursos de rede abrangentes, incluindo seleção de intervalo de endereço IP, firewalls virtuais (grupos de segurança e ACLs de rede), redes privadas virtuais (VPN) de site para site e balanceamento de carga (LBaaS) com elasticidade.

 * É possível configurar sua topologia virtual automaticamente, usando intervalos de prefixo sugeridos e políticas de rede pré-configuradas.
 * É possível customizar seu IBM Cloud VPC e adaptá-lo a seus requisitos de mudança, sem interrupção.
 * É possível trazer seu próprio intervalo de IP.
 * É possível designar o IP flutuante por meio de um conjunto pré-existente.
 * O balanceamento de carga e a VPN possuem planos de controle multiregion, o que significa que cada região na qual o plano de controle é implementado pode suportar todas as regiões para as instâncias de servidor virtual de um cliente. Uma falha em uma única região não afetará o serviço em nenhuma outra região.

### Conectividade global
É possível definir o escopo de seus aplicativos e recursos disponíveis para abranger múltiplas regiões. Usando a VPN, é possível criar conexões privadas com outros projetos e com outras partições de suas implementações na nuvem híbrida.

### Segurança de rede
A segurança é integrada a seu IBM Cloud VPC, com grupos de segurança que agem como firewalls virtuais para proteção de nível de instância e com listas de controle de acesso de rede (ACLs) para proteção de nível de sub-rede.

### Balanceamento de carga
Dentro de seu IBM Cloud VPC, use o balanceamento de carga para distribuir seu tráfego de rede em um conjunto de destinos para melhorar o desempenho e o HA. Os Load Balancers também monitoram o funcionamento de seus aplicativos e serviços. É possível configurar um balanceador de carga para distribuir o tráfego de aplicativo recebido entre as instâncias em uma única zona ou em múltiplas zonas dentro de uma região.

### Acesso à Internet
Duas opções estão disponíveis para ativar as comunicações de suas instâncias de servidor virtual (VSIs) para a Internet pública:
* Use um gateway público (PGW) para ativar a comunicação para todas as instâncias de servidor virtual na sub-rede anexada. Não há encargo para usar um PGW, exceto para a largura da banda usada.
* Use um IP Flutuante (FIP) para ativar a comunicação por meio de uma única instância de servidor virtual (VSI).

![IBM Cloud VPC](images/vpc-experience.png)
**Figura: um exemplo de configuração do IBM Cloud VPC**

## Suportando Cargas de Trabalho Nativas de Nuvem

Um Virtual Private Cloud é ideal para cargas de trabalho nativas de nuvem e para vincular sua infraestrutura existente ao IBM Cloud. É possível criar a melhor nuvem para todas as suas cargas de trabalho importantes, como cálculos cognitivos, IA e Aprendizado de Máquina. Enquanto isso, é possível continuar a utilizar o IBM Cloud Classic para cargas de trabalho tradicionais, conforme desejado.

A seguir estão algumas maneiras pelas quais esse VPC suporta suas cargas de trabalho híbridas, tolerantes à nuvem e nativas de nuvem:

 * Criar e gerenciar ambientes de aplicativos isolados por meio de uma API
 * Projetar topologias de rede com BYOIP (Bring Your Own IP)
 * Utilizar Grupos de Segurança e Listas de Controle de Acesso (ACLs) à Rede para permitir topologias flexíveis acionadas por API
 * Zonas de disponibilidade permitem conexões de alta velocidade e baixa latência em regiões, com HA
 * Auto-scaling
   * Escalar para cima ou para baixo por milhares de servidores por dia
   * Usar balanceamento de carga escalável e confiável com gerenciamento de certificado
   * Estabelecer monitoramento escalável e confiável
   * Manter a ilusão de capacidade infinita para seus clientes
 * Utilize dispositivos de rede de alta velocidade e de armazenamento
 * Permitir serviços Always On (plano de controle)
 * Abranger múltiplas regiões para recuperação de desastre e resiliência
 * Fornecer e utilizar serviços principais: IPAM, VPN, firewalls, SSH, DNS e Balanceamento de carga L4
 * Configurar outros serviços: Auto-scaling, CDNs, NFV de terceiros
 * Permitir fornecimento rápido de VSI com afinidade e antiafinidade
 * Usar o gerenciamento de imagem flexível com imagens pré-armazenadas
 * Fornecer suporte para GPUs

## Sumário das prestações

 * Começar a usar rapidamente as configurações predefinidas para suas instâncias, chamadas de perfis
 * Escopo geográfico flexível com zonas e regiões disponíveis globalmente
 * Proteger-se do zero, com ACLs e grupos de segurança
 * Facilmente escalável e compartilhável, uma rede VPC e os recursos podem se estender de seu recurso no local para sua nuvem
 * Monitorar suas cargas de trabalho para desempenho e eficiência ideais

## Resumo dos recursos

  * Criar sub-redes e trazer seu próprio intervalo de IP.
  * Criar e gerenciar Instâncias de Servidor Virtual (VSIs) usando o Ubuntu 16.04, CentOS 7.x, Windows ou Debian
  * Reservar e associar um IPv4 flutuante
  * Obter acesso à Internet para sub-redes criando um gateway público (PGW), um por zona
  * Criar e designar grupos de segurança às suas VSIs
  * Usar listas de controle de acesso (ACLs) de rede para fornecer segurança para suas sub-redes
  * VSIs single-homed, usando uma placa da interface de rede virtual (vNIC)
  * Instâncias de servidor virtual multivNIC multivNIC multihomed (VSIs)
  * Implementação de zona, na região Sul dos EUA ou região FRA
  * Acesso à Internet por VPN
  * Balanceamento de Carga (LB) que é nativo do VPC

## Avisos BYOIP

É possível trazer sua própria variação de endereços IPv4 públicos (BYOIP) para a sua conta do IBM Cloud VPC. Ao usar o BYOIP, o IBM Cloud deve configurar esses endereços IPv4 nos recursos do IBM Cloud, que enviarão pacotes para e dos endereços fornecidos. Portanto, como resultado do uso de seu intervalo IPv4 fornecido no IBM Cloud, esses endereços IP podem ser expostos para a equipe de suporte da IBM e terceiros como parte de seu uso desse serviço.
{: important}

Deve-se usar a API ou a CLI para usar o BYOIP. Esse recurso avançado não está disponível por meio da IU do console do IBM Cloud.
{: note}

Para obter uma lista integral de limitações conhecidas e recursos não suportados atualmente, consulte o documento [Limitações conhecidas](/docs/infrastructure/vpc?topic=vpc-known-limitations).

## Saiba mais

* [ ** Terminologia do IBM VPC ** ](/docs/infrastructure/vpc?topic=vpc-vpc-glossary)
* [**Segurança do IBM VPC**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-security-in-your-ibm-cloud-vpc#security-in-your-ibm-cloud-vpc)
* [**Regiões e sub-redes do IBM VPC disponíveis**](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets)
* [**Criando e gerenciando recursos de rede no VPC**](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-network-resources-in-vpc)
* [ ** Criando e gerenciando instâncias do servidor virtual ** ](/docs/infrastructure/vpc?topic=vpc-creating-and-managing-virtual-server-instances)
