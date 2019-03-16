---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-02-20"

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:table: .aria-labeledby="caption"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Criando um VPC usando a CLI do IBM Cloud
{: #creating-a-vpc-using-the-ibm-cloud-cli}

Este guia mostra como criar os recursos do {{site.data.keyword.cloud}} Virtual Private Cloud usando a CLI do IBM Cloud.

## Pré-requisitos:

1. Instale a  [ CLI do IBM Cloud ](https://cloud.ibm.com/docs/cli/index.html#overview).

2. Instale ou atualize o plug-in `infrastructure-service` para a CLI do IBM Cloud.

  Para instalar:

  ```
  ibmcloud plugin install infrastructure-service
  ```
  {: pre}

  Para atualizar:

  ```
  ibmcloud plugin update
  ```
  {: pre}

  Para visualizar plug-ins e versões instalados:

  ```
  ibmcloud plugin list
  ```
  {: pre}


3. Gere uma chave SSH pública para provisionar Instâncias de Servidor Virtual (VSIs).

Talvez você já tenha uma chave SSH pública. Procure por um arquivo chamado ``id_rsa.pub`` sob um diretório ``.ssh`` sob seu diretório inicial, por exemplo, ``/Users/<USERNAME>/.ssh/id_rsa.pub ``. O arquivo começa com ``ssh-rsa`` e termina com seu endereço de e-mail.

Se você não tiver uma chave SSH pública ou se tiver esquecido a senha de uma existente, gere uma nova executando o comando ``ssh-keygen`` e seguindo os prompts.


Para aprender a criar um Virtual Private Cloud em diferentes regiões do IBM Cloud, veja o tópico [Regiões](/docs/infrastructure/vpc/vpc-regions.html).
{: tip}


## Etapa 1: Efetuar login no IBM Cloud.

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

### Etapa 2: Criar uma VPC e salvar o ID da VPC.

Use o comando a seguir para criar uma VPC denominada _helloworld-vpc_.

```
ibmcloud is vpc-create helloworld-vpc
```
{: pre}

Você deve ver a saída como esta:

```
Creating VPC helloworld-vpc in resource group Default under account <Account Name> as user <User>...

ID        ba9e785a-3e10-418a-811c-56cfe5669676   
Name      helloworld-vpc   
Default   no   
Created   1 second ago   
Status    available   
```
{:screen}

Salve o ID em uma variável para que possamos utilizá-lo posteriormente, por exemplo:

```
vpc="ba9e785a-3e10-418a-811c-56cfe5669676 "
```
{: pre}

## Etapa 3: Criar uma sub-rede e salvar o ID da sub-rede.

Vamos escolher a zona `us-south-2` para o local da sub-rede e chamar a sub-rede _helloworld-subnet_.

```
ibmcloud is subnet-create helloworld-subnet $vpc us-south-2 --ipv4-address-count 8
```
{: pre}

Você deve ver a saída como esta:

```
Creating Subnet helloworld-subnet in resource group Default under account <Account Name> as user <User>...

ID               50ba0da9-279a-4791-b7cb-cd3d7b2bc14d   
Name             helloworld-subnet   
IPv*             ipv4   
IPv4 CIDR        10.240.64.0/29  
IPv6 CIDR        -   
Addr available   3   
Addr Total       8   
Gen              -   
ACL              allow-all-network-acl-ba9e785a-3e10-418a-811c-56cfe5669676(e9c2790b-cee2-465a-8539-d8cd90d33621)   
Gateway          -   
Created          now   
Status           pending   
Zone             us-south-2   
VPC              helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)   
```
{:screen}

Salve o ID em uma variável para que possamos utilizá-lo posteriormente, por exemplo:

```
subnet="50ba0da9-279a-4791-b7cb-cd3d7b2bc14 "
```
{: pre}

Observe que o status da sub-rede é `pending` quando ela é criada pela primeira vez. Antes de continuar, a sub-rede precisa ser movida para o status `available`, o que leva alguns segundos. Para verificar o status da sub-rede, execute este comando:

```
ibmcloud é sub-rede $subnet
```
{: pre}

## Etapa 4: Criar uma chave SSH no IBM Public Cloud.

Você usará a chave para fornecer uma instância de servidor virtual. É possível usar a mesma chave para provisionar múltiplas instâncias de servidor virtual.

Para ver as chaves disponíveis em sua conta do IBM Cloud, execute este comando:

```
ibmcloud são chaves
```
{: pre}

Para criar uma chave, execute o comando a seguir. Substitua o caminho para o arquivo `id_rsa.pub`.

```
ibmcloud is key-create helloworld-key @ $HOME/ .ssh/id_rsa.pub
```
{: pre}

Você deve ver a saída como esta:

```
Creating key helloworld-key in resource group Default under account <Account Name> as user <User>...

ID               859b4e97-7540-4337-9c64-384792b85653
Name             helloworld-key
Type             rsa
Length           2048
FingerPrint      SHA256:hkcAOGB5z7QXqZLHd0kGqhj735qrfMjZLH9PxS/42vA
Key              ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC9i2joQ8eiFVdJ7pOlC6h5+IoBL6wFFygkk9Na3gV8Bi52dv44YOAjSJ2oduguHEtLp5r4eh4+5jiEBkFYkHNUhE0MxlcVZABTYWePXx4QnlmGr99xyOfi6DAHhSRQiSBhmhjcGjbADavDuIgoyKpVXbU9O1If3P0miNpaouaZmr+d68OHt4yPvNnztlluV3JBISJgqJ7pzg6wFF0SrjqtEYKBd8oxwogHu+rmRgT7IF09oSiKpKZRF0VfeLFz+REh9RuKa4Jh63aa2PRIgDKq6HO7MEdfOtGzCzoqqlFKgpl+VgGyT0b5BjQEnWv13cwx02bv5QCwma/GeAOpW0CD user@email.com   

Created          now   
```
{:screen}

Salve o ID em uma variável para que possamos utilizá-lo posteriormente, por exemplo:

```
key=" 859b4e97-7540-4337-9c64-384792b85653 "
```

## Etapa 5: Selecionar um perfil e uma imagem para a instância de servidor virtual.

Para listar todos os perfis de instância disponíveis, execute o comando a seguir:

```
ibmcloud é instance-profiles
```
{: pre}

Para listar todas as imagens disponíveis, execute o comando a seguir:

```
ibmcloud são imagens
```
{: pre}

Vamos escolher o perfil da instância `b-2x8` e a imagem `ubuntu-16.04-amd64`. Para obter o ID da imagem de `ubuntu-16.04-amd64`, execute o comando a seguir:

```
image=$(ibmcloud is images | grep "ubuntu-16.04-amd64" | cut -d" " -f1)
```
{: pre}

## Etapa 6: Fornecer uma instância de servidor virtual.

```
ibmcloud is instance-create helloworld-vsi $vpc us-south-2 b-2x8 $subnet 1000 --image-id $image --key-ids $key
```
{: pre}

Você deve ver a saída como esta:

```
Creating instance helloworld-vsi in resource group Default under account <Account Name> as user <User>...

ID                4562c5c0-9cf7-4406-bc90-ab4baea91057   
Name              helloworld-vsi   
Gen                  
Profile           b-2x8   
CPU Arch          amd64   
CPU Cores         2   
CPU Frequency     2000   
Memory            8   
Primary Intf      primary(2e850924-b5d7-4386-a778-03556d5850c1)   
Primary Address   10.240.64.4  
Image             ubuntu-16.04-amd64(7eb4e35b-4257-56f8-d7da-326d85452591)   
Status            pending   
Created           5 seconds ago   
VPC               helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)   
Zone              us-south-2   
```
{:screen}

Salve o ID da interface de rede primária `Primary Intf` em uma variável para que possamos usá-la posteriormente, por exemplo:

```
nico="2e850924-b5d7-4386-a778-03556d5850c1 "
```
{:pre}

Observe que o status da instância é `pending` quando ela é criada pela primeira vez. Antes de ser possível continuar, a instância precisa ser movida para o status `running`, o que leva alguns minutos. Para verificar o status de todas as instâncias, execute este comando:

```
ibmcloud is instances
```
{: pre}


## Etapa 7: Criar um endereço IP flutuante.

Você precisa de um endereço IP Flutuante para que seja possível efetuar login na instância de servidor virtual (VSI) por meio da Internet.

```
ibmcloud is floating-ip-reserve helloworld-fip -- nic-id $nic
```
{: pre}

Você deve ver a saída como esta:

```
Creating floating ip helloworld-fip in resource group Default under account <Account Name> as user <User>...

ID               b9d1cc1f-67db-40e3-81de-9228465170a5
Address          169.61.181.53
Name             helloworld-fip
Target           primary(2e850924-.)   
Target Type      intf   
Target IP        10.0.1.5   
Created          now   
Status           available   
Zone             us-south-2   
```
{:screen}

Salve o `Address` em uma variável para que possa ser usado posteriormente:

```
address=169.61.181.53
```
{: pre}

## Etapa 8: Incluir uma regra no grupo de segurança padrão para SSH

Localize o grupo de segurança para a VPC:

```
ibmcloud é vpc-sg $vpc
```
{: pre}

Você deve ver a saída como esta:
```
Getting default security group of vpc ba9e785a-3e10-418a-811c-56cfe5669676 under account <Account Name> as user <User>...

ID               2d364f0a-a870-42c3-a554-000000981149
Name             errand-drastic-imperial-retail-unlocked-jester
Created          1 week ago
VPC              helloworld-vpc(ba9e785a-3e10-418a-811c-56cfe5669676)
Grupo de Recursos - Tags -

Rules
ID                                     Direction   IPv*   Protocol                  Remote
b597cff2-38e8-4e6e-999d-000002031345   inbound     ipv4   all                       errand-drastic-imperial-retail-unlocked-jester(2d364f0a-.)
b597cff2-38e8-4e6e-999d-000002031527   outbound    ipv4   all                       -

```
{:screen}

Salve o ID em uma variável para que possa ser usado posteriormente:

```
sg=2d364f0a-a870-42c3-a554-000000981149
```
{: pre}

Agora crie a regra para permitir a SSH:

```
ibmcloud is sg-rulec $sg inbound tcp --port-min=22 --port-max=22
```
{: pre}

Você deve ver a saída como esta:

```
Creating rule for security group 2d364f0a-a870-42c3-a554-000000981149 under account <Account Name> as user <User>...

ID          b597cff2-38e8-4e6e-999d-000001949921
Direction   inbound
IPv*        ipv4
Protocol    tcp
Min Port    22
Max Port    22
Remote      -
```
{:screen}

## Etapa 9: Efetuar login em sua instância de servidor virtual usando sua chave SSH privada.

Por exemplo, é possível usar um comando deste formulário:

```
ssh -i $HOME/ .ssh/id_rsa root @ $address
```
{:pre}

Você receberá uma resposta semelhante ao exemplo a seguir. Quando for solicitado que continue se conectando, digite `yes`.

```
The authenticity of host '169.61.181.53 (169.61.181.53)' can't be established.
A impressão digital da chave ECDSA é SHA256:9MczXIwJq892DYwu0sZpQZOXORdvNXeP1aFioZpQDsM.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '169.61.181.53' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-133-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 pacotes podem ser atualizados.
0 atualizações são atualizações de segurança.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

root@helloworld-vsi: ~ #
```
{:screen}

## Etapa 10: Hello, World!

Execute o comando a seguir na janela do terminal:

```
echo ` hostname ` diz "Hello, World!"
```
{:pre}

Você deve ver a saída a seguir:

```
helloworld-vsi diz Hello, World!
```
{:screen}

## Parabéns.

Você provisionou e conectou-se com êxito à sua instância do Virtual Private Cloud usando a CLI do IBM Cloud. Para tentar mais comandos da CLI, explore a referência integral:

* [Referência de CLI para VPC](/docs/cli/reference/ibmcloud?topic=infrastructure-service-cli-vpc-reference#vpc-reference)
