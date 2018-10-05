---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Gestión de VMware HCX on IBM Cloud

## Acceso a las consolas de gestión de HCX on IBM Cloud

Para gestionar el servicio HCX on {{site.data.keyword.cloud}}, debe acceder a la consola de HCX Cloud o a la consola de administración de HCX Manager:
1. Utilice el VPN de la infraestructura de {{site.data.keyword.cloud_notm}} o un servidor de gestión para permitir el acceso a la dirección IP del dispositivo virtual HCX Manager (HCX Manager). Encontrará la dirección IP en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
2. Para acceder a la consola de Cloud HCX, pulse **Ver consola de HCX Cloud** en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} e inicie una sesión utilizando las credenciales de vCenter Server.
3. Para acceder a la consola de administración de HCX Manager, pulse **Ver la consola de administración de HCX Manager** en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} e inicie una sesión utilizando las credenciales de HCX Manager que aparecen en la misma página de detalles del servicio.

Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html).

## Aplicación de actualizaciones a HCX en IBM Cloud

HCX on {{site.data.keyword.cloud_notm}} se despliega con la última compilación probada de la tecnología de VMware Hybrid Cloud Extension. VMware envía actualizaciones a estas compilaciones regularmente, lo que incluye arreglos importantes y características nuevas. Estas compilaciones se envían a instalaciones de HCX on {{site.data.keyword.cloud}} automáticamente, incluidas instalaciones de HCX locales.

Para aplicar los arreglos de mantenimiento enviados a su entorno, debe utilizar la Consola de administración de HCX Manager en el centro de datos local y la instancia de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity).

Si no ve una actualización de compilación que está esperando, si tiene problemas con HCX, o si desea que se envíe al sistema la última compilación de HCX enviada inmediatamente, abra una incidencia de soporte siguiendo los pasos de [Cómo ponerse en contacto con el soporte de IBM](../vmonic/trbl_support.html).

### Enlaces relacionados

* [Visión general de HCX on {{site.data.keyword.cloud_notm}}](hcx_considerations.html)
* [Glosario de términos de HCX](hcx_glossary.html)
* [Visión general de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentación de VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
