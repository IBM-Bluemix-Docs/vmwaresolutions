---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-31"

---

# Solicitud de IBM Cloud Private Hosted

{{site.data.keyword.cloud}} Private Hosted on vCenter Server en {{site.data.keyword.cloud_notm}} despliega automáticamente {{site.data.keyword.cloud_notm}} Private Hosted en las instancias de VMware vCenter Server.

{{site.data.keyword.cloud_notm}} Private Hosted incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware y {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}.

## Especificaciones técnicas de IBM Cloud Private Hosted

Estos son los requisitos mínimos para solicitar el servicio {{site.data.keyword.cloud_notm}} Private Hosted:

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
  **Nota**: VMware vCenter Server on {{site.data.keyword.cloud_notm}} con Hybridity Bundle no recibe soporte.
* VMware NSX Advanced o Enterprise Edition
* Tres {{site.data.keyword.baremetal_long}}
* Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz
* 384 GB de RAM por servidor
* Un recurso compartido de archivos de almacenamiento NFS compartido con 8.000 GB a 4 IOPS/GB
* 33 licencias de IBM Cloud Private Virtual Processor Core
* Para la copia de seguridad de datos, se recomienda el servicio Veeam on IBM Cloud.

## Procedimiento para solicitar IBM Cloud Private Hosted

1. Solicite una nueva instancia de vCenter Server siguiendo los pasos del apartado [Solicitud de instancias de vCenter Server](../vcenter/vc_orderinginstance.html). También puede solicitar IBM Cloud Private Hosted para una instancia existente.
  **Importante**: asegúrese de que el entorno cumple con los requisitos mínimos mostrados anteriormente.
2. Asegúrese de que tiene sus titularidades de IBM Cloud privado.
3. Después de recibir la confirmación de que la instancia de vCenter Server está lista para ser utilizada, continúe con los pasos siguientes para solicitar IBM Cloud Private Hosted.
4. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Cómo comenzar** en el panel de navegación izquierdo.
5. Desplácese hacia abajo en la página y bajo **Pedido de servicios adicionales**, pulse en la tarjeta **IBM Cloud Private Hosted**.
6. En la página **IBM Cloud Private Hosted on vCenter Server on IBM Cloud**, en el recuadro **Póngase en contacto con el equipo de DevOps de IBM Cloud Private Hosted**, describa sus requisitos y pulse **Solicitar una consulta**.

Un representante de DevOps de {{site.data.keyword.cloud_notm}} Private Hosted se pondrá en contacto con usted a través de la información de contacto de {{site.data.keyword.cloud_notm}} y le ayudará a comenzar.

### Enlaces relacionados

* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf) (descarga de PDF)
* [Apertura de una incidencia para IBM Cloud privado](https://www.ibm.com/mysupport/s/?language=en_US)
