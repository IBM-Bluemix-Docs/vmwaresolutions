---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Notas del release para V2.6

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades relacionadas con Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obtener más información, consulte [Soluciones para las vulnerabilidades Spectre y Meltdown](../vmonic/trbl_fix_spectre.html).

## Opción de Alto rendimiento con Intel Optane

Este release proporciona la opción de añadir memoria caché de alto rendimiento para el almacenamiento vSAN al solicitar una nueva instancia o al añadir un nuevo clúster vSAN después del despliegue inicial.

Esta opción le permite aumentar el número de discos de capacidad de almacenamiento de ocho a un máximo de diez.

La opción Alto rendimiento con Intel Optane solo está disponible para configuraciones personalizadas con procesadores Dual Intel Xeon Gold 5120 y Dual Intel Xeon Gold 6140.

Para obtener más información, consulte el tema de ordenación adecuado para la instancia o el tipo de clúster.

## Habilitación de una red pública o privada

Ahora puede desplegar vCenter Server y vCenter Server con instancias del paquete híbrido (Hybridity), así como clústeres de VMware vSphere, con tarjetas de interfaz de red públicas y privadas (NIC) habilitadas o NIC habilitadas solo privadas. Esta opción también está disponible cuando se añade un nuevo clúster a la instancia de vCenter Server y vCenter Server con el paquete híbrido (Hybridity).

Algunos servicios adicionales necesitan NIC públicos y no están disponibles si selecciona habilitar una red solo privada.

Para obtener más información, consulte la sección _Valores de interfaz de red_ en los temas siguientes:

* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html#network-interface-settings)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_orderinginstance.html#network-interface-settings)
* [Solicitud de clústeres nuevos de vSphere](../vsphere/vs_orderinginstances.html#network-interface-settings)

## Supresión de servidores ESXi

Ahora puede suprimir cualquier servidor ESXi de la instancia de vCenter Server, vCenter Server con el paquete híbrido (Hybridity) o de Cloud Foundation si cumple con los requisitos mínimos para su instancia.

Para obtener más información sobre los requisitos del servidor ESXi, consulte los temas siguientes:

* [Ampliación y reducción de la capacidad para instancias de vCenter Server](../vcenter/vc_addingremovingservers.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservers.html)
* [Ampliación y reducción de la capacidad para instancias de Cloud Foundation](../sddc/sd_addingremovingservers.html)

## Actualizaciones de instancias de VMware vCenter Server

Este release se aplica a las siguientes actualizaciones y mejoras:

* vSphere ESXi 6.5 Actualización 2c
* vCenter Server Appliance 6.5 Actualización 2c
* Platform Services Controller 6.5 Actualización 2c
* NSX for vSphere 6.4.1

## Actualizaciones para VMware vCenter Server con el paquete híbrido (Hybridity)

### Eliminación del paquete híbrido (Hybridity) de una instancia de vCenter Server

Ahora puede eliminar la licencia del paquete híbrido (Hybridity) de la instancia de vCenter Server. Para ello, es necesario que sustituya las claves de licencia de alquiler de VMware NSX y VMware vSAN con las claves Traiga su propia licencia (BYOL) y que abra una incidencia de soporte para cancelar los cargos por las licencias de alquiler.

Para obtener más información, consulte [Eliminación del paquete híbrido (Hybridity) de una instancia de vCenter Server](../vcenter/vc_hybrid_deletingbundle.html).

### Disponibilidad de vCenter Server con el paquete híbrido (Hybridity)

Los Business Partners ahora pueden solicitar una instancia de vCenter Server con el paquete híbrido (Hybridity). Los Business Partners no pueden actualizar una instancia de vCenter Server existente a una instancia de vCenter Server con el paquete híbrido (Hybridity) y no pueden eliminar el paquete híbrido (Hybridity) de una instancia de vCenter Server con el paquete híbrido (Hybridity).

Para obtener más información, consulte los temas siguientes:

* [Visión general de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_overview.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_orderinginstance.html)

## Actualizaciones de instancias de VMware Cloud Foundation

Este release se aplica a las siguientes actualizaciones y mejoras:

* vSphere ESXi 6.5 Actualización 2c
* vCenter Server Appliance 6.5 Actualización 2c
* Platform Services Controller 6.5 Actualización 2c
* NSX for vSphere 6.4.1

## Actualizaciones de servicios complementarios

### HyTrust KeyControl on IBM Cloud

El servicio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} ahora está disponible para las instancias de VMware Cloud Foundation y las instancias de VMware vCenter Server que están ejecutando vSphere 6.5 y que se despliegan en o se actualizan a V2.5 y releases posteriores. El servicio simplifica la gestión de cargas de trabajo cifradas automatizando y simplificando el ciclo de vida de las claves de cifrado. El servicio puede gestionar fácilmente las claves de cifrado a escala utilizando el cifrado compatible con FIPS 140-2. Al utilizar este servicio, puede gestionar las claves de cifrado para todas las máquinas virtuales y almacenes de datos cifrados, y escalarlo para dar soporte a miles de cargas de trabajo cifradas en despliegues grandes.

Puede solicitar instancias con el servicio incluido al solicitar la instancia, o puede añadir este servicio a las instancias existentes más adelante.

Para obtener más información, consulte los temas siguientes:
* [Componentes y consideraciones para HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)
* [Gestión de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/managinghtkc.html)

### HyTrust CloudControl on IBM Cloud

El release actual instala HyTrust CloudControl 5.4 en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de HyTrust CloudControl 5.4, consulte [Conjunto de documentación en línea de HyTrust CloudControl v 5.4](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html).

### HyTrust DataControl on IBM Cloud

El release actual instala HyTrust DataControl 4.2 en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de HyTrust DataControl 4.2, consulte [Novedades de HyTrust DataControl 4.x](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm).

### Soporte de Veeam on IBM Cloud para vSphere ESXi V6.5 actualización 2c

A partir de V2.6, se suministran nuevas instancias y nuevos hosts utilizando el vSphere ESXi V6.5 Actualización 2c. Si utiliza Veeam Backup and Replication, Veeam le recomienda que actualice la instancia de Veeam on {{site.data.keyword.cloud_notm}} a V9.5u3a o posterior para garantizar la mejor compatibilidad con vSphere ESXi 6.5 Actualización 2c.

Se recomienda que las instancias existentes de Cloud Foundation que tengan Veeam on {{site.data.keyword.cloud_notm}} instalado también se actualicen a V9.5u3a o posterior.

Para obtener más información sobre Veeam on {{site.data.keyword.cloud_notm}}, consulte [Visión general de Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html).

### VMware HCX on IBM Cloud

El release actual instala VMware HCX 3.5.1 R106 en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de HCX 3.5.1 R106, consulte [Documentación de VMware NSX Hybrid Connect](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/index.html).

## Documentación nueva y actualizada

### Documentación de arquitectura de referencia
El documento de arquitectura de {{site.data.keyword.vmwaresolutions_short}} se actualiza para incluir consideraciones importantes para comprender las responsabilidades que tiene para gestionar y operar con la instancia de VMware.

Para obtener más información, consulte [Consideraciones posteriores al despliegue para la instancia de VMware](../archiref/solution/solution_considerations.md).

## Actualizaciones y mejoras de la interfaz de usuario

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
