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

# Resolução de problemas do seu IBM Cloud VPC
{: #troubleshooting-your-ibm-cloud-vpc}

Este documento abrange as dificuldades comuns que você pode encontrar e oferece algumas dicas úteis.

## Ativando o modo `TRACE` ao usar a CLI

Para ativar o modo `TRACE` (depurar) ao usar a CLI, configure `IBMCLOUD_TRACE=true` antes do comando da CLI.

Por exemplo:

 ```
IBMCLOUD_TRACE=true ibmcloud é pubgws
```

## Usando o modo DEBUG ou o modo `verbose` ao usar a API

Por exemplo, é possível incluir `--verbose` em seu comando `curl` e enviar-nos o valor `X-Request-Id:` para que possamos solucionar o problema. A sinalização `--verbose` é particularmente útil se você está tendo problemas de conectividade.

Outra opção é incluir a sinalização `-i` em seu comando `curl` para que a equipe de suporte possa ver os cabeçalhos na resposta de sua solicitação. Essa sinalização é útil na maioria das situações quando você precisa entrar em contato com o suporte.

## As chamadas da API requerem um token Bearer

Ao usar a API com um comando cURL, você pode precisar incluir "Bearer" no cabeçalho de Autorização, dependendo do que estiver no `$iam_token`. Se incluir a palavra "Bearer", você não a incluirá novamente no cabeçalho. A maioria dos nossos exemplos presume que "Bearer" está incluído no cabeçalho.

## Usando um terminal diferente para a CLI

Para mudar o terminal que a CLI do {{site.data.keyword.cloud}} usa para o RIAS por padrão, configure a variável de ambiente `IBMCLOUD_IS_IS_API_ENDPOINT` antes de usar a CLI. Por exemplo,

```
exportar IBMCLOUD_IS_API_ENDPOINT=api.dev.domain.com
```
{: pre}


## Problemas comuns

Aqui estão algumas dificuldades que você pode encontrar.

### Não autorizado (erro 401 ou 403)

Sua conta pode não estar autorizada para VPC. Certifique-se de que você esteja usando uma conta que tenha sido integrada.

### Não é possível criar recursos

Se não for possível criar um VPC ou outros recursos, certifique-se de que o proprietário da conta tenha concedido a você as [permissões] corretas (/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).

### As instâncias estão todas no status Desconhecido

Certifique-se de que o proprietário da conta tenha concedido a você as [permissões] corretas (/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources) para visualizar e gerenciar instâncias.

### Nenhuma resposta da API

Se a API não estiver mais retornando nenhum JSON, é provável que seu token do IAM tenha expirado e precise ser atualizado. Efetue login no IBM Cloud novamente ou atualize seu token executando `iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $4; }')`.

### Erro: conflito 409 ao chamar uma ação em uma instância

Não será possível chamar determinadas ações de instância se o status de sua instância estiver em conflito com a ação. Por exemplo, se o status da instância for `stopped` e você tentar executar uma ação `reboot`, o sistema retornará um erro 409.

| status      | action     | conflict |
| ----------- | ---------- | -------- |
| Running     | start      | yes      |
| Stopped     | any action but start  | yes      |
| Not running | pause      | yes      |
| Not running | reboot     | yes      |
| Not paused  | resume     | yes      |
| Paused      | any action but resume | yes      |


### A instância não está respondendo à solicitação `instance-reboot`

Se a sua instância não estiver respondendo a uma solicitação `instance-reboot`, será possível tentar uma solicitação `instance-reset`. É possível considerar `instance-reboot` como uma solicitação suave e `instance-reset` como uma solicitação brusca. A solicitação `instance-reboot` envia uma solicitação de reinicialização do S.O. para a instância, mas uma solicitação `instance-reset` executa uma reconfiguração brusca da instância da VSI. Você pode considerar a diferença como digitar "ctrl-alt-delete" no teclado de seu computador versus pressionar o botão de reconfiguração ou power. É bom lembrar que a solicitação `instance-reset` leva mais tempo para ser concluída do que a solicitação `instance-reboot`.

### Não é possível excluir recursos

Determinadas operações -- criar e excluir VSIs e criar e excluir sub-redes, por exemplo -- são concluídas de forma assíncrona por meio da API. Por causa desse fato, é recomendável pesquisar os recursos que você está excluindo, para verificar a exclusão antes de continuar.

Pode levar vários minutos para que os recursos sejam excluídos do sistema, devido a essas operações assíncronas. Para facilitar a exclusão, a melhor prática é fazer coisas nesta ordem:

1. Exclua suas instâncias
2. Exclua os gateways públicos
3. Exclua suas sub-redes
4. Excluir seus VPCs
