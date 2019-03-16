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

# Designando acesso baseado em função a recursos do VPC
{: #assigning-role-based-access-to-vpc-resources}

Os Administradores de conta podem utilizar as _políticas_ de autorização, que controlam o acesso a _recursos_ com base na _função_ de um usuário individual. As políticas também podem ser aplicadas para:

(1) a autorização de um grupo de usuários, chamado de _grupo de acesso_,

(2) nas características designadas de um único _recurso_ ou

(3) em uma coleção de recursos chamada de _grupo de recursos_.

As autorizações para os recursos e as autorizações para os usuários podem ser designadas independentemente uma da outra.

Para obter mais informações sobre a criação de usuários, grupos de acesso de usuário, grupos de recursos e políticas, consulte [Sobre recursos](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources).

## Controle de acesso baseado no IAM

Em geral, a autorização do {{site.data.keyword.cloud}} Virtual Private Cloud e as práticas de gerenciamento de recurso são coordenadas com os serviços do IBM Cloud Identity and Access Management (IAM). Para obter mais informações sobre o IAM, grupos de recursos e grupos de acesso em geral, consulte estes documentos do IBM Cloud:

* [IBM Cloud IAM](https://{DomainName}/docs/iam/quickstart.html#getstarted)
* [Grupos de Recursos](https://{DomainName}/docs/overview/resource-groups.html#whatis)
* [Grupos de Acesso](https://{DomainName}/docs/overview/manageaccess.html#cloudaccess)

Determinados recursos do IBM Cloud IAM Service foram customizados para uso no IBM Cloud VPC. O documento [Sobre recursos](/docs/infrastructure/vpc?topic=vpc-about-vpc-infrastructure-resources) explica mais sobre as políticas de autorização do IAM à medida que elas são aplicadas no VPC.

Para resumir, é possível designar autorizações baseadas em IAM com base em:

* usuários individuais
* grupos de acesso (grupos de usuários)
* tipos específicos de recursos
* grupos de recursos

## Designando permissões de usuário

Para usuários, o acesso é controlado designando funções do IAM definidas pelo sistema:

* Administrator
* Editor
* Operador
* Visualizador

Aqui está uma tabela que mostra a correspondência entre cada função de usuário e o tipo de controle permitido para VPCs:

| Nome da Função | Tipo de acesso permitido |
|-----------|-------------------------|
| Visualizador | Visualizar VPC, Listar VPCs  |
| Editor |Visualizar VPC, Listar VPCs, Criar VPCs, Excluir VPCs, Atualizar VPCs |
| Operador  | Visualizar VPC, Listar VPCs |
| Administrator |Visualizar VPC, Listar VPCs, Criar VPCs, Excluir VPCs, Atualizar VPCs, Designar políticas a outros usuários |


## Próximas etapas

Para obter instruções passo a passo sobre a concessão de permissões baseadas em função para usuários para determinadas tarefas, consulte o tópico [Gerenciando permissões de usuário para recursos do VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
