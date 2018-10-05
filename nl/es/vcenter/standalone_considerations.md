---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# Consideraciones para las instancias locales de VMware HCX on IBM Cloud

Revise las siguientes consideraciones antes de instalar o suprimir las instancias locales de HCX on {{site.data.keyword.cloud}} que ha solicitado para su uso local.

**Nota:** Una instancia de vCenter Server con HCX on {{site.data.keyword.cloud_notm}} está limitada a tres conexiones simultáneas de sitios locales.

## Consideraciones al instalar instancias locales de HCX on IBM Cloud

Los componentes de HCX on {{site.data.keyword.cloud_notm}} deben estar instalados en {{site.data.keyword.cloud_notm}} y en el entorno local de vSphere. Se recomienda instalar el servicio HCX on {{site.data.keyword.cloud_notm}} en la instancia de vCenter Server con el paquete híbrido (Hybridity) en {{site.data.keyword.cloud_notm}} antes de instalar la instancia local de HCX on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Consideraciones sobre HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Requisitos sobre direcciones IP

Para obtener todas las funciones de HCX, necesita al menos cinco direcciones IP privadas y debe otorgarles acceso a Internet.

### Proceso de despliegue de instancias locales de HCX on IBM Cloud

Debe completar las tareas siguientes para realizar una instalación correcta de la instancia local de HCX on {{site.data.keyword.cloud_notm}}:
1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, solicite la instancia local de HCX on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Solicitud de instancias locales de VMware HCX on IBM Cloud](standalone_orderingserviceinstances.html).
2. En la **consola de HCX Cloud**, siga estos pasos:
    1. Pulse el separador **Administración**.
    2. En el separador **Actualizaciones del sistema**, pulse **SOLICITAR ENLACE DE DESCARGA**.
    3. Pulse **COPIAR ENLACE** y utilice este enlace para descargar el cliente de HCX Enterprise en un entorno local con acceso a su entorno local de vSphere.
3. En el cliente web de VMware vSphere, despliegue el cliente de HCX Enterprise como dispositivo virtual de HCX Manager (HCX Manager) en el entorno local.

   **Nota**: debe desplegar el HCX Manager local en una red privada y debe otorgarle acceso a la red pública. Puede utilizar NSX Edge, Vyatta o pasarelas similares para permitir el acceso Internet al HCX Manager local. Si las pasarelas utilizadas para el acceso a la red privada y a la red pública son distintas, se recomienda utilizar la pasarela predeterminada para permitir el acceso a la red pública y a la **consola de administración de HCX Manager** privada para crear una ruta estática para el acceso a la red privada.
4. Una vez completado el despliegue de Manager HCX, utilice la **consola de administración de HCX Manager** para activar el HCX Manager local. Para obtener una clave de activación para el HCX Manager local, solicite una instancia de HCX on {{site.data.keyword.cloud_notm}} local en la consola de {{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte [Solicitud de instancias locales de HCX](../services/standalone_orderingserviceinstances.html).
5. Si ha utilizado un certificado SSL autofirmado al solicitar el servicio HCX on {{site.data.keyword.cloud_notm}}, debe importar el certificado en el HCX Manager local siguiendo los siguientes pasos:
    1. En la **consola de administración de HCX Manager** local, pulse el separador **Administración**.
    2. En el panel de navegación de la izquierda, pulse **Certificado de CA de confianza** y luego pulse **IMPORTAR** a la derecha.
    3. Pulse **URL** y escriba el URL del certificado que desea aplicar, es decir, la **IP de HCX Cloud** (``https://<cloud-side public IP>``), que encontrará en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
    4. Pulse **APLICAR**.

Ahora ha completado la configuración básica del HCX Manager local. Puede continuar con el emparejamiento del sitio local de HCX on {{site.data.keyword.cloud_notm}} con el sitio de HCX de la nube.

Para obtener más información, consulte [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Consideraciones para suprimir instancias de locales de HCX on IBM Cloud

Revise las siguientes consideraciones antes de suprimir una instancia de HCX on {{site.data.keyword.cloud_notm}} solicitada para su uso local:
1. En el cliente web de VMware vSphere, vaya a la interfaz de usuario HCX y compruebe los siguientes elementos:
    1. Asegúrese de que no se esté ejecutando ninguna operación de migración de HCX ni de recuperación tras desastre.
    2. Asegúrese de que se hayan eliminado todas las redes ampliadas.
    3. Asegúrese de que se hayan eliminado todos los componentes de interconexión con sitios de nube emparejados.

   **Importante**: Debe realizar todas las consideraciones anteriores antes de continuar con el siguiente paso. De lo contrario, la licencia de la instancia local de HCX on {{site.data.keyword.cloud_notm}} se cancela, por lo que no se pueden realizar migraciones y pueden producirse errores en los componentes de HCX.  
2. En la consola de {{site.data.keyword.vmwaresolutions_short}}, suprima la instancia local de HCX on {{site.data.keyword.cloud_notm}} que se ha solicitado para obtener la clave de activación para el HCX Manager local. Asegúrese de que la instancia suprimida deja de estar disponible en la consola antes de continuar con el siguiente paso.

   Para obtener más información, consulte [Supresión de instancias locales de HCX on {{site.data.keyword.cloud_notm}}](../services/standalone_deletingserviceinstances.html).
3. En el cliente web de VMware vSphere, suprima el HCX Manager local.

### Enlaces relacionados

* [Visualización de instancias locales de HCX on {{site.data.keyword.cloud_notm}}](../services/standalone_viewingserviceinstances.html)
* [Glosario de términos de HCX](hcx_glossary.html)
* [Documentación de VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
* [Guía de instalación y del usuario de VMware HCX Enterprise](https://hcx.vmware.com/content/docs/vmware-hcx-enterprise-install-guide.pdf){:new_window}
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
