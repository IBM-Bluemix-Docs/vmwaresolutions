---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Gestión de Zerto on IBM Cloud

Después de desplegar el servicio Zerto on {{site.data.keyword.cloud}} en la instancia, puede configurar o actualizar el servicio de réplica virtual de Zerto y desplegar más dispositivos de réplica virtuales en los servidores ESXi recién añadidos.

## Utilización de su propio certificado para Zerto

Como práctica recomendada, debe utilizar su propio certificado SSL para Zerto Virtual Manager (ZVM). Después de desplegar Zerto on {{site.data.keyword.cloud_notm}}, sustituya el certificado SSL para ZVM por su propio certificado siguiendo las instrucciones de [Cómo utilizar un certificado SSL CER para sustituir el certificado autofirmado para ZVM, ZSSP o ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Gestión de la configuración de réplicas Zerto

Para gestionar la configuración de las réplicas Zerto (como volver a emparejar instancias de Zerto o configurar grupos de protección virtual para crear réplicas de máquinas virtuales), inicie una sesión en la consola del servicio de réplica virtual de Zerto utilizando las credenciales de vCenter con permisos de administrador.

Si está realizando réplicas entre distintas instancias de {{site.data.keyword.cloud_notm}} Zerto, puede configurar la réplica directamente entre las instancias de Zerto. Si está realizando réplicas entre la instancia de {{site.data.keyword.cloud_notm}} Zerto y su propio centro de datos, debe instalar Zerto en su propio centro de datos. Esta instancia de Zerto que se instala en su propio centro de datos puede obtener una licencia para sí misma automáticamente cuando la empareje con la instancia de {{site.data.keyword.cloud_notm}} Zerto.

Dado que el servicio de réplica de Zerto no da soporte a Network Address Translation (NAT) transversal, es posible que para establecer conectividad entre la instancia de {{site.data.keyword.cloud_notm}} Zerto y su propio centro de datos haya que personalizar las rutas en los dispositivos de Virtual Manager Zerto (ZVM) o en los dispositivos de réplica virtual (VRA) de Zerto en ambos extremos y que haya que establecer un túnel entre los sitios. Cuando configure o reconfigure rutas en dispositivos ZVM, debe asegurarse de que todos los dispositivos ZVM pueden conectarse correctamente a `zerto.com` para crear informes de uso. Para verificar esta conexión, abra una sesión del navegador en `https://www.zerto.com` desde el dispositivo ZVM.

**Nota**: la pasarela Management VMware NSX Edge Services Gateway (ESG) de las instancias de Cloud Foundation y de las instancias de vCenter Server on {{site.data.keyword.cloud_notm}} viene preconfigurada de modo que permite las comunicaciones HTTPS (puerto TCP 443) de salida que se originan en ZVM.

## Actualización de la réplica virtual de Zerto

Para actualizar la réplica virtual de Zerto, inicie una sesión en la consola del servicio de réplica virtual de Zerto.

## Despliegue de VRA en servidores ESXi recién añadidos

Cuando añade o elimina servidores ESXi para el clúster primario de la instancia, los VRA se despliegan o se eliminan automáticamente. Los VRA no se despliegan automáticamente en los servidores ESXi de los clústeres secundarios de la instancia, pero los puede desplegar desde la consola del servicio de réplica virtual de Zerto.

### Enlaces relacionados

* [Visión general de Zerto on {{site.data.keyword.cloud_notm}}](addingzertodr.html)
* [Solicitud de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Recuperación tras desastre de Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explicación de las alertas del servicio de réplica virtual de Zerto](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
