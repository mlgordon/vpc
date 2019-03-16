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

# Iniciación a la infraestructura de IBM Cloud Virtual Private Cloud
{: #getting-started-with-ibm-cloud-virtual-private-cloud-infrastructure}

IBM aceptará la participación de un número limitado de clientes en un programa de acceso temprano a VPC a partir de principios de abril de 2019 y en los meses siguientes se ampliará su uso. Si su organización desea obtener acceso a IBM Virtual Private Cloud, complete este [formulario de nominación](https://cloud.ibm.com/vpc){: new_window} y un representante de IBM se pondrá en contacto con usted para indicarle los siguientes pasos a seguir.
{: important}

Para empezar a trabajar con la infraestructura de {{site.data.keyword.cloud}} Virtual Private Cloud:

1. Cree una nube privada virtual.
2. Cree una o varias subredes en la nube privada virtual en una o varias zonas.
3. Cree una pasarela pública (PGW) en una subred si desea que los recursos de la subred tengan acceso a Internet o viceversa.
4. Seleccione los perfiles de las instancias de servidor virtual (VSI) que desee ejecutar y cree una instancia de los mismos.
5. Reserve una dirección IP flotante y asóciela con una instancia de servidor virtual si desea acceder a ella desde Internet.
5. Despliegue el servicio o las aplicaciones en las instancias de servidor virtual.

## Requisitos previos

 * **Permisos de usuario**: Asegúrese de que el usuario tiene permisos suficientes para crear y gestionar recursos en la VPC. Para obtener una lista de los permisos necesarios, consulte [Cómo otorgar los permisos necesarios para usuarios de VPC](/docs/infrastructure/vpc?topic=vpc-managing-user-permissions-for-vpc-resources).

 * **Tenga la clave SSH preparada**: Utilizará una clave SSH para conectarse a las instancias del servidor virtual.

   * Busque un archivo denominado `id_rsa.pub` en un directorio `.ssh` del directorio de inicio; por ejemplo, `/Users/<USERNAME>/.ssh/id_rsa.pub`. El archivo empieza por `ssh-rsa` y termina con su dirección de correo electrónico.

   * O genere una clave SSH: Si no tiene una clave SSH pública o si ha olvidado la contraseña de una clave existente, genere una nueva ejecutando el mandato `ssh-keygen` y siguiendo la solicitud siguiente. Por ejemplo, puede generar una clave SSH en el servidor Linux ejecutando el mandato `ssh-keygen -t rsa -C "ID_usuario"`. Este mandato genera dos archivos. La clave pública generada se encuentra en el archivo `<your key>.pub`.
   
## Utilice la IU, la CLI o la API REST

Puede suministrar y gestionar todos sus recursos de VPC mediante la IU, la CLI o la API REST.

Si es un nuevo usuario de IBM Cloud Virtual Private Cloud, elija cualquiera de los enlaces siguientes, que le guiarán por el proceso de creación de su IBM Cloud VPC y sus recursos, de principio a fin. Puede elegir si va a comenzar desde la interfaz de usuario de la consola, desde la línea de mandatos (CLI) o desde la API de servicios de infraestructura regional (RIAS).

* Para acceder a través de la interfaz de usuario, inicie una sesión en la [consola de IBM Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]( https://{DomainName}/vpc){: new_window}. Siga la [guía de la interfaz de usuario](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console) si necesita ayuda.
* Para utilizar la interfaz de línea de mandatos, utilice el plugin [infrastructure-service](/docs/infrastructure-service-cli-plugin/vpc-cli-reference.html) de la [CLI de IBM Cloud](https://console.bluemix.net/docs/cli/index.html#overview) y siga el ejemplo [Hello World](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-cli).
* Los usuarios más avanzados pueden llamar directamente a las [API REST](https://{DomainName}/apidocs/rias). Siga la guía de aprendizaje del [código de ejemplo](/docs/infrastructure/vpc?topic=vpc-creating-a-vpc-using-the-rest-apis) para empezar a utilizar las API REST.

## Pasos siguientes
Si está preparado para empezar a trabajar, vaya directamente a la documentación detallada acerca de **Redes de VPC** y **VSI for VPC**:

* [**Redes de IBM Virtual Private Cloud**](/docs/infrastructure/vpc-network?topic=vpc-network-getting-started-with-networking-for-virtual-private-cloud)
* [**IBM Virtual Servers para Virtual Private Cloud**](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen)

