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

# Creación y gestión del almacenamiento en VPC
{: #creating-and-managing-storage-in-vpc}

Actualmente, su {{site.data.keyword.cloud}} Virtual Private Cloud solo permite volúmenes de almacenamiento de arranque.

Cuando suministra una instancia de servidor virtual, se crea un volumen de almacenamiento en bloque de 100 GB y se conecta a la instancia automáticamente. El volumen de arranque proporciona un rendimiento de 3 IOPS/GB y dura todo el ciclo de vida de la VSI. 

Cuando se suprime la instancia, el volumen de arranque se suprime.

## Prácticas recomendadas para crear y asignar un nombre a los volúmenes de almacenamiento de VPC:

* Asegúrese de que asignar un nombre a TODOS los volúmenes en el momento del suministro, incluido el volumen de arranque.
* Asegúrese de que asignar un nombre a TODAS las conexiones del volumen en el momento de realizar la conexión.
* Cada volumen debe tener un nombre distinto en una región dentro de una cuenta. 

Puede volver a utilizar el nombre de un volumen después de que se suprima dicho volumen. Sin embargo, tenga en cuenta que el hecho de volver a utilizar un nombre de volumen podría provocar confusiones a efectos de facturación.
{:note}
