---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Visualización de instancias de Cloud Foundation

Visualice el resumen y la información detallada de las instancias de VMware Cloud Foundation que se suministran para cuentas de usuario diferentes.

## Visualización del resumen de las instancias de Cloud Foundation

Para ver un resumen de todas las instancias de Cloud Foundation que se han suministrado para una cuenta de usuario, complete los pasos siguientes:

1. En la consola de {{site.data.keyword.vmwaresolutions_full}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En el banner de la consola, pulse el icono de la cuenta de usuario y, a continuación, pulse el campo **Cuenta** para seleccionar la cuenta de usuario para la que desea comprobar las instancias.
3. En la tabla **Instancias de Cloud Foundation**, vea la lista de las instancias:

Tabla 1. Elementos de instancias de Cloud Foundation

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre de la instancia |
| Versión | La versión del release en la que se ha desplegado la instancia o a la que se ha actualizado |
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia |
| Hora de creación | La fecha y hora en que se ha creado la instancia |
| Estado | El estado de la instancia |

La instancia puede tener una serie de estados.

Tabla 2. Descripciones de los estados de las instancias de Cloud Foundation

| Estado        | Descripción       |
|:------------- |:------------- |
| Creando | La instancia se está creando. |
| Compilando | La instancia se está configurando. |
| Listo para su uso | La instancia está lista para ser utilizada. |
| Modificando | La instancia se está modificando. |
| Fallido | Se ha producido un error durante el proceso de creación, configuración o modificación. |
| Suprimiendo | La instancia se está suprimiendo. |
| Error de supresión | Se ha producido un error cuando se estaba suprimiendo la instancia. |
| Suprimido | La instancia se ha suprimido. |

## Visualización de los detalles de las propiedades de las instancias de Cloud Foundation

Para ver los detalles de las propiedades de una instancia:

1. En la tabla **Instancias de Cloud Foundation**, pulse un nombre de instancia.
2. En **Propiedades**, consulte los detalles de la instancia.

Tabla 3. Propiedades de instancias de Cloud Foundation

| Propiedad        | Descripción       |
|:------------- |:------------- |
| Nombre | El nombre de la instancia |
| ID | El ID de la instancia |
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia |
| Versión actual | La versión actual de {{site.data.keyword.vmwaresolutions_short}} |
| Versión de vCenter | La versión de VMware vCenter Server<br><br>**Nota**: Hay una ligera variación entre la versión de vCenter Server que se muestra en la consola de {{site.data.keyword.vmwaresolutions_short}} y en el cliente web de VMware vSphere. Ambas son correctas. |
| NSX for vSphere | La versión del producto VMware NSX for vSphere |
| Licencia de _componente VMware_ | Si ha seleccionado que desea utilizar su propia licencia de VMware para cualquiera de los componentes de VMware en la página **Licencias** al solicitar la instancia, se muestra el nombre del componente de VMware y la clave de licencia que ha especificado para el componente.<br><br>**Licencia de vCenter Server** y **Licencia de NSX** son ejemplos de licencias de componentes de VMware. |
| Edición de licencia de NSX | La versión y la edición de la licencia de VMware NSX |
| DNS, Root Domain | El nombre del dominio raíz es el nombre del dominio DNS (Sistema de nombres de dominio) y el nombre raíz del grupo Microsoft Active Directory (AD). |
| DNS, SSO Domain | El dominio SSO es el dominio de inicio de sesión único (Single Sign-On) de vSphere. El nombre de dominio SSO es fijo para todas las instancias de Cloud Foundation desplegadas y tiene el valor <samp class="ph codeph">vsphere.local</samp>. |
| DNS, Subdomain | El subdominio es el nombre del subdominio DNS del nombre del dominio raíz en el que residen los nombres de host de la instancia local de Cloud Foundation. El nombre del subdominio está en el formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Versión de SDDC Manager  |  La versión de SDDC Manager de la instancia |
| Estado  | El estado de la instancia<br><br>La información que se muestra proporciona una actualización sobre el progreso del despliegue o de la acción que se realiza sobre la instancia. Cuando se producen problemas, es posible que se visualice un mensaje que le ayude a investigar y resolver el problema. |

## Visualización de información de acceso para instancias de Cloud Foundation

En **Información de acceso**, consulte la información de acceso para los componentes relacionados con la instancia. Las contraseñas que se muestran son contraseñas iniciales generadas por el sistema. Si las cambia fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, no se actualizarán en la página de resumen de la instancia.

Tabla 4. Información de acceso de Fundación Cloud correspondiente a los componentes relacionados con la instancia

| Componente        | Descripción       |
|:------------- |:------------- |
| AD/DNS IP | La dirección IP de los dos servidores AD |
| AD/DNS FQDN | El nombre de dominio completo del servidor AD/DNS<br><br>**Nota:** se puede utilizar la misma contraseña del administrador para conectarse a todos los servidores AD/DNS mediante una conexión de escritorio remoto. |
| AD/DNS ADMIN (Remote Desktop)  | Para las instancias primarias, muestra el nombre de usuario y la contraseña para acceder al servidor de AD mediante una conexión de escritorio remoto.<br><br>Para instancias secundarias, pulse el enlace **Ver en la instancia primaria** para ir a la información sobre nombre de usuario y contraseña de la instancia primaria.<br><br>**Nota**: después de que la instancia secundaria se añada al dominio DNS primario y de que se produzca la réplica, la contraseña del administrador local de la instancia primaria puede sobrescribir la contraseña del administrador local en la instancia secundaria. Al pulsar el enlace **Ver en la instancia primaria**, obtendrá acceso a la contraseña del administrador correcta.  |
| NSX Manager IP  | La dirección IP de NSX Manager  |
| NSX Manager FQDN  | El nombre de dominio completo de NSX Manager  |
| NSX Manager HTTP  | El nombre de usuario y la contraseña que se utilizan para acceder a la consola web de NSX Manager |
| NSX Manager SSH | El nombre de usuario y la contraseña que puede utilizar para acceder a NSX Manager mediante una conexión SSH |
| PSC IP  | La dirección IP del Platform Services Controller  |
| PSC FQDN  | El nombre de dominio completo de PSC  |    
| PSC SSH  | El nombre de usuario y la contraseña que puede utilizar para acceder a PSC VM mediante una conexión SSH  |
| PSC ADMIN  | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para acceder a la consola web de PSC  |
| vCenter IP  | La dirección IP de vCenter Server  |
| vCenter FQDN  | El nombre de dominio completo de vCenter Server  |
| vCenter SSH  | El nombre de usuario y la contraseña que puede utilizar para acceder a vCenter Server VM mediante una conexión SSH |
| vCenter ADMIN  | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para iniciar una sesión en vCenter Server mediante el cliente web de vSphere  |

## Visualización del historial de despliegues de instancias de Cloud Foundation

Pulse **Historial de despliegue** en el panel de navegación izquierdo para ver el historial de despliegue de la instancia.

Tabla 5. Historial de despliegues de la instancia de Cloud Foundation

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Fecha | La fecha y hora en que se ha modificado el estado de la instancia |
| Resumen | Los detalles del cambio |

## Qué hacer si se producen errores

Si se producen errores durante el despliegue o durante la supresión de la instancia, se notifica automáticamente al equipo de soporte de {{site.data.keyword.cloud_notm}}. Para informarse sobre el estado de la incidencia, puede [ponerse en contacto con el servicio de soporte de IBM](../vmonic/trbl_support.html).

## Qué hacer a continuación

Gestione sus instancias desde la consola de {{site.data.keyword.vmwaresolutions_short}} o desde el cliente web de vSphere.

**Importante**: Antes de pulsar la **Consola de vCenter** en la página de resumen de la instancia para ir al cliente web de vSphere y empezar a gestionar sus servidores ESXi, debe iniciar una sesión en el portal VPN del {{site.data.keyword.CloudDataCent_notm}}. Mueva el puntero del ratón sobre el botón de la consola de vCenter y siga las instrucciones para asegurarse de que cumple los requisitos y de que ha realizado los pasos necesarios antes de acceder al cliente web de vSphere.

Revise los temas siguientes para obtener información que le ayudará a seguir las instrucciones de inicio de sesión:

* Para ver los requisitos y pasos necesarios antes de acceder al cliente web de vSphere, consulte [Se ha alcanzado el tiempo de espera al conectar con el cliente web de vSphere](../vmonic/trbl_timeout_vc_console.html).
* Para obtener una lista de puntos de acceso para iniciar sesión en la red privada de {{site.data.keyword.cloud_notm}} utilizando VPN, consulte [Acceso a VPN](http://www.softlayer.com/vpn-access){:new_window}.
* Si tiene problemas al desplegar un archivo OVF (Open Virtualization Format) utilizando el cliente web de vSphere, consulte [Despliegue de un archivo OVF mediante el cliente web de vSphere](../vmonic/trbl_deploy_ovf.html).

### Enlaces relacionados

* [Pedido de instancias de Cloud Foundation](sd_orderinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de Cloud Foundation](sd_addingremovingservers.html)
* [Supresión de instancias de Cloud Foundation](sd_deletinginstance.html)
