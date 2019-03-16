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
{:DomainName: data-hd-keyref="DomainName"}

# Sobre recursos do VPC Infrastructure
{: #about-vpc-infrastructure-resources}

O termo _recursos_ refere-se às partes do componente de uma implementação do {{site.data.keyword.cloud}} Virtual Private Cloud. Cada VPC pode conter recursos dos tipos a seguir, que podem ser agrupados, conforme necessário:

* ** vpc **
* ** instância **
* ** chave **
* ** imagem **
* ** sub-rede **
* ** volume **
* ** acl **
* ** grupo de segurança **
* **IP flutuante**
* ** vnic **
* ** gateway **
* ** loadbalancer **
* ** vpn **

Você pode considerar a maioria desses tipos de recursos como "filhos" de seu VPC, porque eles adquirem muitas de suas políticas de autorização, que governam seu uso, de seu VPC "pai" (conforme mostrado na tabela de resumo na próxima seção).

Uma exceção é que os tipos de recurso `loadbalancer` e `vpn` mantêm suas próprias políticas de autorização. Mais detalhes sobre a autorização de recurso para os recursos VPN e Load Balancer são fornecidos mais tarde neste documento.
{: note}

## Políticas de recurso

Geralmente, o acesso a recursos em um VPC é controlado por _políticas_. Se você deseja customizar o acesso a recursos para seu VPC, é possível criar políticas customizadas. Uma política de recurso pode ser direcionar:

* todos os recursos
* todos os recursos de um tipo
* todos os recursos em um grupo
* um recurso individual

## Recursos e grupos de recursos
Um _grupo de recursos_ é uma coleção de recursos, por exemplo, um VPC inteiro ou uma única sub-rede e sua ACL, que são associados para o propósito de estabelecer a autorização e o uso. Você pode considerar um grupo de recursos como uma coleção de infraestrutura que pode ser usada por um projeto, um departamento ou uma equipe.

As grandes empresas podem desejar dividir um VPC em grupos de recursos. As empresas menores podem não precisar dividir seu VPC em grupos de recursos, porque toda a equipe deles estaria usando o VPC inteiro. Se você está familiarizado com o _OpenStack_, um grupo de recursos é semelhante em conceito a um _Projeto_ no _OpenStack Keystone_.

A designação de um recurso a um grupo de recursos pode ser feita SOMENTE ao criar seu VPC. Os recursos não podem mudar os grupos de recursos após eles serem criados.
{: .note}

Os grupos de recursos são projetados principalmente para grandes organizações. Para a maioria das empresas e equipes, a quebra de recurso está em um limite de VPC. Essa regra básica geral pode mudar quando é possível designar VSIs (instâncias) individuais a um grupo de recursos e usuários individuais a um recurso VSI (instância).

Quando você estiver configurando seu IBM Cloud VPC, se desejar usar grupos de recursos, será bom ter um plano apropriado antecipadamente de como deseja designar os recursos e os usuários em sua organização a cada grupo de recursos.
{: tip}

## Specifics para VPC

Atualmente, o VPC designa funções e acesso somente ao limite de VPC, para qualquer um ou todos os recursos dentro desse VPC específico. Por exemplo, não é possível designar acesso a sub-redes individuais dentro desse VPC. Em vez disso, as autorizações para todos os tipos de recursos com o VPC -- sub-redes, instâncias, IP flutuante, grupos de segurança, ACLs e assim por diante -- são herdadas do VPC "pai" desse recurso. Determinados recursos, como **balanceadores de carga** e **vpn**, mantêm a autorização separada do VPC ao qual eles estão anexados.

### Autorização de recurso do VPC por tipo de recurso

A tabela resume como os recursos do VPC são autorizados por padrão.

| Tipo de recurso| Onde obtém sua autorização padrão |
|-----------|------------|
| VPC | Verificação de autorização quando criada |
| Balanceador de carga | Verificação de autorização quando criada |
| VPN | Verificação de autorização quando criada |
| Sub-rede | VPC pai |
| Gateway público | VPC pai |
| Ocorrência | VPC pai |
| Grupo de Segurança | VPC pai |
| Key | Conta |
| Imagem | Conta |
| IP Flutuante | Conta |
| ACL | Conta|
| Volume | N/A |

O IP flutuante e as ACLs podem ser criados com a definição de escopo no nível da conta, se não designada. No entanto, assim que um IP flutuante é designado a uma instância ou uma ACL é designada a uma sub-rede, esses recursos se tornam sujeitos ao escopo de autorização do VPC.
{: note}

### Cobertura de VPC de funções e ações autorizadas em recursos

Em um cenário com 2 VPCs, aqui estão alguns exemplos do que acontece quando qualquer usuário com determinadas funções tenta executar determinadas ações:

* Usuário _administrador_, com permissão de **Administrador** em todos os recursos
  * Cria  ` vpc1 `: ok

* Usuário _editor_, com permissão de **Editor** em todos os recursos
  * Cria  ` vpc2 `: ok
  * Atualizações  ` vpc2 `: ok
  * Exclui  ` vpc2 `: ok

* Usuário _operador_, com permissão de **Operador** em todos os recursos
  * Cria  ` vpc `: negado
  * Atualizações  ` vpc1 `: negada
  * Exclui  ` vpc1 `: negado

* Usuário _visualizador_, com permissão de **Visualizador** em todos os recursos
  * Lista VPCs: vê [vpc1]
  * Reads  ` vpc1 `: ok

* O usuário  _ noRole _, sem políticas
  * Lista VPCs: vê [ ]
  * Reads  ` vpc1 `: negado

### Tabela de resumo de cobertura VPC

Para qualquer política que conceda acesso por função (Administrador, Editor, Operador, Visualizador), as ações a seguir são fornecidas (X = negado, o = OK)

 função:      | nenhum | Visualizador | Operador | Editor | Administrator
-----------:|------|--------|-------|--------|-------
Criar      | X    | X      | X     | o      | o
Lista        | X    | o      | X     | o      | o
Ler        | X    | o      | X     | o      | o
Atualizar      | X    | X      | X     | o      | o
Excluir      | X    | X      | X     | o      | o


## Autorização de recurso de VPN para VPC

A autorização de recurso de **VPN para VPC** é configurada separadamente de outros tipos de autorização de recurso do VPC, mas de maneira semelhante.

As políticas em VPN para VPC controlam o acesso a recursos VPN, especificamente Gateways VPN. Ter acesso a um Gateway VPN **não** implica que você também tenha acesso aos seus recursos-filhos, como conexões VPN ou CIDRs local e peer. As políticas IKE e IPsec são independentes do Gateway VPN e não são reguladas pela política do gateway. Uma política de recurso na VPN pode ter como destino:

* todos os Gateways VPN
* um VPN Gateway individual

Um Gateway VPN também pode fazer parte de um grupo de recursos. Se você tiver acesso a um grupo de recursos específico, terá acesso aos Gateways VPN que estão dentro desse grupo também.

O uso de VPN é faturado separadamente também.
{: note}

### VPN para cobertura de VPC de funções e ações autorizadas em recursos

As mesmas funções de usuário são suportadas, como são suportadas na autorização de recurso do VPC, mas com diferentes ações ativadas para cada função.

Aqui estão alguns exemplos do que acontece quando os usuários com determinadas funções tentam executar determinadas ações relacionadas à VPN:

* Usuário _administrador_, com permissão de **Administrador** em todos os recursos
  * Cria, atualiza, exclui, lê, lista Gateways VPN: ok
  * Cria, atualiza, exclui, lê, lista Conexões VPN: ok
  * Cria, atualiza, exclui, lê, lista CIDRs peer e local de conexão VPN: ok
  * Cria, atualiza, exclui, lê, lista Políticas IKE: ok
  * Cria, atualiza, exclui, lê, lista Políticas IPSec: ok

* Usuário _editor_, com permissão de **Editor** em todos os recursos
  * O mesmo que aqueles do Administrador

* Usuário _operador_, com permissão de **Operador** em todos os recursos
  * Cria, atualiza, exclui Gateways VPN: negado
  * Cria, atualiza, exclui Conexões VPN: negada
  * Cria, atualiza, exclui CIDRs peer e local de conexão VPN: ok
  * Cria, atualiza, exclui Políticas IKE: negada
  * Cria, atualiza, exclui Políticas IPSec: negada
  * Lê, lista Gateways VPN: ok - vê dados reais
  * Lê, lista Conexões VPN: ok - vê dados reais
  * Lê, lista CIDRs peer e local de conexão VPN: ok - vê dados reais
  * Lê, lista Políticas IKE: ok - vê dados reais
  * Lê, lista Políticas IPSec: ok - vê dados reais

* Usuário _visualizador_, com permissão de **Visualizador** em todos os recursos
  * O mesmo que os do Operador

* O usuário  _ noRole _, sem políticas
  * Lê, lista Gateways VPN: negado - vê dados vazios
  * Lê, lista Conexões VPN: negado - vê dados vazios
  * Lê, lista CIDRs peer e local de conexão VPN: negado - vê dados vazios
  * Lê, lista Políticas IKE: negado - vê dados vazios
  * Lê, lista Políticas IPSec: negado - vê dados vazios

### VPN para a tabela de resumo de cobertura VPC

O mapeamento de função de ação na VPN para VPC pode ser visualizado pela tabela a seguir (X = negado, o = OK):

função:       | nenhum | Visualizador | Operador | Editor | Administrator
-----------:|------|--------|-------|--------|-------
Criar      | X    | X      | X     | o      | o
Lista        | X    | o      | o     | o      | o
Ler        | X    | o      | o     | o      | o
Atualizar      | X    | X      | X     | o      | o
Excluir      | X    | X      | X     | o      | o

## Autorização de recurso do Load Balancer para VPC

A autorização de recurso para o uso do **Load Balancer para VPC** é configurada separadamente de outra autorização de recurso em seu VPC, mas de maneira semelhante.

O uso de Load Balancer é faturado separadamente também.
{: note}

### Cobertura do Load Balancer de funções e ações autorizadas em recursos

Aqui estão alguns exemplos do que acontece quando os usuários com determinadas funções tentam executar determinadas ações relacionadas ao VPC Load Balancer:

* Usuário _administrador_, com permissão de **Administrador** em todos os recursos
  * Cria, atualiza, exclui, lê, lista Load Balancers: ok
  * Cria, atualiza, exclui, lê, lista Listeners: ok
  * Cria, atualiza, exclui, lê, lista Conjuntos: ok
  * Cria, atualiza, exclui, lê, lista Membros: ok
  * Cria, atualiza, exclui, lê, lista Estatísticas do Load Balancer: ok

* Usuário _editor_, com permissão de **Editor** em todos os recursos
  * O mesmo que aqueles do Administrador

* Usuário _operador_, com permissão de **Operador** em todos os recursos
  * Cria, atualiza, exclui, lê, lista Load Balancers: negado
  * Cria, atualiza, exclui, lê, lista Listeners: negado
  * Cria, atualiza, exclui, lê, lista Conjuntos: negado
  * Cria, atualiza, exclui, lê, lista Membros: negado
  * Cria, atualiza, exclui, lê, lista Estatísticas do Load Balancer: negado

* Usuário _visualizador_, com permissão de **Visualizador** em todos os recursos
  * Lê, lista Load Balancers: ok
  * Lê, lista Listeners: ok
  * Lê, lista Conjuntos: ok
  * Lê, lista Membros: ok
  * Lê Estatísticas do Balanceador de Carga: ok

* O usuário  _ noRole _, sem políticas
  * Lê, lista Load Balancers: negado - a lista mostra dados vazios
  * Lê, lista Listeners: negado
  * Lê, lists Pools: negado
  * Lê, lista Membros: negado
  * Lê Estatísticas do Balanceador de Carga: negado

### Tabela de resumo de cobertura do Load Balancer

O mapeamento de função de ação no Load Balancer para VPC pode ser visualizado pela tabela a seguir (X = negado, o = OK):

função:       | nenhum | Visualizador | Operador | Editor | Administrator
-----------:|------|--------|-------|--------|-------
Criar      | X    | X      | X     | o      | o
Lista        | X    | o      | X     | o      | o
Ler        | X    | o      | X     | o      | o
Atualizar      | X    | X      | X     | o      | o
Excluir      | X    | X      | X     | o      | o
