---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# Visión general de FortiGate Virtual Appliance on IBM Cloud

El servicio de FortiGate Virtual Appliance on {{site.data.keyword.cloud}} despliega un par de FortiGate Virtual Appliances en el entorno, lo que puede ayudar a reducir el riesgo implementando los controles de seguridad importantes dentro de la infraestructura virtual.

Puede instalar varias instancias de este servicio si las necesita. Puede gestionar este servicio utilizando el cliente web de FortiOS o la interfaz de línea de mandatos a través de SSH.

**Disponibilidad**: Este servicio solo está disponible para las instancias que se han desplegado en la V2.0 y posteriores releases.

## Especificaciones técnicas para FortiGate Virtual Appliance on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:

### Máquinas virtuales

* Todas las opciones incluyen un par de alta disponibilidad (HA) de máquinas virtuales
* 2, 4 u 8 vCPU por máquina virtual en función del tamaño del despliegue y el tipo de suscripción
* 4, 6 o 12 GB de RAM por máquina virtual en función del tamaño del despliegue y el tipo de suscripción

### Alta disponibilidad

Dos máquinas virtuales están desplegadas y listas para la configuración HA o Virtual Router Redundancy Protocol (VRRP).

### Redes

El acceso a la consola de FortiGate® se proporciona a través de una red de gestión privada.

### Licencias y tarifas

Las tarifas de licencia para cada máquina virtual se aplican a cada ciclo de facturación en función del tamaño del despliegue seleccionado y el modelo de licencia de suscripción mensual.

**Importante:** No podrá cambiar el nivel de licencia después de la instalación del servicio. Para cambiar el nivel de licencia, debe eliminar el servicio existente y reinstalarlo utilizando otra opción de licencia.

## Consideraciones al instalar FortiGate Virtual Appliance on IBM Cloud

Revise las siguientes consideraciones antes de instalar el servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:
* Las máquinas virtuales (VM) de FortiGate se despliegan solo en el clúster predeterminado.
* El 100% de la CPU y de la RAM para las dos VM FortiGate también está reservado porque estas VM están en el plano de datos de las comunicaciones de red y es fundamental que tengan recursos disponibles.

  Para calcular la reserva de CPU y de RAM para una sola VM FortiGate, utilice la fórmula siguiente:
   * `Reserva de CPU = Velocidad de CPU del servidor ESXi * número de vCPU`
   * `Reserva de RAM = Tamaño de RAM`
* Cuando despliegue un par de alta disponibilidad (HA) de dispositivos virtuales FortiGate en su instancia, se definirán reglas de SNAT y de cortafuegos en Management NSX Edge Services Gateway (ESG) junto con las rutas estáticas en los dispositivos virtuales FortiGate para permitir las comunicaciones HTTPS de salida desde su instancia hacia la red pública para la activación de licencias y para adquirir el contenido y las políticas de seguridad más recientes.
* No puede cambiar el nivel de licencia después de la instalación del servicio. Para cambiar el nivel de licencia, debe eliminar el servicio existente y luego reinstalar el servicio seleccionando otra opción de licencia.
* Debe cumplir los requisitos siguientes para evitar anomalías con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:
   * Al menos dos servidores ESXi activos deben estar disponibles para que las dos VM FortiGate se desplieguen con la regla de antiafinidad de mantener las VM en distintos servidores.
   * Los dos servidores ESXi activos deben tener suficientes recursos disponibles para que una VM FortiGate se pueda alojar en cada servidor ESXi con el 100% de reserva de CPU y de RAM.
   * VMware vSphere HA debe tener suficientes recursos para alojar dos VM FortiGate con el 100% de CPU y de RAM.

  Debido a estos requisitos, debe planificar cuidadosamente el espacio necesario para FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. Si es necesario, antes de solicitar FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, añada 1 o 2 servidores ESXi a la instancia o reduzca la reserva de CPU de vSphere HA para la migración tras error, o ambos.

## Ejemplo de solicitud de FortiGate Virtual Appliance on IBM Cloud

Solicita una instancia de tipo **Pequeño** de VMware vCenter Server con 2 servidores ESXi con la siguiente configuración: 16 núcleos a 2,10 GHz cada uno con 128 GB de RAM. Para FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, selecciona la opción **Grande** (8 vCPU y 12 GB de RAM) para el tamaño de despliegue y cualquier modelo de licencia de suscripción.

En este caso, una sola VM FortiGate necesita, en cada servidor:
* 2,1 GHz * 8 vCPU = 16,8 GHz de CPU, y
* 12 GB de RAM

En total, suman 33,6 GHz de CPU y 24 GB de RAM para dos VM FortiGate.

Cada servidor ESXi tiene una capacidad de 16 núcleos * 2,1 GHz = 33,6 GHz, de modo que se cumplen los dos primeros requisitos si ambos servidores están activos y hay al menos 16,8 GHz de CPU y 12 GB de RAM disponibles en cada servidor.

Sin embargo, de forma predeterminada vSphere HA reserva el 50% de CPU y RAM para la migración tras error en las instancias de vCenter Server que se han desplegado inicialmente con 2 servidores ESXi, de modo que solo tenemos:

`50% de 2 * 16 núcleos * 2,1 GHz = 33,6 GHz disponibles`

Puesto que existen otras cargas de trabajo en los servidores ESXi, como por ejemplo, VMware vCenter Server, VMware NSX Controller o VMware NSX Edge, utilizando estos recursos no queda satisfecho el tercer requisito. Esto se debe a que se necesitan 33,6 GHz de CPU y 24 GB de RAM para las dos VM de FortiGate.

En este caso, la instalación de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} puede fallar, a menos que se añada al menos un servidor ESXi al entorno y las reservas para migración tras error de vShpere HA se actualicen adecuadamente para garantizar que haya suficientes recursos para las dos VM FortiGate.

Si se necesitan recursos adicionales para ejecutar el servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, puede añadir más servidores ESXi antes de instalar el servicio.

## Consideraciones al eliminar FortiGate Virtual Appliance on IBM Cloud

Antes de eliminar el servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, asegúrese de que la configuración de los dispositivos virtuales FortiGate existentes se elimine correctamente. Concretamente, el tráfico de red se debe direccionar alrededor de los dispositivos virtuales FortiGate en lugar de a través de los dispositivos virtuales FortiGate. De lo contrario, el tráfico de datos del entorno podría verse afectado.

### Enlaces relacionados

* [Solicitud de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_ordering.html)
* [Gestión de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos de Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
