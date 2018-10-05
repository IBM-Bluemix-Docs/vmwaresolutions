---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Visualización de instancias de NetApp ONTAP Select

Ver el resumen y la información detallada de las instancias de NetApp ONTAP Select que se suministran para cuentas de usuario diferentes.

## Visualización del resumen de instancias de NetApp ONTAP Select

Para ver un resumen de todas las instancias de NetApp ONTAP Select que se han suministrado para una cuenta de usuario, complete los pasos siguientes:

1. En la consola de {{site.data.keyword.vmwaresolutions_full}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En el banner de la consola, pulse el icono de la cuenta de usuario y, a continuación, pulse el campo **Cuenta** para seleccionar la cuenta de usuario para la que desea comprobar las instancias.
3. En la tabla **Instancias de NetApp ONTAP Select**, visualice la lista de instancias que se han suministrado en la cuenta de usuario seleccionada.

Tabla 1. Elementos de la instancia de NetApp ONTAP Select

| Elemento        | Descripción       |  
|:------------- |:--------------- |
| Nombre | Nombre de la instancia. |
| Versión | La versión de la instancia. |  
| Ubicación | El centro de datos en el que se aloja la instancia. |
| Hora de creación | La fecha y hora en que se ha creado la instancia. |   
| Estado | El estado de la instancia. El estado puede tener uno de los valores siguientes:<ul><li>Creando: la instancia se está creando.</li><li>Compilando: la instancia se está configurando.</li><li>Listo para su uso: la instancia está lista para ser utilizada.</li><li>Modificando: la instancia se está modificando.</li><li>Fallido: Se ha producido un error durante el proceso de creación, configuración o modificación.</li><li>Suprimiendo: la instancia se está suprimiendo.</li><li>Error de supresión: se ha producido un error cuando se estaba suprimiendo la instancia.</li><li>Suprimido: la instancia se ha suprimido.</li></ul>|

## Visualización de los detalles de las propiedades de las instancias de NetApp ONTAP Select

Para ver los detalles de las propiedades de una instancia:

1. En la tabla **Instancias de NetApp ONTAP Select**, pulse un nombre de instancia.
2. En **Propiedades**, consulte los detalles de la instancia.

Tabla 2. Propiedades de la instancia de NetApp ONTAP Select

| Propiedad        | Descripción       |
|:--------------- |:----------------- |
| Nombre | Nombre de la instancia. |
| ID | El ID de la instancia. |
| Ubicación | El centro de datos en el que se aloja la instancia. |
| Versión desplegada | La versión desplegada de {{site.data.keyword.vmwaresolutions_short}}. |
| Versión de vCenter | La versión de VMware vCenter Server.<br><br>**Nota**: Hay una ligera variación entre la versión de vCenter Server que se muestra en la consola de {{site.data.keyword.vmwaresolutions_short}} y en el cliente web de VMware vSphere. Ambas son correctas. |
| NSX for vSphere | La versión del producto VMware NSX for vSphere. |
| Edición de licencia de NSX | La versión y la edición de la licencia de VMware NSX. |
| Versión de NetApp | La versión de NetApp ONTAP Select. |
| Tipo de licencia de NetApp | El tipo de licencia de NetApp ONTAP Select. |
| DNS, Root Domain | El nombre del dominio raíz es el nombre del dominio DNS (Sistema de nombres de dominio) y el nombre raíz del grupo Microsoft Active Directory (AD) correspondiente a la instancia. |
| DNS, SSO Domain | El dominio SSO es el dominio de inicio de sesión único (Single Sign-On) de vSphere. El nombre de dominio SSO se establece para todas las instancias de NetApp ONTAP Select desplegadas con el valor `vsphere.local`. |
| DNS, Subdomain | El subdominio es el nombre del subdominio DNS del nombre del dominio raíz en el que residen los nombres de host de la instancia local de NetApp ONTAP Select. El nombre del subdominio está en el formato `<subdomain_label>.<root_domain>`. |
| Estado | El estado de la instancia. |

## Visualización de información de acceso para instancias de NetApp ONTAP Select

En **Información de acceso**, consulte la información de acceso para los componentes relacionados con la instancia. Estas contraseñas son contraseñas iniciales que genera el sistema. Si las cambia fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, no se actualizarán en la página de resumen de la instancia.

Tabla 3. Información de acceso correspondiente a los componentes relacionados con la instancia de NetApp ONTAP Select

| Componente        | Descripción       |
|:---------------- |:----------------- |
| AD/DNS IP | Las direcciones IP de los dos servidores AD. |
| AD/DNS FQDN | El nombre de dominio completo del servidor AD/DNS. |
| AD/DNS ADMIN (Remote Desktop) | El nombre de usuario y la contraseña que puede utilizar para acceder al servidor AD mediante una conexión remota de escritorio. |
| NSX Manager IP | La dirección IP de NSX Manager. |
| NSX Manager FQDN | El nombre de dominio completo de NSX Manager. |
| NSX Manager HTTP | El nombre de usuario y la contraseña que puede utilizar para acceder a la consola web de NSX Manager. |
| NetApp Cluster IP | La dirección IP del clúster de NetApp ONTAP Select. |
| NetApp Cluster FQDN | El nombre de dominio completo del clúster de NetApp ONTAP. |
| NetApp Cluster HTTPS | El nombre de usuario y la contraseña que puede utilizar para acceder al clúster de NetApp ONTAP Select. |
| NetApp Deploy Tool IP | La dirección IP de la máquina virtual de NetApp ONTAP Select Deploy. |
| NetApp Deploy Tool FQDN | El nombre de dominio completo de NetApp ONTAP Select Deploy. |
| NetApp Deploy Tool HTTPS | El nombre de usuario y la contraseña que puede utilizar para acceder a la máquina virtual de NetApp ONTAP Select Deploy. |
| PSC IP | La dirección IP de Platform Services Controller. |
| PSC FQDN | El nombre de dominio completo de PSC. |
| PSC ADMIN | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para acceder a la consola web de PSC. |
| PSC SSH | El nombre de usuario y la contraseña que puede utilizar para acceder a PSC VM mediante una conexión SSH. |
| vCenter IP | La dirección IP de vCenter Server. |
| vCenter FQDN | El nombre de dominio completo de vCenter Server. |
| vCenter ADMIN | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para iniciar una sesión en vCenter Server mediante el cliente web de vSphere. |
| vCenter SSH | El nombre de usuario y la contraseña que puede utilizar para acceder a vCenter Server VM mediante una conexión SSH. |

## Visualización del historial de despliegues de instancias de NetApp ONTAP Select

Pulse **Historial de despliegue** en el panel de navegación izquierdo para ver el historial de despliegue de la instancia.

Tabla 4. Historial de despliegues de la instancia de NetApp ONTAP Select

| Elemento        | Descripción       |  
|:------------|:------------- |
| Fecha | La fecha y hora en que se ha modificado el estado de la instancia |
| Resumen | Los detalles del cambio |

Si se producen errores durante el despliegue o durante la supresión de la instancia, se notifica automáticamente al equipo de soporte de {{site.data.keyword.cloud_notm}}. Para informarse sobre el estado de la incidencia, puede [ponerse en contacto con el servicio de soporte de IBM](../vmonic/trbl_support.html).

## Visualización de clústeres de NetApp ONTAP Select

1. Pulse **Infraestructura** en el panel de navegación izquierdo.
2. En **CLÚSTERES**, vea el resumen sobre los clústeres de NetApp ONTAP Select.

	Tabla 5: Elementos de clústeres de NetApp ONTAP Select

	 <table>
	   <tr>
	     <th>Elemento</th>
	     <th>Descripción</th>
	   </tr>
	   <tr>
	     <td>Nombre</td>
	     <td>El nombre del clúster.</td>
	   </tr>
	   <tr>
	     <td>Servidores ESXi</td>
	     <td>El número de servidores ESXi del clúster.</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>La especificación de CPU de los servidores ESXi del clúster.</td>
	   </tr>
	   <tr>
	      <td>Almacenamiento efectivo</td>
	      <td>La capacidad total de disco de los servidores ESXi del clúster.</td>
	   </tr>
	   <tr>
	      <td>Memoria</td>
	      <td>El tamaño total de la memoria de los servidores ESXi del clúster.</td>
	   </tr>
	   <tr>
	      <td>Ubicación del centro de datos</td>
	      <td>El centro de datos en el que se aloja el clúster. Coincide con la ubicación del centro de datos de la instancia.</td>
	   </tr>
		 <tr>
		   <td>Pod</td>
			 <td>El pod en el que se ha creado el clúster.</td>
		 </tr>
		 <tr>
		  <td>Estado</td>
			<td>El estado del clúster. El estado puede tener uno de los valores siguientes:<ul><li>Inicializando: el clúster se está creando y configurando.</li><li>Modificando: el clúster se está modificando.</li><li>Listo para su uso: el clúster está listo para ser utilizado.</li></ul></td>
		 </tr>
		 <tr>
		  <td>Acciones</td>
			<td>Pulse el icono **Suprimir** para suprimir el clúster.</td>
		 </tr>
	 </table>

3. Pulse el nombre del clúster para ver los detalles de su servidor ESXi.

Tabla 6. Detalles de servidor ESXi de un clúster de NetApp ONTAP Select

| Elemento        | Descripción       |  
|:------------|:----------------- |
| Nombre | El nombre del servidor ESXi está en el formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde:<br><br>`host_prefix` es el prefijo del nombre de host, `n` es la secuencia del servidor, `subdomain_label` es la etiqueta del subdominio y `root_domain` es el nombre del dominio raíz. |
| Versión | La versión del servidor ESXi. |
| Credenciales | El nombre de usuario y la contraseña para acceder al servidor ESXi. |
| IP privada | La dirección IP privada del servidor ESXi. |
| Estado | El estado del servidor ESXi, que puede tener uno de estos valores:<ul><li>Activo: el servidor ESXi está listo para ser utilizado.</li><li>Suprimiendo: el servidor ESXi se está suprimiendo.</li></ul> |

## Qué hacer a continuación

Gestione sus instancias desde la consola de {{site.data.keyword.vmwaresolutions_short}}, el cliente web de VMware vSphere o la consola de NetApp.

**Importante**: Antes de pulsar la **Consola de vCenter** en la página de resumen de la instancia para ir al cliente web de vSphere y empezar a gestionar sus servidores ESXi, debe iniciar una sesión en el portal VPN del {{site.data.keyword.CloudDataCent_notm}}. Mueva el puntero del ratón sobre el botón de la **consola de vCenter** y siga las instrucciones para asegurarse de que cumple los requisitos y de que ha realizado los pasos necesarios antes de acceder al cliente web de vSphere.

Para obtener más información que le ayudará a seguir las instrucciones de inicio de sesión, revise los temas siguientes:

*  Para ver los requisitos y pasos necesarios antes de acceder al cliente web de vSphere, consulte [Se ha alcanzado el tiempo de espera al conectar con el cliente web de vSphere](../vmonic/trbl_timeout_vc_console.html).
*  Para ver una lista de puntos de acceso para iniciar una sesión en la red privada de la infraestructura de {{site.data.keyword.cloud_notm}} utilizando VPN, consulte [Acceso VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Si tiene problemas al desplegar un archivo OVF (Open Virtualization Format) mediante el cliente web de vSphere, consulte [Despliegue de un archivo OVF mediante el cliente web de vSphere](../vmonic/trbl_deploy_ovf.html).

### Enlaces relacionados

* [Solicitud de instancias de NetApp ONTAP Select](np_orderinginstances.html)
* [Supresión de instancias de NetApp ONTAP Select](np_deletinginstance.html)
* [Conexión de almacenamiento dedicado a despliegues de NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
