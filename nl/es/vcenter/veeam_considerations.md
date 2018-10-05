---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Visión general de Veeam on IBM Cloud

El servicio Veeam on {{site.data.keyword.cloud}} se puede integrar de forma fácil y directa con sus hipervisores VMware para ayudar a la empresa a alcanzar un alto grado de disponibilidad. Este servicio puede proporcionar objetivos de puntos de recuperación y de tiempo para sus datos y aplicaciones. Los objetivos de puntos de recuperación y de tiempo se pueden proporcionar menos de 15 minutos después de finalizar la configuración. Con este servicio, puede controlar las copias de seguridad y las operaciones de restauración de todas las máquinas virtuales (VM) de la infraestructura directamente desde la consola de Veeam.

**Disponibilidad**: Este servicio solo está disponible para instancias desplegadas en V1.8 o releases posteriores.

## Especificaciones técnicas para Veeam on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio Veeam on {{site.data.keyword.cloud_notm}}:

### VSI

* VSI único con el complemento de sistema operativo Veeam Backup and Replication 9.5
* Windows Server 2016 Standard Edition (64 bits)
* 4 núcleos x 2,0 GHz
* 8 GB RAM
* Enlace ascendente de red privada de 1 Gbps
* Disco de 100 GB (SAN)

### Almacenamiento para copias de seguridad

* Almacenamiento iSCSI de resistencia (2000, 4000, 8000 o 12000 GB)
* Rendimiento del almacenamiento (0,25, 2 o 4 IOPS/GB)

### Redes

Una dirección IP privada primaria.

### Licencias y tarifas

Veeam Backup and Replication 9.5 Enterprise Plus (licencia de 10, 25, 50, 100 o 200 máquinas virtuales).

### Gestión

Copias de seguridad de gestión configuradas de forma predeterminada con hasta cinco máquinas virtuales y 2000 GB de almacenamiento.

## Consideraciones al instalar Veeam on IBM Cloud

El repositorio del almacenamiento y del servidor Veeam están en el pod y en el centro de datos originales. Por lo tanto, el rendimiento de las operaciones de copia de seguridad para los clústeres remotos puede deteriorarse.

## Consideraciones al eliminar Veeam on IBM Cloud

Antes de eliminar el servicio Veeam on {{site.data.keyword.cloud_notm}}, tenga en cuenta que la eliminación de este servicio detiene todas las copias de seguridad (incluida la copia de seguridad de las VM de gestión) y suprime todas las copias de seguridad anteriores (la supresión es irreversible). Si las VM de gestión resultan dañadas, no se podrán restaurar.

### Enlaces relacionados

* [Solicitud de Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Solicitud de servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Veeam](https://www.veeam.com/){:new_window}
* [Centro de ayuda de Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
