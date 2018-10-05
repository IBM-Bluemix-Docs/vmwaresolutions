---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# Ampliación y reducción de la capacidad para instancias de Cloud Foundation

Puede ampliar o reducir la capacidad de la instancia de VMware Cloud Foundation según sus necesidades empresariales añadiendo o eliminando servidores ESXi.

Una instancia de Cloud Foundation puede tener un máximo de cinco clústeres, uno de los cuales es el predeterminado. Cada clúster inicial puede tener un máximo de 51 servidores ESXi y más clústeres pueden tener hasta 59.

## Adición de servidores ESXi a instancias de Cloud Foundation

### Antes de añadir servidores ESXi

* No añada servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de VMware vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_full}}.
* La plataforma base que ha solicitado tiene 4 servidores ESXi de forma predeterminada. Puede ampliar la plataforma hasta un máximo de 32 servidores ESXi. Sin embargo, el número de {{site.data.keyword.baremetal_short}} que puede añadir simultáneamente funciona del siguiente modo:
   * Para la configuración de tipo **Pequeño** y **Grande**, puede añadir entre 1 y 10 servidores ESXi simultáneamente.
   * Para la configuración de tipo **Personalizado**, puede añadir entre 1 y 20 servidores ESXi simultáneamente.

## Procedimiento para añadir servidores ESXi

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de Cloud Foundation**, pulse la instancia para la que desea ampliar la capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir servidores ESXi.
5. En la sección **Servidores ESXi**, pulse **Añadir**.
6. En la ventana **Añadir servidor**, escriba el número de servidores que desea añadir, revise el coste estimado y pulse **Añadir**.

### Resultados después de añadir servidores ESXi

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar cambios adicionales en la instancia.
2. Se le notificará mediante correo electrónico cuando se hayan añadido servidores ESXi.
3. Si no ve que los nuevos servidores ESXi se han añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

## Eliminación de servidores ESXi de instancias de Cloud Foundation

### Antes de eliminar los servidores ESXi

* No elimine servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de VMware vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}.
* La plataforma base que ha solicitado tiene 4 servidores ESXi de forma predeterminada. Puede eliminar los servidores ESXi que ha añadido. No puede eliminar los servidores ESXi predeterminados.
* Antes de eliminar servidores ESXi con el servicio de F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalado, debe migrar las máquinas virtuales de F5 BIG-IP y FortiGate a un servidor ESXi distinto al que está alojando las máquinas virtuales.
* Antes de eliminar servidores ESXi con el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} instalado, asegúrese de que no haya operaciones de copia de seguridad o restauración activas. Las operaciones activas, ya hayan fallado o estén en curso, pueden impedir que se eliminen los servidores ESXi.

## Procedimiento para eliminar servidores ESXi

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de Cloud Foundation**, pulse la instancia para la que desea to contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster desde el que desea eliminar los servidores ESXi.
6. En la sección **Servidores ESXi**, seleccione los servidores que desea eliminar y pulse **Eliminar**.

### Resultados después de eliminar servidores ESXi

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará mediante correo electrónico cuando se hayan eliminado servidores ESXi.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo los servidores ESXi al final del ciclo de facturación de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   **Atención**: se le facturará por los servidores ESXi eliminados hasta el final del ciclo de facturación de {{site.data.keyword.cloud_notm}}.

### Enlaces relacionados

* [Lista de materiales de Cloud Foundation](sd_bom.html)
* [Requisitos y planificación de instancias de Cloud Foundation](sd_planning.html)
* [Adición, visualización y supresión de clústeres para instancias de Cloud Foundation](sd_addingviewingclusters.html)
* [Colocación de un host en modalidad de mantenimiento](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Soporte del procesador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
