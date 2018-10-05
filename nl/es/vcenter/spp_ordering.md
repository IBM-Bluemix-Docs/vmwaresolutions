---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Solicitud de IBM Spectrum Protect Plus on IBM Cloud

Puede solicitar el servicio de {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de IBM Spectrum Protect Plus on IBM Cloud para una instancia nueva

Puede solicitar una instancia nueva con IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **IBM Spectrum Protect Plus on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **IBM Spectrum Protect Plus on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de IBM Spectrum Protect Plus on IBM Cloud para una instancia existente

Puede añadir el servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **IBM Spectrum Protect Plus on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Configuración del servicio de IBM Spectrum Protect Plus on IBM Cloud

Al solicitar el servicio, proporcione los valores siguientes:

### Número de volúmenes de almacenamiento

El número de volúmenes que satisfagan sus necesidades de almacenamiento.

### Tamaño de almacenamiento por volumen

La capacidad de almacenamiento por volumen.

### Rendimiento de almacenamiento

El valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de los requisitos de carga de trabajo.
* Si desea solicitar licencias para IBM Spectrum Protect Plus, especifique **Número de máquinas virtuales para licencia** en el separador **Pedido de licencias**.
* Si desea traer su propia licencia (BYOL), pulse el separador **Licencias de IBM Spectrum Protect Plus** y luego pulse **Añadir archivos de licencia** para cargar sus propios archivos de licencia de IBM Spectrum Protect Plus.

## Proceso de despliegue de IBM Spectrum Protect Plus on IBM Cloud

El despliegue de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} es automático. Tanto si solicita una instancia con este servicio incluido como si despliega el servicio posteriormente en la instancia, se llevan a cabo los siguientes pasos mediante el proceso de automatización de {{site.data.keyword.vmwaresolutions_short}}:

1. Basándose en los valores especificados, se solicita almacenamiento NFS de resistencia desde la infraestructura de {{site.data.keyword.cloud_notm}} para el repositorio de copia de seguridad de IBM Spectrum Protect Plus.
2. Basándose en los valores especificados, se solicitan varias licencias para IBM Spectrum Protect Plus desde la infraestructura de {{site.data.keyword.cloud_notm}}. Las licencias se solicitan en incrementos de paquetes de 10 licencias de máquina virtual (VM), en función del número de licencias de máquinas virtuales que especifica el usuario al solicitar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Si el usuario opta por traer una licencia existente de IBM Spectrum Protect Plus, no se realiza ningún pedido de la infraestructura de {{site.data.keyword.cloud_notm}}.
3. El almacenamiento de NFS solicitado para este servicio se monta en todos los servidores ESXi en el clúster predeterminado de la instancia, incluida la adición de las rutas estáticas correctas en cada servidor ESXi a la subred privada de almacenamiento.
4. Se crean almacenes de datos NFS en vCenter Server para todos los volúmenes de almacenamiento NFS montados en los servidores ESXi.
5. Se despliegan, activan y configuran las VM de IBM Spectrum Protect Plus en el clúster predeterminado de la instancia.
6. El almacenamiento NFS solicitado para este servicio se adjunta a la máquina virtual de IBM Spectrum Protect Plus y se configura el repositorio de copia de seguridad.
7. Se registra el nombre de host y la dirección IP de la máquina virtual de IBM Spectrum Protect Plus con el servidor DNS de la instancia.

### Enlaces relacionados

* [Visión general de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [Planificación del servicio preventivo de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html)
* [Documentación de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
