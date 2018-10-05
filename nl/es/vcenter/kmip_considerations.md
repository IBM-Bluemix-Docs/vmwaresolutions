---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Visión general de KMIP for VMware on IBM Cloud

El servicio KMIP for VMware on {{site.data.keyword.cloud}} ofrece un servicio altamente disponible de tipo 24x7 para gestionar las claves de cifrado que utiliza VMware en {{site.data.keyword.cloud_notm}}. Este servicio ofrece capacidad de tiempo de ejecución que permite a los clientes crear, recuperar, activar, revocar y destruir las claves de cifrado. También proporciona capacidad de gestión para mantener las asociaciones entre las credenciales del cliente y las claves de cifrado.

**Disponibilidad**: Este servicio solo está disponible para instancias desplegadas en V2.2 o releases posteriores.

## Especificaciones técnicas para KMIP for VMware on IBM Cloud

Las siguientes especificaciones se incluyen con el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* Un protocolo Key Management Interoperability (KMIP) compatible con VMware
* Un servicio gestionado
* Disponible en múltiples regiones geográficas de todo el mundo
* Un punto final de servicio KMIP altamente disponible en cada región

## Consideraciones al instalar KMIP for VMware on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} utiliza el servicio IBM Key Protect para {{site.data.keyword.cloud_notm}} para crear, cifrar y descifrar claves de cifrado. Por lo tanto, antes de instalar KMIP para VMware en {{site.data.keyword.cloud_notm}}, asegúrese de que:
* Ha solicitado un servicio utilizable de Key Protect.
* Se ha creado un ID de servicio de {{site.data.keyword.cloud_notm}} siguiendo los pasos indicados en [Creación de un ID de servicio](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id). Este ID de servicio se utiliza para acceder a la instancia del servicio Key Protect que ha creado.
* Ha otorgado los siguientes niveles de acceso al ID de servicio:
   * A nivel de acceso a la plataforma: autorización de visualización a la instancia de IBM Key Protect.
   * A nivel de acceso al servicio: autorización de escritura a la de IBM Key Protect.
* Tiene una clave de API para el ID de servicio creado. La clave es necesaria al solicitar el servicio.
* Ha creado al menos una clave raíz de cliente (CRK) desde la interfaz de usuario de Key Protect siguiendo los pasos del apartado [Creación de claves raíz](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) o utilizando la API REST de [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect).

   **Importante**: No puede solicitar el servicio sin CRK. Se recomienda utilizar el método para crear una CRK utilizando el material de claves existente y hacer una copia de seguridad del material de claves que se crea. De este modo se asegura de que puede recuperar sus claves en el caso de que se produzca un fallo del centro de datos en el que se aplica IBM Key Protect para almacenar los CRK.

## Consideraciones sobre la utilización de KMIP for VMware on IBM Cloud

* Para utilizar un servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} solicitado como Servidor de gestión de claves (KMS) registrado ante VMware vCenter Server, asegúrese de que la conectividad de red entre vCenter Server y el punto final del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} solicitado resulte funcional.
* Para utilizar el servicio para el cifrado de VMware vSAN, asegúrese de que la conectividad de red entre los hosts del vSAN de destino y el punto final del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} resulte funcional.

## Consideraciones al eliminar KMIP for VMware on IBM Cloud

El certificado público de VMware que proporcione durante la solicitud o la utilización del servicio se utiliza como certificado cliente para comunicarse con la instancia de servicio. Cuando se elimina el servicio, también se eliminan todas las claves de cifrado creadas por esta instancia de servicio para el certificado público asociado de VMware.

Por lo tanto, antes de eliminar el servicio, asegúrese de que no se cifre ninguna máquina virtual ni vSAN mediante las claves creadas por el servicio KMIP.

### Enlaces relacionados

* [Solicitud de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_ordering.html)
* [IBM Key Protect para {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [Seguridad de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
