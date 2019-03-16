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
{:important: .important}
{:download: .download}
{:table: .aria-labeledby="caption"}
{:DomainName: data-hd-keyref="DomainName"}

# Configurando o acesso ao seu Classic Infrastructure por meio do VPC
{: #setting-up-access-to-your-classic-infrastructure-from-vpc}

É possível configurar o acesso ao seu {{site.data.keyword.cloud}} Classic Infrastructure, incluindo conectividade de Direct Link, por meio de um VPC em cada região, para qualquer conta. Esses "VPCs de Acesso Clássico" especiais usam o mesmo roteador implícito que a sua infraestrutura clássica do {{site.data.keyword.cloud}}.

Quando você configura um VPC para acesso clássico, cada host de cálculo (VSI ou Bare Metal) em sua conta clássica pode enviar e receber pacotes para e do VPC de acesso clássico. No entanto, lembre-se de que firewalls, gateways, ACLs de rede ou grupos de segurança podem filtrar esse tráfego. Como uma melhor prática, recomendamos que você permita somente o tráfego que é necessário para que seus aplicativos funcionem adequadamente.

## Pré-requisitos:
1. Sua conta clássica deve ser vinculada à sua conta do IBM Cloud. Veja [Vinculando contas do IBMid](/docs/account/softlayerlink.html) para obter instruções sobre como fazer isso.
1. Sua conta clássica deve ser ativada para VRF.
    * Se já tiver o Direct Link em sua conta, você estará pronto.
    * Se a sua conta não estiver ativada para VRF, abra um chamado para solicitar "Migração VRF" para sua conta. Veja [Como é possível iniciar a conversão](/docs/infrastructure/direct-link?topic=direct-link-how-you-can-initiate-the-conversion) na documentação do Direct Link para saber mais sobre o processo de conversão.

Firewalls, gateways, ACLs de rede ou grupos de segurança podem filtrar alguns ou todo o tráfego de rede entre os recursos Classic e VPC.
{: important}

## Criar um VPC de Acesso Clássico
É possível criar um VPC com recurso de Acesso Clássico usando a Interface com o Usuário (IU), a Interface da Linha de Comandos (CLI) ou a Interface de Programação de Aplicativos (API).

Um VPC deve ser configurado para o Acesso Clássico quando ele é criado: não é possível atualizar um VPC para incluir ou remover o recurso de Acesso Clássico.
{: note}

### Criar um VPC de Acesso Clássico por meio da interface com o usuário

Crie um VPC de Acesso Clássico na página **Criar VPC**, clicando na caixa de seleção intitulada **Ativar acesso ao recurso clássico**, sob o rótulo **Acesso clássico**.

![classic-access-ui](/images/classic-access-ui.png)

### Criar um VPC de Acesso Clássico usando a CLI

Use a sinalização `--classic-access` ao criar o VPC. Por exemplo,

```
ibmcloud é vpc-create my-access-vpc -- classic-access
```
{: pre}


### Criar um VPC de Acesso Clássico usando a API

Passe o parâmetro `classic_access` ao criar o VPC. Por exemplo,

```bash
curl -X POST $rias_endpoint/v1/vpcs?version=2019-01-01 \
  -H "Authorization: $iam_token" \
  -d '{
        "name": "my-access-vpc",
        "classic_access": true
      }'
```
{: pre}


## Limitações

* Somente suas redes privadas (de volta) serão conectadas ao roteador implícito privado da sua conta.
* Somente sub-redes alocadas com APIs clássicas são conectadas ao lado clássico de seu roteador implícito privado. As sub-redes em VLANs clássicas não são roteadas pelo roteador implícito.
* Somente um VPC por região, por conta, pode ser ativado para o Acesso Clássico.
