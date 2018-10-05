---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Gestión de FortiGate Security Appliance on IBM Cloud

Después de que se instale correctamente el servicio FortiGate Security Appliance on {{site.data.keyword.cloud}}, podrá gestionar y configurar reglas de cortafuegos para FSA desde la consola de FortiGate.

**Importante**: Debe asegurarse de que las reglas de cortafuegos de FSA estén definidas de modo que permitan comunicaciones HTTPS salientes (puerto TCP 443) iniciadas por componentes de gestión, como Zerto Virtual Manager, para establecer comunicación con la base de datos de gestión externa de la infraestructura de {{site.data.keyword.cloud_notm}} a través de Internet. Las comunicaciones HTTPS salientes (puerto TCP 443) se originan en la dirección IP pública de los servicios de gestión de VMware NSX Edge Services Gateway (ESG) de su instancia.

## Acceso a la consola de FortiGate serie 300

Para gestionar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, debe acceder a la consola de FortiGate® serie 300 de una de estas formas:
* Inicie una sesión en el cliente web de FortiOS utilizando las credenciales que encontrará en la página de detalles del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.
* Acceda a la consola mediante una conexión SSH utilizando las credenciales que encontrará en la página de detalles del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte los temas siguientes:
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)

### Enlaces relacionados

* [Visión general de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_considerations.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web fortinet.com](https://www.fortinet.com/)
* [Documentación técnica de Fortinet](http://docs.fortinet.com/fortigate/admin-guides)
