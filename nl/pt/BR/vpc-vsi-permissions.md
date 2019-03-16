---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:table: .aria-labeledby="caption"}

# Planejando  {{site.data.keyword.vsi_is_short}}  Permissões
{: #planning-virtual-servers-for-vpc-permissions}

Quando você está planejando provisionar o {{site.data.keyword.vsi_is_full}}, deve-se entender o acesso ao servidor virtual disponível com base em sua função de usuário.
{:shortdesc}

Ao trabalhar com VSIs, os usuários são designados a uma função com base no {{site.data.keyword.vpc_short}} para o qual uma instância é provisionada. Se um usuário tiver acesso de editor ou administrador ao {{site.data.keyword.vpc_short}}, ele herdará a capacidade de criar, excluir, modificar instâncias de servidor virtual dentro desse {{site.data.keyword.vpc_short}}.

Revise a tabela a seguir para saber mais sobre funções de usuário e o nível específico de acesso que cada função abrange.

* Como um administrador de uma conta, é possível definir funções e tomar quaisquer ações disponíveis no {{site.data.keyword.vsi_is_short}}.
* Como um editor de uma conta, é possível modificar o estado e criar/excluir sub-recursos.
* Como um visualizador de uma conta, é possível tomar ações que não mudam o estado dos recursos.

Os recursos do servidor virtual *herdam* todas as permissões de usuário de seu VPC pai. As permissões não podem ser configuradas no nível de instância.
{:note}

<table>
<CAPTION>Tabela 1. Permissões do usuário</CAPTION>
<THEAD>
<TR>
<th>Permissão VPC</th>
<th>Descrição</th>
<th>Ações</th>
</TR>
</THEAD>
<TBODY>
<tr>
<td>Administração</td>
<td>Todas as ações, incluindo a capacidade de gerenciamento<br>
controle de acesso.</td>
<td>
Controle de acesso:
<ul>
<li>Incluir e remover usuários</li>
<li>Designar funções para cada usuário</li>
</ul>
<p>
Servidores Virtuais:
<ul>
<li>Criar servidores virtuais</li>
<li>Parar servidores virtuais</li>
<li>Excluir servidores virtuais</li>
<li>Reiniciar servidores virtuais</li>
<li>Duplicar servidores virtuais</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and delete volumes</li> -->
<li>Visualizar e listar servidores virtuais</li>
<li>Renomear servidores virtuais</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Criar e editar chaves SSH</li>
<li>Excluir chaves SSH</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<!-- <li>View monitoring and log data</li> -->
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>
</p>
</td>
</tr>
<tr>
<td>Editor</td>
<td>Ações que também podem modificar o estado <br>
como, criar e excluir sub-recursos.</td>
<td>
Servidores Virtuais:
<ul>
<li>Criar servidores virtuais</li>
<li>Parar servidores virtuais</li>
<li>Excluir servidores virtuais</li>
<li>Reiniciar servidores virtuais</li>
<li>Duplicar servidores virtuais</li>
<!-- <li>Resize virtual servers</li> -->
<!-- <li>Add and delete vNICs</li> -->
<!-- <li>Attach and detach volumes</li> -->
<li>Visualizar e listar servidores virtuais</li>
<li>Renomear servidores virtuais</li>
<!-- <li>Create image snapshots</li> -->
<!-- <li>Delete image snapshots</li> -->
<!-- <li>Create virtual servers off of image snapshots</li> -->
<li>Criar chaves SSH</li>
<li>Excluir chaves SSH</li>
<!-- <li>Add autoscaling policies</li> -->
<!-- <li>Delete autoscaling policies</li> -->
<!-- <li>Modify autoscaling policies</li> -->
<li>Visualizar dados de monitoramento e de log</li>
<!-- <li>Modify alarms and notifications from monitoring</li> -->
</ul>     
</td>
</tr>
<tr>
<td>Visualizador</td>
<td>Ações que não mudam o estado</td>
<td>
Servidores Virtuais:
<ul>
<li>Visualizar e listar servidores virtuais</li>
<!-- <li>View and list image snapshots</li> -->
<li>Visualizar dados de monitoramento e de log</li>
</ul>
</td>
</tr>
</TBODY>
</table>

## Próximas etapas
Para obter mais informações sobre como mudar as permissões de um usuário, veja [Gerenciando permissões de usuário para recursos do VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).
