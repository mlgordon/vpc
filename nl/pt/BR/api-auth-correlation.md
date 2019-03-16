---

copyright:
  years: 2018, 2019
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

# Autorizações de recurso necessárias para chamadas da API e CLI
{: #resource-authorizations-required-for-api-and-cli-calls}

A tabela a seguir lista as autorizações necessárias para interagir com os objetos do {{site.data.keyword.cloud}} Virtual Private Cloud Infrastructure. Essas informações são particularmente úteis para saber quando você está fazendo chamadas da API. Aqui está o que você precisa saber para usar esta tabela:

Os termos _anexado_ ou _não anexado_ se referem a se o recurso está associado a um VPC ou VPCs (direta ou indiretamente por meio das sub-redes do recurso). Um IP flutuante ou uma ACL de rede não anexada não tem sub-redes e, portanto, não está associada a nenhum VPC, deste modo, a autorização por VPC não é aplicável.

* As ações **Visualizar** e **Listar** correspondem às funções de **Visualizador** ou **Operador**.
* **Atualizar** e as ações relacionadas correspondem às funções de **Editor** ou **Administrador**.
* Os recursos são protegidos por autorização, os objetos de referência de recurso não são (ID, CRN e assim por diante).


| Recurso | Operation | Autorização necessária |
|--------|--------|---------|
| VPC | Criar | A autorização de Visualização no Grupo de recursos para esse VPC e a autorização de Atualização em Recursos do VPC|
| VPC | Atualizar, Excluir |  Atualizar autorização no VPC |
| VPC |  Visualizar, Listar | Visualizar autorização no VPC  |
| ACL padrão do VPC, SG padrão|  Visualizar, Listar | Visualizar autorização no VPC |
| Prefixos do endereço VPC |  Criar, Atualizar, Excluir | Atualizar autorização no VPC |
| Prefixos do endereço VPC |  Visualizar, Listar | Visualizar autorização no VPC  |
|—————|——————|———————|
| IP Flutuante (desassociado)| Criar, Atualizar, Excluir | Qualquer usuário da Conta e autorização de Visualização em todos os Serviços de Gerenciamento de Conta, se o recurso for criado no grupo de recursos padrão. Clique [aqui](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources#setting-up-viewer-access) para obter instruções sobre como configurar o acesso de visualizador. **Nota: associar e desassociar faz parte da operação de Atualização de IP flutuante**|
| IP Flutuante (desassociado)| Visualizar, Listar | Usuário da conta |
| IP Flutuante (associado) | Atualizar | Autorização de Atualização para a sub-rede associada e seu VPC (não é possível Criar ou Excluir um IP flutuante após ele ser associado) |
| IP Flutuante (associado) | Visualizar, Listar | Autorização de Visualização para a sub-rede do IP flutuante | 
|——————|———————|————————|
| ACL de rede (não anexada), regras de ACL | Criar, Atualizar, Excluir | Qualquer usuário da Conta |
| ACL de rede (não anexada), regras de ACL | Visualizar, Listar | Qualquer usuário da Conta |
| ACL de rede (anexada), regras de ACL | Criar, Atualizar, Excluir | Autorização de Atualização em todas as sub-redes anexadas e no VPC |
| ACL de rede (anexada), regras de ACL | Visualizar, Listar | Autorização de Visualização em pelo menos 1 das sub-redes anexadas e no VPC |
|——————|———————|————————|
| Gateway público | Criar, Atualizar, Excluir |  Atualizar a autorização no VPC da PGW |
| Gateway público | Visualizar, Listar | Visualizar autorização no VPC da PGW |
|—————————|————————|———————————|
| Geografia | Visualizar, Listar |  Para regiões e zonas, qualquer usuário da Conta |
|———————|————————|—————————|
| chave SSH | Criar, Atualizar, Excluir | Qualquer usuário da Conta |
| chave SSH | Visualizar, Listar |  Qualquer usuário da Conta |
|————————|—————————|————————|
| Sub-rede | Criar, Atualizar, Excluir | Atualizar autorização para o VPC da sub-rede |
| Sub-rede | Visualizar, Listar | Visualizar autorização para o VPC da sub-rede |
| ACL de sub-rede ou PGW | Attach, Detach | Atualizar autorização para o VPC da sub-rede |
| ACL de sub-rede ou PGW | Visualizar, Listar | Visualizar autorização para o VPC da sub-rede |
|——————|—————————|————————|
| Grupo de Segurança, Regras SG | Criar, Atualizar, Excluir | Autorização de Atualização para o VPC do grupo de segurança |
| Grupo de Segurança, Regras SG | Visualizar, Listar  | Autorização de Visualização para o VPC do grupo de segurança |
|Interface de rede do grupo de segurança | Criar, Atualizar, Excluir | Autorização de Atualização para o VPC do grupo de segurança (que também é o VPC da NIC) |
|Interface de rede do grupo de segurança | Visualizar, Listar  | Autorização de Visualização para o VPC do grupo de segurança (que também é o VPC da NIC) |
|—————————|—————————|—————————|
| Imagens | Criar, Atualizar, Excluir | Qualquer usuário da Conta |
| Imagens | Visualizar, Listar  | Qualquer usuário da Conta |
| Instâncias | Criar, Atualizar, Excluir | Atualizar a autorização para o VPC da instância |
| Instâncias | Visualizar, Listar  | Visualizar autorização para o VPC da instância |
| Ações da instância, NICs, FIPs | Criar, Atualizar, Excluir | Atualizar a autorização para o VPC da instância |
| Ações de instância, Inicialização, NICs, FIPs | Visualizar, Listar  | Visualizar autorização para o VPC da instância |
|————————|——————|————————|
| Gateway VPN | Criar, Atualizar, Excluir | Atualizar autorização para a VPN |
| Gateway VPN | Visualizar, Listar  | Visualizar autorização para a VPN |
| Conexões de gateway VPN | Criar, Atualizar, Excluir | Atualizar autorização para a VPN |
| Conexões de gateway VPN | Visualizar, Listar  | Visualizar autorização para a VPN |
| VPN gateway ike_policies, ipsec_policies and connections | Criar, Atualizar, Excluir | Atualizar autorização para a VPN |
| VPN gateway ike_policies, ipsec_policies and connections|Visualizar, Listar  | Visualizar autorização para a VPN |
|————————|——————|————————|
| Balanceador de carga | Criar, Atualizar, Excluir | Autorização de Atualização para o Load Balancer|
| Balanceador de carga | Visualizar, Listar  | Visualizar autorização para o Balanceador de Carga |
| Conjuntos e listeners do balanceador de carga | Criar, Atualizar, Excluir | Autorização de Atualização para o Load Balancer|
| Conjuntos e listeners do balanceador de carga | Visualizar, Listar  | Visualizar autorização para o Balanceador de Carga |
|————————|——————|————————|
| Volumes | Criar, Atualizar, Excluir | Atualizar autorização para o Volume
| Volumes | Visualizar, Listar  | Visualizar autorização para o volume |
| Perfis de volume | Visualizar, Listar  | Qualquer usuário da Conta |


