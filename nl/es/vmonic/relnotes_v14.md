---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# Notas del release para V1.4

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Actualizaciones de componentes para instancias de Cloud Foundation

Los siguientes componentes son nuevos o se han actualizado:

* VC y PSC (vCenter y Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* Se solicita una nueva VSI (instancia de servidor virtual) de Windows para los servicios Microsoft Active Directory (AD) y Sistema de nombres de dominio (DNS), necesarios para el soporte de la configuración de varios sitios en este release. Esta VSI tiene las siguientes especificaciones: Windows 2012 R2 (8 GB de RAM / 2 núcleos de CPU / 100 GB de disco / enlaces ascendentes duales privados de 1 Gbps).

Para obtener más información, consulte [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Actualizaciones de componentes para instancias de vCenter Server

Los siguientes componentes son nuevos o se han actualizado:

### VMware NSX for vSphere 6.2.4

Ahora VMware NSX for vSphere 6.2.4 se instala de forma predeterminada en todas las instancias de vCenter Server (antes solo en instancias de Cloud Foundation).

Como parte de la instalación de NSX, NSX Manager se instala y se obtiene una licencia del mismo en todas las instancias nuevas que se despliegan. Además, se crea un NSX Edge para la gestión de la instancia, aunque puede crear sus propios componentes de NSX Edge si es necesario. Para obtener más información sobre NSX Edge, consulte la sección _VMware NSX Edge_ en esta página.

**Nota**: el controlador NSX no se instala en las instancias de vCenter Server (del modo en que se instala en las instancias de Cloud Foundation). Si utiliza VXLAN o direccionadores lógicos distribuidos para sus instancias de vCenter Server, debe instalar el controlador NSX usted mismo.

Para obtener más información sobre las mejoras incorporadas en VMware NSX para vSphere 6.2.4, sus requisitos y problemas conocidos, consulte las [Notas del release de NSX for vSphere 6.2.4](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### VMware NSX Edge

Ahora NSX Edge se incluye como parte de las nuevas instancias de vCenter Server que se solicitan. NSX Edge ofrece seguridad de extremo a extremo de la red y servicios de pasarela para aislar una red virtualizada.

Durante el despliegue de la instancia, IBM despliega Management VMware NSX Edge Services Gateway (ESG). Las máquinas virtuales de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización. Esta ESG se despliega para incluir dos interfaces: una interfaz está conectada a la VLAN privada de {{site.data.keyword.cloud_notm}}, y la otra está conectada a la VLAN pública de {{site.data.keyword.cloud_notm}}.

Para garantizar la seguridad, se imponen reglas de cortafuegos que solo permiten las comunicaciones HTTPS de salida iniciadas por las máquinas virtuales de gestión. Esta ESG se despliega en una configuración de tipo Grande y solo el equipo de soporte de IBM puede modificar la configuración. Para obtener más información, consulte los temas siguientes:

* [Especificaciones técnicas de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [¿Representa NSX Edge de servicios de gestión un riesgo para la seguridad?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentación de VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### Licencia de NSX

Se solicita una licencia de VMware NSX Base para Service Providers Edition por nodo.

### Nuevo bloque de direcciones de subred

Se solicita un bloque de subred de 16 direcciones portátiles públicas por nodo.

## Actualizaciones del modelo de cargo por servicio

El modelo de cargo por servicio se ha simplificado:

* Para las instancias de Cloud Foundation, se han eliminado las cuotas del _servicio de instancias de VMware Cloud Foundation_, del _servicio de almacenamiento de VMware Cloud Foundation_ y de _VMware Solutions Hypervisor_.
* Para las instancias de vCenter Server, se han eliminado las cuotas de la _instancia de VMware vCenter Server_ y de _VMware Solutions Hypervisor_.
* Para ambos tipos de instancias, se ha incorporado una nueva cuota de _soporte y servicios_, que es una cuota mensual que se aplica a cada nodo.

## Actualizaciones de la topología de la red de instancias

Este release incluye las siguientes mejoras en la topología de las instancias:

* Tanto para instancias de Cloud Foundation como para instancias de vCenter Server: configuración optimizada del sistema de red, es decir, solo la red pública primaria y las direcciones IP privadas asignadas por SoftLayer® se conectan a los servidores ESXi. Las direcciones privadas portátiles ya no se despliegan para el tráfico de gestión.
* Solo para instancias de Cloud Foundation: Windows AD SSO (inicio de sesión único de Active Directory) y servidor del Sistema de nombres de dominio (DNS)

**Nota**: debido a estos cambios, no puede utilizar las instancias existentes previas a V1.4 en el release actual. Para reutilizar la configuración de las instancias existentes, debe actualizarlas a la versión actual. Para obtener más información, consulte [Actualización de instancias de versiones anteriores a V1.4](movinginstances.html).

## Soporte de la configuración de varios sitios para instancias de Cloud Foundation

Ahora puede desplegar una instancia sola instancia de Cloud Foundation, al igual que en releases anteriores o, además, puede desplegar instancias secundarias que se conectan a una instancia primaria. El modelo de configuración de varios sitios utiliza una topología de estrella ("hub and spoke") con un sitio primario y un máximo de siete sitios secundarios.

Para obtener más información, consulte [Configuración de varios sitios para instancias de Cloud Foundation](../sddc/sd_multisite.html).

## Mejoras en el despliegue de la recuperación tras desastre de Zerto

* Para instancias de Cloud Foundation, el despliegue de la recuperación tras desastre de Zerto es automático en lugar de gestionarse mediante una incidencia de soporte. Todos los componentes Zerto, como por ejemplo una subred privada portátil, una VSI (instancia de servicio virtual) de Windows y los cargos de licencia de Zerto, aparecen listados en el coste estimado, de modo que los puede revisar antes de realizar el pedido.
* Para instancias de vCenter Server, el despliegue de la recuperación tras desastre de Zerto se realiza mediante una incidencia de soporte, como en el release anterior. Sin embargo, ya no se necesitan NSX Edge ni la subred portátil pública, ya que ahora están incluidos en el despliegue básico. Los cargos correspondientes a una subred privada portátil, a una VSI (instancia de servicio virtual) de Windows y a la licencia de Zerto se siguen aplicando.

Para obtener más información, consulte [Recuperación tras desastre de Zerto](../services/addingzertodr.html).

## Proceso de pedido de una instancia

El proceso de pedido de una instancia se ha simplificado significativamente:

* Tanto para instancias de Cloud Foundation como para instancias de vCenter Server, ya no se muestra página de credenciales de SoftLayer durante el proceso de pedido. Se utilizan de forma predeterminada las credenciales de SoftLayer definidas en la página de valores y se solicita al usuario que las actualice solo si no cumplen los requisitos.
* Además, para instancias de vCenter Server, solo está disponible la opción **Grande** para el tipo de **Hardware** y el valor **10 Gbps Dual** para la opción **Velocidad de puerto de enlace ascendente**, lo que reduce el número de valores que se deben especificar cuando se realiza el pedido.

Para obtener más información, consulte los temas siguientes:

* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)

## Gestión de instancias

Se han realizado mejoras y se han incorporado nuevas características al proceso de gestión de instancias:

* Para instancias de Cloud Foundation, puede ver el nombre de usuario y las contraseñas de distintos componentes de la instancia en la página de detalles de la instancia. Para obtener más información, consulte [Visualización de instancias de Cloud Foundation](../sddc/sd_viewinginstances.html).
* Para instancias de vCenter Server, ahora puede instalar actualizaciones de software y parches para componentes de IBM directamente desde la consola. Para obtener más información, consulte [Aplicación de actualizaciones y de parches a instancias de vCenter Server](../vcenter/vc_applyingupdates.html).

## Notificaciones de la consola

Puede configurar notificaciones de la consola en la página **Configuración**. De forma predeterminada, el valor está habilitado, lo que significa que recibe una notificación en la consola para todos los sucesos. También puede inhabilitar las notificaciones de la consola en la página **Configuración**.

Para obtener más información, consulte los temas siguientes:

* [Cuentas de usuario y valores](useraccount.html)
* [Notificaciones](notifications.html)
