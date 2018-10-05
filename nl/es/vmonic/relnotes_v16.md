---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# Notas del release para V1.6

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Actualizaciones de instancias de VMware Cloud Foundation

Los siguientes componentes son nuevos o se han actualizado:

*  SDDC Manager 2.2.1
*  Componentes de gestión de IBM V1.6
*  Nuevas especificaciones de hardware: **Pequeño** o **Estándar**, dependiendo de sus requisitos.
*  Nuevos centros de datos disponibles para el despliegue: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seúl**, **SNG01 - Singapur** y **SYD04 - Sídney**.

Para la lista completa de componentes, consulte [Visión general de VMware Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Actualizaciones de instancias de VMware vCenter Server

### Mejoras de hardware para instancias de vCenter Server

A partir del release V1.6, dispone de varias mejoras para sus instancias de vCenter Server.

*  Implementación completa de la especificación V2.0 para la oferta vCenter Server. Para obtener más información, consulte la [Arquitectura de la solución VMware vCenter Server on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0).
*  Nuevas especificaciones de hardware: **Pequeño**, **Medio** o **Grande**, dependiendo de sus requisitos.
*  Nuevos centros de datos disponibles para el despliegue: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seúl**, **SNG01 - Singapur** y **SYD04 - Sídney**.
*  Al menos dos servidores ESXi en el pedido de la instancia, con VMware vSphere DRS (Distributed Resource Scheduler) y VMware HA (alta disponibilidad) habilitados de forma predeterminada.
*  Se pueden añadir un máximo de siete comparticiones de archivos NFS al solicitar instancias. Los componentes de gestión (vCenter, PSC, NSX Manager y controladores, CloudDriver) ahora se ejecuta en una compartición de archivos NFS para alta disponibilidad.
*  Despliegue y configuración automáticos de VMware NSX Edge Services Gateway gestionada por el cliente.

Debido a estos cambios, no puede utilizar (ni actualizar) las instancias existentes de vCenter Server tal cual en el release actual. Las instancias de vCenter Server de releases previos a V1.6 siguen estando visibles en la consola de {{site.data.keyword.vmwaresolutions_short}} en modalidad de solo vista. Estas instancias están marcadas en la interfaz de usuario como **En desuso** con un icono con un símbolo de aviso.

Dispone de las siguientes acciones en las instancias de vCenter Server anteriores a V1.6:

*  Ver la información en la página de detalles de la instancia. La información que se muestra en las propiedades de la instancia refleja los datos en la fecha del release V1.6 y ya no se renueva.
*  Abrir el cliente web de VMware vSphere y utilizar la instancia en vCenter.
*  Suprimir la instancia.

Las demás acciones ya no están disponibles en instancias anteriores a V1.6.

### Mejoras en el sistema de redes para instancias de vCenter Server

*  Se solicita una subred pública con 16 direcciones IP en la VLAN pública en su nombre para permitir el acceso a Internet de las VM (máquinas virtuales).
*  Se solicita una subred privada con 64 direcciones IP en la VLAN privada en su nombre para permitir el acceso a la red interna de SoftLayer® de las máquinas virtuales.
*  Se despliegan controladores NSX con reglas anti afinidad y se ejecutan en distintos servidores ESXi en una configuración de despliegue de 3 nodos.
*  Nueva VMware NSX Edge Services Gateway para que la utilice el cliente.

   Ahora se despliega una NSX Edge Services Gateway (ESG) adicional como parte de las nuevas instancias de vCenter Server que se solicitan.

   Esta ESG se proporciona para que se utilice con sus propias VM para las comunicaciones entre las subredes privadas y públicas que se solicitan en su nombre e incluye dos interfaces: una interfaz está conectada a las VXLAN virtualizadas asociadas con las VM y la otra está conectada a la VLAN pública. Además, se configuran los siguientes valores:
   *  Regla de cortafuegos para permitir todo el tráfico de salida procedente del rango de direcciones IP de la subred privada.
   *  Una regla SNAT (conversión de direcciones de red de origen) (inhabilitada de forma predeterminada) para convertir todas las direcciones IP de la subred privada en una dirección IP única en la subred pública.
   * Se configura VMware HA (alta disponibilidad) para utilizar un nuevo grupo de puertos que se comparte entre la ESG de gestión y la ESG gestionada por el cliente.

   Esta ESG se despliega para todos los tipos de hardware de la instancia y los clientes pueden modificar la configuración. Para obtener más información, consulte los temas siguientes:
   *  [Configuración de la red para que utilice NSX Edge Services Gateway gestionada por el cliente con sus máquinas virtuales](../vcenter/vc_esg_config.html)
   *  [Documentación de VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Mejoras en la usabilidad

Se han realizado mejoras en la interfaz de usuario:

*  La navegación principal de la consola se ha mejorado significativamente con la incorporación del panel de navegación izquierdo con acceso a todas las áreas de la interfaz de usuario. Puede solicitar rápidamente una nueva instancia, ver las instancias desplegadas, revisar las notificaciones del sistema, cambiar valores y acceder a la documentación en línea.
*  La nueva página **Cómo comenzar**, a la que se accede desde el panel de navegación izquierdo, le proporciona suficientes detalles directamente en la consola para ayudarle a tomar una decisión informada sobre los componentes de la instancia que va a solicitar. En la página **Cómo comenzar** también se le guía paso a paso por el proceso de solicitar una instancia, empezando por el cumplimiento de los requisitos previos para solicitar una instancia, como las cuentas de usuario necesarias, y terminando por la realización de un pedido.
*  Los detalles de resumen de las instancias de Cloud Foundation y de las instancias de vCenter Server se han consolidado en una sola página, a la que se accede desde el menú **Instancias desplegadas** del panel de navegación izquierdo. Desde esta página, puede seleccionar el separador adecuado para filtrar instancias de Cloud Foundation o instancias de vCenter Server.
* Si tiene el servicio de recuperación tras desastre de Zerto que está instalado en la instancia, puede acceder a la consola de Zerto desde la página de detalles del servicio directamente con una sola pulsación. Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html) y [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html).
