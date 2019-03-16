---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Criando um VPC usando as APIs de REST
{: #creating-a-vpc-using-the-rest-apis}

Este guia mostra como criar os recursos do {{site.data.keyword.cloud}} Virtual Private Cloud usando as APIs Regionais do IBM Cloud (RIAS).

## Pré-requisitos:

1. Instale a  [ CLI do IBM Cloud ](https://cloud.ibm.com/docs/cli/index.html#overview).

## Etapa 1: efetuar login no IBM Cloud para obter um token do IAM para ser usado nas chamadas da API.

Se você tiver uma conta federada:
```
ibmcloud login -sso
```
{: pre}

otherwise

```
ibmcloud login
```
{: pre}

Esse comando retorna uma URL e solicita uma senha. Acesse essa URL em seu navegador e efetue login. Se bem-sucedido, você obterá uma senha descartável. Copie essa senha e cole-a como uma resposta no prompt. Após as etapas de autenticação, você será solicitado a escolher uma conta. Responda a quaisquer prompts restantes para concluir o login.

## Etapa 2: obter um token do IBM Identity and Access Management (IAM)

O comando a seguir chama a CLI do IBM Cloud, analisa o token do IAM e o identificador de token `Bearer ` e o armazena em uma variável que pode ser usada em comandos posteriores.

```
iam_token=$(ibmcloud iam oauth-tokens | awk '/IAM/{ print $3 " " $4; }')
```
{: pre}

 Para visualizar seu token do IAM, execute o comando ``echo $iam_token``.

O resultado deve ser semelhante a este:

```
Bearer <your token>
```
{: screen}

O cabeçalho de Autorização espera que o token inicie com "Bearer". Se o resultado acima não incluir "Bearer", atualize a variável `iam_token` para incluí-la. Esses exemplos presumem que "Bearer" está incluído no `iam_token`.

Deve-se repetir a etapa anterior para atualizar seu token do IAM a cada hora, pois o token expira.
{: important}

## Etapa 3: armazenar o terminal de API como uma variável

Armazene o terminal de API em uma variável para que ele possa ser reutilizado posteriormente. Os terminais de API são por região
e seguem a convenção `https://<region>.iaas.cloud.ibm.com `. Por exemplo, o terminal de API `us-south` é `https://us-south.iaas.cloud.ibm.com`.

```
rias_endpoint=https: //us-south.iaas.cloud.ibm.com
 ```
{: pre}

Para verificar se essa variável foi salva, execute `echo $rias_endpoint` e certifique-se de que a resposta não esteja vazia.

## Etapa 4: executar a API GET Regions

Se você se deparar com resultados inesperados, inclua a sinalização `--verbose` (depuração) após o comando `curl` para obter informações detalhadas de criação de log. Também é possível verificar os erros normalmente encontrados na [página de resolução de problemas](/docs/infrastructure/vpc?topic=vpc-troubleshooting-your-ibm-cloud-vpc).
{: tip}

O comando a seguir retorna as regiões disponíveis para VPC, no formato JSON. Pelo menos um objeto deve retornar.

Anote o parâmetro de consulta `version` necessário para cada comando da API.
{: note}

```
curl $rias_endpoint/v1/regions?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Etapa 5: executar a API GET Zones

O comando a seguir retorna todas as zonas disponíveis para VPC na região `us-south`, no formato JSON. Pelo menos três objetos devem retornar.

```
curl $rias_endpoint/v1/regions/us-south/zones?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Etapa 6: executar a API GET Profiles

O comando a seguir retorna os perfis disponíveis para suas instâncias, no formato JSON. Pelo menos um objeto deve retornar.

Inclua ` | json_pp` após o comando curl para obter a sequência JSON legível
{: tip}


```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Se a saída da API for limitada por paginação, configure o limite maior que o `total_count`, por exemplo:

```
curl "$rias_endpoint/v1/instance/profiles?version=2019-01-01&limit=50" -H "Authorization: $iam_token"
```
{: pre}

## Etapa 7: executar a API GET Images

O comando a seguir retorna as imagens disponíveis para suas instâncias, no formato JSON. Pelo menos um objeto deve retornar.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Etapa 8: executar a API GET VPCs

O comando a seguir retorna os VPCs que foram criados sob sua conta (se houver), no formato JSON.

```
curl $rias_endpoint/v1/vpcs?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

## Etapa 9: Criar um Virtual Private Cloud

Crie um IBM Cloud VPC chamado `my-vpc`.

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
      	"name": "my-vpc"
      }'
```
{: pre}

Para o restante das chamadas, você precisará saber o ID do IBM Cloud VPC recém-criado. Cole seu ID na variável, conforme mostrado:

Algo como isso:  ` vpc="35fb0489-7105-41b9-99de-033fae723006 " `

```bash
vpc="<YOUR_VPC_ID>"
```
{: pre}

## Etapa 10: Criar uma Sub-rede

Crie uma sub-rede em seu IBM Cloud VPC. Por exemplo, vamos colocá-la na zona `us-south-2`.

```bash
curl -X POST $rias_endpoint/v1/subnets?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-subnet",
        "ipv4_cidr_block": "10.0.1.0/24",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Assim como com o Virtual Private Cloud, salve o ID da sub-rede em uma variável.

```bash
subnet= "< YOUR_SUBNET_ID>"
```
{: pre}

## Etapa 11: verificar o status de sua sub-rede

Para provisionar recursos em sua sub-rede, a sub-rede deve estar no status `available`. Consulte o recurso de sub-rede e certifique-se de que o status seja `available` antes de continuar. Se o status for `failed`, entre em contato com o [suporte](/docs/infrastructure/vpc?topic=vpc-getting-help-and-support) com os detalhes. É possível tentar continuar experimentando provisionar outra sub-rede.

```bash
curl $rias_endpoint/v1/subnets/ $subnet?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}


## Etapa 12: Criar um Gateway Público

Para permitir que as instâncias de servidor virtual na sub-rede tenham acesso à Internet pública, inclua um gateway público (PGW) na sub-rede.  

```bash
curl -X POST $rias_endpoint/v1/public_gateways?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-gateway",
        "zone": { "name": "us-south-2" },
        "vpc": { "id": "'$vpc'" }
      }'
```
{: pre}

Como você fez com o Virtual Private Cloud e a sub-rede, salve o ID do gateway público em uma variável.

```bash
gateway= "< YOUR_GATEWAY_ID>"
```
{: pre}

## Etapa 13: anexar o gateway público à sub-rede.

```bash
curl -X PUT $rias_endpoint/v1/subnets/$subnet/public_gateway?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "id": "'$gateway'"
      }'
```
{: pre}


## Etapa 14: criar uma chave SSH

Crie uma chave com sua chave SSH pública. Essa chave é usada ao criar a instância de servidor virtual e ela é necessária para efetuar login na instância de servidor virtual.

```bash
curl -X POST $rias_endpoint/v1/keys?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-key",
        "public_key": "ssh-rsa AAA....n",
        "type": "rsa"
      }'
```
{: pre}

Salve o ID da chave em uma variável.

```bash
key= "< YOUR_KEY_ID>"
```
{: pre}

## Etapa 15: escolher um perfil e uma imagem para sua instância de servidor virtual

Execute as APIs para listar todos os perfis e imagens disponíveis para sua instância de servidor virtual e escolha uma combinação.

```
curl $rias_endpoint/v1/instance/profiles?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Para obter detalhes adicionais sobre os perfis, é possível consultar o catálogo global usando o comando da CLI do IBM Cloud `ibmcloud catalog entry <profile-name> -- json `. Por exemplo,

```
entrada no catálogo ibmcloud b-2x8 -- json
```
{: pre}

O comando a seguir lista as imagens disponíveis.

```
curl $rias_endpoint/v1/images?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Salve o Nome do perfil e o ID da imagem em variáveis, que serão usadas posteriormente para provisionar uma instância de servidor virtual.

```bash
profile_name = "< CHOSEN_PROFILE_NAME>" image_id = "< CHOSEN_IMAGE_ID>"
```
{: pre}

## Etapa 16: provisionar uma instância de servidor virtual

Provisione uma instância de servidor virtual na sub-rede recém-criada. Passe a sua chave SSH pública para que seja possível efetuar login depois que a instância for provisionada.

```bash
curl -X POST $rias_endpoint/v1/instances?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "server-1",
        "type": "virtual",
        "zone": {
          "name": "us-sul-2"
        },
        "vpc": {
          "id": "'$vpc'"
        },
        "primary_network_interface": {
          "port_speed": 1000,
          "subnet": {
            "id": "'$subnet'"
          }
        },
        "keys":[{"id": "'$key'"}],
        "flavor": {
          "name": "'$profile_name'"
         },
        "image": {
          "id": "'$image_id'"
         },
        "userdata": ""
      }'
```
{: pre}

Como você fez com os outros recursos, salve o ID da instância de servidor virtual em uma variável.

```bash
server= "< YOUR_INSTANCE_ID>"
```
{: pre}

## Etapa 17: verificar o status de sua instância de servidor virtual

Provisionar uma Instância de Servidor Virtual pode levar de vários segundos a alguns minutos. Antes de continuar, consulte o status do servidor e certifique-se de que seja `running`.

```bash
curl $rias_endpoint/v1/instances/ $server?version=2019-01-01 -H "Authorization: $iam_token"
```
{: pre}

Além disso, salve o ID da interface de rede primária da instância de servidor virtual que é retornado na chamada da API acima.  

```bash
network_interface = "< YOUR_NETWORK_INTERFACE_ID>"
```
{: pre}

Não é possível obter a interface de rede primária até que você consulte a instância específica.
{: note}

## Etapa 18: Criar um IP Flutuante

Crie um IP flutuante para a instância de servidor virtual, usando a interface de rede primária da instância como o destino para o novo endereço IP flutuante.

```bash
curl -X POST $rias_endpoint/v1/floating_ips?version=2019-01-01 \
  -H "Authorization:$iam_token" \
  -d '{
        "name": "my-server-floatingip",
        "target": {
            "id":"'$network_interface'"
        }
      }
'
```
{: pre}


Salve o ID do IP flutuante.

```bash
floating_ip = "< YOUR_FLOATING_IP_ID>"
```
{: pre}

## Etapa 19: usar SSH em sua instância de servidor virtual

Para usar SSH para o servidor, use o `address` do IP Flutuante que você criou. Para obter o `address` do IP Flutuante, execute o comando a seguir:

```bash
curl -X GET $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Use o `address` do IP Flutuante para se conectar à instância de servidor virtual com SSH:

```bash
ssh -i <private_key_file> root@<floating ip address>
```
{: pre}

O acesso SSH ao servidor virtual pode ser evitado por grupos de segurança. Se o acesso SSH é necessário, deve-se usar um [grupo de segurança apropriado](/docs/infrastructure/vpc-network?topic=vpc-network-using-security-groups).
{: note}

Veja [Conectando-se à sua instância usando o Linux](/docs/vsi-is/vsi_is_connecting_linux_gc.html) para obter mais informações sobre como se conectar à sua instância.


## Etapa 20 (Opcional): exclua os recursos

Exclua os recursos, se desejado. Um recurso não poderá ser excluído se ele contiver outros recursos. Por exemplo, um Virtual Private Cloud não poderá ser excluído se ele contiver sub-redes e uma sub-rede não poderá ser excluída se ela contiver instâncias de servidor virtual. Em uma exclusão, a API pode retornar rapidamente, mas a exclusão do recurso pode ainda estar em andamento. É recomendável consultar o recurso para certificar-se de que ele seja excluído antes de excluir outros recursos.

### Exclua o IP flutuante.

```bash
curl -X DELETE $rias_endpoint/v1/floating_ips/$floating_ip?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Exclua a instância de servidor virtual.

```bash
curl -X DELETE $rias_endpoint/v1/instances/$server?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Exclua a chave.

```bash
curl -X DELETE $rias_endpoint/v1/keys/$key?version=2019-01-01 \
  -H "Authorization: $iam_token"
```
{: pre}


### Exclua o gateway público.

```bash
curl -X DELETE $rias_endpoint/v1/public_gateways/$gateway?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Exclua a sub-rede.

```bash
curl -X DELETE $rias_endpoint/v1/subnets/$subnet?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

### Exclua o VPC.

```bash
curl -X DELETE $rias_endpoint/v1/vpcs/$vpc?version=2019-01-01 \
  -H "Authorization:$iam_token"
```
{: pre}

Uma vNIC não pode ser excluída de uma VSI, portanto, não há necessidade de fazer uma etapa para exclusão de vNICs.
{: note}

## Parabéns.

Você provisionou com êxito uma instância do Virtual Private Cloud usando as APIs de REST. Para tentar mais comandos da API, explore a referência integral:

* [Referência de API para VPC](https://{DomainName}/apidocs/rias)
