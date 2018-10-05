---

copyright:

  years:  2016, 2018

lastupdated: "2016-12-12"

---

# Notas del release para V1.2

Este release incluye nuevas características, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Actualizaciones de componentes

La nueva versión de VMware ESXi es vSphere 6.0 u2 p03, actualizada desde ESXi 6.0 u2 en el release anterior.

## Asociación de cuentas de IBMid y de Bluemix

{{site.data.keyword.vmwaresolutions_full}} se proporciona como una solución de infraestructura en el catálogo de IBM Bluemix®. Debe asociar la cuenta de **IBMid** con una cuenta de Bluemix para utilizar la cuenta de **IBMid** para iniciar sesión en la consola de {{site.data.keyword.vmwaresolutions_short}}.

Para obtener más información, consulte los temas siguientes:
* [Iniciación](../index.html)
* [Resolución de problemas de acceso a Bluemix](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html){:new_window}

## Recuperación tras desastre de Zerto

Puede solicitar tanto instancias de VMware Cloud Foundation como instancias de VMware vCenter Server con la recuperación tras desastre de Zerto incluida al solicitar la instancia. También puede añadir la recuperación tras desastre de Zerto a las instancias existentes de Cloud Foundation y de vCenter Server en la página de detalles de la instancia.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Visualización de instancias de Cloud Foundation](../sddc/sd_viewinginstances.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Visualización de instancias de vCenter Server](../vcenter/vc_viewinginstances.html)
* [Recuperación tras desastre de Zerto](../services/addingzertodr.html)

## Información sobre precios

Ahora puede ver y revisar el coste estimado de la instancia solicitada antes de decidir si realiza el pedido. Después de seleccionar los componentes al solicitar instancia, se muestra el coste total y los precios detallados de todos los componentes en la página **Resumen**.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)

## Mejoras en el proceso de solicitud de instancias

El proceso de pedido de una instancia se ha mejorado significativamente con las siguientes mejoras:
* Tanto para instancias de Cloud Foundation como para instancias de vCenter Server, se realizan nuevas comprobaciones de validación para garantizar que la cuenta de usuario de SoftLayer® que se utiliza tiene los permisos de usuario adecuados, que la expansión de VLAN está habilitada y que se ha suministrado la clave de API correcta. Si no se cumple algún requisito, el usuario recibe instrucciones en la interfaz de usuario para solucionar el problema.
*  Para instancias de vCenter Server, el orden en que se seleccionan los componentes de la instancia se ha optimizado para que solo se visualicen los centros de datos que tienen disponibles el hardware y los servidores ESXi que necesita. Este cambio reduce la posibilidad de errores futuros.

Para obtener más información, consulte los temas siguientes:
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)

## Notificaciones adicionales por correo electrónico

Ahora el usuario recibe una notificación por correo electrónico cuando se añaden nuevos servidores ESXi a las instancias y cuando se eliminan servidores ESXi existentes. Además, se notifica al usuario por correo electrónico cuando se suprime una instancia. Los valores de notificación están habilitados de forma predeterminada. Según sus preferencias, puede establecer qué notificaciones desea recibir en la página **Configuración**.

Para obtener más información, consulte [Cuenta de usuario y valores](useraccount.html).
