---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-08"

---

# Visión general de FortiGate Security Appliance on IBM Cloud

El servicio de FortiGate Security Appliance on {{site.data.keyword.cloud}} despliega un par de dispositivos de seguridad FortiGate (FSA) serie 300 en modalidad altamente disponible para ofrecer servicios de cortafuegos, direccionamiento, NAT y VPN para proteger todos los servidores y máquinas virtuales de la VLAN pública de sus instancias.

Puede gestionar este servicio mediante el cliente web FortiOS o la interfaz de línea de mandatos a través de SSH.

**Disponibilidad**: Este servicio solo está disponible para instancias desplegadas en V1.8 o releases posteriores.

## Especificaciones técnicas para FortiGate Security Appliance on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:

### Hardware

FortiGate 300 series Security Appliance.

### Alta disponibilidad

Se despliegan dos dispositivos en una configuración activa-pasiva.

### Redes

* Dual 1 GbE vinculado en redes ascendentes y descendentes
* Una nueva VLAN pública de {{site.data.keyword.cloud_notm}} ascendente
* Una VLAN pública de {{site.data.keyword.cloud_notm}} descendente existente

## Consideraciones al instalar FortiGate Security Appliance on IBM Cloud

Revise las siguientes consideraciones antes de instalar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que la cuenta de {{site.data.keyword.cloud_notm}} que utiliza tiene el permiso **Hardware Firewall**. Este permiso se necesita para editar o ver registros y valores del cortafuegos correspondientes al servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} en su instancia.
* Si desea añadir el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} a una instancia desplegada, asegúrese de que no hay otro cortafuego desde la infraestructura {{site.data.keyword.cloud_notm}} ya instalado en la VLAN pública de la instancia.
* La instalación del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} añade una nueva VLAN pública.
* Durante el despliegue del servicio, es posible que la instancia no pueda acceder a Internet temporalmente.
* Después de que se instale correctamente el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, podrá gestionar y configurar reglas de cortafuegos para FSA desde la consola de FortiGate. Debe asegurarse de que las reglas de cortafuegos de FSA estén definidas de modo que permitan comunicaciones HTTPS salientes (puerto TCP 443) iniciadas por componentes de gestión, como Zerto Virtual Manager, para establecer comunicación con la base de datos de gestión externa de {{site.data.keyword.cloud_notm}} a través de Internet. Las comunicaciones HTTPS salientes (puerto TCP 443) se originan en la dirección IP pública de los servicios de gestión de VMware NSX Edge Services Gateway (ESG) de su instancia.
* Debe gestionar la configuración del dispositivo de seguridad FortiGate cuidadosamente para que se permitan solo las comunicaciones necesarias y se denieguen todas las demás comunicaciones.
* Si solicita clústeres adicionales, las VLAN públicas para estos clústeres recién añadidos no tienen el par HA de dispositivos de seguridad.

## Consideraciones al eliminar FortiGate Security Appliance on IBM Cloud

Revise las siguientes consideraciones antes de eliminar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* La eliminación del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} elimina la VLAN pública que se ha añadido.
* Durante la eliminación del servicio, es posible que la instancia no pueda acceder a Internet temporalmente.
* Todas las reglas de FortiGate para permitir, inspeccionar, bloquear o direccionar el tráfico NAT se eliminan junto con el servicio Fortinet. Si tiene alguna regla NAT, deberá volverla a configurar.

### Enlaces relacionados

* [Solicitud de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [Gestión de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos de Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
