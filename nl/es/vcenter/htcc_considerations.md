---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Visión general de HyTrust CloudControl on IBM Cloud

El servicio HyTrust CloudControl on {{site.data.keyword.cloud}} aplica y controla el cumplimiento de las normas de seguridad y proporciona funciones detalladas de control de acceso basado en roles (RBAC), aprobación y auditoría. Cuando se combina con HyTrust DataControl, el servicio puede asegurarse de que los datos de las cargas de trabajo y las máquinas virtuales no abandonen una región, un clúster o un servidor ESXi determinados en el {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilidad:** este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

## Especificaciones técnicas para HyTrust CloudControl on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust CloudControl

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: 70 GB VMDK residente en vSAN en un clúster convergente
* Red: ubicada en una red portátil privada respaldada por VLAN para la gestión

### Alta disponibilidad

Se despliegan dos dispositivos CloudControl en una configuración activa-pasiva.

### Licencias y tarifas

Licencia por host: se solicita una licencia de HyTrust CloudControl por cada host del entorno.

## Consideraciones al eliminar HyTrust CloudControl on IBM Cloud

Antes de eliminar el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, asegúrese de inhabilitar **Blindaje de la contraseña raíz**, si está configurado, y de suprimir todos los hosts protegidos de HyTrust CloudControl.

### Enlaces relacionados

* [Solicitud de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestión de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
