---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# Visión general de F5 on IBM Cloud

El servicio F5 on {{site.data.keyword.cloud}} (F5 BIG-IP® Virtual Edition) proporciona servicios de equilibrio inteligente de carga L4-L7 y de gestión del tráfico a escala local y global, potentes funciones de protección de red y de cortafuegos de aplicaciones web y acceso seguro y federado a las aplicaciones.

Puede instalar más de una instancia de este servicio según sea necesario.

**Disponibilidad**: Este servicio solo está disponible para instancias desplegadas en V1.9 o releases posteriores.

## Especificaciones técnicas para F5 on IBM Cloud

Los componentes siguientes se incluyen con el servicio de F5 on {{site.data.keyword.cloud_notm}}:

### Máquinas virtuales
* Dos máquinas virtuales (VM) con todas las opciones disponibles.
* 2, 4 u 8 vCPU por máquina virtual en función de la opción de licencia.
* 4, 8 o 16 GB de RAM por máquina virtual en función de la opción de licencia.

### Redes
* Private Virtual Extensible LAN (VXLAN) para la sincronización de alta disponibilidad (HA).
* Acceso a Traffic Management Shell (TMSH) y la consola de gestión mediante una red de gestión privada.

### Licencias y tarifas
Las tarifas de licencia para cada máquina virtual se aplican a cada ciclo de facturación en función de la opción de licencia (Good, Better o Best) y el ancho de banda seleccionado.

**Importante:** No podrá cambiar el nivel de licencia después de la instalación del servicio. Para cambiar el nivel de licencia, debe eliminar el servicio existente y reinstalarlo utilizando otra opción de licencia.

## Consideraciones sobre la instalación para F5 en IBM Cloud

Antes de instalar el servicio F5 on {{site.data.keyword.cloud_notm}}, revise las siguientes consideraciones.

En función del modelo de licencia y del ancho de banda que selecciona, se despliegan dos VM (máquinas virtuales) BIG-IP VE con la configuración siguiente:

Tabla 1. Despliegues de CPU y de RAM para distintas las selecciones de ancho de banda y modelo de licencia

| Ancho de banda máximo | Modelo de licencia: Good | Modelo de licencia: Better | Modelo de licencia: Best |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbps           | 2 vCPU, 4 GB de RAM    | 4 vCPU, 8 GB de RAM      | 8 vCPU, 16 GB de RAM   |
| 200 Mbps          | 2 vCPU, 4 GB de RAM    | 4 vCPU, 8 GB de RAM      | 8 vCPU, 16 GB de RAM   |
| 1 Gbps            | 2 vCPU, 4 GB de RAM    | 4 vCPU, 8 GB de RAM      | 8 vCPU, 16 GB de RAM   |
| 3 Gbps            | 8 vCPU, 16 GB de RAM   | 8 vCPU, 16 GB de RAM     | 8 vCPU, 16 GB de RAM   |
| 5 Gbps            | 8 vCPU, 16 GB de RAM   | 8 vCPU, 16 GB de RAM     | 8 vCPU, 16 GB de RAM   |
| 10 Gbps           | 8 vCPU, 16 GB de RAM   | 8 vCPU, 16 GB de RAM     | 8 vCPU, 16 GB de RAM   |

**Notas:**

* F5 BIG-IP limita el rendimiento del dispositivo en función del ancho de banda máximo elegido. Como el rendimiento de la red se ve afectado por muchos factores, no todas las configuraciones y topologías pueden alcanzar el ancho de banda máximo seleccionado.
* El par de HA (alta disponibilidad) de las VM BIG-IP VE se solo desplegarán en el clúster predeterminado.

  Además, el 100% de la CPU y de la RAM para las dos VM BIG-IP VE también está reservado porque estas VM están en el plano de datos de las comunicaciones de red y es fundamental que tengan recursos disponibles.

  Para calcular la reserva de CPU y de RAM para una sola VM BIG-IP VE, utilice la fórmula siguiente:

  `Reserva de CPU = Velocidad de CPU del servidor ESXi * número de vCPU` (de la Tabla 1)

  `Reserva de RAM = Tamaño de RAM` (de la Tabla 1)

### Consideraciones de planificación
Debe cumplir los requisitos siguientes para evitar anomalías con F5 on {{site.data.keyword.cloud_notm}}:
* Al menos dos servidores ESXi activos deben estar disponibles para que las dos VM BIG-IP VE se desplieguen con la regla de antiafinidad de mantener las VM en distintos servidores.
* Los dos servidores ESXi activos deben tener suficientes recursos disponibles para que una VM BIG-IP VE se pueda alojar en cada servidor ESXi con el 100% de reserva de CPU y de RAM.
* VMware vSphere HA debe tener suficientes recursos para alojar dos VM BIG-IP con el 100% de CPU y de RAM.

Debido a estos requisitos, debe planificar el espacio necesario para F5 on {{site.data.keyword.cloud_notm}}. Si es necesario, antes de solicitar F5 on {{site.data.keyword.cloud_notm}}, añada de 1 a 2 servidores ESXi a la instancia o reduzca la reserva de CPU de HA de vSphere para la migración tras error, o ambos.

## Ejemplo de solicitud de F5 on IBM Cloud

Puede solicitar una instancia de VMware vCenter Server **Small** con 2 servidores ESXI con la siguiente configuración: dieciséis núcleos a 2,10 GHz cada uno con 128 GB de RAM. Para F5 on {{site.data.keyword.cloud_notm}}, selecciona el modelo de licencia **Best** y un valor de 5 Gbps para el valor de **ancho de banda máximo**.

En este caso, una sola VM BIG-IP necesita, en cada servidor:
* 2,1 GHz * 8 vCPU = 16,8 GHz de CPU, y
* 16 GB de RAM

En total, suman 33,6 GHz de CPU y 32 GB de RAM para dos VM BIG-IP.

Cada servidor ESXi tiene una capacidad de 16 núcleos * 2,1 GHz = 33,6 GHz, de modo que se cumplen los dos primeros requisitos si ambos servidores están activos y hay al menos 16,8 GHz de CPU y 16 GB de RAM disponibles en cada servidor.

Sin embargo, de forma predeterminada, vSphere HA reserva el 50 por ciento de la CPU y la RAM para la migración tras error en las instancias de vCenter Server que se han desplegado inicialmente con 2 servidores ESXi. Para este ejemplo, está disponible lo siguiente:

`50% de 2 * 16 núcleos * 2,1 GHz = 33,6 GHz disponibles`

Puesto que habrá otras cargas de trabajo en los servidores ESXi, como por ejemplo, VMware vCenter Server, VMware NSX Controller y VMware NSX Edge, utilizando estos recursos no podemos satisfacer el tercer requisito, ya que necesitamos 33,6 GHz de CPU y 32 GB de RAM para las dos VM BIG-IP.

En este caso, la instalación de F5 on {{site.data.keyword.cloud_notm}} puede fallar, a menos que se añada al menos un servidor ESXi al entorno y las reservas para migración tras error de vSphere HA se actualicen adecuadamente para garantizar que haya suficientes recursos para las dos VM BIG-IP. Si se necesitan recursos adicionales para ejecutar el servicio F5 on {{site.data.keyword.cloud_notm}}, puede añadir más servidores ESXi antes de instalar F5 on {{site.data.keyword.cloud_notm}}.

## Consideraciones al eliminar F5 on IBM Cloud

Antes de eliminar el servicio F5 on {{site.data.keyword.cloud_notm}}, asegúrese de que la configuración existente de BIG-IP VE se elimine correctamente. Concretamente, el tráfico de red se debe direccionar alrededor de BIG-IP VE en lugar de a través de BIG-IP VE. De lo contrario, el tráfico de datos existentes de su entorno puede verse afectado.

### Enlaces relacionados

* [Solicitud de F5 on {{site.data.keyword.cloud_notm}}](f5_ordering.html)
* [Gestión de F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de F5](https://f5.com/){:new_window}
