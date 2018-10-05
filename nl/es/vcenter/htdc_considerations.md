---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-18"

---

# Visión general de HyTrust DataControl on IBM Cloud

El servicio HyTrust DataControl on {{site.data.keyword.cloud}} ofrece un cifrado de alta seguridad con claves de gestión integrada para proteger las cargas de trabajo en todo su ciclo de vida. El servicio puede proporcionar cifrado tanto a nivel de sistema operativo como a nivel de datos, lo que significa que se puede cifrar y descifrar cualquier directorio, carpeta o archivo de una carga de trabajo.

**Disponibilidad:** este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

## Especificaciones técnicas para HyTrust DataControl on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust DataControl
* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente en vSAN en un clúster convergente
* Red: ubicada en una red portátil privada respaldada por VLAN para la gestión

### Alta disponibilidad
Se despliegan dos dispositivos DataControl en una configuración activa-activa.

### Licencias y tarifas

Licencia por host: se solicita una licencia de HyTrust DataControl por cada host del entorno.

## Consideraciones al eliminar HyTrust DataControl on IBM Cloud

Antes de eliminar el HyTrust DataControl en el servicio de {{site.data.keyword.cloud_notm}}, asegúrese de que ha desvinculado a todos los clientes del uso de DataControl. Después de eliminar el servicio, puede que las claves se supriman y que se le desconecte de las VM por seguridad.

### Enlaces relacionados

* [Solicitud de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestión de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtdc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
