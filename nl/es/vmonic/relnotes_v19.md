---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# Notas del release para V1.9

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud

Este release presenta la oferta de VMware vSphere on {{site.data.keyword.cloud_notm}}. Esta oferta le permite crear su propio entorno virtual de VMware alojado por IBM personalizando y solicitando los recursos de cálculo, almacenamiento y de red compatibles con VMware en función de los componentes de VMware seleccionados. Aunque vSphere on {{site.data.keyword.cloud_notm}} no automatiza la instalación, la configuración ni la apertura de los componentes de VMware opcionales, tiene la máxima flexibilidad para diseñar y planificar la arquitectura del entorno que mejor se adapte a sus necesidades empresariales. Empiece creando un nuevo clúster de vSphere de servidores ESXi o escalando un clúster vSphere existente en un {{site.data.keyword.CloudDataCent_notm}}.

Para obtener más información, consulte los temas siguientes:
* [Solicitud de clústeres nuevos de vSphere](../vsphere/vs_orderinginstances.html)
* [Escalado de clústeres existentes de vSphere](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

Este release incorpora la oferta NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}, un dispositivo virtual para software definido por almacenamiento que implementa NetApp ONTAP Select como un servicio en un {{site.data.keyword.baremetal_short}} dedicado de IBM Cloud. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} se ofrece en configuraciones de alto rendimiento (todo SSD) y de alta capacidad (todo SATA).
Esta oferta aloja el almacenamiento en la infraestructura dedicada y proporciona funciones de NetApp, como deduplicación, compresión y cifrado de datos en reposo. Suministre recursos de almacenamiento con agilidad y flexibilidad mientras protege los datos utilizando funciones avanzadas de gestión de datos. Por ejemplo, utilice las copias rápidas y eficientes de NetApp Snapshot®, las copias de FlexClone® y la réplica SnapMirror®.

Para obtener más información, consulte los temas siguientes:
* [Visión general de NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Solicitud de instancias de NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Servicio F5 on IBM Cloud

El servicio F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} ya está disponible tanto para instancias de VMware Cloud Foundation como para instancias de VMware vCenter Server. Este servicio proporciona servicios de equilibrio inteligente de carga L4-L7 y de gestión del tráfico a escala local y global, potentes funciones de protección de red y de cortafuegos de aplicaciones web y acceso seguro y federado a las aplicaciones.
Solicite instancias con el servicio F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} incluido al solicitar la instancia, o añada este servicio a las instancias existentes más adelante desde el separador **Servicios** de la página de detalles de las propiedades de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}. Dependiendo de sus necesidades, puede seleccionar una de las tres opciones de licencia para VE de BIG-IP.

Para obtener más información, consulte los temas siguientes:
* [Consideraciones sobre F5 on {{site.data.keyword.cloud_notm}}](../services/f5_considerations.html)
* [Gestión de F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html)

## Servicios gestionados desde IBM-Integrated Managed Infrastructure

Los servicios gestionados de IBM-Integrated Managed Infrastructure (IMI) ya están disponibles para instancias de VMware Cloud Foundation. IMI puede simplificar la gestión de la infraestructura virtual de VMware con servicios de gestión modulares y puede actuar como un único proveedor de confianza para reducir la complejidad de la supervisión y la gestión de infraestructuras de IT virtuales. Descargue determinadas operaciones diarias a IMI, como la de supervisión, para poder centrarse en iniciativas de más valor.

Puede solicitar una consulta y una estimación en cualquier momento desde la página **Cómo empezar**.
Para obtener más información, consulte [Solicitud de servicios gestionados de IMI](../services/managing_imi.html#requesting-managed-services-from-imi).

## Restricciones de los nombres de instancia para instancias de vCenter Server y de NetApp ONTAP Select

Los nombres de instancia especificados en {{site.data.keyword.vmwaresolutions_short}} al solicitar instancias no pueden contener caracteres especiales (como el carácter guión). Solo se permiten caracteres alfanuméricos. Esta restricción no se aplica a las instancias de Cloud Foundation.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Solicitud de instancias de NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Actualizaciones de instancias de VMware Cloud Foundation

### Personalice la CPU y la memoria de su instancia

Dispone de una opción de servidor personalizado por el usuario junto con las opciones integradas y probadas Pequeño y Estándar. Para ajustar mejor la proporción entre CPU y RAM de sus cargas de trabajo al hardware compatible con VMware, ahora puede seleccionar de forma independiente el número total de núcleos del servidor de CPU dual y la cantidad de RAM. El almacenamiento local no se puede personalizar.

Para obtener más información, consulte [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html).

## Actualizaciones de instancias de VMware vCenter Server

### Soporte de clústeres entre centros de datos

Para mejorar la capacidad de escalado del entorno VMware alojado, ahora puede crear un nuevo clúster en otro pod de la infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) o en un {{site.data.keyword.CloudDataCent_notm}} distinto del correspondiente al clúster inicial desplegado en la instancia.

Para obtener más información, consulte [Adición y visualización de clústeres para instancias vCenter Server](../vcenter/vc_addingviewingclusters.html).

### Cambio de componentes

Esta versión elimina el impacto en las operaciones de la consola de {{site.data.keyword.vmwaresolutions_short}} cuando el administrador de inicio de sesión único cambia ciertos recursos de vCenter Server desde la herramienta nativa de VMware. Por ejemplo, ahora puede modificar los nombres del centro de datos virtual de VMware, del clúster, de los conmutadores, de los grupos de puertos y de los almacenes de datos desde el cliente web de VMware vSphere para personalizar los despliegues y adaptarlos a los convenios de denominación de la empresa o personales sin detener las operaciones desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

Para obtener más información, consulte [Efectos de cambiar los componentes de instancias de vCenter Server](../vcenter/vcenter_chg_impact.html).

### Tamaños de RAM adicionales

Cuando solicite instancias de vCenter Server o añada clústeres a instancias de servidor vCenter, ahora dispone de más tamaños de RAM entre los que escoger para ayudarle a ajustar la proporción entre CPU y RAM de la carga de trabajo al hardware. Dispone de las siguientes opciones en la opción de configuración **Personalizado por el usuario** cuando solicite un servidor desde la consola de {{site.data.keyword.vmwaresolutions_short}}: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB.

Para obtener más información, consulte [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html).

### Actualización de la versión Network File System

Network File System (NFS) Versión 4.1 ya no está disponible como valor de almacenamiento en la interfaz de usuario. Todas las instancias de vCenter Server se despliegan con NFS V3. Aunque NFS V3 es una versión del protocolo más antigua, permite características mejoradas en entornos VMware con el soporte de VMware Storage Distributed Resource Scheduler (SDRS) y Storage I/O Control (SIOC).

Para obtener más información, consulte [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html).

### Nombre del dominio del servicio de nombres de dominio de un solo sitio

Ahora puede especificar el nombre del dominio del servidor de nombres de dominio (DNS) para una instancia de vCenter Server durante un pedido. Se despliega y se puede consultar una VSI (instancia de servidor virtual) de Microsoft Windows Server que funciona como DNS para la instancia en la que se han registrado los hosts y las máquinas virtuales. Microsoft Active Directory (AD) también se configura en la VSI Microsoft Windows y el nombre del dominio DNS es la raíz del grupo del dominio de AD. Esta VSI Microsoft Windows solo está disponible en V1.9 y posteriores.

Para obtener más información, consulte los temas siguientes:
* [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Visualización de instancias de vCenter Server](../vcenter/vc_viewinginstances.html)

## Requisitos para la instalación automática de actualizaciones de Windows Server

Microsoft Active Directory (AD) / Domain Name Server (DNS) se configura automáticamente de modo que solo descargue las actualizaciones. No instala ni rearranca automáticamente estas actualizaciones. El usuario debe instalar manualmente las actualizaciones y reiniciar en un momento planificado que evite cualquier interrupción de la configuración actual del servidor Active Directory y de otros trabajos de copia de seguridad. Para aplicar las actualizaciones de Windows, instale las actualizaciones manualmente.

## Documentación nueva y actualizada

* Obtenga información sobre cómo proteger sus instancias de Cloud Foundation privadas de varios sitios mientras amplía sus aplicaciones VMware para que utilicen servicios públicos de {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Conexión segura de sus cargas de trabajo privadas de VMware en {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* Se proporciona más documentación para configurar cortafuegos que permitan toda la comunicación de protocolo entre las máquinas virtuales IBM CloudDriver y SDDC Manager. Para obtener más información, consulte [Componentes y consideraciones sobre Fortinet on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html).
