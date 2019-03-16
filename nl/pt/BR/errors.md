---

copyright:

  years: 2018, 2019

lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}

# Mensagens de erro da API do IBM Cloud Virtual Private Cloud
{: #rias-error-messages}

Quando você recebe uma mensagem de erro das APIs do {{site.data.keyword.cloud}} Virtual Private Cloud, é possível usar o ID de mensagem para localizar mais informações sobre como resolver o problema.
{:shortdesc}

## acl_in_use
**Mensagem**: a ACL de rede não pode ser excluída porque ela está anexada a recursos.

A ACL de rede não pode ser excluída porque ela está anexada a recursos. Tente verificar suas sub-redes.

## address_prefix_conflict
**Mensagem**: o prefixo de endereço com esse CIDR está em uso.

O CIDR para o prefixo de endereço solicitado está em conflito com um prefixo de endereço existente.

## address_prefix_in_use
**Mensagem**: não é possível excluir um prefixo de endereço em uso.

Uma ou mais sub-redes estão usando o prefixo de endereço. Deve-se desconectar todas as sub-redes antes de poder excluir um prefixo.

## backend_service_indisponível
** Mensagem **: o serviço de backend está indisponível.

Um serviço de nuvem de back-end falhou ao responder. Uma causa para o recebimento desse erro pode ser um token do IAM ausente ou expirado. Tente novamente em alguns minutos. Se o problema persistir, entre em contato com o suporte.

## Bad_field
**Mensagem**: o UUID de instância correto deve ser fornecido

O nome do novo volume deve ser fornecido

Tente novamente, fornecendo um UUID ou volume válido em sua solicitação. 

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## Bad_request                                   
**Mensagem**: as informações fornecidas eram inválidas, estavam malformadas ou um campo obrigatório estava ausente.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## classic_access_vpc_conflict_duplicate_res
**Mensagem**: somente um VPC de Acesso Clássico pode ser criado.

Não é possível criar mais de um VPC de Acesso Clássico para uma conta

## default_address_prefix_not_localizado
** Mensagem **: prefixo de endereço padrão não localizado.

Você poderá ver essa mensagem de erro quando o prefixo de endereço padrão não for localizado.

## duplicate_error
** Mensagem **: a entrada fornecida já existe.

O recurso que você especificou já existe. Para resolver esse problema, use um nome diferente para o recurso que você deseja criar. Por exemplo, ao criar um novo VPC, será possível revisar uma lista de nomes para os VPCs já criados e escolher um nome que não seja conflitante, se você chamar primeiro `get VPC` usando ID, como este: `GET "/v1/vpcs/{id}” -H  "accept: application/json"`. 

## floating_ip_in_use
**Mensagem**: o IP flutuante está em uso.

Esse IP flutuante já está associado a uma interface de rede ou um gateway público.

## floating_ip_not_empty
**Mensagem**: não é possível excluir um servidor com um IP flutuante associado.

Certifique-se de desassociar o IP flutuante antes de excluir o servidor. 

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## gateway_too_muitos
**Mensagem**: é possível ter somente um gateway público por zona em um VPC.

Somente um gateway público por zona é permitido em um VPC, mas o gateway público pode ser anexado a múltiplas sub-redes na zona. Para localizar o gateway público para uma zona, execute a API GET public_gateways e veja os valores "vpc" e "zone". Se estiver usando a CLI, será possível executar o comando `ibmcloud is public-gateways` e ver os valores "VPC" e "Zone".

Use o ID do gateway público para anexá-lo a uma sub-rede, veja um exemplo em nossos [Exemplos de API](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis#step-13-attach-the-public-gateway-to-the-subnet-). Se estiver usando a CLI, será possível usar o comando de atualização de sub-rede para anexá-la a um gateway público, por exemplo, `ibmcloud is subnet-update SUBNET_ID --public-gateway-id PUBLIC_GATEWAY_ID`.


## http_request_size_exceeded                    
**Mensagem**: a solicitação de HTTP é muito grande.

Esse problema ocorre quando a carga útil que você enviou em sua solicitação tem muitos caracteres. Tente novamente com uma carga útil menor. Por exemplo, em vez de tentar fazer tudo em uma única solicitação, tente criar um recurso mínimo em uma solicitação e, em seguida, anexar o estado a ele incrementalmente em várias solicitações subsequentes. 

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## iam_failure
** Mensagem **: Nenhuma

Essa mensagem poderá ser exibida quando uma falha tiver ocorrido no serviço IAM, verificando a autenticação ou autorização. Essa indisponibilidade do serviço IAM pode ser temporária. Tente novamente a solicitação após alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policies_quota_exceeded
**Mensagem**: a cota para políticas IKE foi excedida para a conta.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar as políticas IKE atuais, use a API `GET /ike_policies`.

## ike_policy_duplicate_name
** Mensagem **: o nome  `<ike_policy_name>` já está em uso pela política IKE `<ike_policy_id>`.

Forneça um nome de política IKE diferente. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ike_policy_in_use
**Mensagem**: a política IKE `<ike_policy_id>` está em uso por uma ou mais conexões.

Uma política IKE não poderá ser excluída se ela estiver em uso por uma ou mais conexões.

## ike_policy_invalid_name
** Mensagem **: o nome  `<ike_policy_name>` não é um nome de política IKE válido.

Um nome de política IKE válido inicia com uma letra, seguida por letras, dígitos, sublinhados ou hifens.

## ike_policy_not_localizado
**Mensagem**: a política IKE `<ike_policy_id>`  não pôde ser localizado.

Você referenciou uma política IKE que não existe. Revise sua solicitação para assegurar que você tenha especificado o ID de política IKE adequado. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## insufficient_space_for_subnet
**Mensagem**: espaço insuficiente para sub-rede no prefixo de endereço

Você poderá obter esse erro se tentar criar uma sub-rede e ela não puder ser criada porque o número de endereços solicitados não pode ser alocado.

## internal_error
** Mensagem **: ocorreu um erro interno.

Por favor, tente novamente. Se esse erro persistir, entre em contato com o suporte.

## internal_server_error
** Mensagem **: Nenhuma

Esse erro ocorre quando o serviço encontra um erro inesperado. Esse problema pode ser temporário. Tente a solicitação novamente em alguns minutos.

Se o problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## internal_solution
** Mensagem **: entre em contato com seu administrador.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_id_format
** Mensagem **: Formato de ID inválido. Assegure-se de que o formato esteja correto.

Certifique-se de que o ID fornecido não contenha dados malformados.

Você poderá obter essa mensagem de erro se uma consulta de início malformada for usada ao fazer uma solicitação de paginação. Por exemplo,
`GET /v1/network_acls?start=23fbba08-ceb3-4cbe-a951-84ff20a06069?version=2019-01-01` contém dois `?`s. Corrija a consulta e tente novamente.

## invalid_state
** Mensagem **: Nenhuma

O comando RIAS `ibmcloud is in-reboot Instance_uuid` pode retornar o código de mensagem "invalid_state"

Em uma situação, a mensagem é lançada quando uma operação de reinicialização é tentada enquanto a VSI já está sendo reinicializada. Essa mensagem também pode ser recebida em uma situação em que múltiplas reinicializações não estão acontecendo ao mesmo tempo.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## invalid_version
**Mensagem**: o parâmetro `version` é inválido, ele deve estar no formato `YYYY-MM-DD`.

A versão deve obedecer ao formato _YYYY-MM-DD_. Para meses ou datas de dígito único, como 1º de janeiro, a versão deve ser semelhante a `2019-01-01`. O parâmetro de versão deve estar presente na URL. A data fornecida no parâmetro de versão deve ser após 01/01/2019 e antes da data atual. Por exemplo, para obter uma lista de VPCs, anexe a versão ao final da solicitação `GET "/v1/vpcs?version=2019-01-01”`.

## invalid_version_range
**Mensagem**: o valor de `version` não pode ser configurado em uma data futura nem antes de `2019-01-01`.

A versão deve obedecer ao formato _YYYY-MM-DD_. Para meses ou datas de dígito único, como 1º de janeiro, a versão deve ser semelhante a `2019-01-01`. O parâmetro de versão deve estar presente na URL. A data fornecida no parâmetro de versão deve ser após 01/01/2019 e antes da data atual. Por exemplo, para obter uma lista de VPCs, anexe a versão ao final da solicitação `GET "/v1/vpcs?version=2019-01-01”`.

## invalid_zone
**Mensagem**: verifique se os recursos que você está solicitando estão na mesma zona.

Você poderá ver essa mensagem se o recurso solicitado não estiver em uma zona válida.

## ipsec_policies_quota_exceeded
**Mensagem**: a cota para políticas IPsec foi excedida para a conta.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar políticas IPsec atuais, use a API `GET /ipsec_policies`.

## ipsec_policy_duplicate_name
** Mensagem **: o nome  `<ipsec_policy_name>` já está em uso pela política IPsec `<ipsec_policy_id>`.

Forneça um nome de política IPsec diferente. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## ipsec_policy_in_use
** Mensagem **: A política IPsec  `<ipsec_policy_id>` está em uso por uma ou mais conexões.

Uma política IPsec não poderá ser excluída se ela estiver em uso por uma ou mais conexões.

## ipsec_policy_invalid_name
** Mensagem **: o nome  `<ipsec_policy_name>` não é um nome de política IPsec válido.

Um nome de política IPsec válido inicia com uma letra, seguida por letras, dígitos, sublinhados ou hifens.

## ipsec_policy_not_localizado
** Mensagem **: A política IPsec  `<ipsec_policy_id>`  não pôde ser localizado.

Você referenciou uma política IPsec que não existe. Revise sua solicitação e certifique-se de que tenha especificado o ID de política IPsec adequado. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## key_exists
**Mensagem**: o mesmo conteúdo de chave já existe.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## listener_certificate_not_localizado
** Mensagem **: Instância de certificado com CRN  `<listener_certificate_crn>` não pode ser localizada ou não há nenhuma permissão para acessar a instância de certificado.

Forneça um CRN de instância de certificado existente ou peça ao administrador da conta para conceder a você permissões de acesso para a instância de certificado fornecida.

## listener_duplicate_port
** Mensagem **: porta  `<listener_port>`  é usado por outra instância do listener. Escolha uma porta diferente.

Escolha uma porta diferente.

## listener_invalid_certificate
**Mensagem**: o CRN de instância de certificado para o listener HTTPS é inválido.

Forneça um CRN de instância de certificado válido.

## listener_invalid_connection_limit
** Mensagem **: Limite de conexão do listener  `<listener_connection_limit>`  em inválido.

Forneça um limite de conexão válido. O limite de conexão tem que ser um número inteiro entre 1 e 15000.

## listener_invalid_port
**Mensagem**: a porta do listener `<listener_port>`  é inválido.

Escolha uma porta diferente.

## listener_invalid_protocol
** Mensagem **: protocolo Listener  `<listener_protocol>`  é inválido.

Forneça um protocolo listener válido. Os valores aceitáveis para o protocolo do listener são `http`, `https` e `tcp`.

## listener_missing_certificate_crn
**Mensagem**: o CRN da instância de certificado para o listener `https` está ausente.

O CRN da instância de certificado é um campo obrigatório.

## listener_missing_port
** Mensagem **: A porta do atendente está ausente.

A porta do atendente é um campo obrigatório.

## listener_missing_protocol
** Mensagem **: o protocolo Listener está ausente.

O protocolo Listener é um campo obrigatório. Forneça o protocolo do listener em sua solicitação. Os valores aceitáveis são `http`, `https` e `tcp`.

## listener_not_localizado
** Mensagem **: o listener com ID  `<listener_id>`  não pode ser localizado.

Forneça um ID do listener existente.

## listener_over_quota
** Mensagem **: o Listener não pode ser criado. A cota de listeners para o recurso de balanceador de carga atingiu o limite máximo.

As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## listener_pool_protocols_conflict
** Mensagem **: protocolo Listener (`<listener_protocol>`) e protocolo de conjunto (`<pool_protocol>`) estão em conflito.

Um listener com o protocolo `https` ou `http` pode ser associado somente a um conjunto com o protocolo `http`. Da mesma forma, um listener `tcp` pode ser associado somente a um conjunto `tcp`.

## listener_reserved_port_conflict
**Mensagem**: a porta do listener `<listener_port>`  é uma das portas reservadas. O intervalo de portas de 56500 a 56520 é reservado para propósitos de gerenciamento. Escolha uma porta diferente.

Escolha uma porta diferente.

## load_balancer_duplicate_name
** Mensagem **: Nome  `<load_balancer_name>` é usado por outra instância do balanceador de carga. Escolha um nome diferente.

Forneça um nome diferente para a instância do balanceador de carga.

## load_balancer_invalid_description
** Mensagem **: Descrição do balanceador de carga  `<load_balancer_description>`  é inválido.

A descrição do balanceador de carga não pode exceder 255 caracteres.

## load_balancer_invalid_is_public
** Mensagem **: valor de is_public  `<load_balancer_is_public>`  é inválido.

O balanceador de carga is_public deve ser true ou false.

## load_balancer_invalid_is_public_value
**Mensagem**: somente balanceadores de carga públicos são suportados.

Os balanceadores de carga privados ainda não são suportados.

## load_balancer_invalid_name
** Mensagem **: Nome  `<load_balancer_name>`  é inválido.

O nome não deve estar vazio. O comprimento do nome não deve exceder 40 caracteres. Um nome de balanceador de carga válido inicia com uma letra, seguida por letras, dígitos, sublinhados.

## load_balancer_missing_is_public
** Mensagem **: o campo 'is_public ' está ausente.

'is_public' é um campo obrigatório. Forneça o campo is_public do balanceador de carga.

## load_balancer_missing_name
** Mensagem **: o nome do balanceador de carga está ausente.

Forneça o nome do balanceador de carga. O nome do balanceador de carga é um campo obrigatório.

## load_balancer_missing_subnets
** Mensagem **: as sub-redes do balanceador de carga estão ausentes.

'subnets' é um campo obrigatório. Forneça as sub-redes nas quais criar o balanceador de carga em sua solicitação.

## load_balancer_not_localizado
** Mensagem **: o balanceador de carga com o ID  `<load_balancer_id>`  não pode ser localizado.

Forneça um ID do balanceador de carga existente.

## load_balancer_over_quota
** Mensagem **: o balanceador de carga não pode ser criado. A cota de instâncias do balanceador de carga sob sua conta atingiu o limite máximo.

Exclua um balanceador de carga existente ou entre em contato com o suporte para aumentar a cota do balanceador de carga em sua conta.

As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## load_balancer_unchanged_update
**Mensagem**: não há nada para atualizar o balanceador de carga com o ID `<load_balancer_id>`.

Não há nada para atualizar a instância do balanceador de carga.

## member_invalid_port
** Mensagem **: A porta do membro especificada  `<member_port>`  é inválido.

Forneça um número de porta válido. Um número de porta válido está no intervalo de 1 a 65535.

## member_invalid_weight
**Mensagem**: o peso do membro especificado `<member_weight>`  é inválido.

Forneça um peso de membro válido. Ele deve ser um número inteiro entre 0 e 100.

## member_missing_address
** Mensagem **: o endereço do membro está ausente.

O endereço do membro é um campo obrigatório. Forneça o endereço do membro em sua solicitação.

## member_missing_protocol_port
** Mensagem **: a porta do membro está ausente.

A porta do membro é um campo obrigatório. Forneça a porta do membro em sua solicitação.

## member_over_quota
** Mensagem **: o membro não pode ser criado. A cota de instâncias do membro sob o conjunto atingiu o limite máximo.

As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## missing_ims_account_id
** Mensagem **: Nenhuma

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## missing_version
**Mensagem**: o parâmetro `version` é necessário e deve estar no formato `YYYY-MM-DD`.

A versão deve obedecer ao formato _YYYY-MM-DD_. Para meses ou datas de dígito único, como 1º de janeiro, a versão deve ser semelhante a `2019-01-01`. O parâmetro de versão deve estar presente na URL. A data fornecida no parâmetro de versão deve ser após 01/01/2019 e antes da data atual. Por exemplo, para obter uma lista de VPCs, anexe a versão ao final da solicitação `GET "/v1/vpcs?version=2019-01-01”`.cs?version=2019-01-01”`.

## network_conflict
**Mensagem**: CIDR entra em conflito com o Prefixo de endereço existente no VPC

Você poderá ver essa mensagem se fornecer um CIDR de rede que entra em conflito com um CIDR de rede existente no mesmo espaço de IP.

## not_authorized                               
** Mensagem **: A solicitação não está autorizada.

Um motivo comum pelo qual você pode ver esse erro é se o token do IAM está ausente ou expirado. Para obter instruções sobre como gerar um token, consulte [Criando um VPC usando as APIs de REST](/docs/infrastructure/vpc/example-code.html#creating-a-vpc-using-the-rest-apis). Se o token não estiver expirado, poderá ser necessário verificar suas permissões e entrar em contato com seu administrador. 

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_localizado
**Mensagem**: verifique se o recurso que você está solicitando existe.

Você referenciou um recurso que não existe ou para o qual não tem acesso. Revise sua solicitação para assegurar que você tenha especificado os IDs e referências adequados.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## not_implementada
** Mensagem **: Nenhuma

O método não está implementado.

## not_in_address_prefix
**Mensagem**: o CIDR fornecido não se ajusta a nenhum dos prefixos de endereço na zona fornecida.

Esse erro ocorrerá se um usuário estiver tentando criar uma sub-rede com um CIDR que não caia em nenhum prefixo de endereço para a zona especificada.

Execute GET /vpcs/{vpc_id}/address_prefixes para obter a lista de prefixos de endereço para o VPC. Consulte os valores `cidr` e `zone` da resposta e certifique-se de que o `cidr` da sub-rede seja um subconjunto do `cidr` do prefixo de endereço para a zona em que você está tentando criá-lo.

## over_quota                                    
**Mensagem**: a solicitação excederia a cota para um tipo de recurso.

As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## password_not_ready
** Mensagem **: Nenhuma

Sua instância deve estar em execução antes que seja possível recuperar a senha. Tente novamente em alguns minutos. Se o problema persistir, entre em contato com o suporte.

## pool_delete_conflict
**Mensagem**: o conjunto não pode ser excluído porque ele ainda está associado a um ou mais listeners.

Assegure-se de que o conjunto seja desassociado a quaisquer listeners e tente novamente.

## pool_duplicate_name
** Mensagem **: nome do conjunto  `<pool_name>`  já está sendo usado por outro conjunto. Escolha um nome diferente.

Escolha um nome de conjunto diferente.

## pool_missing_algorithm
** Mensagem **: o algoritmo de balanceamento de carga está ausente.

O algoritmo de balanceamento de carga é um campo obrigatório. Forneça o algoritmo de balanceamento de carga em sua solicitação. Os valores aceitáveis são `round_robin`, `weighted_round_robin` e `least_connections`.

## pool_missing_health_monitor
** Mensagem **: o monitor de funcionamento do conjunto está ausente.

O monitor de funcionamento do conjunto é um campo obrigatório.

## pool_missing_name
**Mensagem**: o nome do conjunto está ausente.

O nome do conjunto é um campo obrigatório.

## pool_missing_protocol
** Mensagem **: O protocolo do conjunto está ausente.

O protocolo do conjunto é um campo obrigatório. Forneça o protocolo do conjunto em sua solicitação. Os valores aceitáveis são `http` e `tcp`.

## pool_not_localizado
** Mensagem **: o conjunto com ID  `<pool_id>`  não pode ser localizado.

Forneça um ID do conjunto existente.

## pool_over_quota
** Mensagem **: o conjunto não pode ser criado. A cota de conjuntos para o recurso de balanceador de carga atingiu o limite máximo.

As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc/?topic=vpc-quotas){: new_window}.

## public_gateway_in_use
**Mensagem**: não é possível excluir um gateway público quando ele está em uso.

O gateway público está atualmente anexado a uma ou mais sub-redes. Deve-se remover o gateway público de todas as sub-redes antes de poder excluí-lo.

## rate_limit_exceeded
**Mensagem**: muitas solicitações dentro de um curto tempo.

Essa mensagem de erro será retornada se muitas solicitações forem recebidas dentro de um intervalo de tempo especificado. Espere um pouco e tente novamente. 

## security_group_active_transactions
**Mensagem**: a interface não pode ser anexada ou removida até que a instância apareça no estado Ativo.

É necessário que a instância esteja ativa antes que suas interfaces de rede possam ser anexadas a um grupo de segurança. Use `GET /v1/instances/{id}?version=2019-01-01` ou `ibmcloud is instance` para verificar o status da instância. Quando o status for `running`, tente novamente. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_already_attached
**Mensagem**: a interface já está anexada ao grupo de segurança.


A interface já está anexada ao grupo de segurança. Use `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` ou `ibmcloud is security-group-network-interfaces` para visualizar as interfaces anexadas.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_exists
** Mensagem **: o grupo de segurança já existe.


Os nomes do grupo de segurança devem ser exclusivos. Já existe um grupo de segurança com esse nome. Use `GET /v1/security_groups?version=2019-01-01` ou `ibmcloud is security-groups` para visualizar os grupos de segurança atuais.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias) ou o [documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_attached
**Mensagem**: não é possível excluir o grupo de segurança enquanto as interfaces são anexadas.


Remova todas as interfaces antes de excluir o grupo de segurança. Use `DELETE /v1/security_groups/{id}/network_interfaces/{id}?version=2019-01-01` ou `ibmcloud is security-group-network-interface-remove` para remover uma interface.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias) ou o
[documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_interfaces_per_sg_exceeded
**Mensagem**: limite excedido de interfaces por grupo de segurança.

A anexação de outra interface ao grupo de segurança excederia o limite de interfaces por grupo de segurança. As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas) {: new_window}. Avalie sua estratégia e considere criar outro grupo de segurança com regras semelhantes.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias) ou o
[documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_last_security_group_is_default
**Mensagem**: o grupo de segurança padrão não pode ser removido quando ele é o único grupo de segurança anexado.

Uma interface de rede deve ser anexada a pelo menos um grupo de segurança.
Ela será anexada ao grupo de segurança padrão do VPC, se um não for especificado.
Anexe a interface a um grupo de segurança diferente e, em seguida, tente novamente removê-la do grupo de segurança padrão.
Para obter informações sobre o grupo de segurança padrão, consulte o [documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_limit_exceeded
** Mensagem **: limite do grupo de segurança excedido.

Você tentou criar um novo grupo de segurança, mas está atualmente em sua cota de conta. As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Avalie sua estratégia para designar instâncias a grupos de segurança. Muitas vezes, é possível reduzir o número geral de grupos de segurança designando múltiplas instâncias ao mesmo grupo de segurança. Essa estratégia reduzirá o número de grupos de segurança e fará você ficar abaixo sua cota de conta. Em casos raros, geralmente para grandes organizações, há a necessidade de expandir a cota. Nesse caso, [entre em contato com o suporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) para consultar se isso é possível.

## security_group_network_interface_not_active
**Mensagem**: a interface não pode ser anexada porque ela não está ativa.

As interfaces de rede devem estar ativas antes de anexar a grupos de segurança. Use `GET /v1/instances/{id}/network_interfaces/{id}?version=2019-01-01` ou `ibmcloud is instance-network-interface` para visualizar o status de uma interface. Quando o status for 'available', tente novamente. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_not_attached
** Mensagem **: A interface não está conectada.

A interface não está anexada ao grupo de segurança. Use `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` ou `ibmcloud is security-group-network-interfaces` para visualizar as interfaces anexadas.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias) ou o [documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group-using-the-cli){: new_window}.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).


## security_group_not_in_vpc
**Mensagem**: a interface e o grupo de segurança estão em VPCs diferentes.

Para anexar uma interface de rede a um grupo de segurança, a instância deve estar no mesmo VPC que o grupo de segurança. Use `GET /v1/security_groups/{id}?version=2019-01-01` ou `ibmcloud is security-group` para visualizar os detalhes de grupos de segurança e o VPC. Use `GET /v1/instances/{id}?version=2019-01-01` ou `ibmcloud is instance` para visualizar os detalhes da instância e o VPC.

## security_group_order_bindings
**Mensagem**: não é possível excluir o grupo de segurança enquanto ele tem ordens de instância pendentes.

Se uma instância foi criada com um ou mais grupos de segurança especificados nas interfaces de rede, a instância e as interfaces de rede deverão estar ativas antes que o grupo de segurança possa ser excluído.
Use `GET /v1/security_groups/{id}/network_interfaces?version=2019-01-01` ou `ibmcloud is security-group-network-interfaces` para visualizar as interfaces de rede conectadas e seus status. Quando o status das interfaces for 'available', tente novamente. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## security_group_port_max_less_than_port_min
**Mensagem**: a porta máxima do TCP/UDP não pode ser menor que a porta mínima.

O valor máximo de porta não pode ser menor que o valor mínimo de porta. Especifique um valor máximo de porta que seja maior que o valor mínimo de porta.

## security_group_port_range_both_or_neither
**Mensage **: o intervalo de portas deve ser desconfigurado ou uma porta mínima e uma máxima devem ser configuradas para 'tcp' e 'udp'.

As regras com um protocolo 'tcp' ou 'udp' podem ter um intervalo de portas desconfigurado (para aplicar a regra a todo o tráfego) ou elas podem especificar um intervalo de portas. Para restringir o tráfego para uma única porta, configure as portas mínima e máxima para o valor de porta. Por exemplo, o comando a seguir criaria uma regra para permitir SSH na porta 22: `ibmcloud is security-group-rule-add <id> tcp de entrada -- port-min 22 -- port-max 22 `.

Para obter informações adicionais sobre configurações de regra do grupo de segurança, consulte a [documentação da API](https://{DomainName}/apidocs/rias).


## security_group_port_range_invalid_protocol
**Mensagem**: um intervalo de portas foi especificado com um protocolo 'icmp'. Um intervalo de portas é válido somente para um protocolo 'tcp' ou 'udp'.

As regras com um protocolo 'icmp' têm um tipo e um código. As regras com os protocolos 'tcp' ou 'udp' têm um intervalo de portas. Para obter informações adicionais sobre configurações de regra do grupo de segurança, consulte a [documentação da API](https://{DomainName}/apidocs/rias).

## security_group_remote_group_not_in_vpc
**Mensagem**: o grupo remoto não está no mesmo VPC que este grupo de segurança.

As regras do grupo de segurança podem se referir a um grupo de segurança remoto, permitindo o tráfego entre as interfaces anexadas dos dois grupos. Os grupos de segurança remotos devem estar no mesmo VPC. Use `GET /v1/security_groups?2019-01-01` ou `ibmcloud is security-groups` para visualizar os grupos de segurança atuais e seus VPCs.

Para obter instruções adicionais para corrigir esse problema, consulte o [documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules
**Mensagem**: não é possível excluir o grupo de segurança enquanto regras remotas são anexadas.

O grupo de segurança contém uma ou mais regras que referenciam um grupo de segurança remoto. Use `GET /v1/security_groups/{id}/rules?version=2019-01-01` ou `ibmcloud is security-group-rules` para visualizar as regras. O campo 'remoto' especificará quaisquer grupos de segurança remotos. Tente novamente depois de excluir ou editar a regra remota.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias) ou o [documento Usando grupos de segurança](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups){: new_window}.


## security_group_remoting_rules_per_sg_exceeded
**Mensagem**: limite excedido de regras remotas por grupo de segurança.


A inclusão de outra regra que se refere a um grupo de segurança remoto excederia o limite de regras remotas por grupo de segurança. As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}.


## security_group_rules_per_sg_exceeded
**Mensagem **: limite excedido de regras por grupo de segurança.

A inclusão de uma regra excederia o limite de regras por grupo de segurança. As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Avalie sua estratégia e considere criar outro grupo de segurança.


## security_group_sgs_per_interface_exceeded
**Mensagem**: limite excedido de grupos de segurança por interface.

Anexar essa interface a outro grupo de segurança excederia o limite de grupos de segurança por interface. As cotas por recurso são fornecidas em [Cotas e limites para VPC](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#security-groups-quotas){: new_window}. Avalie sua estratégia e considere incluir regras em um grupo de segurança existente.


## security_group_type_code_invalid_protocol
**Mensagem**: um tipo/código de 'icmp' foi fornecido, mas o protocolo solicitado não era 'icmp'. Configure o protocolo como 'icmp' ou especifique um intervalo de portas.

Somente regras com um protocolo 'icmp' têm um tipo e um código. As regras com os protocolos 'tcp' ou 'udp' têm um intervalo de portas. Para obter informações adicionais sobre configurações de regra do grupo de segurança, consulte a [documentação da API](https://{DomainName}/apidocs/rias).

## security_group_vpc_default
**Mensagem**: não é possível excluir o grupo de segurança padrão para um VPC.

O grupo de segurança padrão não pode ser excluído. Para obter informações sobre o grupo de segurança padrão, consulte o guia em [Atualizando o grupo de segurança padrão](https://{DomainName}/docs/infrastructure/vpc-network?topic=vpc-network-updating-the-default-security-group).

## service_manager_service_failure
** Mensagem **: Nenhuma

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_acl_conflict
**Mensagem**: não é possível excluir a ACL de rede, ela é anexada a uma sub-rede.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_conflict
**Mensagem**: o CIDR entra em conflito com a Sub-rede existente no VPC.

Execute a API GET /subnets para recuperar todas as sub-redes no VPC. Certifique-se de que o CIDR fornecido não esteja sendo usado por outras sub-redes, verificando o valor de `ipv4_cidr_block`.

Se estiver usando a CLI, será possível executar `ibmcloud is subnets` e consultar o valor "Subnet CIDR" quanto a conflitos.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty
**Mensagem**: a sub-rede não está vazia, entre em contato com seu administrador.

Houve uma solicitação para excluir uma sub-rede, mas a sub-rede ainda contém recursos. As sub-redes podem conter instâncias, VPNs, balanceadores de carga ou gateways públicos. Deve-se excluir seus recursos na sub-rede antes de poder excluir a sub-rede. 

Em algumas situações, esse erro pode ocorrer mesmo quando o console mostra 0 VSIs e 0 balanceadores de carga, porque a exclusão é assíncrona e pode demorar alguns minutos para que o status interno mude. Tente a exclusão da sub-rede novamente em alguns minutos.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_pgway_exists
**Mensagem**: não é possível excluir a sub-rede enquanto ela está anexada a um gateway público. Remova o gateway público e tente novamente.

Houve uma solicitação para excluir uma sub-rede, mas a sub-rede ainda tem um gateway público anexado a ela. Deve-se excluir ou remover o gateway público antes de poder excluir a sub-rede. 

Se estiver usando a CLI, será possível executar `ibmcloud is public-gateways` para listar os gateways públicos e `ibmcloud is sub-net-public-gateway-detach` para remover um gateway público de uma sub-rede. 

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_ipaddr_exists
**Mensagem**: não é possível excluir a sub-rede enquanto ela contém endereços IP. Exclua qualquer instância do servidor associada ao endereço IP e tente novamente.

Houve uma solicitação para excluir uma sub-rede, mas a sub-rede ainda contém endereços IP. Deve-se excluir a instância do servidor associada ao endereço IP antes de poder excluir a sub-rede.

Se estiver usando a CLI, será possível executar `ibmcloud is instances` para listar as instâncias do servidor e consultar o valor "Address" para determinar seu Endereço IP e "Status" para determinar seu status. Execute `ibmcloud is instance-delete` para excluir uma instância do servidor que ainda não tenha um Status de "deleting". 

Em algumas situações, esse erro pode ocorrer mesmo quando o console mostra 0 VSIs, porque a exclusão é assíncrona e pode demorar alguns minutos para que o status interno mude. Tente a exclusão da sub-rede novamente em alguns minutos.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_loadbalancer_exists
**Mensagem**: não é possível excluir a sub-rede enquanto ela contém um balanceador de carga. Exclua o balanceador de carga e tente novamente.

Houve uma solicitação para excluir uma sub-rede, mas a sub-rede ainda contém um balanceador de carga. Deve-se excluir o balanceador de carga antes de poder excluir a sub-rede.

Se estiver usando a CLI, será possível executar `ibmcloud is load-balancers` para listar os balanceadores de carga e consultar o valor "Subnets" para determinar sua Sub-rede e "Status" para determinar seu status. Execute `ibmcloud is load-balancer-delete` para excluir um balanceador de carga que ainda não tenha um Status de "deleting". 

Em algumas situações, esse erro pode ocorrer mesmo quando o console mostra 0 balanceadores de carga, porque a exclusão é assíncrona e pode demorar alguns minutos para que o status interno mude. Tente a exclusão da sub-rede novamente em alguns minutos.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_not_empty_vpn_gway_exists
**Mensagem**: não é possível excluir a sub-rede enquanto ela contém um gateway VPN. Exclua o gateway VPN e tente novamente.

Houve uma solicitação para excluir uma sub-rede, mas a sub-rede ainda tem um gateway VPN anexado a ela. Deve-se excluir o gateway VPN antes de poder excluir a sub-rede. 

Se estiver usando a CLI, será possível executar `ibmcloud is vpn-gateways` para listar os balanceadores de carga e consultar o valor "Subnets" para determinar sua Sub-rede e "Status" para determinar seu status. Execute `ibmcloud is vpn-gateway-delete` para excluir um gateway VPN que ainda não tenha um Status de "deleting". 

Em algumas situações, esse erro pode ocorrer mesmo quando o console mostra 0 gateways VPN, porque a exclusão é assíncrona e pode demorar alguns minutos para que o status interno mude. Tente a exclusão da sub-rede novamente em alguns minutos.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## subnet_unknown_state
** Mensagem **: Nenhuma

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## system_limit_exceeded
**Mensagem**: essa operação excederia um limite do sistema

Um cenário possível para receber essa mensagem de erro é se você tentar criar um prefixo de endereço, mas o número máximo de prefixos de endereço já existir.

## target_in_use
**Mensagem**: o destino já tem IP flutuante anexado.

## token_invalid
**Mensagem**: o token de serviço estava expirado ou era inválido.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## token_missing
**Mensagem **: o token de serviço estava vazio ou não existia na solicitação.

Recrie um token e tente novamente.

## validation_enum
**Mensagem**: o valor fornecido não era uma opção válida.

Um dos campos fornecidos tem um valor que deve vir de uma enumeração de valores possíveis.

Para regras de ACL de rede, é possível especificar uma direção:

```
direction*	string
Whether the traffic to be matched is inbound or outbound

Enum: [ inbound, outbound ]
```

Por exemplo, o valor a seguir seria inválido, porque `northbound` não é uma opção válida na enumeração `[ inbound, outbound ]`.

```json
{
    "direction": "northbound"
}
```

## validation_failure                            
**Mensagem**: o JSON fornecido não correspondeu à estrutura esperada.

Para corrigir esse problema, certifique-se de que o conteúdo de sua solicitação seja JSON válido e que sua solicitação se adéque à [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_invalid_cidr                       
**Mensagem**: o valor não é um CIDR válido.

O valor deve ser um bloco CIDR interno válido com uma parte de 0 host.

Determinados intervalos de endereços IP são reservados. Mais informações sobre os intervalos de IP reservados estão disponíveis na visão geral de [Usando seu VPC com regiões e sub-redes](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv4_cidr        
**Mensagem**: o valor não é um CIDR IPv4 válido.

Deve ser um bloco CIDR interno IPv4 com uma parte de 0 host.

Determinados intervalos de endereços IP são reservados. Mais informações sobre os intervalos de IP reservados estão disponíveis na visão geral de [Usando seu VPC com regiões e sub-redes](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets){: new_window}.

## validation_invalid_ipv6_cidr
**Mensagem**: o valor não é um CIDR IPv6 válido.

Atualmente, o IPv6 não é suportado. Use um endereço IPv4.

## validation_invalid_address
**Mensagem**: o valor não é um endereço válido.

Deve ser um endereço IP válido

Uma lista de endereços IP reservados individualmente é fornecida no documento [Regiões e sub-redes](/docs/infrastructure/vpc-network?topic=vpc-network-working-with-ip-address-ranges-address-prefixes-regions-and-subnets).

## validation_invalid_ipv4_address
**Mensagem**: o valor não é um endereço IPv4 válido.

Forneça um endereço IPv4 válido.

## validation_invalid_ipv6_address
**Mensagem**: o valor não é um endereço IPv6 válido.

Forneça um endereço IPv6 válido. Atualmente, o IPv6 não é suportado; use um endereço IPv4.

## validation_invalid_field_type
**Mensagem**: o tipo de valor não corresponde ao tipo de campo.

Para corrigir esse problema, certifique-se de que o conteúdo de sua solicitação se adéque à [documentação da API](https://{DomainName}/apidocs/rias){: new_window} para o terminal que você está chamando.

## validation_max_value
**Mensagem**: o valor fornecido era muito grande.

Forneça um valor menor que atenda ao máximo conforme fornecido pela especificação. Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_min_value
**Mensagem**: o valor fornecido era muito pequeno.

Forneça um valor maior que atenda ao mínimo conforme fornecido pela especificação. Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_not_null
**Mensagem**: o campo fornecido deve ser nulo.

Certifique-se de que o valor seja nulo. Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

Aqui está um exemplo inválido:

```json
{
    "name": null }
```

## validation_only_one
**Mensagem**: o valor deve corresponder a um dos subesquemas.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## validation_discriminator_UNK
**Mensagem**: o campo discriminador proíbe essa subestrutura.

Por exemplo, se você especificar
```
{
protocolo: icmp port_min: 5 port_max: 100
}
```

O protocolo é `icmp` e _port_min_ é um campo `tcp`, portanto, você obterá um erro.
1. validation_discriminator_required para regras de  ` icmp `  ausentes
2. validation_discriminator_forbidden para campos `tcp` com `icmp` especificado

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_internal_error
** Mensagem **: Nenhuma

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_invalid_name
**Mensagem**: o valor não é um nome válido.


## validation_invalid_ref
**Mensagem**: o valor não é um HREF válido.


## validation_non_empty_uuid
** Mensagem **: Nenhuma

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_required_field
** Mensagem **: Ausente um campo obrigatório.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## validation_unique_failed
**Mensagem**: o campo fornecido deve ser exclusivo.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

Você pode ter especificado um nome que já esteja em uso. Tente um valor diferente.

## vpc_acl_conflict                           
**Mensagem**: não é possível excluir a ACL de rede padrão, ela é anexada a um VPC.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias) ou o [documento Usando ACLs de rede](/docs/infrastructure/vpc-network?topic=vpc-network-setting-up-network-acls-using-the-cli){: new_window}.

Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_not_empty
**Mensagem**: o VPC não pode ser excluído porque ele não está vazio.

Todos os recursos devem ser removidos de um VPC antes que ele possa ser excluído.

Você poderá receber esse erro se ainda tiver um gateway em seu VPC, mesmo quando todas as sub-redes forem excluídas, pois o gateway poderá existir no VPC sem uma sub-rede. Pode ser necessário usar a CLI para verificar os recursos órfãos.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpc_resource_separation
**Mensagem**: os recursos estão em VPCs diferentes

## vpn_connection_cidr_not_UNK
**Mensagem**: um bloco CIDR não pôde ser incluído na conexão VPN `<vpn_connection_id>`.

Forneça um CIDR válido que atenda aos requisitos fornecidos pela especificação. 

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_cidr_not_deleted
**Mensagem**: um bloco CIDR não pôde ser excluído da conexão VPN `<vpn_connection_id>`.

Forneça um CIDR válido que exista na conexão. Uma conexão deve ter pelo menos um CIDR local e peer.

 Para visualizar os blocos CIDR da conexão, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e verifique os campos `local_cidrs` e `peer_cidrs`.

## vpn_connection_cidr_not_localizado
**Mensagem**: o bloco CIDR não foi localizado na conexão VPN `<vpn_connection_id>`.

Forneça um CIDR válido que esteja na conexão.

Para visualizar os blocos CIDR da conexão, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e verifique os campos `local_cidrs` e `peer_cidrs`.

## vpn_connection_cidr_not_valid
** Mensagem **: o bloco CIDR  `<cidr_block>`  não representa um endereço válido.

O valor deve ser um bloco CIDR interno válido sem nenhum bit de host configurado.

Para visualizar os blocos CIDR da conexão, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e verifique os campos `local_cidrs` e `peer_cidrs`.

## vpn_connection_cidr_sobreposição
** Mensagem **: o bloco CIDR  `<cidr_block_1>`  se sobrepõe ao  `<cidr_block_2>`. Dois blocos CIDR de peer não podem se sobrepor no mesmo VPC e dois blocos CIDR locais não podem se sobrepor na mesma conexão.

Forneça um valor CIDR válido que atenda aos requisitos fornecidos pela especificação.

Para visualizar os blocos CIDR da conexão, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e verifique os campos `local_cidrs` e `peer_cidrs`.

## vpn_connection_duplicate_name
** Mensagem **: o nome  `<vpn_connection_name>` já está em uso pela conexão VPN `<vpn_connection_id>`.

Forneça um nome de conexão diferente. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_invalid_name
** Mensagem **: o nome  `<vpn_connection_name>` não é um nome de conexão VPN válido.

Um nome de conexão válido inicia com uma letra, seguida por letras, dígitos, sublinhados ou hifens.

## vpn_connection_invalid_psk_format
** Mensagem **: A chave pré-compartilhada (PSK)  `<psk>`  não está no formato válido.

Um PSK válido deve conter somente de 6 a 128 caracteres, que são letras, dígitos, `-`, `+`, `&`, `!`, `@`, `#`, `$`, `%`,`^`,`*`,`(`,`)`,`,`,`.`,`:`,`_`.

## vpn_connection_local_cidrs_required
**Mensagem**: pelo menos um bloco CIDR local é necessário ao criar uma conexão VPN.

Forneça um valor CIDR local válido que atenda aos requisitos fornecidos pela especificação.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## vpn_connection_local_subnets_quota_exceeded
**Mensagem**: a cota para sub-redes locais em conexões VPN foi excedida para o gateway VPN `<vpn_gateway_id>`.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar as sub-redes locais atuais em conexões VPN, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections` e verifique o campo `local_cidrs` para cada conexão.

## vpn_connection_local_subnets_quota_exceeded_for_connection
**Mensagem**: a cota de sub-redes locais '<quota_limit>' para a conexão VPN foi excedida.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vp?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar as sub-redes locais atuais para uma conexão VPN, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e verifique o campo `local_cidrs`.

## vpn_connection_not_localizado
** Mensagem **: A conexão VPN  `<vpn_connection_id>`  não pôde ser localizado.

Verifique se o ID de conexão está correto. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_peer_cidrs_required
**Mensagem**: pelo menos um bloco CIDR de peer é necessário ao criar uma conexão VPN.

Forneça um valor CIDR de peer válido que atenda aos requisitos fornecidos pela especificação.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## vpn_connection_peer_subnets_quota_exceeded
**Mensagem**: a cota para sub-redes de peer em conexões VPN foi excedida para o gateway VPN `<vpn_gateway_id>`.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar as sub-redes de peer atuais em conexões VPN, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections` e verifique o campo `peer_cidrs` para cada conexão.

## vpn_connection_peer_subnets_quota_exceeded_for_connection
** Mensagem **: A cota de  `<quota_limit>` sub-redes de peer para conexão VPN foi excedida.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar as sub-redes de peer atuais para uma conexão VPN, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections/<vpn_connection_id>` e verifique o campo `peer_cidrs`.

## vpn_connections_quota_exceeded
**Mensagem**: a cota para conexões VPN foi excedida para o gateway VPN `<vpn_gateway_id>`.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar as conexões VPN atuais para um gateway VPN, use a API `GET /vpn_gateways/<vpn_gateway_id>/connections `.

## vpn_connection_static_route_not_created
**Mensagem**: falha ao incluir uma rota estática para o bloco CIDR `<peer_cidr>`.

Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_static_route_not_deleted
**Mensagem**: falha ao remover uma rota estática para o bloco CIDR `<peer_cidr>`.

Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_connection_update_cidrs_not_permitido
**Mensagem**: os blocos CIDR não podem ser mudados ao atualizar uma conexão. Use a API correta ao criar ou excluir CIDRs.

Forneça um valor de solicitação válido que atenda aos requisitos fornecidos pela especificação.

Para obter instruções adicionais para corrigir esse problema, consulte a [documentação da API](https://{DomainName}/apidocs/rias){: new_window}.

## vpn_gateway_duplicate_name
** Mensagem **: o nome  `<vpn_gateway_name>` já está em uso pelo gateway VPN `<vpn_gateway_id>`.

Forneça um nome de gateway VPN diferente. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_initialization_error
**Mensagem**: o gateway VPN não pôde ser inicializado.

Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_invalid_name
** Mensagem **: o nome  `<vpn_gateway_name>` não é um nome de gateway VPN válido.

Um nome de gateway VPN válido inicia com uma letra, seguida por letras, dígitos, sublinhados ou hifens.

## vpn_gateway_invalid_state
** Mensagem **: o gateway VPN  `<vpn_gateway_id>` está em um estado inválido para a operação solicitada.

O Gateway VPN deve estar no status `available` antes de poder operá-lo. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_ip_create_error
**Mensagem**: não é possível criar um endereço IP para o gateway VPN.

Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_not_localizado
** Mensagem **: o gateway VPN  `<vpn_gateway_id>`  não pôde ser localizado.

Verifique se o ID do gateway VPN está correto. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_not_localizado
** Mensagem **: não foi possível localizar a sub-rede  `<subnet_id>`  para o gateway VPN fornecido.

Você referenciou uma sub-rede que não existe. Revise sua solicitação para assegurar que você tenha especificado o ID de sub-rede adequado. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateway_subnet_status_error
**Mensagem**: o gateway VPN não pôde ser criado devido ao status da sub-rede.

Forneça uma sub-rede que esteja no status `available`. Tente novamente em alguns minutos. Se esse problema persistir,  [ entre em contato com o suporte ](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support).

## vpn_gateways_quota_exceeded
**Mensagem**: a cota para gateways VPN foi excedida para a conta e/ou para a região.

As cotas por recurso são fornecidas na página [Cotas](https://{DomainName}/docs/infrastructure/vpc?topic=vpc-quotas#vpn-quotas){: new_window}.

Para visualizar os gateways VPN atuais, use a API `GET /vpn_gateways`.
