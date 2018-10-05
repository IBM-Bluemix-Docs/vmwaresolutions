---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-14"

---

# Adición, visualización y supresión de clústeres para instancias de Cloud Foundation

Los servidores ESXi que ha configurado al solicitar una instancia se agrupan bajo un clúster predeterminado. El nombre del clúster predeterminado es:
* Para las instancias desplegadas en V2.1 o releases posteriores: **MGMT-Cluster-`<subdomain_label>`**
* Para las instancias desplegadas en V2.0 o releases anteriores: **SDDC-Cluster**

Puede añadir sus propios clústeres a las instancias de VMware Cloud Foundation para ampliar la capacidad de cálculo y de almacenamiento. Dentro de un clúster, puede gestionar los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Cuando ya no sea necesario, puede suprimir los clústeres añadidos de las instancias.

**Disponibilidad**:
* La característica de adición de clúster solo está disponible para las instancias que se han desplegado en la V2.0 y posteriores releases o que se han actualizado a estos.
* La característica de supresión de clúster solo está disponible para las instancias que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.  

## Adición de clústeres a instancias de Cloud Foundation

Puede añadir hasta cinco clústeres a una instancia de Cloud Foundation.

### Valores del sistema

Cuando añada un clúster a una instancia de Cloud Foundation, debe especificar los valores siguientes.

#### Nombre de clúster

El nombre del clúster debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre del clúster debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre del clúster es de 30 caracteres.
* El nombre del clúster debe ser exclusivo dentro de la instancia de Cloud Foundation.

#### Ubicación del centro de datos

La ubicación del {{site.data.keyword.CloudDataCent}} del clúster está definido en {{site.data.keyword.CloudDataCent_notm}} en la instancia de Cloud Foundation de forma predeterminada. Puede desplegar el clúster en un {{site.data.keyword.CloudDataCent_notm}} distinto del de la instancia desplegada, pero debe asegurarse de que la latencia de red entre los dos {{site.data.keyword.CloudDataCents_notm}} sea inferior a 150 ms. Para comprobar la latencia de red, puede utilizar una herramienta como [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Los centros de datos de los que dispone dependen de la configuración del servidor nativo seleccionada para el despliegue. Si selecciona la configuración **Personalizada**, también puede desplegar el clúster en un pod de infraestructura de {{site.data.keyword.cloud}} diferente, si el centro de datos seleccionado contiene más pods. Esta configuración es útil cuando el pod de infraestructura de {{site.data.keyword.cloud_notm}} predeterminado en el que se ha desplegado la instancia inicial ha alcanzado su capacidad máxima.

**Nota:** las configuraciones nativas estandarizadas **Pequeño** y **Grande** utilizan un pod predeterminado que no se puede modificar.

Si despliega el clúster en un centro de datos o pod diferente, se solicitan otras tres VLAN para que se utilicen con el {{site.data.keyword.baremetal_short}} solicitado.

### Valores de Servidor nativo

Puede elegir **Personalizado** o **Preconfigurado**.

#### Personalizado

Para el valor **Personalizado**, dispone de varias opciones para **Modelo de CPU** y **RAM**. Las opciones disponibles pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

Tabla 1. Opciones para {{site.data.keyword.baremetal_short}} personalizados

| Opciones de modelo de CPU   | Opciones de RAM   |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Preconfigurado

Para el valor **Preconfigurado**, puede seleccionar una **configuración de servidor nativo** en función de sus requisitos:
* Pequeño (Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz / 128 GB de RAM / 12 discos)
* Grande (Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz / 512 GB de RAM / 12 discos)

### Valores de almacenamiento vSAN

En la configuración de servidor nativo **Preconfigurado**, no puede modificar los valores de almacenamiento vSAN:
* Para la configuración **Pequeño**, se solicitan dos unidades de disco de 1,9 TB SSD SED.
* Para la configuración **Grande**, se solicitan cuatro unidades de disco de 3,8 TB SSD SED.

Para la configuración del servidor nativo **Personalizado**, puede personalizar el almacenamiento vSAN especificando los valores siguientes:

* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* **Tipo de disco para discos de memoria caché vSAN**: Seleccione una opción para los discos de memoria caché que necesite.

    **Nota**: Si desea añadir discos de capacidad por encima del límite de ocho, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto. La opción **Intel Optane de alto rendimiento** solo está disponible para los procesadores Dual Intel Xeon Gold 5120 y 6140.
* **Número de discos de memoria caché de vSAN**: Especifique el número de discos de memoria caché que desea añadir.

### Valores de licencia

Puede especificar las opciones de licencia para los componentes de VMware en el clúster, incluidos VMware vSphere y VMware vSAN:
* Para los usuarios de Business Partners, se incluyen y se adquieren en su nombre la licencia de vSphere (edición Enterprise Plus) y la licencia de vSAN. Sin embargo, debe especificar la edición para la licencia de vSAN.
* Para usuarios que no son Business Partners, puede utilizar las licencias de VMware que proporciona IBM para los componentes seleccionando **Incluir con la compra** o puede traer su propia licencia (BYOL) para los componentes seleccionando **Proporcionaré** e indicando sus propias claves de licencia.

## Procedimiento para añadir clústeres a instancias de Cloud Foundation

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de Cloud Foundation**, pulse la instancia a la que desea añadir clústeres.

   **Nota:** asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede añadir clústeres a la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo y pulse **Añadir** en la esquina superior derecha de la tabla **CLÚSTERES**.
4. En la página **Añadir clúster**, escriba el nombre de clúster.
5. Si desea alojar el clúster en un {{site.data.keyword.CloudDataCent_notm}} diferente al que se aloja la instancia, en **Servidor nativo**, marque el recuadro de selección **Seleccione otra ubicación** y elija el {{site.data.keyword.CloudDataCent_notm}} para alojar la instancia.
6. Complete la configuración del servidor nativo:
   * Si ha seleccionado **Personalizado**, seleccione el **Modelo de CPU** y el tamaño de **RAM**.
   * Si ha seleccionado **Preconfigurado**, seleccione el valor de **Configuración de servidor nativo**.
7. Complete la configuración de almacenamiento:
   * Si ha seleccionado **Preconfigurado** para la configuración de servidor nativo, los valores de almacenamiento para las configuraciones de servidor nativo **Pequeño** y **Grande** no se pueden cambiar.
   * Si ha seleccionado **Personalizado** para la configuración de servidor nativo, especifique los tipos de disco para la capacidad vSAN y los discos de memoria caché, y el número de discos. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
8. Especifique cómo se proporcionan las claves de licencia:
   * Para los usuarios de Business Partners, se incluyen y se adquieren en su nombre la licencia de vSphere (edición Enterprise Plus) y la licencia de vSAN. Sin embargo, debe especificar la edición para la licencia de vSAN.
   * Para los usuarios que no son Business Partners, puede seleccionar una de las siguientes opciones:
       * Si desea que se adquieran nuevas licencias en su nombre, seleccione **Incluir con la compra** para los componentes. Para VMware vSAN, seleccione también la edición de la licencia.
       * Si desea utilizar su propia licencia de VMware para un componente, seleccione **Proporcionaré** y escriba la clave de la licencia del componente.
9. En el panel **Resumen del pedido**, verifique la configuración del clúster antes de añadir el clúster.
   1. Revise los valores para el clúster.
   2. Revise el coste estimado del clúster. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de añadir el clúster.
   4. Pulse **Suministro**.

### Resultados después de añadir clústeres a instancias de Cloud Foundation

1. El despliegue del clúster se inicia automáticamente y el estado del clúster pasa a ser **Inicializando**. Puede comprobar el estado del despliegue consultando el historial de despliegue en la página de resumen de la instancia.
2. Cuando el clúster esté listo para ser utilizado, su estado pasará a ser **Listo para su uso**. El clúster recién añadido está habilitado con alta disponibilidad (HA) de vSphere y con el planificador de recursos distribuidos (DRS) de vSphere.

**Importante**: no puede cambiar el nombre del clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.

## Visualización de clústeres en instancias de Cloud Foundation

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de Cloud Foundation**, pulse una instancia para ver los clústeres que contiene.
3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, vea el resumen sobre los clústeres:
   * **Nombre**: el nombre del clúster.
   * **Servidores ESXi**: el número de servidores ESXi del clúster.
   * **CPU**: la especificación de CPU de los servidores ESXi del clúster.
   * **Discos vSAN personalizados**: el número de discos vSAN del clúster, incluido el tipo y la capacidad del disco.
   * **Memoria**: el tamaño total de la memoria de los servidores ESXi del clúster.
   * **Ubicación del centro de datos**: el centro de datos en el que está alojado el clúster.
   * **Pod**: el pod en el que se ha desplegado el clúster.
   * **Estado**: el estado del clúster. El estado puede tener uno de los valores siguientes:
   <dl class="dl">
       <dt class="dt dlterm">Inicializando</dt>
       <dd class="dd">El clúster se está creando y configurando.</dd>
       <dt class="dt dlterm">Modificando</dt>
       <dd class="dd">El clúster se está modificando.</dd>
       <dt class="dt dlterm">Listo para su uso</dt>
       <dd class="dd">El clúster está listo para ser utilizado.</dd>
       <dt class="dt dlterm">Suprimiendo</dt>
       <dd class="dd">El clúster se está suprimiendo.</dd>
       <dt class="dt dlterm">Suprimido</dt>
       <dd class="dd">El clúster se ha suprimido.</dd>
   </dl>
   * **Acciones**: Pulse el icono **Suprimir** para suprimir el clúster.
4. Pulse un nombre de clúster para ver la lista de servidores ESXi y su información:

   * **Nombre**: el nombre del servidor ESXi está en el formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde:

      `host_prefix` es el prefijo del nombre de host,
       `n` es la secuencia del servidor ESXi,
       `subdomain_label` es la etiqueta del subdominio y
       `root_domain` es el nombre del dominio raíz.

   * **Versión**: la versión del servidor ESXi.
   * **Credenciales**: el nombre de usuario y la contraseña para acceder al servidor ESXi.
   * **IP privada**: la dirección IP privada del servidor ESXi.
   * **Estado**: el estado del servidor ESXi, que puede tener uno de estos valores:
        <dl class="dl">
        <dt class="dt dlterm">Añadido</dt>
        <dd class="dd">El servidor ESXi se ha añadido y está listo para ser utilizado. </dd>
        <dt class="dt dlterm">Añadiendo</dt>
        <dd class="dd">El servidor ESXi se está añadiendo. </dd>
        <dt class="dt dlterm">Suprimiendo</dt>
        <dd class="dd">El servidor ESXi se está suprimiendo.</dd>
        </dl>
   * Los detalles de la licencia de vSAN y la licencia de vSphere. Los detalles de licencia de vSphere solo están disponibles cuando se han seleccionado para utilizar su propia licencia de VMware (BYOL) al realizar el pedido del clúster.
       * **Tipo de licencia**: la licencia de vSAN o la licencia de vSphere.
       * **Tipo de pedido**: la licencia la proporciona el usuario (BYOL) o se adquiere en nombre del usuario.
       * **Edición de licencia**: la edición de la licencia.
       * **Clave de licencia**: la clave de licencia.
       * **Capacidad total (CPU)**: la capacidad total o el número de CPU que proporciona la licencia.
       * **Capacidad libre (CPU)**: La capacidad que está disponible en la licencia.

## Supresión de clústeres de instancias de Cloud Foundation

Puede que desee suprimir un clúster de una instancia cuando ya no sea necesario.

### Antes de suprimir

* Utilice este procedimiento para suprimir clústeres de instancias que se han desplegado en V2.3 o releases posteriores.
* Para los clústeres desplegados en V2.2 o instancias anteriores, debe actualizar la instancia a V2.3 para poder suprimir los clústeres que ha añadido a la instancia.
* Puede suprimir un único clúster al mismo tiempo. Para suprimir varios clústeres, debe hacerlo de forma secuencial: esperando a que el clúster anterior se suprima antes de intentar suprimir el clúster siguiente.
* Asegúrese de que todos los nodos de un clúster estén encendidos y operativos antes de suprimir el clúster.
* Cuando se suprime un clúster, todas las VM (máquinas virtuales) del clúster también se suprimen y no se pueden recuperar. Si desea mantener las VM, mígrelas a otros clústeres.
* El clúster predeterminado no se puede suprimir.

## Procedimiento para suprimir clústeres de instancias de Cloud Foundation

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de Cloud Foundation**, pulse la instancia de la que desea suprimir clústeres.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede suprimir clústeres de la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, localice el clúster que desea suprimir y pulse el icono **Suprimir**.
4. Confirme que ha completado la migración de las VM a otros clústeres, si corresponde, y que desea suprimir el clúster.

### Enlaces relacionados

* [Visualización de instancias de Cloud Foundation](sd_viewinginstances.html)
* [Ampliación y reducción de la capacidad para instancias de Cloud Foundation](sd_addingremovingservers.html)
