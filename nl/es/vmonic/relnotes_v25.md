---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

---

# Notas del release para V2.5

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades conocidas como Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obtener más información, consulte [Soluciones para las vulnerabilidades Spectre y Meltdown](../vmonic/trbl_fix_spectre.html).

## Actualización de componente NSX

Este release instala VMware NSX for vSphere 6.4.1 para los nuevos despliegues de VMware vCenter Server on {{site.data.keyword.cloud_notm}}, VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity), NetApp ONTAP Select y VMware Federal on {{site.data.keyword.cloud_notm}}.

## Eliminación de la configuración de copia de seguridad predeterminada

{{site.data.keyword.vmwaresolutions_short}} ofrece dos servicios complementarios integrados para la copia de seguridad: IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} y Veeam on {{site.data.keyword.cloud_notm}}. Con estos servicios, puede planificar y proporcionar funciones de recuperación, tanto de la infraestructura de gestión como de la carga de trabajo. Además, IBM Resiliency Services ofrece servicios gestionados para copias de seguridad de Veeam.

A partir del release V2.5, los servicios de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} y de Veeam on {{site.data.keyword.cloud_notm}}, cuando se despliegan, ya no preconfiguran la copia de seguridad de ninguna máquina virtual. Con este cambio, puede garantizar la configuración adecuada de todos los aspectos de los trabajos de copia de seguridad, incluidos la planificación, el periodo de retención, el uso de deduplicación, la supervisión y las alertas, y la gestión de claves de cifrado. Además, la máquina virtual de IBM CloudDriver ya no está configurada como un servidor de archivos persistente para las copias de seguridad de NSX.

Usted es responsable de la configuración, la gestión y la supervisión de todos los componentes de software, incluida la copia de seguridad y la disponibilidad de la infraestructura de gestión y las cargas de trabajo. Para obtener más información, consulte [Copia de seguridad de componentes](../archiref/solution/solution_backingup.html#backing-up-components).

**Nota:** Este cambio no afecta a las instancias desplegadas antes de la V2.5 que ya tienen instalado el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}.

## Resiliencia de IBM CloudDriver

Para las instancias desplegadas o actualizadas en releases de V2.5 o posteriores, el componente IBM CloudDriver ya no está configurado como una máquina virtual (VM) dentro del clúster de vSphere. En su lugar, se despliega como una instancia de servidor virtual (VSI) de la infraestructura {{site.data.keyword.cloud_notm}}, según sea necesario, con el último código de {{site.data.keyword.cloud_notm}} for VMware para operaciones como, por ejemplo, el despliegue de más nodos, clústeres o servicios. Además, se modifica IBM CloudDriver para que se comunique con el plano de gestión de {{site.data.keyword.cloud_notm}} utilizando la red privada de {{site.data.keyword.cloud_notm}}. Con este cambio, se eliminan las reglas de cortafuegos de NSX Edge Services Gateway (ESG) de gestión y de conversión de direcciones de red (NAT) que permiten que IBM CloudDriver envíe el tráfico de salida a la red pública.

Algunos servicios complementarios como F5 on {{site.data.keyword.cloud_notm}}, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, y Zerto on {{site.data.keyword.cloud_notm}} siguen necesitando acceso de red público, para que NSX ESG de gestión siga desplegado en todas las instancias.

## Gestión de accesos y usuarios habilitados para IAM

A partir del release V2.5, {{site.data.keyword.vmwaresolutions_short}} está integrado con IBM Identity and Access Management (IAM) para proporcionar un enfoque unificado para gestionar las cuentas de usuario y el acceso de usuario dentro de la cuenta de {{site.data.keyword.cloud_notm}}. Debido a lo cual:
* Ahora puede añadir varios usuarios a la cuenta de {{site.data.keyword.cloud_notm}} para la colaboración, y puede gestionar su acceso a los servicios y recursos que se suministran en su cuenta, asignándoles diferentes roles de acceso a la plataforma.  
* Las instancias que se despliegan en V2.5 y releases posteriores se enlazan automáticamente a la cuenta de usuario que se está utilizando cuando se solicita la instancia.
* Para las instancias que se han desplegado en V2.4 y releases anteriores, puede migrarlas a una cuenta de {{site.data.keyword.cloud_notm}} especificada y luego gestionarlas utilizando IAM también.

Para obtener más información, consulte los temas siguientes:
* [Invitación de usuarios para acceder a servicios y recursos](../vmonic/iamuserinvite.html)
* [Gestión de acceso de usuario con IAM](../vmonic/iam.html)

## Cambios en cuentas de usuario y grupos para instancias de VMware vCenter Server y VMware Cloud Foundation

El grupo de usuarios **ic4v-vCenter** se ha creado en el servidor de Microsoft Active Directory y se ha añadido a permisos globales en el vCenter Server y en los grupos de usuarios para el NSX Manager. El grupo contiene la cuenta de usuario de **automatización** para las instancias de vCenter Server y cuentas de usuario específicas del servicio para las instancias de vCenter Server y Cloud Foundation.

No edite los permisos globales del grupo **ic4v-vCenter** en la página **Usuarios y grupos** del cliente web de VMware vSphere. Hacerlo puede afectar a las operaciones de gestión.

Para las instancias de Cloud Foundation, utilice el ID de usuario de host **customerroot** en lugar del ID de usuario de host **root**. Continúe utilizando el ID de usuario de host **root** para las instancias de vCenter Server.

Para obtener más información sobre las cuentas de usuario, consulte los temas siguientes:

* [Consideraciones sobre el cambio de artefactos de vCenter Server](../vcenter/vcenter_chg_impact.html)
* [Consideraciones sobre el cambio de artefactos de Cloud Foundation](../sddc/cf_chg_impact.html)

## Actualizaciones de servicios complementarios

### IBM Cloud Private Hosted (actualizado el 30 de agosto de 2018)

El servicio {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} ya está disponible para las instancias de vCenter Server desplegadas en la versión V2.5 o releases posteriores y actualizadas a las mismas.

{{site.data.keyword.cloud_notm}} Private Hosted incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware y {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}.

Puede solicitar este servicio después de solicitar la instancia de vCenter Server. Para obtener más información, consulte [Solicitud de {{site.data.keyword.cloud_notm}} Private Hosted](../services/managing_icp.html).

### IBM Spectrum Protect Plus on IBM Cloud

A partir del release V2.5, el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} se despliega como dos máquinas virtuales independientes basadas en las mejores prácticas, con una máquina virtual que ejecuta el servidor de IBM Spectrum Protect Plus y otra máquina virtual que ejecuta el servidor vSnap y el proxy VADP.

Ahora puede solicitar hasta 10 almacenes de datos de copia de seguridad, que le permiten hasta 120 TB de almacenamiento de copia de seguridad. La máquina virtual vSnap y VADP se dimensionan en función del tamaño de almacenamiento de copia de seguridad seleccionado y de acuerdo con la información de [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).

### KMIP for VMware on IBM Cloud

Ahora hay disponible un punto final nuevo en Alemania para el servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [Configuración del servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_ordering.html#kmip-for-vmware-on-ibm-cloud-service-configuration).

## Documentación nueva y actualizada

### Documentación de almacenamiento adjunto

El almacenamiento adjunto para la documentación técnica de vCenter Server on IBM Cloud ahora está disponible en la sección *Referencia* de la región documentación de usuario. Este documento de arquitectura de referencia solo está disponible en inglés. Para obtener más información, consulte [Almacenamiento adjunto para vCenter Server on IBM Cloud](../archiref/attached-storage/storage-benefits.html).

### Especificaciones técnicas

Las especificaciones técnicas para todos los tipos de instancias y tipos de servicios ahora están disponibles en la documentación de usuario y están enlazadas desde la interfaz de usuario. Para obtener más información, consulte el tema de visión general adecuado para la instancia y el servicio.

### Documentación de servicios

La información de servicios se mejora para identificar fácilmente el soporte de servicio basado en el número de release en el que se ha puesto disponible.

Para obtener más información, consulte los temas siguientes:

* [Servicios disponibles para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html#available-services-for-vcenter-server-instances)
* [Servicios disponibles para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Servicios disponibles para las instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html#available-services-for-cloud-foundation-instances)

## Actualizaciones y mejoras de la interfaz de usuario

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* Si tiene una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) enlazada a su cuenta de {{site.data.keyword.cloud_notm}}, ahora puede pulsar el botón **Recuperar** recién añadido en la página **Valores** para obtener el nombre de usuario y la clave de API para la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) automáticamente.
* Se añade un nuevo separador **Historial de despliegue** en el panel de navegación izquierdo de la página de detalles de la instancia para comprobar el historial de despliegue de una instancia.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
