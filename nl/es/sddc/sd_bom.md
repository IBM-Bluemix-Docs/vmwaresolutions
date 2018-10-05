---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-07"

---

# Lista de materiales de Cloud Foundation

Revise la información de la Lista de materiales (BOM) de las instancias de VMware Cloud Foundation.

## Lista de materiales de VLAN para instancias de Cloud Foundation

En la tabla siguiente se muestra la información de la lista de materiales para las VLAN de Cloud Foundation.

Tabla 1. Lista de materiales para las VLAN de instancias de Cloud Foundation

| VLAN      | Tipo      | Detalles      |
|:----------|:----------|:-------------|
| VLAN1     | Pública, Primaria | Asignada a servidores ESXi físicos para acceso público de red. No se utiliza tras el despliegue inicial. Disponible para el acceso a internet. |
| VLAN2     | Privada A, Primaria | Asignado por {{site.data.keyword.cloud}} a servidores físicos de ESXi. La utiliza la interfaz de gestión para el tráfico de gestión de VMware vSphere.<br><br>Asignada a VM (máquinas virtuales) que funcionan como componentes de gestión.<br><br>Asignada a VMware NSX VTEP (punto final de túnel VXLAN) |
| VLAN3     | Privada B, Portátil | Asignada a VMware vSAN, si se utiliza.<br><br>Asignada a VMware NFS, si se utiliza.<br><br>Asignada a VMware vSphere vMotion. |

## Lista de materiales de software para instancias de Cloud Foundation

En la tabla siguiente se muestra la información de la lista de materiales para los componentes de software de Cloud Foundation.

Tabla 2. Lista de materiales para los componentes de software de instancias de Cloud Foundation

| Fabricante | Componente                                | Versión      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 Actualización 2c (hasta el nivel de parche ESXi650-201808001) |
| VMware       | vCenter Server Appliance                 | 6.5 Actualización 2c |
| VMware       | Platform Services Controller             | 6.5 Actualización 2c |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.4.1        |
| VMware       | SDDC Manager                             | 2.4          |
| Microsoft    | Windows Server Standard Edition (64 bits) | 2012R2       |

## Valores de configuración avanzada para servidores ESXi

Revise la tabla siguiente para obtener una visión general de los valores de configuración avanzada que se aplican en los servidores ESXi. Los valores son diferentes en función de si la instancia de Cloud Foundation se ha desplegado en (o actualizado a) V2.2 o posterior a partir de un release anterior (V2.1 o anterior).

Tabla 3. Valores de configuración avanzada de servidores ESXi para clústeres e instancias de Cloud Foundation

| Valor de configuración | Si se ha desplegado en 2.2 o post.  | Si se ha actualizado desde V2.1 o ant. |   
|:------------- |:------------- |:------------- |
| Tamaño pila TCP/IP | **TcpipHeapSize** = 32 | No definido |
| Máx. pila TCP/IP | **TcpipHeapMax** = 1536 | No definido |  
| Máximo de volúmenes | **MaxVolumes** = 256 | Tanto **/NFS/MaxVolumes** como **/NFS41/MaxVolumes** = 256 |  
| Máximo errores latido | **HeartbeatMaxFailures** = 10 | No definido |  
| Frecuencia latido | **HeartbeatFrequency** = 12 | No definido |  
| Tiempo espera latido | **HeartbeatTimeout** = 5 | No definido |
| Profundidad máx. cola | **MaxQueueDepth** = 64 | No definido |
| Tamaño muestra cola completa | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Umbral cola completa | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

**Notas**:
* El valor **MaxVolumes** es obligatorio para el servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} porque el servicio puede utilizar más del número predeterminado de montajes de NFS en el servidor ESXi.
* Un valor de **No definido** para un valor de configuración indica que el nuevo valor no se aplica automáticamente porque requiere que se rearranquen los servidores ESXi, lo que puede suponer una interrupción.

  Se recomienda cambiar los valores de configuración **No definido** por los nuevos valores para mantener la coherencia entre todas las instancias y permitir un soporte adecuado para la ampliación de almacenamiento. IBM tiene intención de realizar pruebas solo con estos nuevos valores para {{site.data.keyword.vmwaresolutions_short}} V2.2 y releases posteriores.

  Para obtener más información, consulte [Cómo aumentar el valor predeterminado que define el número máximo de montajes de NFS en un host ESXi/ESX](https://kb.vmware.com/s/article/2239).

### Enlaces relacionados

* [Números de compilación y versiones de VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Números de compilación y versiones de VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Visión general de Cloud Foundation](sd_cloudfoundationoverview.html)
* [Planificación de instancias de Cloud Foundation](sd_planning.html)
