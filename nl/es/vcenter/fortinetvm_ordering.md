---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Solicitud de FortiGate Virtual Appliance on IBM Cloud

Puede solicitar el servicio de FortiGate Virtual Appliance on {{site.data.keyword.cloud}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de FortiGate Virtual Appliance on IBM Cloud para una nueva instancia

Puede solicitar una nueva instancia con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **FortiGate Virtual Appliance on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **FortiGate Virtual Appliance on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de FortiGate Virtual Appliance on IBM Cloud para una instancia existente

Puede añadir el servicio de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} a una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **FortiGate Virtual Appliance on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Configuración del servicio de FortiGate Virtual Appliance on IBM Cloud

Al solicitar el servicio, proporcione los valores siguientes:

### Nombre

Especifique el nombre de servicio.

### Tamaño del despliegue

{{site.data.keyword.cloud_notm}} proporciona las siguientes opciones de tamaño de despliegue:
* Pequeño (2 vCPU / 4 GB de RAM)
* Medio (4 vCPU / 6 GB de RAM)
* Grande (8 vCPU / 12 GB de RAM)

### Modelo de licencia

El modelo de licencia de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} ofrece las siguientes opciones:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Este paquete incluye inspección de paquetes con estado, registro avanzado y protección de VLAN, reglas de cortafuegos Ingress/Egress, terminación SSL/IPSec VPN y soporte continuo.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Este paquete incluye todos los servicios del cortafuegos estándar además de NGFW IPS y filtrado de web, AntiVirus y AntiSpam, reputación de IP y de dominio y servicios de seguridad de núcleo de FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Este paquete incluye todos los servicios de cortafuegos estándar y de UTM además de FortiSandbox Cloud y seguridad de datos móviles.</dd>
</dl>

**Importante**: No puede cambiar el modelo de licencia después de la instalación del servicio. Para cambiar el modelo de licencia, debe eliminar el servicio existente y reinstalar el servicio seleccionando otra opción de licencia.

### Enlaces relacionados

* [Visión general de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_considerations.html)
* [Gestión de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos de Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
