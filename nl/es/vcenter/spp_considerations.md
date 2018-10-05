---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Visión general de IBM Spectrum Protect Plus on IBM Cloud

El servicio {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementar el servicio como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect para descargar copias para su almacenamiento y gestión de datos a largo plazo.

**Disponibilidad**: este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.2 y posteriores releases o que se han actualizado a estos.

**Notas:**
* Si instala el servicio para instancias que se despliegan en V2.4 o releases posteriores, se instalará IBM Spectrum Protect Plus V10.1.1 Parche 1.
* Si instala el servicio para instancias que se despliegan en V2.3, se instalará IBM Spectrum Protect Plus V10.1.1.
* Si instala el servicio para instancias que se despliegan en V2.2, se instalará IBM Spectrum Protect Plus V10.1.0.


## Especificaciones técnicas para IBM Spectrum Protect Plus on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:

### Recursos de vCenter

* VM de servidor que ejecuta el servidor de IBM Spectrum Protect Plus
   * Sistema operativo: Linux 3.10.0-693.11.1.el7.x86_64
   * 4 núcleos x 2,0 GHz
   * 32 GB de RAM
   * Disco de 370 GB
* VM secundarias que ejecutan el servidor de IBM Spectrum Protect Plus vSnap y el proxy VADP
   * Sistema operativo: Linux 3.10.0-693.11.1.el7.x86_64
   * CPU y RAM configuradas en función del tamaño de almacenamiento seleccionado y de la guía de dimensionamiento de [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)
   * Disco de 150 GB

### Almacenamiento para copias de seguridad

Almacenamiento personalizable para copias de seguridad con las opciones siguientes:
* Número de almacenamiento de archivos: de 1 a 10
* Cada almacenamiento de archivo de resistencia: 500, 1000, 2000, 4000, 8000 o 12000 GB
* Rendimiento de almacenamiento: 0,25, 2 o 4 IOPS/GB

Consulte la publicación [Herramienta de dimensionamiento y de blueprint IBM Spectrum Protect Plus](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) para la planificación y el dimensionamiento.

### Almacenamiento para gestión

Un almacenamiento de archivos de resistencia de 1000 GB, 2 IOPS/GB que aloje la máquina virtual IBM Spectrum Protect Plus y se ejecute en la misma subred que el almacenamiento de copia de seguridad.

### Redes

Dos direcciones IP privadas portátiles.

### Licencias y tarifas

* IBM Spectrum Protect Plus (10 hasta un máximo de 1000 licencias de máquina virtual en incrementos de 10)
* Licencia de IBM Spectrum Protect Plus ofrecida mediante la consola de {{site.data.keyword.vmwaresolutions_short}} (número de VM en los paquetes de 10) o como BYOL

## Consideraciones al instalar IBM Spectrum Protect Plus on IBM Cloud

Revise las siguientes consideraciones antes de instalar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Asegúrese de que la CPU y la memoria del clúster predeterminado de la instancia sean suficientes para la máquina virtual de IBM Spectrum Protect Plus.
* Asegúrese de que los montajes de NFS disponibles en los servidores ESXi sean suficientes en función de la versión de los servidores ESXi.

  Las instancias de Cloud Foundation y las instancias de vCenter Server que se despliegan o actualizan en la V2.2 o posteriores tienen un valor del parámetro `NFS.MaxVolumes` en VMware. Este parámetro define el número máximo de montajes de NFS de un servidor ESXi y se puede establecer en un máximo de 256, dependiendo de la versión del servidor ESXi. Para obtener más información, consulte [Cómo aumentar el valor predeterminado que define el número máximo de montajes de NFS en un host ESXi/ESX](https://kb.vmware.com/s/article/2239).

  El servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} puede consumir hasta once de los volúmenes de NFS en cada servidor de ESXi del clúster predeterminado de la instancia. Además, el servicio creará montajes de NFS transitorios para realizar copias de seguridad y restauraciones. Por lo tanto, debe establecer el número de montajes de NFS en un mínimo de 64 para asegurarse de que el servicio pueda instalarse y funcionar correctamente.

## Consideraciones al eliminar IBM Spectrum Protect Plus on IBM Cloud

Revise las siguientes consideraciones antes de eliminar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que todas las configuraciones de los trabajos de copia de seguridad se eliminen y de que no haya ninguna operación activa de copia de seguridad o de restauración.
* Cuando elimine el servicio, el almacenamiento del repositorio de copia seguridad se elimina de la VM de IBM Spectrum Protect Plus y el pedido de almacenamiento se cancela, lo cual suprime de forma permanente los datos del repositorio de copia de seguridad.
* Cuando se elimina el servicio, también se elimina el almacenamiento de copia de seguridad del servicio. Por lo tanto, todas las copias de seguridad pasan a estar inaccesibles durante la eliminación en el servicio.

### Enlaces relacionados

* [Planificación del servicio preventivo de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Solicitud de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentación de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
