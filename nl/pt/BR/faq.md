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
{:faq: data-hd-content-type='faq'}
{:DomainName: data-hd-keyref="DomainName"}


# Perguntas Mais Freqüentes
{: #faqs}

## Qual é o limite do número de caracteres em um nome de VPC?
{:faq}

Atualmente, o limite é 100. Se esse limite for excedido, você poderá receber uma mensagem de "erro interno".

## Qualquer um dos nomes de recurso do VPC pode iniciar com um número?
{:faq}

Não, embora o nome possa conter números, ele deve iniciar com uma letra.

## Há restrições com relação a quais caracteres posso usar em um nome?
{:faq}

Sim, a IU bloqueia os traços duplos consecutivos, sublinhados e pontos de serem parte de um nome de VSI.


## Durante a designação de IP flutuante em um VPC, um cliente deve especificar a vNIC da VSI. Isso é correto?
{:faq}

Sim, de fato ela deve ser a interface de rede primária de um servidor.

No entanto, se incluíssemos um recurso "address" na API sob a área de rede, poderíamos muito bem mudar a associação do IP flutuante para o endereço em vez da interface.

## Pode uma vNIC em uma instância de servidor virtual em meu VPC ter o IP flutuante e o IP privado?
{:faq}
 
Sim.

## Na IU do IBM Cloud Console para VPC, há somente uma ”alternância" para cada sub-rede para anexar ou remover do Gateway Público. Quem cria a PGW? O PGW será padronizado para estar pronto quando um cliente desejar anexar a sub-rede ao PGW na IU?
{:faq}

O PGW precisa ser criado explicitamente por meio da API em sua forma atual, porque a API requer uma associação explícita de uma sub-rede a um determinado gateway público.

## Imagine que a VSI1 em um VPC tenha somente a vNIC1 e esteja anexada à Subnet1. A Subnet1 é anexada a um Gateway Público (PGW). Um cliente ainda pode designar um IP flutuante à VSI1?
{:faq}

Sim, um servidor pode estar em uma sub-rede anexada a um gateway público e também ter um IP flutuante. A designação de IP flutuante a uma VSI não está relacionada a se há um gateway público anexado à sub-rede. Um IP flutuante associado a uma VSI terá precedência sobre o gateway público anexado à sub-rede.

## Em meu VPC, a VSI1 tem 2 vNICs, chamadas vNIC1 e vNIC2. É possível que essas duas vNICs sejam anexadas à mesma sub-rede?
{:faq}
 
Sim, não há limitação em ter múltiplas interfaces de rede no mesmo servidor anexado à mesma sub-rede. No entanto, múltiplas NICs em uma VSI não são atualmente suportadas.

## Uma VSI pode ser criada sem uma sub-rede, apenas com o IP flutuante?
{:faq}

Não.

## Uma VSI pode ser anexada a mais de um VPC?
{:faq}

Não.

## É possível mudar o tamanho da sub-rede depois que ela é criada em um VPC?
{:faq}

Não.

## Durante a criação do PGW, eu preciso reservar o FIP ou o sistema reserva automaticamente o FIP? Eu verei esse IP flutuante quando eu consultar todos os IPs flutuantes?

Como a especificação está atualmente definida, o RIAS criará automaticamente um IP flutuante junto com o gateway público se um IP flutuante existente não for especificado. E sim, o IP flutuante será mostrado na lista.

## Quem impõe que deve haver somente 1 Gateway Público por zona para um VPC?
{: faq}

O Regional Infrastructure API Service (RIAS) força esse limite.

## Como o VRF afeta meus outros recursos de rede e minhas sub-redes?
{:faq}

Avisos para VLANs e VRF:

* A ampliação da VLAN interconta não é permitida no ambiente VRF.
* O serviço VPN IPSec é limitado.

**Nota:** o VRF não evita o acesso à VPN SSL ou PPTP, mas seu comportamento muda. Sem o VRF, uma conexão VPN é suficiente para ver todos os servidores em sua conta. Com o VRF, é possível acessar somente recursos no mercado associados à sua VPN. Portanto, se você se conectar à VPN do DAL, será possível apenas se conectar a servidores do DAL.

## Qual é a maneira correta de usar o subcomando `instance-network-interface-floating-ip-add` no VPC? Alguém cria/aloca um endereço IP flutuante antecipadamente?
{:faq}

 É necessário alocar um IP flutuante primeiro e, em seguida, fornecer o endereço FIP no comando de IP flutuante da interface `add`.

 Por exemplo: `ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE | --nic NIC_ID)`. Forneça a zona.

 ## Por que preciso especificar uma sub-rede ao configurar minha VPN para VPC e o que devo especificar?
 {:faq}

Ao configurar um gateway VPN, deve-se especificar uma sub-rede, para que o gateway VPN possa obter os endereços IP que ele requer para o serviço VPN. Especificando a sub-rede, você retém o controle sobre como o tráfego de VPN é manipulado e tem a flexibilidade de especificar um local que esteja mais próximo dos recursos que utilizam a VPN. Dessa maneira, é possível reduzir a latência e melhorar o desempenho. 

## Há encargos de largura da banda de egresso para tráfego de VPC para COS?
{:faq}

Não há encargos de largura da banda de egresso, desde que o terminal de ADN seja usado para se conectar do VPC ao COS, mas os encargos de chamada da API ainda se aplicam.

## Como eu sei onde as instâncias do balanceador de carga serão implementadas?
{:faq}

As sub-redes escolhidas determinam onde o balanceador de carga do VPC será implementado. O balanceador de carga do VPC é um recurso regional. A melhor prática é escolher sub-redes de diferentes zonas sob uma determinada região para aumentar a redundância
