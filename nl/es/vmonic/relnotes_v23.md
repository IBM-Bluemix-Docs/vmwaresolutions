---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Notas del release para V2.3

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades conocidas como Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Para obtener más información, consulte [Soluciones para las vulnerabilidades Spectre y Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware vCenter Server on IBM Cloud con el paquete híbrido (Hybridity)

Este release introduce la oferta VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity). vCenter Server con el paquete híbrido (Hybridity) es una nube privada alojada que permite ampliar la infraestructura local a la nube de forma rápida y sencilla. El entorno de VMware se basa en las licencias de centro de datos definido por software de VMware proporcionadas por IBM e incluye el servicio VMware HCX on {{site.data.keyword.cloud_notm}}, que conecta de forma sencilla y segura un entorno vSphere 5.0+ local con sitios de {{site.data.keyword.cloud_notm}} para ofrecer una infraestructura híbrida y una auténtica movilidad de aplicaciones.

El servicio HCX on {{site.data.keyword.cloud_notm}} sólo está disponible mediante la instancia de vCenter Server con el paquete híbrido (Hybridity). Puede actualizar la instancia existente de vCenter Server a una instancia de vCenter Server con el paquete híbrido (Hybridity) después de aplicar por primera vez el software base de vCenter Server V2.3. Para obtener más información, consulte [Aplicación de actualizaciones a instancias de vCenter Server](../vcenter/vc_applyingupdates.html).

Para obtener más información sobre vCenter Server con el paquete híbrido (Hybridity), consulte los temas siguientes:

* [Visión general de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_overview.html)
* [Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_planning.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_orderinginstance.html)

## Soporte de supresión de clústeres de instancias de vCenter Server y Cloud Foundation

Ahora puede suprimir clústeres de una instancia sin tener que suprimir la instancia completa. Para los clústeres desplegados en V2.2 o instancias anteriores, debe actualizar la instancia a V2.3 para poder suprimir los clústeres que ha añadido a la instancia.

Para obtener más información, consulte los temas siguientes:

* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Adición, visualización y supresión de clústeres para instancias de Cloud Foundation](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## Actualizaciones de instancias de VMware vCenter Server

Este release se aplica a las siguientes actualizaciones y mejoras:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 con nivel de parche ESXi650-201803001 aplicado)
*	VMware vCenter Server 6.5 Update 1g

### Mejoras para instancias y clústeres de vCenter Server

A partir del release V2.3, está disponible el despliegue de estos nuevos modelos de CPU al seleccionar el valor de servidor nativo **Personalizado**:
* Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz
* Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz

Para obtener más información, consulte los temas siguientes:

* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Actualizaciones de instancias de VMware Cloud Foundation

Este release se aplica a las siguientes actualizaciones y mejoras:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 con nivel de parche ESXi650-201803001 aplicado)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Actualizaciones de instancias de VMware Federal

### Configuración de DNS para instancias de VMware Federal

Ahora tiene la opción de seleccionar el despliegue de una sola instancia de servidor virtual (VSI) de Microsoft Windows Server Virtual para Microsoft Active Directory (AD) o dos máquinas virtuales Microsoft Windows de alta disponibilidad en el clúster de gestión. Para V2.2, se despliega de forma predeterminada y automáticamente una sola VSI Microsoft Windows para Microsoft AD. La nueva opción de seleccionar dos máquinas virtuales Microsoft Windows proporciona más privacidad y la opción de hacer copia de seguridad y restaurar las máquinas virtuales mediante el servicio Veeam.

**Nota:** Debe proporcionar 2 licencias de Microsoft Windows Server 2012 R2 si configura la instancia de modo que utilice las dos máquinas virtuales Microsoft Windows. Utilice la licencia de Microsoft Windows Server 2012 R2 Standard Edition y/o la licencia de Microsoft Windows Server 2012 R2 Datacenter Edition. Tiene 30 días para activar las máquinas virtuales.

Para obtener más información, consulte la sección *Valores de interfaz de red* en [Solicitud de instancias de VMware Federal](../vcenter/vc_fed_orderinginstance.html#network-interface-settings)​.

### Soporte de adición y supresión de clústeres de instancias de VMware Federal

Ahora puede utilizar clústeres para gestionar servidores ESXi en instancias de VMware Federal desplegadas en V2.3 y releases posteriores para mejorar la gestión y alta disponibilidad de los recursos. Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada. Puede ver los detalles del clúster en la página de visión general de la instancia o añadir hasta un total de 10 clústeres a una instancia. Cuando amplíe o reduzca la capacidad de una instancia, puede seleccionar el clúster al que se van a añadir los servidores ESXi o del que se van a eliminar los servidores ESXi.

También tiene la opción de suprimir uno o varios clústeres de la instancia sin suprimir la instancia completa.

Para obtener más información, consulte [Adición, visualización y supresión de clústeres para instancias de VMware Federal](../vcenter/fed_addviewdeleteclusters.html).

## Actualizaciones de servicios complementarios

### HyTrust CloudControl on IBM Cloud

El servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} solo está disponible para las instancias de VMware Cloud Foundation y las instancias de VMware vCenter Server que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos. El servicio aplica y controla el cumplimiento de las normas de seguridad y proporciona un control de acceso basado en roles (RBAC). Cuando se combina con HyTrust DataControl, el servicio puede asegurarse de que los datos de las cargas de trabajo y las máquinas virtuales no abandonen una región, un clúster o un servidor ESXi determinados en el centro de datos de {{site.data.keyword.cloud_notm}}.

Puede solicitar instancias con el servicio incluido al solicitar la instancia, o puede añadir este servicio a las instancias existentes más adelante.

Para obtener más información, consulte los temas siguientes:
* [Componentes y consideraciones sobre HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)
* [Gestión de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

El servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}} solo está disponible para las instancias de VMware Cloud Foundation y las instancias de VMware vCenter Server que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos. El servicio ofrece un cifrado de alta seguridad con claves de gestión integrada para proteger las cargas de trabajo en todo su ciclo de vida. El servicio puede proporcionar cifrado tanto a nivel de sistema operativo como a nivel de datos, lo que significa que se puede cifrar y descifrar cualquier directorio, carpeta o archivo de una carga de trabajo.

Puede solicitar instancias con el servicio incluido al solicitar la instancia, o puede añadir este servicio a las instancias existentes más adelante.

Para obtener más información, consulte los temas siguientes:
* [Componentes y consideraciones sobre HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)
* [Gestión de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

El release actual instala IBM Spectrum Protect&trade; Plus V10.1.1 como servicio de copia de seguridad predeterminado en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de IBM Spectrum Protect Plus V10.1.1, consulte [Actualizaciones de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentación nueva y actualizada

Dispone de una nueva receta de developerWorks con instrucciones paso a paso sobre cómo añadir almacenamiento a IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} con posterioridad al despliegue. Para obtener más información, consulte [Adición de almacenamiento a IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} con posterioridad al despliegue](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Actualizaciones y mejoras de la interfaz de usuario

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:
* **Coherencia**: La interfaz de usuario ahora ofrece un aspecto coherente con otros servicios de {{site.data.keyword.cloud_notm}}.
* **Facilidad de acceso**: Ahora puede acceder a las ofertas de VMware directamente desde el **Catálogo** de {{site.data.keyword.cloud_notm}}.
* **Experiencia de pedidos optimizada y simplificada**: ahora puede realizar el pedido de una instancia de VMware y desplegar sus servicios complementarios en una sola interfaz. Además, el coste estimado se calcula y se muestra al instante en la misma interfaz, de modo que puede ajustar su configuración en función del plan de costes.
* Al solicitar instancias o añadir clústeres, la opción de traer su propia licencia (BYOL) no está disponible para usuarios de Business Partners.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
