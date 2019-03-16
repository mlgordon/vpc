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
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Introdução ao IBM Cloud Virtual Private Cloud Infrastructure
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

A IBM aceitará um número limitado de clientes para participar de um programa de Acesso Antecipado ao VPC em abril de 2019, com o uso expandido sendo aberto nos meses seguintes. Se a sua organização desejar obter acesso ao IBM Virtual Private Cloud, preencha este [formulário de nomeação](https://cloud.ibm.com/vpc){: new_window} e um representante IBM entrará em contato com você sobre as próximas etapas.
{: important}

Para começar com o {{site.data.keyword.cloud}} Virtual Private Cloud Infrastructure:

1. Crie uma Nuvem Privada Virtual.
2. Crie uma ou mais sub-redes na nuvem particular virtual em uma ou mais zonas.
3. Crie um gateway público (PGW) em uma sub-rede se você desejar que os recursos em sua sub-rede tenham acesso à Internet ou vice-versa.
4. Selecione os perfis de instâncias de servidor virtual (VSIs) que você gostaria de executar e instancie-os.
5. Reserve um endereço IP flutuante e associe-o a uma instância de servidor virtual se desejar atingi-la por meio da Internet.
5. Implemente seu serviço ou aplicativos entre as instâncias de servidor virtual.

## Pré-requisitos

 * **Permissões do usuário**: certifique-se de que seu usuário tenha permissões suficientes para criar e gerenciar recursos na VPC. Para obter uma lista de permissões necessárias, consulte [Concedendo permissões necessárias para usuários da VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).

 * **Tenha sua chave SSH pronta**: você usará uma chave SSH para se conectar às suas instâncias do servidor virtual.

   * Procure por um arquivo chamado `id_rsa.pub` sob um diretório `.ssh` sob seu diretório inicial, por exemplo, `/Users/<USERNAME>/.ssh/id_rsa.pub `. O arquivo começa com `ssh-rsa` e termina com seu endereço de e-mail.

   * Ou gere uma chave SSH: se você não tiver uma chave SSH pública ou se tiver esquecido a senha de uma existente, gere uma nova executando o comando `ssh-keygen` e seguindo os prompts. Por exemplo, é possível gerar uma chave SSH em seu servidor Linux executando o comando `ssh-keygen -t rsa -C "user_ID"`. Esse comando gera dois arquivos. A chave pública gerada está no arquivo `<your key>.pub ` .
   
## Usar a IU, a CLI ou a API de REST

É possível provisionar e gerenciar todos os seus recursos do VPC por meio da IU, CLI ou API de REST.

Se você for novo no IBM Cloud Virtual Private Cloud, escolha qualquer um dos links abaixo, que o guiará por meio do processo de criação do IBM Cloud VPC e seus recursos, desde o início até a conclusão. É possível escolher se deve ser iniciado por meio da IU do console, da linha de comandos (CLI) ou da API de serviços de infraestrutura regional (RIAS).

* Para acesso por meio da interface com o usuário, efetue login no [IBM Cloud Console ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]( https://{DomainName}/vpc){: new_window}. Siga o [Guia da IU](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console) se precisar de ajuda.
* Para usar a interface da linha de comandos, use o plug-in [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) da [CLI do IBM Cloud](https://console.bluemix.net/docs/cli/index.html#overview) e siga o exemplo [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli).
* Para usuários mais avançados, é possível chamar as [APIs de REST](https://{DomainName}/apidocs/rias) diretamente. Siga o tutorial de [código de exemplo](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis) para começar com as APIs de REST.

## Próximas etapas
Se você estiver pronto para entrar em ação, vá diretamente para a documentação detalhada sobre **Rede VPC** e **VSIs para VPC**:

* [ ** IBM Virtual Private Cloud Networking ** ](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**IBM Virtual Servers for Virtual Private Cloud**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

