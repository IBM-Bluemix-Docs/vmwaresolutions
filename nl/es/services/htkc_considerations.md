---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-11"

---

# Visión general de HyTrust KeyControl on IBM Cloud

El servicio HyTrust KeyControl on {{site.data.keyword.cloud}} simplifica la gestión de las cargas de trabajo cifradas automatizando y simplificando el ciclo de vida de las claves de cifrado, incluido el almacenamiento de claves, la distribución de claves, la rotación de claves y la revocación de claves. Mediante el cifrado compatible con FIPS 140-2, las empresas pueden gestionar fácilmente las claves de cifrado a escala. 

**Disponibilidad:** Este servicio solo está disponible para las instancias que están ejecutando vSphere 6.5 y que se despliegan en (o se han actualizado a) V2.5 y releases posteriores.

## Especificaciones técnicas para HyTrust KeyControl on IBM Cloud

Los componentes siguientes se solicitan y se incluyen en el servicio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust KeyControl

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente en vSAN en un clúster convergente
* Red: ubicada en una red portátil privada respaldada por VLAN para la gestión

### Alta disponibilidad

De forma predeterminada, se despliegan dos dispositivos KeyControl en una configuración de clúster activo-activo.

Opcionalmente, puede especificar el despliegue de dos dispositivos KeyControl en una configuración autónoma no en clúster.

### Licencias y tarifas

Se solicita una licencia de HyTrust KeyControl para cada instalación de instancia.

## Consideraciones al eliminar HyTrust KeyControl on IBM Cloud

Antes de eliminar el servicio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, asegúrese de que ha desvinculado a todos los clientes del uso de KeyControl. Después de eliminar el servicio, puede que las claves se supriman y que se le desconecte de las VM por seguridad.

### Enlaces relacionados

* [Solicitud de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](htkc_ordering.html)
* [Gestión de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](managinghtkc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
