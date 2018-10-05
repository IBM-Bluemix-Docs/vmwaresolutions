---

copyright:

  years:  2016, 2018

lastupdated: "2017-11-20"

---

# Notas del release para V2.0

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud

El servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} ya está disponible para la V2.0 y posteriores de instancias de VMware Cloud Foundation y para instancias de VMware vCenter Server. Este servicio despliega un par de alta disponibilidad (HA) de dispositivos virtuales FortiGate en el entorno, lo que le puede ayudar a reducir el riesgo mediante la implementación de controles de seguridad estrictos en la infraestructura virtual.

Solicite instancias con el servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} incluido al solicitar la instancia, o puede añadir este servicio a las instancias existentes más adelante desde el separador **Servicios** de la página de detalles de la instancia. Dependiendo de sus necesidades, seleccione uno de los tres tamaños de despliegue y opciones de licencia para este servicio. Después de que se instale correctamente el servicio, gestione y configure reglas de cortafuegos para los dispositivos virtuales FortiGate desde la consola de FortiGate.

Para obtener más información, consulte los temas siguientes:
* [Componentes y consideraciones sobre FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html)
* [Gestión de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html)

## Instalación de varios servicios para F5 on IBM Cloud y FortiGate Virtual Appliance on IBM Cloud

Ahora puede instalar varias instancias del servicio F5 on {{site.data.keyword.cloud_notm}} y del servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} para una instancia de Cloud Foundation o una instancia de vCenter Server. Cuando seleccione el servicio F5 o el servicio FortiGate durante la solicitud de una instancia, debe especificar un nombre exclusivo para la instancia de servicio para distinguirla de las instancias de servicio adicionales que pueda instalar posteriormente.

Una vez finalizado el despliegue de la instancia, puede añadir más instancias del servicio F5 o del FortiGate instalando el servicio en el separador **Añadir servicios** de la página de detalles de la instancia. Debe añadir las instancias de servicio de una en una y debe repetir el proceso para todas las instancias que desee añadir para un servicio.

Para obtener más información, consulte los temas siguientes:
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)

## Actualizaciones para FortiGate Security Appliance on IBM Cloud

En este release, se ha cambiado el nombre del servicio Fortinet on {{site.data.keyword.cloud_notm}} por el de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}. El par de dispositivos de seguridad FortiGate (FSA) del servicio se configura de modo que esté protegido de forma predeterminada cuando se despliega en la instancia.
* Si despliega un par de FSA como parte de una nueva instancia de Cloud Foundation en vCenter Server, los FSA se configuran de modo que solo permitan las comunicaciones de salida necesarias entre su instancia y la red pública y denieguen todas las demás comunicaciones.
* Si despliega un par de FSA como parte de una instancia de Cloud Foundation o de una instancia de vCenter Server existente, los FSA se configuran con una regla explícita que permite todas las comunicaciones de gestión de salida entre la instancia y la red pública, y los FSA también se configuran con una regla que permite todas las demás comunicaciones para garantizar que no se interrumpe el tráfico de aplicaciones existente.

En cualquiera de los casos, debe gestionar la configuración de los FSA cuidadosamente para que solo se permitan las comunicaciones necesarias y se denieguen todas las demás comunicaciones.

## Coherencia del formato de los nombres de dominio completos

Ahora el nombre de dominio completo (FQDN) se representa de forma coherente para todas las instancias. Cuando realiza un pedido, puede especificar su propio prefijo de subdominio y un prefijo de nombre de host para asegurarse de que se sigue el convenio del sector para el formato FQDN. Por ejemplo, `host-name-prefix<n>.subdomain-prefix.domain-name`.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Solicitud de clústeres nuevos de vSphere](../vsphere/vs_orderinginstances.html)

## Estimaciones de carga de trabajo y de almacenamiento durante una solicitud de la instancia

* Durante una solicitud de VMware vSphere on {{site.data.keyword.cloud_notm}}, se le proporciona una estimación del número de máquinas virtuales que se pueden ejecutar en la instancia solicitada.
* Durante una solicitud de Cloud Foundation y de vCenter Server, se le proporciona una estimación de la capacidad de almacenamiento utilizable para la instancia solicitada.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Solicitud de clústeres nuevos de vSphere](../vsphere/vs_orderinginstances.html)

## Actualizaciones de instancias de VMware Cloud Foundation

El release actual aplica las siguientes actualizaciones y mejoras de componentes para nuevos despliegues:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Release de parche ESXi650-201710401-BG. Actualiza los VIB esx-base, esx-tboot, vsan y vsanhealth (2151061). Para obtener más información sobre los detalles del parche, consulte [Parches de seguridad del SO VMware vCenter Server Appliance Photon](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}.

**Nota**: Las instancias existentes (de releases V1.9 y anteriores) no se pueden actualizar a las versiones de componentes de esta lista.

Para obtener más información sobre los componentes, consulte [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

### Soporte de clúster para instancias de Cloud Foundation

Ahora puede utilizar clústeres para gestionar servidores ESXi en instancias de Cloud Foundation desplegadas en V2.0 y releases posteriores para mejorar la gestión y alta disponibilidad de los recursos. Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **SDDC-Cluster** de forma predeterminada.

Puede ver los detalles del clúster o añadir hasta un total de cinco clústeres a una instancia en el separador **Infraestructura** de la página de detalles de la instancia. Cuando amplíe o reduzca la capacidad de una instancia, puede seleccionar el clúster al que se van a añadir los servidores ESXi o del que se van a eliminar los servidores ESXi. Para obtener más información, consulte [Adición y visualización de clústeres para instancias de Cloud Foundation](../sddc/sd_addingviewingclusters.html).

### Soporte de almacenamiento vSAN personalizado para instancias de Cloud Foundation

Ahora puede personalizar la configuración del almacenamiento vSAN seleccionando el número y el tamaño de las unidades de almacenamiento vSAN como parte del pedido de la instancia.

Para obtener más información, consulte los temas siguientes:

* [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)

### Opción de edición de licencia de VMware vSAN para instancias de Cloud Foundation: Advanced o Enterprise

Ahora puede seleccionar la edición de la licencia de vSAN que desea durante el pedido de la instancia de Cloud Foundation. Puede adquirir la licencia como parte de su pedido o puede traer su propia licencia (BYOL). Para obtener más información, consulte [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html).

### Nuevas configuraciones estandarizadas de IBM Bare Metal Server para instancias de Cloud Foundation

Dispone de los siguientes valores de configuración de servidor nativo (Bare Metal Server):
* Pequeño (Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz / 128 GB de RAM / 12 discos)
* Grande (Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz / 512 GB de RAM / 12 discos)

**Nota**: El chasis tiene espacio para 12 discos. No todas las ranuras están rellenadas. La configuración **Pequeño** proporciona dos unidades de 1,9 TB Micron 5100 MAX y la configuración **Grande** proporciona cuatro unidades de 3,8 TB Micron 5100 PRO.

Para obtener más información, consulte los temas siguientes:
* [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)

## Actualizaciones de instancias de VMware vCenter Server

El release actual aplica las siguientes actualizaciones de componentes para nuevos despliegues:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

**Nota:** Los pedidos personalizados de vCenter Server con o sin el componente VMware vSAN siempre incluyen un servidor con un chasis para 12 discos. Este servidor da lugar a un coste ligeramente superior para el {{site.data.keyword.baremetal_short}} para el caso de pedido no vSAN en el PDF de estimación de precios.

Para obtener más información sobre los componentes, consulte [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Soporte de la configuración de varios sitios para instancias de vCenter Server

Ahora puede desplegar una sola instancia de vCenter Server, además de instancias secundarias que se conectan a una instancia primaria. El modelo de configuración de varios sitios utiliza una topología de estrella ("hub and spoke") con un sitio primario y un máximo de siete sitios secundarios.

Para obtener más información, consulte [Configuración de varios sitios para instancias de vCenter Server](../vcenter/vc_multisite.html).

### Soporte de almacenamiento vSAN personalizado para instancias de vCenter Server

El almacenamiento vSAN ahora está disponible en las instancias de vCenter Server para las instancias primaria y secundarias. Solo está disponible cuando se selecciona una configuración personalizada por el usuario. Ahora puede seleccionar la edición de la licencia de vSAN (Advanced o Enterprise) que desea durante el pedido de la instancia de vCenter Server. Puede adquirir la licencia como parte de su pedido o puede traer su propia licencia (BYOL).

Para obtener más información, consulte [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html).

### Traiga su propia licencia (BYOL) para instancias de VMware vCenter Server

Ahora BYOL está disponible para instancias de vCenter Server. Utilice una o varias de sus propias licencias de vCenter Server, vSphere, vSAN y NSX VMware cuando solicite instancias de vCenter Server.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Solicitud de clústeres nuevos de vSphere](../vsphere/vs_orderinginstances.html)

## Actualizaciones para VMware vSphere on IBM Cloud

### Nuevos tipos de servidores nativos

Para el componente VMware vSAN, ahora dispone de los siguientes tipos de discos para {{site.data.keyword.baremetal_short}}:
* SSD SED de 960 GB
* SSD SED de 1,9 TB
* SSD SED de 3,8 TB

**Notas**:
* Las unidades SSD SED de 3,8 TB reciben soporte cuando estén disponibles a nivel general en un {{site.data.keyword.CloudDataCent_notm}}.
* Los pedidos con o sin el componente VMware vSAN siempre incluyen un servidor con un chasis para 12 discos. Este servidor da lugar a un coste ligeramente superior para el {{site.data.keyword.baremetal_short}} para el caso de pedido no vSAN en el PDF de estimación de precios.

Para obtener más información, consulte [Solicitud de clústeres nuevos de vSphere](../vsphere/vs_orderinginstances.html).

## Actualizaciones para NetApp ONTAP Select on IBM Cloud

### Nuevas opciones de servicio nativo

Ahora dispone de las siguientes opciones de configuración de servidor nativo:
* **Alto rendimiento (Medio)**: Licencia Premium / Dual Intel Xeon E5-2650 v4 (24 núcleos en total, 2,2 GHz) / 128 GB de RAM / Capacidad por nodo de 22 unidades SSD de 1,9 TB / Capacidad efectiva de un clúster de 4 nodos – 59 TB
* **Alto rendimiento (Grande)**: Licencia Premium / Dual Intel Xeon E5-2650 v4 (24 núcleos en total, 2,2 GHz) / 128 GB de RAM / Capacidad por nodo de 22 unidades SSD de 3,8 TB / Capacidad efectiva de un clúster de 4 nodos – 118 TB
* **Alta capacidad** – Licencia Estándar / Dual Intel Xeon E5-2650 v4 (24 núcleos en total, 2,2 GHz) / 64 GB de RAM / Capacidad por nodo de diez unidades SATA de 4 TB / Capacidad efectiva de un clúster de 4 nodos – 60 TB

**Nota:** Las unidades SSD de 3,8 TB reciben soporte cuando estén disponibles a un nivel general en un {{site.data.keyword.CloudDataCent_notm}}.

Para obtener más información, consulte los temas siguientes:
* [Visión general de NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Solicitud de instancias de NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Documentación nueva y actualizada

Los usuarios de VMware Cloud Foundation pueden seguir instrucciones paso a paso junto con la plataforma NSX VMware en {{site.data.keyword.cloud_notm}} para permitir que las máquinas virtuales se comuniquen entre sí y en internet. Para obtener más información, consulte [Configuración de NSX para las máquinas virtuales de carga de trabajo en VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Actualizaciones y mejoras de la interfaz de usuario

* El número máximo de servidores ESXi que se pueden añadir a un clúster se ha actualizado a 32 servidores. El número máximo de clústeres sigue siendo cinco.
* En la página **Instancias desplegadas**, la columna **ESXi servers** de las tablas de resumen de instancia se ha sustituido por la columna **Versión**, en la que encontrará la versión del release en el que se han desplegado las instancias o al cual se han actualizado.
* La versión de SDDC Manager para instancias de Cloud Foundation ahora está disponible en la página de detalles de la instancia.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
