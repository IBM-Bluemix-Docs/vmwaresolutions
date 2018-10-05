---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Consideraciones posteriores al despliegue para la instancia de VMware

Las ofertas de {{site.data.keyword.vmwaresolutions_full}}, VMware vCenter Server y VMware Cloud Foundation no son servicios gestionados. Usted es responsable de la configuración, la seguridad, la gestión y la supervisión de todos los componentes de software. Con el acceso administrativo completo a la solución, tiene una gran potencia y flexibilidad que requiere conocimientos técnicos, administrativos y operativos significativos en varios dominios. La gestión de una instancia de VMware en el {{site.data.keyword.cloud_notm}} requiere la misma planificación y experiencia que la planificación de una instancia local. Las tecnologías definidas por software, como VMware NSX y VMware vSAN, simplifican considerablemente algunos aspectos de la gestión de instancias, pero pueden requerir nuevas habilidades y herramientas para gestionarse y operarse correctamente. Combinar la potencia, la velocidad y la fiabilidad del despliegue de VMware automatizado de {{site.data.keyword.cloud_notm}} con la planificación operativa adecuada y las pruebas garantiza una navegación rápida y satisfactoria en la nube híbrida.

Revise las siguientes consideraciones para comprender las responsabilidades que tiene para gestionar y operar con la instancia antes y después de que se haya desplegado. 

**Nota:** La lista siguiente no es exhaustiva. Para obtener más información, consulte [Servicios gestionados por IBM](../../services/managing_imi.html).

## Acceso a la cuenta de IBM Cloud

Para gestionar el acceso a la cuenta de {{site.data.keyword.cloud_notm}}, permita que otros miembros del equipo accedan a la instancia en la consola de {{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte [Invitar a los usuarios a acceder a servicios y recursos](../../vmonic/iamuserinvite.html).

## Limitaciones

Familiarícese con las limitaciones siguientes para su instancia:

- [Impacto de cambiar los artefactos de vCenter](../../vcenter/vcenter_chg_impact.html)
- [Consideraciones y limitaciones de red](../../vcenter/vc_networkingonvcenterserver.html)
- [Preguntas más frecuentes](../../vmonic/faq.html)

## Diseño y conectividad de red

Complete los pasos siguientes para gestionar el acceso a la red de {{site.data.keyword.cloud_notm}} y a los componentes de gestión de VMware y para planificar la topología de red de {{site.data.keyword.cloud_notm}}.

- Acceda a los puntos finales de gestión de la instancia utilizando la [VPN de {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/vpn-access) o la [Conexión de Direct-Link de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/direct-link).
- Idee una estrategia para la conectividad de red pública desde dentro de su instancia. Entre sus opciones se incluyen: el cliente de ejemplo VMware NSX Edge Services Gateway (ESG), dispositivos de pasarela tales como Vyatta y FortiGate, y servidores proxy desplegados en la red de {{site.data.keyword.cloud_notm}} o en su propia red a la que se accede a través de DirectLink.
- Planifique si desea desplegar la carga de trabajo en VLAN de {{site.data.keyword.cloud_notm}} con [direcciones IP portátiles de {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/subnets/getting-started.html) o [en conmutadores lógicos NSX (VXLAN) utilizando sus propias direcciones IP](../nsx/nsx_overview.html). Tenga en cuenta que el uso de redes definidas por software (SDN) de NSX le proporciona la mayor flexibilidad para gestionar y proteger la red de carga de trabajo en el {{site.data.keyword.cloud_notm}}.
- Utilice ESG de NSX, [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance) y la interconexión de DirectLink para planificar la conectividad con cargas de trabajo (Network Address Translation, Virtual Private Network, direccionamiento).
- Si implementa Cross-vCenter NSX, asegúrese de que los rangos de ID de segmento local no se solapen antes de desplegar las cargas de trabajo locales.

## Planificación y refuerzo de la seguridad

El usuario es responsable de proteger, cifrar y supervisar la instancia de VMware y las cargas de trabajo para cumplir con los estándares corporativo, industrial y regulatorio. Complete los pasos siguientes para garantizar una seguridad adecuada.

- Cambie todas las contraseñas visualizadas en la consola de {{site.data.keyword.vmwaresolutions_short}} y utilice su propio sistema de gestión de contraseñas. Tenga en cuenta que IBM mantiene los ID de usuario distintos necesarios para la automatización y el soporte en curso.
- Revise las políticas de contraseñas, como por ejemplo la complejidad y el período de caducidad, en todos los componentes.
- Revise los valores de cifrado en todos los componentes.
- Planifique e implemente soluciones de cortafuegos físicas o virtuales adecuadas, como por ejemplo NSX Distributed Firewall (DFW), NSX ESG, [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html) e [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance).
- Planifique e implemente las soluciones adecuadas de equilibrio de carga de aplicaciones y de seguridad, como [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html).
- Planifique e implemente las soluciones adecuadas de información de seguridad y de gestión de sucesos (SIEM), como por ejemplo [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence).
- Planifique e implemente la exploración de vulnerabilidades adecuada.
- Planifique e implemente la gestión de cambios adecuada, la aprobación, la auditoría y el control de accesos para su instancia, utilizando soluciones como [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html).

## Personalización

Complete los pasos siguientes para personalizar la instalación de la instancia de VMware base para que se ajuste a sus requisitos.

- Utilice su propia entidad emisora de certificados (CA) para generar certificados para componentes como, por ejemplo, vCenter, VMware Platform Services Controller (PSC) y NSX Manager.
- Configure los servicios desplegados. Por ejemplo:
  - Para HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, configure la integración de AD, el control de acceso, los valores de SMTP (Simple Mail Transfer Protocol) y las políticas de conformidad.
  - Para Zerto on {{site.data.keyword.cloud_notm}}, el plan de direccionamiento y direccionamiento de IP de las comunicaciones Zerto VRA (Virtual Replication Appliance) desde el cruce de conversores de direcciones de red (NAT) no está soportado. Considere el tunelado o el redespliegue de los VRA para el direccionamiento y el direccionamiento adecuados.
  - Para servicios de copia de seguridad como, por ejemplo, Veeam on {{site.data.keyword.cloud_notm}} e IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}, configure el trabajo de copia de seguridad, configure de forma opcional almacenamiento adicional y configure alertas de supervisión.
  - Para servicios de red y de seguridad como, por ejemplo, F5 on {{site.data.keyword.cloud_notm}} y FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, configure interfaces de red, certificados, configuración de alta disponibilidad (HA) y reglas según la topología de red y otros requisitos.

## Active Directory

Complete los pasos siguientes para garantizar la configuración y gestión adecuadas del inicio de sesión único (SSO).

- Configure la actualización del servidor y la planificación del rearranque de Active Directory (AD).
- Si ha elegido la opción de desplegar servidores AD en el clúster de vSphere, proporcione la licencia y la activación de Microsoft Windows para los servidores para garantizar la conformidad y la disponibilidad.
- Establezca la confianza mutua entre la instancia y el servidor AD local.
- Integre NSX VPN, si procede, con AD SSO.
- Integre hosts ESXi con AD SSO.

## Planificación de mantenimiento

Complete los pasos siguientes para garantizar una planificación adecuada para el mantenimiento de software.

- Configure VMware Update Manager (VUM) a través de un proxy para obtener actualizaciones de VMware.
- Si es aplicable, configure vSAN a través de un proxy para mantener la base de datos de la lista de compatibilidad de hardware (HCL) de vSAN.
- Planifique el mantenimiento normal de los componentes de VMware que no están soportados por VUM. Por ejemplo, VMware vCenter, PSC y NSX.
- Revise la configuración de EVC (Enhanced vMotion Compatibility) de vSphere. Es posible que el clúster no esté configurado con EVC habilitado si la versión actual de vSphere no da soporte a EVC para el nivel de hardware.
- Planifique el mantenimiento normal para servicios adicionales como Veeam on {{site.data.keyword.cloud_notm}}, Zerto on {{site.data.keyword.cloud_notm}} y F5 on {{site.data.keyword.cloud_notm}}.

## Supervisión

Asegúrese de planificar e implementar las soluciones siguientes para supervisar los componentes de instancia e instancia.

- Un servidor de registro que incluye el reenvío de registros o la recopilación para todos los componentes de la instancia y la retención de registros adecuada.
- Una infraestructura de alerta, incluida la configuración de la pasarela del servidor SMTP y del servicio de mensajes cortos (SMS), según sea necesario.
- Supervisión proactiva de hosts, unidades, software de gestión y red.
- Supervisión de vSAN, si procede.
- Supervisión y planificación de la capacidad. Puede [añadir y eliminar clústeres](../../vcenter/vc_addingviewingclusters.html) y [añadir y eliminar hosts](../../vcenter/vc_addingremovingservers.html) de la instancia desde la consola de {{site.data.keyword.vmwaresolutions_short}}.
- Supervisión de la infraestructura de copia de seguridad y de los trabajos de copia de seguridad.

## Continuidad y disponibilidad de las empresas

La instancia de VMware se está ejecutando en servidores nativos en el {{site.data.keyword.cloud_notm}}. Complete los pasos siguientes para asegurarse de que tiene planes adecuados para la alta disponibilidad y la continuidad de negocio.

- Revise la configuración de vSphere HA y vSphere Distributed Resource Scheduler (DRS) en relación con sus requisitos.
- Revise la configuración de la red y del control de E/S de almacenamiento según sus requisitos.
- Configure el orden de inicio de la máquina virtual en relación con sus requisitos.
- Configure las agrupaciones de recursos, según sea necesario, para la gestión y la carga de trabajo.
- Planifique, implemente y supervise una solución de copia de seguridad tanto para [componentes de gestión de instancias](solution_backingup.html) como para la carga de trabajo.
- Planifique la alta disponibilidad de la gestión de instancias, incluida la posibilidad de varias instancias, varios clústeres, la alta disponibilidad de vCenter y la alta disponibilidad de PSC.
- Planifique la continuidad de negocio para sus cargas de trabajo utilizando soluciones como [Zerto Disaster Recovery](../../services/addingzertodr.html), [Copia de seguridad y replicación de Veeam](../../services/veeam_considerations.html), e [IBM Spectrum Protect Plus](../../services/spp_considerations.html).

## Planificación del almacenamiento

Además de la planificación de la capacidad, complete los siguientes pasos para asegurarse de que la configuración de almacenamiento cumple con los requisitos de rendimiento y disponibilidad.

- El rendimiento de almacenamiento depende de varios factores, como la configuración de RAID y la fragmentación de disco; la configuración de red; el tamaño de bloque; las IOPS (operaciones de entrada/salida por segundo) configuradas para el almacenamiento conectado a la red; la configuración de hardware de VM y el método de conexión de almacenamiento; los métodos de agrupación y réplica; y el uso de políticas de almacenamiento como, por ejemplo, el cifrado, la eliminación de datos duplicados y la compresión. Planifique el tiempo necesario para probar y ajustar la configuración para satisfacer las necesidades de rendimiento del almacenamiento.
- Revise la política de almacenamiento de vSAN
  - RAID-1 proporciona un mejor rendimiento y menor susceptibilidad a un fallo secuencial, como un tiempo de reconstrucción más corto, en comparación con RAID-5. Sin embargo, RAID-5 tiene menos sobrecarga de almacenamiento.
  - RAID-6 proporciona protección frente a errores dobles, pero requiere un mínimo de seis hosts en comparación con cuatro hosts para RAID-5.
- Para añadir más almacenamiento al clúster de vSAN, debe añadir nuevos hosts al clúster o añadir en su lugar el almacenamiento NFS de {{site.data.keyword.cloud_notm}} Endurance. No se da soporte en este momento a la adición de discos a los hosts existentes.
- Si monta almacenamiento de NFS {{site.data.keyword.cloud_notm}} Endurance adicional en el clúster, asegúrese de seguir la orientación de la arquitectura y de configurar rutas de hosts en el almacenamiento utilizando las direcciones de grupo de puertos `SDDC-DPortGroup-NFS`. Debe autorizar estas direcciones, en lugar de los propios hosts, en el almacenamiento. Para obtener más información, consulte [Gestión de la infraestructura de almacenamiento adjunto](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing). Consulte también la receta de developerWorks que muestra cómo [añadir más almacenamiento de resistencia a su clúster VMware](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/) utilizando IBM Spectrum Protect Plus como ejemplo.

### Enlaces relacionados

* [Visión general de la solución](solution_overview.html)
* [Visión general del diseño](design_overview.html)
* [Capacidad de escalado](solution_scaling.html)

