---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# Preguntas más frecuentes sobre licencias y BYOL

Encuentre las respuestas a las preguntas más frecuentes sobre licencias, incluida la característica Traer su propia licencia (BYOL), de {{site.data.keyword.vmwaresolutions_full}}.

## ¿Qué es BYOL?

Traer su propia licencia (Bring Your Own License o BYOL) es una característica disponible para las instancias de VMware Cloud Foundation de la V1.8 y releases posteriores y para los clústeres de vCenter Server y vSphere de la V2.0 y releases posteriores. Con BYOL, puede utilizar sus propias licencias de VMware para uno o varios de los siguientes componentes de software de VMware cuando solicite instancias:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Si opta por utilizar su propia licencia para un componente de VMware y proporciona para el mismo una clave de licencia válida, no se solicita ninguna licencia a IBM para dicho componente y no se incurre en cargos de licencia mensuales en su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) para este componente.

**Nota:** La característica BYOL no está disponible para los usuarios de Business Partners.

## ¿Dónde se gestionan las licencias y los componentes solicitados a través de VMware vSphere on IBM Cloud?

Después de solicitar la creación de un nuevo clúster para VMware vSphere on {{site.data.keyword.cloud_notm}}, se suministra licencias de VMware, servidores ESXi y otros componentes de red y se pueden gestionar desde el {{site.data.keyword.slportal}}.

Después del despliegue, vaya a la consola de {{site.data.keyword.vmwaresolutions_short}} para escalar el clúster nuevo utilizando la configuración guardada. Para obtener más información sobre el escalado, consulte [Escalado de clústeres existentes de vSphere](../vsphere/vs_scalingexistingclusters.html).

## ¿Qué ediciones de licencias y cantidades de CPU se necesitan para BYOL?

Se aplican los siguientes requisitos a las ediciones de licencias para BYOL.

### Requisitos de BYOL para instancias de vCenter Server

Tabla 1. Ediciones de licencias y requisitos mínimos de CPU para instancias de vCenter Server

  | Componente VMware | Edición licencia necesaria | CPU mínima necesaria
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | N/D |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Standard, Advanced o Enterprise | 8 CPU |

### Requisitos de BYOL para instancias de Cloud Foundation

Tabla 2. Ediciones de licencias y requisitos mínimos de CPU para instancias de Cloud Foundation

  | Componente VMware | Edición licencia necesaria | CPU mínima necesaria
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | N/D |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Enterprise | 8 CPU |

## ¿Qué sucede si la clave de licencia que proporciono no es correcta?

Todas las claves de licencia que proporcione se validan para garantizar de que son correctos para los componentes correspondientes de VMware y que cumplen los requisitos mínimos de edición y de CPU de los componentes de VMware. Si la validación de alguna clave de licencia falla, recibe una notificación y no puede continuar con el pedido de la instancia.

## ¿Puedo proporcionar una clave de licencia con más de 8 CPU?

Sí. Para cada componente de VMware se necesita una licencia por CPU. Actualmente, todos los servidores de vCenter Server y de Cloud Foundation tienen dos CPU. Por lo tanto, se necesitan dos licencias por cada servidor. Se recomienda proporcionar una clave de licencia que dé soporte a la instancia básica y a los nodos de expansión que desee añadir a la instancia en el futuro.

## ¿Puedo proporcionar la licencia de SDDC Manager cuando utilice la característica BYOL?

No. Nuestro acuerdo con VMware implica que debemos aceptar la clave de licencia real de un cliente. Aunque el despliegue de Cloud Foundation incluye licencias de SDDC Manager, no podemos aceptar los archivos de claves de licencia de SDDC Manager ni validarlos para BYOL. Por lo tanto, IBM realiza un cargo de licencias de SDDC Manager para todas las instancias. Las licencias de SDDC Manager representan una pequeña parte de los cargos totales de licencias correspondientes a una instancia de Cloud Foundation.

## ¿Puedo utilizar la característica BYOL para algunos componentes de VMware y adquirir licencias mensuales para otros?

Sí. Puede utilizar la característica BYOL o adquirir licencias para cualquier combinación de los cuatro componentes de VMware. La consola de {{site.data.keyword.vmwaresolutions_short}} le facilita la selección de la opción de licencia cuando solicita la instancia de vCenter Server o de Cloud Foundation. La opción de licencia en vigor en el momento de realizar el pedido de la instancia inicial se aplica durante todo el tiempo de vida de dicha instancia.

## Para un componente específico de VMware, ¿puedo utilizar BYOL para algunas licencias y comprar el resto de las licencias de IBM?

Sí. Si ha seleccionado BYOL para un componente VMware específico, cuando cree un nuevo clúster tiene la opción de entrar una nueva clave de BYOL, de seguir utilizando una clave de BYOL existente o de comprar licencias proporcionadas por IBM para dicho clúster. En la actualidad, solo VMware vSphere Enterprise y VMware vSAN están disponibles para licencias por clúster.

## ¿Puedo utilizar BYOL cuando cree un nuevo clúster?

Sí. Puede utilizar BYOL de licencias BYOL existentes o especificar BYOL cuando cree un nuevo clúster. También puede adquirir una licencia de suscripción proporcionada por IBM al crear un nuevo clúster. En la actualidad, solo VMware vSphere Enterprise y VMware vSAN están disponibles para licencias por clúster.

## ¿Cómo gestiono mis licencias BYOL?

Puede gestionar sus licencias BYOL mediante el cliente web de VMware vSphere una vez finalizado el despliegue de la instancia.

## Cuando posteriormente añada más servidores ESXi a mi instancia, ¿valida la instancia si la capacidad de mis licencias BYOL es suficiente?

Sí. Cuando añada más servidores ESXi a una instancia desplegada, se comprueba automáticamente la capacidad de las licencias BYOL para el número especificado de servidores ESXi. Si la capacidad no es suficiente, los servidores ESXi no se añaden y recibe una notificación en la consola.

## ¿Cómo puedo saber la capacidad de licencia que tengo disponible en un clúster con BYOL?

Para encontrar el número de CPU disponibles en la clave de licencia, complete los pasos siguientes:
1. Vaya a la página **Instancias desplegadas**.
2. Localice y pulse la instancia.
3. En el separador **Infraestructura**, pulse en el clúster para el que desee comprobar la capacidad de la licencia. 
   El número de CPU disponibles se muestra en la tabla **Licencia proporcionada por el usuario**.

## ¿Proporciona IBM soporte si selecciono la opción de licencia BYOL?

El equipo de soporte de IBM sigue siendo su punto de contacto para cualquier duda o problema relacionado con la configuración de una instancia. Sin embargo, si el problema notificado corresponde a un componente de VMware BYOL, se le dirigirá al equipo de soporte de VMware.

## ¿Por qué aparecen cargos de licencia de vSphere en la lista de estimaciones de precio si utilizo BYOL? ¿Se me va a facturar por ello?

Los {{site.data.keyword.baremetal_short}} se suministran con VMware vSphere ya instalado y con las licencias de vSphere ya incluidas. Si ha seleccionado BYOL para vSphere, se inicia automáticamente un proceso sobre el despliegue de la instancia para eliminar las licencias de vSphere incluidas. Luego, los cargos de licencia se abonarán a su cuenta de {{site.data.keyword.cloud_notm}}. En este proceso no tiene que hacer nada.

## ¿Puedo seguir utilizando el proceso manual existente para BYOL?

Con la introducción de la característica BYOL, no se recomienda seguir utilizando el proceso manual. Si desea utilizar BYOL, proporcione sus propias licencias al solicitar la instancia.

## ¿Recibe BYOL soporte para otros productos VMware, como VMware vRealize Automation, VMware vRealize Operations o VMware vRealize Log Insight?

No, porque estos productos VMware no forman parte del despliegue de la instancia. Estos productos VMware se pueden instalar además del despliegue inicial, lo que requiere que los clientes o sus agentes realicen la instalación y la obtención de licencias.

## ¿Puedo solicitar almacenamiento de NFS con vCenter Server con el paquete híbrido (Hybridity)?

Para instancias desplegadas recientemente, solo se da soporte al almacenamiento all-flash de vSAN. La oferta de vCenter Server con el paquete híbrido (Hybridity) incluye licencia de vSAN Advanced o Enterprise.

Si tiene una instancia de vCenter Server con almacenamiento NFS, puede actualizar la instancia existente a vCenter Server con el paquete híbrido (Hybridity). Aunque la licencia de vSAN Advanced se solicite durante la actualización, no será necesario que suministre un clúster all-flash vSAN.

## ¿Puedo utilizar BYOL con vCenter Server con el paquete híbrido (Hybridity)?

No puede traer su propia licencia VMware (BYOL) a {{site.data.keyword.cloud_notm}}. vCenter Server con el paquete híbrido (Hybridity) requiere que IBM proporcione todas las licencias de VMware.

## ¿Cuál es la diferencia entre vCenter Server con licencia del paquete híbrido (Hybridity) y licencia de vCenter Server?

Las licencias individuales de VMware que están disponibles en vCenter Server se tarifican por CPU. Al igual que todas las licencias por CPU VMware proporcionadas por IBM, hay un recargo de 1,3x en el precio en todos los servidores que tienen más de 16 núcleos por CPU, por ejemplo, para Dual Intel Xeon Gold 6140.

vCenter Server con el paquete híbrido (Hybridity) es un conjunto prescrito de licencias y ediciones de VMware que se licencian por núcleo, y no por CPU. Por lo tanto, el precio de licencias para estas instancias no cambia.

## ¿Qué componentes y ediciones de licencia de VMware proporcionados por IBM están disponibles para vCenter Server con el paquete híbrido (Hybridity)?

Las nuevas instancias de vCenter Server con el paquete híbrido (Hybridity) incluyen VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced o Enterprise, VMware vSAN Advanced o Enterprise y VMware Hybrid Cloud Extension (HCX).

Si tiene una instancia de vCenter Server con la edición NSX Base, se le actualizará a NSX Advanced automáticamente al solicitar vCenter Server con el paquete híbrido (Hybridity).

## ¿Puedo actualizar la edición de NSX Advanced que se incluye en vCenter Server con el paquete híbrido (Hybridity) a la edición NSX Enterprise?

Aunque el vCenter Server con el paquete híbrido (Hybridity) incluye NSX Advanced, puede actualizar a la edición NSX Enterprise después de solicitar el vCenter Server con el paquete híbrido (Hybridity). Para ello, utilice el separador **Actualización y parche** en el separador de página de detalles de instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}.

### Enlaces relacionados

* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Instancias de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Acceso a la consola](loginmethod.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
