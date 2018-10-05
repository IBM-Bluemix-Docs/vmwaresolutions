---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Proceso de eliminación de Zerto on IBM Cloud

El proceso de eliminación del servicio Zerto on {{site.data.keyword.cloud}} es automático. Se llevan a cabo los siguientes pasos para eliminar correctamente el servicio Zerto on {{site.data.keyword.cloud_notm}}.

## Cómo eliminar Zerto on IBM Cloud

1. Pulse **Instancias desplegadas** en el panel de navegación izquierdo y luego pulse la instancia desde la que desea eliminar el servicio.
2. Pulse el separador **Servicios**.
3. En el separador **Servicios instalados**, pulse el icono de menú de desbordamiento de la parte superior derecha de la tarjeta del servicio y pulse **Eliminar servicio**.
4. En la ventana **Eliminar servicio**, revise las consideraciones o avisos si hay alguno. Pulse **Lo entiendo**.
5. Una vez aceptada su solicitud de eliminación del servicio, el estado del servicio pasa a ser **Eliminando** y se llevan a cabo los siguientes pasos:   
   1. Se eliminan los dispositivos de réplica virtual de Zerto desplegados en todos los servidores ESXi.
   2. Se desinstala el servicio de réplica virtual de Zerto.
   3. Se suprime la VSI (instancia de servicio virtual) de Windows en la que estaba instalado el servicio de réplica virtual de Zerto.
   4. Se devuelve la subred privada portátil que se había solicitado para la comunicación del servicio de réplica virtual de Zerto con la infraestructura de {{site.data.keyword.cloud_notm}}.   
   5. Se eliminan de la factura de {{site.data.keyword.cloud_notm}} los cargos por el servicio de recuperación tras desastre de Zerto.

      **Nota**: se le facturará por el servicio de recuperación tras desastre de Zerto eliminado hasta el final del ciclo de facturación.

## Resultados

Después de que el servicio se elimine correctamente, se le notificará por correo electrónico y la entrada del servicio se suprimirá del separador **Servicios instalados**.

### Enlaces relacionados

* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Instancias de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Instancias de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
