---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Solicitud de F5 on IBM Cloud

Puede solicitar el servicio de F5 on {{site.data.keyword.cloud}} al pedir una instancia nueva incluida con BIG-IP Virtual Edition (VE) o añadiendo BIG-IP VE a la instancia existente.

## Solicitud de F5 on IBM Cloud para una nueva instancia

Puede solicitar una nueva instancia con F5 on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **F5 on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **F5 on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de F5 on IBM Cloud para una instancia existente

Puede añadir el servicio de F5 on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **F5 on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Configuración del servicio de F5 on IBM Cloud

Al solicitar el servicio, proporcione los valores siguientes:

### Nombre

Especifique el nombre de servicio.

### Modelo de licencia

El modelo de licencia del servicio F5 on {{site.data.keyword.cloud_notm}} ofrece las siguientes opciones:
<dl class="dl">
        <dt class="dt dlterm">Good</dt>
        <dd class="dd">Esta oferta aprovecha BIG-IP Local Traffic Manager™ (LTM) VE, que funciona como arquitectura completa de proxy, para ofrecer una gestión inteligente del tráfico local, visibilidad completa del tráfico SSL y analíticas y supervisión de estado para garantizar que los servidores de aplicaciones siempre están disponibles para sus usuarios.</dd>
        <dt class="dt dlterm">Better</dt>
        <dd class="dd">Esta oferta se basa en las ventajas de la opción **Good**, con la adición de los módulos BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM) y BIG-IP Application Acceleration Manager™ (AAM). Ofrece servicios de gestión global del tráfico, optimización del rendimiento de las aplicaciones y funciones avanzadas de cortafuegos de red y de mitigación de denegación de servicio distribuida (DDoS).</dd>
        <dt class="dt dlterm">Best</dt>
        <dd class="dd">Además de las ofertas **Good** y **Better**, BIG-IP Application Security Manager™ (ASM) ofrece una completa protección de las aplicaciones frente a las 10 principales amenazas de L7 DDoS, Open Web Application Security Project (OWASP) y a las vulnerabilidades más comunes de las aplicaciones. BIG-IP Access Policy Manager™ (APM) ofrece a los usuarios acceso seguro y simplificado a las aplicaciones situadas en cualquier punto del entorno de nube e incorpora funciones como SSO (inicio de sesión único) y MFA (Multi-Factor Authentication).</dd>
</dl>

**Importante**: No puede cambiar el modelo de licencia después de la instalación del servicio. Para cambiar el modelo de licencia, debe eliminar el servicio existente y reinstalar el servicio utilizando otro modelo de licencia.

### Ancho de banda máximo

Especifique el rendimiento máximo del dispositivo F5 BIG–IP.

### Enlaces relacionados

* [Visión general de F5 on {{site.data.keyword.cloud_notm}}](f5_considerations.html)
* [Gestión de F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Guías de despliegue de F5](https://f5.com/solutions/deployment-guides){:new_window}
