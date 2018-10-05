---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# Diseño de la infraestructura de almacenamiento adjunto

{{site.data.keyword.vmwaresolutions_full}} proporciona tecnología de VMware que se despliega de forma automatizada en los {{site.data.keyword.CloudDataCents_notm}} de todo el mundo. En el conjunto de soluciones {{site.data.keyword.cloud_notm}}, el VMware vCenter Server base de la oferta {{site.data.keyword.cloud_notm}} consta de hasta 10 clústeres que contiene cada uno hasta 59 hosts vSphere, un solo controlador de servicios de la plataforma (PSC) y un dispositivo vCenter Server capaz de gestionar hasta 400 hosts y 4.000 máquinas virtuales.

La arquitectura que se presenta aquí complementa la solución de vCenter Server añadiendo almacenamiento adjunto como un dispositivo de almacenamiento compartido para el entorno. El dispositivo de almacenamiento adjunto se encuentra en el mismo {{site.data.keyword.CloudDataCent_notm}} que el despliegue de vCenter Server y consiste en un solo recurso de sistema de archivos de red (NFS) compartido o de varias exportaciones de NFS de {{site.data.keyword.cloud_notm}}.

En el siguiente gráfico se muestra la arquitectura general del almacenamiento adjunto en el despliegue de vCenter Server.

Figura 1. Arquitectura de alto nivel del almacenamiento conectado en {{site.data.keyword.cloud_notm}}

![Arquitectura de almacenamiento conectado](../solution/physical_nfs.svg "Arquitectura de alto nivel de almacenamiento conectado en IBM Cloud")

## Diseño de infraestructura física

La infraestructura física consta de tres componentes principales que incluyen el cálculo físico, almacenamiento físico y red física. Esto incluye la red de servicios {{site.data.keyword.cloud_notm}}, así como el almacenamiento físico que utiliza la infraestructura.

## Diseño de red física

La red física la gestiona {{site.data.keyword.cloud_notm}}. En esta sección se describe la red física que proporciona {{site.data.keyword.cloud_notm}} y su relación con el almacenamiento adjunto.

### Visión general de la red de IBM Cloud

La red física de {{site.data.keyword.cloud_notm}} está separada en tres redes distintas: pública, privada y de gestión. Para obtener más información sobre las redes pública, privada y de gestión, consulte [Visión general de la solución](../solution/solution_overview.html).

Para obtener más información sobre la red de {{site.data.keyword.cloud_notm}}, consulte [La red de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud-computing/bluemix/our-network){:new_window}.

Revise la información siguiente para ver una descripción de la red de servicios que forma parte de la red privada.

### Red de servicios privados

{{site.data.keyword.cloud_notm}} contiene una red de servicios privados que ofrece servicios comunes, como almacenamiento en bloque, almacenamiento de archivos, almacenamiento de objetos, programas de resolución de DNS y servidores NTP. Esta red privada es independiente de la red privada del cliente y permite que los entornos se conecten sin problemas a los servicios que se encuentran en {{site.data.keyword.cloud_notm}}. La red privada tiene varios niveles en la forma en que los servidores y otras infraestructuras están conectados a los conmutadores de cliente de fondo (BCS) agregados. Estos conmutadores agregados están conectados a un par de direcciones separados, es decir, direccionadores de clientes de fondo o BCR, para redes L3. La red privada también da soporte a la capacidad de utilizar tramas Jumbo, es decir, MTU 9000, para las conexiones de host físicas.

### VLAN

Para obtener más información acerca de las VLAN, consulte la sección _Diseño de la red física_ en el tema sobre [Diseño de la infraestructura física](../solution/design_physicalinfrastructure.html).

## Diseño de almacenamiento físico

En esta sección se muestra la configuración del dispositivo de almacenamiento adjunto que se encuentra en {{site.data.keyword.cloud_notm}}. El dispositivo de almacenamiento adjunto complementa la solución de servidor vCenter existente. Como resultado, los discos conectados localmente que son internos de los hosts físicos no se muestran.

## Rendimiento del almacenamiento adjunto

El almacenamiento de rendimiento y el resistente son soluciones de almacenamiento de {{site.data.keyword.cloud_notm}} diseñadas para dar soporte a aplicaciones con gran cantidad de E/S que requieren niveles de rendimiento predecibles. Este rendimiento predecible se consigue con la asignación de operaciones de entrada/salida de nivel de protocolo por segundo (IOPS) a volúmenes individuales.

Se puede suministrar un IOPS comprendido entre 100 y 48.000 con tamaños de almacenamiento que oscilan entre 20 GB y 12 TB. Los volúmenes de almacenamiento de rendimiento y resistentes están disponibles tanto para almacenamiento en bloque como para almacenamiento de archivos.

En este diseño, la solución de vCenter Server ofrece almacenamiento resistente para el almacenamiento adjunto. Como resultado, puede seleccionar y adjuntar (mediante automatización) exportaciones de NFS resistente comprendidas entre 20 GB y 12 TB. {{site.data.keyword.cloud_notm}} permite conectar un máximo de 64 hosts ESXi de vSphere a una sola exportación de NFS resistente.

La resistencia está disponible en tres niveles de rendimiento de IOPS para dar soporte a requisitos de aplicaciones variables. Tenga en cuenta que, después de que se suministre un recurso compartido NFS, se puede redimensionar o volver a configurar para permitir más o menos IOPS.

Para ver las opciones de IOPS detalladas, consulte la sección _Valores de almacenamiento_ del tema [Solicitud de instancias de vCenter Server](../../vcenter/vc_orderinginstance.html).

Además de los niveles de almacenamiento, el almacenamiento resistente de {{site.data.keyword.cloud_notm}} da soporte a un amplio abanico de requisitos de aplicaciones, que incluyen instantáneas, réplica y cifrado de datos inactivos en las ubicaciones del {{site.data.keyword.CloudDataCent_notm}}.

### Enlaces relacionados

* [Visión general de la solución](../solution/solution_overview.html)
