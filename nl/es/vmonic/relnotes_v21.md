---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# Notas del release para V2.1

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades conocidas como Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obtener más información, consulte [Soluciones para las vulnerabilidades Spectre y Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware HCX on IBM Cloud

El servicio HCX on {{site.data.keyword.cloud_notm}} solo está disponible para las instancias de VMware Cloud Foundation y las instancias de VMware vCenter Server que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.1 y posteriores releases o que se han actualizado a estos. Este servicio permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) bidireccionales entre sus centros de datos locales y {{site.data.keyword.cloud_notm}} sin realizar ningún cambio. Al establecer un puente de capa 2, HCX utiliza la optimización, deduplicación, compresión y cifrado de WAN para migrar datos de forma más rápida y segura sobre un enlace directo o un túnel VPN. La migración masiva de máquinas virtuales es compatible con VMware vSphere 5.1 o superior. Si utiliza vSphere 6.0 o superior local, puede ejecutar vMotion de las máquinas virtuales en directo (encendidas) a un {{site.data.keyword.CloudDataCent_notm}}. No es necesario tener VMware NSX instalado en el centro de datos cuando se utiliza HCX.

Puede solicitar instancias de Cloud Foundation o de vCenter Server con el servicio HCX on {{site.data.keyword.cloud_notm}} incluido al solicitar la instancia, o puede añadir este servicio a las instancias existentes más adelante desde el separador **Servicios** de la página de detalles de la instancia.

Puede solicitar una instancia local de HCX local para la obtención de licencias y la activación de la instalación local de HCX.

Para obtener más información, consulte los temas siguientes:
* [Consideraciones sobre HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)
* [Gestión de HCX on {{site.data.keyword.cloud_notm}}](../services/managinghcx.html)
* [Consideraciones sobre instancias locales de HCX](../services/standalone_considerations.html)
* [Solicitud de instancias locales de HCX](../services/standalone_orderingserviceinstances.html)

## Modelo de licencia Traer su propia licencia más flexible para VMware Cloud Foundation y vCenter Server

Puede traer su propia licencia (BYOL) o adquirir licencias de suscripción proporcionadas por IBM cuando cree un nuevo clúster en instancias de VMware Cloud Foundation y de VMware vCenter Server V2.1 y posteriores. Estas opciones le permiten utilizar la clave de componente existente o bien alquilar la licencia de IBM. Antes de la V2.1, no podía adquirir licencias proporcionadas por IBM para un componente específico de VMware si utilizaba el sistema BYOL. En este momento, solo VMware vSphere y VMware vSAN están disponibles para licencias por clúster.

Además, cuando añada nodos a un clúster cuya licencia ha conseguido con su clave, la consola le solicita que especifique una nueva clave de licencia si el número de nodos supera la capacidad de la clave.

Para obtener más información, consulte los temas siguientes:

* [Adición y visualización de clústeres correspondientes a instancias de Cloud Foundation](../sddc/sd_addingviewingclusters.html)
* [Adición y visualización de clústeres correspondientes a instancias de vCenter Server](../vcenter/vc_addingviewingclusters.html)
* [Preguntas frecuentes sobre BYOL](../vmonic/faq_byol.html)

## Actualizaciones de componentes del servicio Zerto on IBM Cloud

Para el servicio Zerto on {{site.data.keyword.cloud_notm}} desplegado en instancias de Cloud Foundation y de vCenter Server de la V2.1 y posteriores, se suministra Zerto Virtual Replication 5.5u2. Ahora los dispositivos de réplica virtual (VRA) de Zerto se despliegan en el almacén de datos de gestión (que puede ser vSAN o Endurance) en lugar de en el almacén de datos local por motivos de rendimiento. Si tiene VRA existente, tenga en cuenta la posibilidad de migrar su almacenamiento al almacén de datos de gestión para mejorar su rendimiento.

Para obtener más información, consulte [Visión general de Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html).

## Actualizaciones de instancias de VMware vCenter Server

### Valores de configuración de MTU de red

Para V2.1 o releases posteriores, las nuevas instancias de vCenter Server se solicitan con el valor de conmutador virtual distribuido (DVS) público MTU 1500 (predeterminado). Para obtener más información, consulte _Valores de configuración de MTU de red_ en [Lista de materiales de vCenter Server](../vcenter/vc_bom.html).

### Aplicación automática de parches y actualizaciones de VMware ESXi a hosts

En las instancias de VMware vCenter Server de la V2.0 y anteriores, los parches no se aplicaban automáticamente a los hosts ESXi que se añadían a un clúster.

En las instancias de la V2.1 y posteriores, el sistema de automatización aplica los parches a los nuevos hosts ESXi, de modo que el nivel de parche coincide con el nivel de parche en el momento en el que se suministró la instancia inicial. El usuario es el responsable de aplicar manualmente los futuros parches y actualizaciones.
Cuando estén disponibles nuevos parches y actualizaciones de VMware en futuros releases, el sistema de automatización explora los hosts ESXi de las instancias existentes y le enviará por correo electrónico un recordatorio para que aplique manualmente los parches y actualizaciones más recientes.

Para obtener más información, consulte [Aplicación de actualizaciones a instancias de vCenter Server](../vcenter/vc_applyingupdates.html).

### Estimaciones de precios para actualizaciones de licencia de VMware NSX

Ahora puede ver una estimación del precio antes de realizar un pedido para actualizar a la edición VMware NSX Advanced o Enterprise. Los precios dependen del número de hosts ESXi de la instancia de vCenter Server. Esta adquisición solo cambia la clave de licencia de NSX y actualiza la edición Base de VMware NSX a la edición Advanced o Enterprise. La adquisición no actualiza la versión de software de NSX.

Para obtener más información, consulte [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Se ha aumentado el número máximo de servidores por clúster, 32

Para el clúster predeterminado de una instancia, puede desplegar o ampliar hasta 51 servidores. Para todos los siguientes clústeres de una instancia, puede desplegar o ampliar hasta 59 servidores. Para obtener más información, consulte [Adición y visualización de clústeres para instancias vCenter Server](../vcenter/vc_addingviewingclusters.html).

**Nota:** esta característica solo está disponible para instancias desplegadas en V2.1 y posteriores. Las instancias que se han actualizado a V2.1 desde releases anteriores a V2.1 no tienen esta opción.

### Opciones de configuración personalizadas por el usuario de servidores nativos de IBM Cloud

La configuración de servidores nativos personalizada por el usuario ahora ofrece Dual Intel Xeon Gold 6140 con 36 núcleos en total y 2,3 GHz.

Para obtener más información, consulte los temas siguientes:
* [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)

### Configuraciones de comparticiones de archivos NFS individuales

Ahora puede configurar comparticiones de archivos NFS de forma individual. Seleccione el tamaño de archivo y el nivel de rendimiento de cada compartición de archivos individual o seleccione el mismo tamaño de archivo y nivel de rendimiento para todas las comparticiones de archivos del pedido.

Para obtener más información, consulte los temas siguientes:
* [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Adición y visualización de clústeres correspondientes a instancias de vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Actualizaciones y mejoras de la interfaz de usuario

Se han realizado mejoras en la interfaz de usuario:

* La opción **Solicitar instancia** ya no está disponible en el panel de navegación de la izquierda. Pulse **Cómo comenzar** para seguir los pasos para solicitar una instancia.
* Se ha cambiado el nombre del campo **Prefijo de subdominio** de la página **Aspectos básicos** cuando se solicita una instancia por **Etiqueta de subdominio**.
* Además de ver la estimación del coste en la página **Resumen** cuando solicite una instancia primaria o secundaria de vCenter Server o de Cloud Foundation, ahora puede calcular una estimación de coste en cualquier página a medida que especifica los detalles del pedido de la instancia.
* Se añade un rastro de navegación a la página **Instancias desplegadas** como método de navegación alternativo, lo que reduce el número de pasos necesarios para llegar a las páginas padre.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.

## Documentación nueva y actualizada

Dispone de una nueva receta de developerWorks con instrucciones paso a paso sobre cómo conectar almacenamiento dedicado a despliegues existentes de {{site.data.keyword.vmwaresolutions_full}} que utiliza NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Pasos para conectar almacenamiento dedicado a VMware Solutions on IBM Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/).
