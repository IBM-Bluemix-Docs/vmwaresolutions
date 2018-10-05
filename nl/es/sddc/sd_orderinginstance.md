---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Pedido de instancias de Cloud Foundation

Para desplegar una plataforma unificada de centro de datos definido por software (SDDC) con una configuración estándar en cuanto a capacidad de cálculo, almacenamiento y red, solicite una instancia de VMware Cloud Foundation. Durante el pedido inicial, también puede añadir servicios, como [Zerto on {{site.data.keyword.cloud}} para la recuperación tras desastre](../services/addingzertodr.html).

## Requisitos

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](../vmonic/useraccount.html).
*  Ha revisado los requisitos y las consideraciones del apartado [Requisitos y planificación de instancias de Cloud Foundation](sd_planning.html).

**Importante**: No modifique ningún valor definido durante la solicitud o el despliegue de la instancia. Hacerlo puede hacer que la instancia se vuelva inutilizable. Por ejemplo, si se cierra la red pública, si los servidores y las Instancias de servidor virtual (VSI) se mueven detrás de una media disposición de Vyatta, o si el VSI de IBM CloudBuilder se detiene o se suprime. Tampoco cambie el nombre de la instancia, el nombre del dominio raíz, la etiqueta de subdominio ni el prefijo de nombre de host después de que se haya desplegado la instancia.

## Valores del sistema

Debe especificar los valores del sistema siguientes cuando solicite una instancia de Cloud Foundation.

### Nombre de instancia

El nombre de instancia debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre de instancia debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre de instancia es de 10 caracteres.
* El nombre de instancia debe ser exclusivo dentro de su cuenta.

### Primaria o secundaria

Seleccione si desea solicitar una nueva instancia primaria o una instancia secundaria para una instancia primaria existente.

## Valores de licencia

Especifique las opciones de licencia para los siguientes componentes de VMware de la instancia:  
* Licencia de vCenter Server - Standard
* Licencia de vSphere - Enterprise Plus
* Licencia de NSX - Enterprise
* Licencia de vSAN: seleccione la edición Advanced o Enterprise

Para los usuarios de Business Partners, se incluyen y se adquieren en su nombre la licencia de vCenter Server (edición Standard), la licencia de vSphere (edición Enterprise Plus), la licencia de NSX y la licencia de vSAN. Sin embargo, debe especificar la edición para la licencia de vSAN.

Para usuarios que no son Business Partner, puede utilizar las licencias de VMware que proporciona IBM para estos componentes seleccionando **Incluir con la compra** o puede traer su propia licencia (BYOL) seleccionando **Proporcionaré** e indicando sus propias claves de licencia.

## Valores de Servidor nativo

### Ubicación del centro de datos

Seleccione el {{site.data.keyword.CloudDataCent_notm}} en el que se alojará la instancia.

### Preconfigurado

Cuando selecciona **Preconfigurado**, no puede cambiar los valores de CPU o RAM.

En función de sus requisitos, seleccione una configuración de servidor nativo:
  * Pequeño (Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz / 128 GB de RAM / 12 unidades)
  * Grande (Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz / 512 GB de RAM / 12 unidades)

### Personalizado

Cuando selecciona **Personalizado**, puede elegir la combinación de CPU y RAM según sus necesidades.

Seleccione el modelo de CPU y la RAM del servidor nativo.

Tabla 1. Opciones para {{site.data.keyword.baremetal_short}} personalizados

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Número de servidores nativos

Una instancia de Cloud Foundation consta de cuatro servidores nativos en el despliegue inicial. No puede cambiar el número de servidores nativos cuando realiza el pedido.

## Valores de almacenamiento

Para las instancias de Cloud Foundation, solo puede solicitar almacenamiento VMware vSAN.
* Cuando selecciona una configuración de servidor nativo **Preconfigurado**, los valores de almacenamiento están estandarizados y no se pueden cambiar:
  * Para la configuración de servidor nativo **Pequeño**, se solicitan dos unidades de disco de 1,9 TB SSD SED.
  * Para la configuración de servidor nativo **Grande**, se solicitan cuatro unidades de disco de 3,8 TB SSD SED.
* Cuando selecciona la configuración de servidor nativo **Personalizado**, puede personalizar el almacenamiento vSAN para la instancia. Especifique los siguientes valores de vSAN:

* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* **Tipo de disco para discos de memoria caché vSAN**: Seleccione una opción para los discos de memoria caché que necesite.

    **Nota**: Si desea añadir discos de capacidad por encima del límite de ocho, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto. La opción **Intel Optane de alto rendimiento** solo está disponible para los procesadores Dual Intel Xeon Gold 5120 y 6140.
* **Número de discos de memoria caché de vSAN**: Especifique el número de discos de memoria caché que desea añadir.

## Valores de interfaz de red

Debe especificar los siguientes valores de la interfaz de red cuando solicite una instancia de Cloud Foundation.

### Prefijo de nombre de host

El prefijo del nombre de host debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  El prefijo de nombre de host debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima del prefijo de nombre de host es de 10 caracteres.

### Etiqueta de subdominio

La etiqueta de subdominio debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  La etiqueta de subdominio debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima de la etiqueta de subdominio es de 10 caracteres.
*  La etiqueta de subdominio debe ser exclusiva dentro de su cuenta.

### Nombre de dominio

El nombre del dominio raíz debe cumplir los siguientes requisitos:
* El nombre de dominio debe constar de dos o más series de caracteres separadas por un punto (.)
* La primera serie debe comenzar por un carácter alfabético y terminar por un carácter alfanumérico.
* Todas las series, excepto la última, solo pueden contener caracteres alfanuméricos y caracteres de guión (-).
* La última serie solo puede contener caracteres alfabéticos.
* La longitud de la última serie debe estar comprendida entre 2 y 24 caracteres.

**Nota:** la longitud máxima del FQDN (nombre de dominio completo) para hosts y máquinas virtuales (VM) es de 50 caracteres. Los nombres de dominio deben cumplir con esta longitud máxima.

### Formato de valor de los valores de red

El nombre de dominio y la etiqueta de subdominio se utilizan para generar el nombre de usuario y los nombres de servidor de la instancia, tal como se muestra en la tabla siguiente.

Tabla 2. Formato de valor de nombres de usuario, nombres de dominio y nombres de servidor

| Nombre        | Formato del valor      |
  |:------------- |:------------- |
  | Nombre de dominio | `<root_domain>` |  
  | Nombre completo de servidor ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde `<n>` es la secuencia del servidor ESXi. La longitud máxima es de 50 caracteres. |   
  | Nombre usuario inicio sesión vCenter Server | `<user_id>@<root_domain>` (usuario de Microsoft Active Directory) o `administrator@vsphere.local` |
  | FQDN de vCenter Server | `vcenter-1.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |  
  | FQDN de SDDC Manager | `sddcmanager.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |
  | Nombre sitio inicio sesión único (SSO) | `<subdomain_label>`
  | PSC FQDN | `PSC-<subdomain_label>.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |  

  El FQDN de SDDC Manager no se puede resolver públicamente. De lo contrario, la configuración de la instancia de Cloud Foundation podría fallar, y el error no es recuperable. Antes de especificar un nombre de dominio, revise [Consideraciones al elegir un nombre de dominio raíz](../vmonic/trbl_limitations.html#considerations-when-choosing-a-root-domain-name-for-cloud-foundation-instances).

### VLAN

Los valores del sistema de redes dependen de si ha seleccionado **Realizar pedido de nuevas VLAN** o **Seleccionar las VLAN existentes**.

Se necesita una VLAN pública y dos VLAN privadas para el pedido de la instancia. Las dos VLAN privadas se conectan en modalidad troncal en cada servidor nativo.

#### Realizar pedido de nuevas VLAN
Seleccione esta opción para solicitar una VLAN pública nueva y dos VLAN privadas nuevas.

#### Seleccionar las VLAN existentes  
En función del {{site.data.keyword.CloudDataCent_notm}} que haya seleccionado, puede que haya VLAN públicas y privadas existentes disponibles.

Cuando seleccione reutilizar las VLAN públicas y privadas existentes, especifique las VLAN y las subredes:
  * **VLAN pública** es para acceder a la red pública.
  * **VLAN privada** es para la conectividad entre los centros de datos y los servicios de {{site.data.keyword.cloud_notm}}.
  * **VLAN privada secundaria** es para las características de VMware, como vSAN.
  * **Subred primaria** se asigna a hosts físicos para acceder a la red pública.
  * **Subred primaria privada** se asigna a hosts físicos para el tráfico de gestión.

**Importante:**
* Asegúrese de que la configuración del cortafuegos en las VLAN seleccionadas no bloquee el tráfico de datos de gestión.
* Asegúrese de que todas las VLAN que seleccione estén en el mismo pod, porque los servidores ESXi no se pueden suministrar en VLAN de pod mixtos.

## Servicios

Cuando solicite una instancia de Cloud Foundation, también puede solicitar servicios adicionales. Para obtener más información sobre los servicios disponibles, consulte [Servicios para instancias de Cloud Foundation](sd_planning.html#services-for-cloud-foundation-instances).

## Resumen del pedido

En función de la configuración seleccionada para la instancia y los servicios complementarios, el coste estimado se genera y se muestra al instante en el panel derecho. Pulse **Detalles sobre precios** en el panel de la derecha para generar un documento PDF que proporcione los detalles de la estimación.

## Procedimiento para solicitar instancias de Cloud Foundation

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** desde el panel de navegación de la izquierda y, a continuación, pulse **Cloud Foundation** en la sección **Centros de datos virtuales**.
2. En la página **VMware Cloud Foundation on IBM Cloud**, pulse **Crear**.
3. En la página **Cloud Foundation**, escriba el nombre de la instancia.
4. Seleccione el tipo de instancia:
   * Pulse **Instancia primaria** para desplegar una sola instancia en el entorno o para desplegar la primera instancia en una topología de varios sitios.
   * Pulse **Instancia secundaria** para conectar la instancia con una instancia existente (primaria) en el entorno para obtener una alta disponibilidad. Siga estos pasos:
     1. Seleccione la instancia primaria a la que desea conectar la instancia secundaria.
     2. Para las instancias primarias V2.5 o posteriores, especifique el valor para la **Contraseña de administrador del PSC de la instancia primaria**.
     3. Para las instancias primarias V2.4 o anteriores, verifique que el valor prerrellenado para el campo **Contraseña del administrador para el PSC de instancia primaria** es correcto.
5. Complete los valores de licencia de los componentes de la instancia:
   *  Para utilizar licencias proporcionadas por IBM, seleccione **Incluir con la compra**.
   *  Para utilizar su propia licencia, seleccione **Proporcionaré** y escriba la clave de la licencia.  
6. Complete los valores del servidor nativo:
   1. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.
   2. Seleccione la configuración del servidor nativo.
      * Si selecciona **Preconfigurado**, elija una configuración de **Pequeño** y **Grande**.
      * Si seleccione **Personalizado**, especifique el modelo de CPU y el tamaño de RAM.
7. Complete la configuración del almacenamiento.
   * Si ha seleccionado **Preconfigurado** para la configuración de servidor nativo, los valores de almacenamiento para las configuraciones de servidor nativo **Pequeño** y **Grande** estandarizados no se pueden cambiar.
   * Si ha seleccionado **Personalizado** para la configuración de servidor nativo, especifique los tipos de disco para la capacidad vSAN y los discos de memoria caché, y el número de discos. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
8. Complete los valores de interfaz de red:
   1. Especifique el prefijo de nombre de host, la etiqueta de subdominio y el nombre de dominio raíz. Para una instancia secundaria, el nombre de dominio se rellena automáticamente.
   2. Seleccione los valores de VLAN:
      * Si desea solicitar nuevas VLAN públicas y privadas, pulse **Realizar pedido de nuevas VLAN**.
      * Si desea reutilizar las VLAN públicas y privadas existentes cuando estén disponibles, pulse **Seleccionar las VLAN existentes** y especifique las VLAN y las subredes.

9. Seleccione los servicios complementarios que desea desplegar en la instancia pulsando la tarjeta del servicio correspondiente. Si un servicio requiere configuración, complete los valores específicos del servicio y pulse **Añadir servicio** en la ventana de emergente de configuración. Para obtener más información sobre cómo proporcionar valores para un servicio, consulte el tema de servicios de ordenación correspondiente.

10. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
    1. Revise los valores de la instancia.
    2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
    3. Asegúrese de que la cuenta a la que se va a realizar el cobro es correcta y luego marque el recuadro de selección **Comprendo que la cuenta que se enumera a continuación se cobrará**.
    4. Pulse el enlace o enlaces de los términos que se aplican a su pedido. Asegúrese de que está de acuerdo con estos términos y marque el recuadro de selección **He leído y acepto los acuerdos de servicio de terceros enumerados a continuación**.
    5. Pulse **Suministro**.

## Resultados

El despliegue de la instancia comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del despliegue consultando los detalles de la instancia.

Cuando la instancia se haya desplegado correctamente, los componentes que se describen en [Especificaciones técnicas para las instancias de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances) se instalan en la plataforma virtual de VMware. Los servidores ESXi que ha solicitado se agrupan de forma predeterminada como **SDDC-Cluster**. Si ha solicitado servicios adicionales, el despliegue de los servicios se inicia después de que se haya completado el pedido.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Listo para su uso** y recibirá una notificación por correo electrónico.

Cuando se solicita una instancia secundaria, es posible que el cliente web de VMware vSphere para la instancia primaria (enlazada a la secundaria) se rearranque cuando finalice el pedido de la instancia secundaria.

## Qué hacer a continuación

Puede ver y gestionar la instancia de Cloud Foundation que ha solicitado.

**Importante**: Solo debe gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no desde el {{site.data.keyword.slportal}} ni mediante ningún otro método fuera de la consola. Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola.

**ATENCIÓN**: el hecho de gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} (que se instalaron en la cuenta de {{site.data.keyword.cloud_notm}} al solicitar la instancia) desde fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} podría hacer que el entorno quedara inestable. Estas actividades de gestión incluyen:

*  Añadir, modificar, devolver o eliminar componentes
*  Ampliar o reducir la capacidad de la instancia mediante la adición o eliminación de servidores ESXi
*  Apagar componentes
*  Rearrancar servicios

   Las excepciones a estas actividades incluyen la gestión de comparticiones del archivo de almacenamiento compartido desde el {{site.data.keyword.slportal}}. Estas actividades incluyen: solicitar, suprimir (lo que puede afectar los almacenes de datos si están montados), autorizar y montar comparticiones del archivo de almacenamiento compartido.

### Enlaces relacionados

* [Registro de una cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Visualización de instancias de Cloud Foundation](sd_viewinginstances.html)
* [Adición, visualización y supresión de clústeres para instancias de Cloud Foundation](sd_addingviewingclusters.html)
* [Ampliación y reducción de la capacidad para instancias de Cloud Foundation](sd_addingremovingservers.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](sd_addingremovingservices.html)
* [Supresión de instancias de Cloud Foundation](sd_deletinginstance.html)
* [Preguntas frecuentes sobre BYOL](../vmonic/faq_byol.html)
