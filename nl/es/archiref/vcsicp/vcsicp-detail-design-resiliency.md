---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# Copia de seguridad, recuperación tras desastre y escalabilidad

## Copia de seguridad y DR

###	Copia de seguridad VCS

Como parte de las soluciones IBM Cloud for VMware, el software de copia de seguridad de Veeam se puede desplegar de forma opcional en una instancia de servidor virtual de IBM Cloud (VSI) utilizando IBM Cloud Endurance Storage fuera del clúster VMware. El objetivo de este software es hacer copia de seguridad de los componentes de gestión de la solución.

### Copia de seguridad NSX

La copia de seguridad adecuada de todos los componentes de NSX es crucial para restaurar el sistema a su estado de trabajo si se produce una anomalía. No es suficiente realizar una copia de seguridad de las VM NSX; se debe utilizar la función de copia de seguridad NSX dentro del NSX Manager para realizar copia de seguridad adecuada. Esto requiere que se especifique un servidor FTP o SFTP para el repositorio de datos de copia de seguridad NSX.
La copia de seguridad de NSX Manager contiene toda la configuración de NSX, incluidos controladores, entidades de conmutación y de direccionamiento lógicos, seguridad, reglas de cortafuegos y todo lo demás que configure dentro de la interfaz de usuario o API de NSX Manager. Se debe hacer copia de seguridad por separado de la base de datos de vCenter y de los elementos relacionados, como los conmutadores virtuales. Se debe hacer una copia de seguridad de la configuración de NSX junto con una copia de seguridad de vCenter.

###	Copia de seguridad y DR para IBM Cloud Private

Las copias de seguridad de un despliegue de ICP resultan cruciales para restaurar el sistema a su estado de trabajo si se produce una anomalía. Sobre una copia de seguridad de VM tradicional, hay un punto de fricción: cada nodo maestro de ICP ejecuta etcd, y en la documentación de etcd se indica claramente que no se utilice la copia de seguridad de VM tradicional para restaurarlo.

En IBM Cloud Private a nivel de plataforma, necesita realizar una copia de seguridad de estos componentes:

-	**Etcd** — se utiliza para almacenar recursos de Kubernetes, así como la información de estado de Calico.
-	**Registro de Docker** — registro de imágenes privadas que se utiliza para almacenar archivos de imágenes de contenedor en un repositorio de imágenes.
-	**MongoDB** — base de datos que utiliza el servicio de medición, el servidor de repositorio de Helm, el servidor de API de Helm, la configuración de LDAP, el arrendatario (espacio de nombres) y las configuraciones de rol de team/user/usergroup.
-	**MariaDB** — base de datos que utiliza OIDC.
-	**Elasticsearch** — almacena los registros del sistema y de las aplicaciones.
-	**Prometheus** — almacena datos para la supervisión.
-	**Almacenamiento persistente** — se utiliza para los servicios de gestión que aprovechan ICP o el volumen persistente de Kubernetes y para el proveedor de almacenamiento. Puede utilizar la tecnología de copia de seguridad o restauración que proporciona el proveedor de almacenamiento. También se puede extender un proceso similar a la aplicación del usuario.

###	Copia de seguridad y DR para CAM
La copia de seguridad para un despliegue de CAM resulta crucial para restaurar el sistema a su estado de trabajo si se produce una anomalía. La copia de seguridad de CAM requiere que el cliente realice una copia de seguridad de los componentes siguientes:
-	**Base de datos Mongo**: base de datos principal de CAM.
-	**Base de datos de Maria**: utilizada por CAM Blueprint Designer.
-	**NFS/GlusterFS**: los datos de CAM residen en cuatro volúmenes persistentes.

### Copia de seguridad y DR para IKS
Las copias de seguridad de la base de datos etcd se proporcionan al cliente como parte del servicio gestionado; el cliente es el responsable de realizar la copia de seguridad de los datos de las aplicaciones.

## Escalabilidad

### Escalabilidad de VCS

Después del despliegue de los hosts iniciales, el usuario tiene la capacidad de escalar la capacidad de cálculo desde dentro del portal de IBM Cloud for VMware.

Este proceso de escalada del entorno sigue uno de estos tres métodos:
- Adición de nuevos sitios gestionados por distintos vCenter Servers.
- Adición de nuevos clústeres.
- Adición de nuevos hosts a un clúster existente.

####	Despliegues de varios sitios
VMware on IBM Cloud puede aprovechar la presencia del centro de datos a nivel mundial de IBM Cloud y la red troncal integrada para permitir que varios casos de uso entre geografía se desplieguen y funcionen en una fracción del tiempo que se necesitaría para crear dicha infraestructura desde cero.

####	Escalada con nuevo clúster
El usuario también tiene la opción de escalar la capacidad de cálculo creando un nuevo clúster desde dentro de la consola, solicitando los hosts, y los nuevos hosts se añaden automáticamente al nuevo clúster. Esta opción creará otro clúster en el entorno y proporcionará a los usuarios la posibilidad de segregar de forma física y lógica la gestión de cargas de trabajo desde las cargas de trabajo de la aplicación, la posibilidad de segregar las cargas de trabajo en función de otras características (por ejemplo, clúster de base de datos de Microsoft SQL) y la posibilidad de desplegar aplicaciones en topologías de alta disponibilidad.

####	Escalada de un clúster existente
El usuario puede escalar un clúster existente solicitando hosts desde dentro de la consola y los nuevos hosts se añaden automáticamente al clúster. Tenga en cuenta que es posible que los usuarios tengan que ajustar la política de reserva de HA para el clúster en función de sus requisitos de reserva.

### Escalabilidad de ICP
En función de la capacidad de cálculo disponible en las ubicaciones locales o en la nube, el usuario tiene la posibilidad de escalar la arquitectura de nodos desde el nodo de arranque desplegado inicialmente.

Este proceso de escalada del entorno sigue uno de los siguientes métodos:
- Ampliar los nodos trabajadores de ICP.
- Ampliar y utilizar la oferta IKS.

####	Expansión de ICP
Los nodos trabajadores de máquina virtual de ICP se escalan para ampliar la capacidad de cálculo y la aplicación:
  - El cliente suministra una nueva máquina virtual, en la misma VXLAN que la que está desplegado ICP.
  - Los clientes pueden escalar los nodos trabajadores, suministrando nuevas máquinas virtuales y luego iniciando una sesión en el nodo de arranque y ejecutando un mandato para incorporar los nuevos nodos al clúster.
  - Utilice CAM para automatizar el suministro de la VM y la ejecución de mandatos para añadirla al clúster ICP.


###  Expansión de IKS
Los usuarios pueden suministrar un entorno IKS a través de IBM Cloud Portal para ampliar/utilizar un entorno de contenedor.

Los despliegues de aplicaciones en IKS se pueden realizar a través de:
- La conexión o los servicios de IKS que se desarrollan en CAM y se publican en el catálogo ICP.
- Futura mejora de Multi-Cloud Manager para gestionar instancias de IKS.
- Línea de mandatos de Helm.
- Uso de clústeres multizona para aumentar la alta disponibilidad.

### Enlaces relacionados
* [Adición o eliminación de nodos de clúster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Adición de nodos trabajadores cambiando el tamaño de una agrupación de nodos trabajadores existente](https://console.bluemix.net/docs/containers/cs_clusters.html#add_workers)
* [Cómo hacer copia de seguridad y restaurar IBM Cloud Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [Copia de seguridad de ICP](https://github.com/ibm-cloud-architecture/icp-backup/)
* [VMware vCenter Server on IBM Cloud con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)