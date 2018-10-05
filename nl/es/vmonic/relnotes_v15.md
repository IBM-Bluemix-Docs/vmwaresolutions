---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-30"

---

# Notas del release para V1.5

Este release incluye nuevas características, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Requisitos de las cuentas de SoftLayer VRF frente a las clásicas

Para cuentas de SoftLayer® clásicas, la expansión de VLAN es un valor que se puede habilitar a nivel de cuenta. {{site.data.keyword.vmwaresolutions_short}} requiere que la expansión de VLAN esté habilitada.

Para las cuentas de SoftLayer VRF (direccionamiento y reenvío virtual), el equivalente de la expansión de VLAN es un valor permanente que no se puede cambiar. No se requiere configuración de usuario para las cuentas VRF.

Antes de realizar el pedido de una instancia, asegúrese de que su cuenta de SoftLayer sea una cuenta VRF o una cuenta clásica (no VRF) con la expansión de VLAN habilitada. De lo contrario, el pedido puede fallar.

Para confirmar si su cuenta de SoftLayer es una cuenta VRF, verifíquelo con el equipo de soporte de IBM Bluemix. Para las cuentas clásicas, debe habilitar la expansión de VLAN siguiendo las instrucciones de [Habilitación o inhabilitación de la expansión de VLAN](../../../infrastructure/vlans/vlan-spanning.html){:new_window}.

## Actualizaciones del modelo de cargo por servicio

Para las instancias de Cloud Foundation, se ha incorporado una nueva licencia _SDDC Manager_, que supone una cuota mensual que se aplica a cada nodo. Para obtener más información, consulte [Especificaciones técnicas para instancias de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Mejoras en la usabilidad

Se han realizado mejoras en la interfaz de usuario:

* La disponibilidad de varios {{site.data.keyword.CloudDataCents_notm}} y si tienen suficiente inventario para satisfacer el pedido se indica claramente en la interfaz de usuario. Utilice estos detalles para tomar una decisión informada sobre el {{site.data.keyword.CloudDataCent_notm}} para seleccionar cuándo se solicita una instancia. Para obtener más información, consulte [Requisitos y planificación de instancias de Cloud Foundation](../sddc/sd_planning.html) y [Requisitos y planificación de instancias de vCenter Server](../vcenter/vc_planning.html).
* Para instancias de Cloud Foundation, se muestra automáticamente información como el nombre de instancia, el nombre del dominio y del subdominio y la ubicación del centro de datos en formato gráfico mientras se especifica la información necesaria en los campos de entrada. Para obtener más información, consulte [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html).
