---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# Visión general de VMware vSphere on IBM Cloud

VMware vSphere on {{site.data.keyword.cloud}} es una plataforma de solicitud racional y optimizada para VMware. Con esta plataforma, puede crear su propio entorno de VMware alojado por IBM personalizando y solicitando el hardware compatible con VMware en función de los componentes de VMware seleccionados.

La consola de {{site.data.keyword.vmwaresolutions_short}} filtra el hardware automáticamente, en función de los componentes de VMware ha seleccionado. Por ejemplo, cuando se crea un nuevo clúster all-flash VMware vSAN, solo se presenta el hardware validado según la [Guía de compatibilidad de VMware](https://www.vmware.com/resources/compatibility/search.php). Además, se necesita un mínimo de cuatro servidores ESXi.

VMware vSphere on {{site.data.keyword.cloud_notm}} no automatiza la instalación, la configuración ni la activación de los componentes opcionales de VMware. La plataforma permite el máximo de flexibilidad para diseñar y crear su entorno VMware alojado mientras incorpora hardware compatible con VMware.

Utilice esta oferta para crear un nuevo clúster de servidores ESXi o para escalar un clúster existente de servidores ESXi en un {{site.data.keyword.CloudDataCent_notm}}. Dependiendo de los componentes de VMware que seleccione, puede empezar con un solo servidor ESXi y luego escalar el clúster más adelante cuando sea necesario.

## Especificaciones técnicas para clústeres de VMware vSphere on IBM Cloud

Revise los componentes de VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Nota**: la disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.

### Componentes de VMware

Seleccione licencias (proporcionadas por IBM o BYOL) para los siguientes componentes de VMware:
* VMware vSphere Enterprise Plus 6.0u2, 6.5u1 o 6.5u2
* Los siguientes componentes de VMware son opcionales:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced o Enterprise)
   * VMware vSAN (Advanced o Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Servidor nativo

Seleccione uno o varios {{site.data.keyword.baremetal_short}} de {{site.data.keyword.cloud_notm}} con el modelo de CPU y el tamaño de RAM seleccionados:
* 2-CPU Intel Broadwell generation (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)

Las opciones disponibles dependen de si ha seleccionado el componente vSAN de VMware.

Adicionalmente, las siguientes especificaciones de disco y de red:
* Enlaces ascendentes de red pública y privada de 10 Gbps
* Un controlador de disco RAID

### Redes

* Una VLAN (LAN virtual) pública y dos VLAN privadas
* (Opcional) Un par de alta disponibilidad de dispositivos de seguridad FortiGate

### Almacenamiento

Almacenamiento personalizado por el usuario para la configuración de vSAN cuando se selecciona el componente VMware vSAN:
* Opciones de disco de almacenamiento de SSD SED de 960 GB, SSD SED de 1,9 TB o SSD SED de 3,8 TB
* Opciones de cantidad de disco de 2, 4, 6 u 8

  Además, también se solicitan dos discos de memoria caché de 960 GB por host.

  **Nota:** Las unidades SSD (disco de estado sólido, Solid Disk) de 3,8 TB reciben soporte cuando estén disponibles a nivel general en un centro de datos.
* Opción de Intel Optane de alto rendimiento, que proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad. Esta opción depende del modelo de CPU.

## Especificaciones técnicas para nodos de expansión de clúster de vSphere

Cada nodo de expansión de clúster de vSphere desplegará e incurrirá en cargos por los siguientes componentes en su cuenta de {{site.data.keyword.slportal}}.

### Hardware para nodos de expansión

Un servidor nativo de {{site.data.keyword.cloud_notm}} con la configuración de hardware presentada en [Especificaciones técnicas para clústeres de VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Sistema de redes para nodos de expansión

Un servidor nativo de {{site.data.keyword.cloud_notm}} con la configuración de red presentada en [Especificaciones técnicas para clústeres de VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Componentes de VMware para nodos de expansión

* Un servidor nativo {{site.data.keyword.cloud_notm}} con VMware vSphere Enterprise Plus 6.0u2 o 6.5u1  
* Componentes opcionales de VMware que se presentan en [Especificaciones técnicas para clústeres de VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

**Importante**: debe gestionar los servidores ESXi, los componentes opcionales de VMware y el hardware adicional solicitados y distribuidos a su cuenta de {{site.data.keyword.cloud_notm}} solo desde el {{site.data.keyword.slportal}}. Después de crear un nuevo clúster en la consola de {{site.data.keyword.vmwaresolutions_short}}, puede volver a la consola y utilizar la información guardada para escalar el nuevo clúster. Para obtener más información, consulte [Escalado de clústeres existentes de vSphere](vs_scalingexistingclusters.html).

### Enlaces relacionados

* [Lista de materiales de software de VMware vSphere](vs_bom.html)
* [Planificación de clústeres de vSphere](vs_planning.html)
* [Solicitud de clústeres de vSphere](vs_orderinginstances.html)
* [Escalado de clústeres existentes de vSphere](vs_scalingexistingclusters.html)
