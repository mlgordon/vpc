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
{:note: .note}
{:download: .download}

# Criando e gerenciando o armazenamento no VPC
{: #creating-and-managing-storage-in-vpc}

Atualmente, seu {{site.data.keyword.cloud}} Virtual Private Cloud permite somente volumes de armazenamento de inicialização.

Ao provisionar uma instância de servidor virtual, um volume de armazenamento de bloco de 100 GB é criado como um volume de inicialização primário e anexado à instância, automaticamente. O volume de inicialização fornece desempenho de 3 IOPS/GB e ele existe durante o ciclo de vida da VSI. 

Ao excluir a instância, o volume de inicialização é excluído.

## Melhores práticas para criar e nomear seus volumes de armazenamento VPC:

* Assegure-se de que você esteja nomeando TODOS os volumes no momento da provisão, incluindo o volume de inicialização.
* Assegure-se de que você esteja nomeando TODOS os seus anexos de volume no momento do anexo
* Cada volume deve ter um nome distinto dentro de uma região dentro de uma conta. 

Será possível reutilizar o nome de um volume depois que esse volume tiver sido excluído. No entanto, esteja ciente de que a reutilização de um nome de volume pode causar confusão para propósitos de faturamento.
{:note}
