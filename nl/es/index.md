---

copyright:

  years: 2016, 2018

lastupdated: "2018-09-07"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Iniciación IBM Cloud for VMware Solutions

En esta guía de aprendizaje de inicio, le guiamos a través del proceso de pedido de una instancia y algunos servicios adicionales para el mismo.
{:shortdesc}

## Antes de empezar
{: #prereqs}

Antes de empezar a trabajar con {{site.data.keyword.vmwaresolutions_full}}, revise la siguiente información importante sobre los requisitos del navegador, las cuentas de usuario, las opciones de despliegue y los servicios de complemento.

### Requisitos del navegador

Se admiten los siguientes navegadores:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

**Nota**: no se admite Microsoft Internet Explorer.

Para ver y trabajar mejor con la consola de {{site.data.keyword.vmwaresolutions_short}}, defina una resolución de pantalla de al menos 1024 px de anchura por 500 px de altura.

### Cuentas de usuario

Necesita una cuenta de {{site.data.keyword.cloud_notm}} y una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer). Estas cuentas deben cumplir ciertos requisitos.

   Tabla 1. Cuentas de usuario necesarias
   <table>
   <tr>
      <th>Cuenta</th>
      <th>Descripción</th>
   </tr>
   <tr>
      <td>IBMid</td>
      <td>Al utilizar el **IBMid**, puede tener un único nombre de usuario de inicio de sesión para todos los productos y servicios de IBM que utilice, incluido {{site.data.keyword.cloud_notm}}. {{site.data.keyword.vmwaresolutions_short}} se proporciona como una solución de infraestructura en el catálogo de {{site.data.keyword.cloud_notm}}. Para acceder a la consola de {{site.data.keyword.vmwaresolutions_short}}, debe tener un **IBMid**.<br><br>Para utilizar **IBMid** para iniciar sesión en la consola de {{site.data.keyword.vmwaresolutions_short}}, debe asociar el **IBMid** con una cuenta de {{site.data.keyword.cloud_notm}}. Cuando inicie una sesión en la consola por primera vez, se le indicará que asocie su **IBMid** existente con una cuenta de {{site.data.keyword.cloud_notm}} o que se registre para conseguir una nueva cuenta de {{site.data.keyword.cloud_notm}}. La nueva cuenta de {{site.data.keyword.cloud_notm}} se asociará automáticamente con el **IBMid**. Debe pasar por este proceso una sola vez.<br><br>Si tiene problemas para asociar su **IBMid** con una cuenta de {{site.data.keyword.cloud_notm}}, consulte [Resolución de problemas para acceder a {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html).</td>
   </tr>
   <tr>
      <td>Cuenta de IBM Cloud</td>
      <td>Para solicitar y utilizar servicios de {{site.data.keyword.cloud_notm}}, se necesita una cuenta de {{site.data.keyword.cloud_notm}}. La información de facturación está asociada a la cuenta de {{site.data.keyword.cloud_notm}}. El coste de la infraestructura física y virtual y las licencias resultantes se cargarán a su cuenta de {{site.data.keyword.cloud_notm}}.</td>
   </tr>
   <tr>
      <td>Cuenta de infraestructura de IBM Cloud (SoftLayer)</td>
      <td>La cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) se conocía anteriormente como la cuenta de IBM SoftLayer.  Para obtener más información sobre los requisitos que debe cumplir la cuenta, consulte [Requisitos de la cuenta de infraestructura de {{site.data.keyword.cloud_notm}}](vmonic/slaccountrequirement.html).<br><br>Puede enlazar las cuentas de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) con las cuentas de {{site.data.keyword.cloud_notm}} para utilizar la infraestructura combinada como servicio (IaaS) y los recursos de la plataforma como servicio (PaaS). A continuación, puede acceder a los recursos de IaaS y a los recursos de PaaS desde un solo inicio de sesión. El enlace de las cuentas también le proporciona una sola factura para todos los recursos de PaaS e IaaS que utiliza.<ul><li>Si no tiene una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer), solicite una siguiendo el procedimiento de [Inicio de sesión para una cuenta de infraestructura de IBM Cloud (SoftLayer)](vmonic/signing_softlayer_account.html) y, a continuación, enlace la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) con la cuenta de {{site.data.keyword.cloud_notm}} siguiendo el procedimiento de [Enlace de cuentas de IBMid](https://console.bluemix.net/docs/account/softlayerlink.html).</li><li>Si tiene una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer), puede enlazarla con la cuenta de {{site.data.keyword.cloud_notm}} siguiendo el procedimiento de [Enlace de cuentas de IBMid](https://console.bluemix.net/docs/account/softlayerlink.html).</li></ul></td>
   </tr>
   </table>

Para obtener más información, consulte los temas siguientes:
* [Registro de cuentas necesarias](vmonic/signing_softlayer_account.html)
* [Requisitos para la cuenta de infraestructura de {{site.data.keyword.cloud_notm}}](vmonic/slaccountrequirement.html)

### Ofertas de despliegue

Revise y elija la oferta de despliegue.

  Tabla 2. Ofertas de despliegue
  <table>
    <tr>
       <th>Oferta de despliegue</th>
       <th>Descripción</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](vcenter/vc_vcenterserveroverview.html)</td>
       <td>Con la oferta de vCenter Server, puede desplegar un entorno virtual de VMware utilizando recursos de cálculo, almacenamiento y red personalizados para que se adapten mejor a sus necesidades empresariales.</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud con el paquete híbrido (Hybridity)](vcenter/vc_hybrid_overview.html)</td>
       <td>La oferta de vCenter Server con el paquete híbrido (Hybridity) es una nube privada alojada que permite ampliar la infraestructura local a la nube de forma rápida y sencilla. El entorno VMware se basa en licencias de centro de datos definido por software de VMware proporcionadas por IBM e incluye VMware Hybrid Cloud Extension (HCX). Mediante el uso de HCX, puede conectarse de forma segura a un entorno vSphere 5.0+ local con sitios de {{site.data.keyword.cloud_notm}} para ofrecer una infraestructura híbrida y una auténtica movilidad de aplicaciones.</td>
    </tr>
    <tr>
       <td>[VMware Cloud Foundation on IBM Cloud](sddc/sd_cloudfoundationoverview.html)</td>
       <td>La oferta Cloud Foundation proporciona un entorno virtual VMware unificado mediante el uso de recursos estándares de cálculo, almacenamiento y red de {{site.data.keyword.cloud_notm}} que están dedicados al despliegue de cada usuario.</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](vsphere/vs_vsphereclusteroverview.html)</td>
       <td>La oferta de vSphere on {{site.data.keyword.cloud_notm}} proporciona un servicio de virtualización personalizable que combina {{site.data.keyword.baremetal_short}} compatibles con VMware, componentes de hardware y licencias para crear su propio entorno VMware alojado por IBM.</td>
    </tr>
    <tr>
       <td>[NetApp ONTAP Select](netapp/np_netappoverview.html)</td>
       <td>La oferta NetApp ONTAP Select le permite desplegar un clúster de almacenamiento definido por software que se ajusta a sus necesidades de un dispositivo de almacenamiento dedicado y altamente disponible basado en NetApp ONTAP Select.</td>
    </tr>
    <tr>
       <td>[VMware Federal on IBM Cloud](vcenter/vc_fed_overview.html)</td>
       <td>La oferta VMware Federal on {{site.data.keyword.cloud_notm}} ofrece soporte para solicitar una instancia de base vCenter Server además de ofrecer la opción de proteger las instancias desplegadas eliminando la información confidencial y la conexión de gestión abierta para el acceso continuado a la instancia para las funciones de gestión.</td>
    </tr>
  </table>

### Servicios complementarios

Revise y elija los servicios de complemento para la oferta de despliegue.

  Tabla 3. Servicios de complementos disponibles para las ofertas de despliegue
  <table>
    <tr>
       <th>Nombre de servicio</th>
       <th>Descripción</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](services/f5_considerations.html)</td>
       <td>El servicio F5 on {{site.data.keyword.cloud_notm}} (F5 BIG-IP® Virtual Edition) proporciona servicios de equilibrio inteligente de carga L4-L7 y de gestión del tráfico a escala local y global, potentes funciones de protección de red y de cortafuegos de aplicaciones web y acceso seguro y federado a las aplicaciones.</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](services/fsa_considerations.html)</td>
       <td>El servicio de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} despliega un par de dispositivos de seguridad FortiGate (FSA) serie 300 en modalidad altamente disponible para ofrecer servicios de cortafuegos, direccionamiento, NAT y VPN para proteger todos los servidores y máquinas virtuales de la VLAN pública de sus instancias.</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](services/fortinetvm_considerations.html)</td>
       <td>El servicio de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} despliega un par de FortiGate Virtual Appliances en el entorno, lo que puede ayudar a reducir el riesgo implementando los controles de seguridad importantes dentro de la infraestructura virtual.</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](services/htcc_considerations.html)</td>
       <td>El servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} aplica y controla el cumplimiento de las normas de seguridad y proporciona funciones detalladas de control de acceso basado en roles (RBAC), aprobación y auditoría. Cuando se combina con HyTrust DataControl, el servicio puede asegurarse de que los datos de las cargas de trabajo y las máquinas virtuales no abandonen una región, un clúster o un servidor ESXi determinados en el {{site.data.keyword.CloudDataCent_notm}}.</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](services/htdc_considerations.html)</td>
       <td>El servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}} ofrece un cifrado de alta seguridad con claves de gestión integrada para proteger las cargas de trabajo en todo su ciclo de vida. El servicio puede proporcionar cifrado tanto a nivel de sistema operativo como a nivel de datos, lo que significa que se puede cifrar y descifrar cualquier directorio, carpeta o archivo de una carga de trabajo.</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](services/htkc_considerations.html)</td>
       <td>El servicio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} simplifica la gestión de las cargas de trabajo cifradas automatizando y simplificando el ciclo de vida de las claves de cifrado. El servicio puede gestionar fácilmente las claves de cifrado a escala utilizando el cifrado compatible con FIPS 140-2.</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](services/managing_icp.html)</td>
       <td>{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware y {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}.</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](services/spp_considerations.html)</td>
       <td>El servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementar el servicio como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect para descargar copias para su almacenamiento y gestión de datos a largo plazo.</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](services/kmip_considerations.html)</td>
       <td>El servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} ofrece un servicio altamente disponible para gestionar las claves de cifrado que utiliza VMware en {{site.data.keyword.cloud_notm}}. Este servicio ofrece capacidad de tiempo de ejecución que permite a los clientes crear, recuperar, activar, revocar y destruir las claves de cifrado. También proporciona capacidad de gestión para mantener las asociaciones entre las credenciales del cliente y las claves de cifrado.</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](services/veeam_considerations.html)</td>
       <td>El servicio Veeam on {{site.data.keyword.cloud_notm}} se puede integrar de forma fácil y directa con sus hipervisores VMware para ayudar a la empresa a alcanzar un alto grado de disponibilidad. Este servicio puede proporcionar objetivos de puntos de recuperación y de tiempo para sus datos y aplicaciones. Los objetivos de puntos de recuperación y de tiempo se pueden proporcionar menos de 15 minutos después de finalizar la configuración. Con este servicio, puede controlar directamente las copias de seguridad y las operaciones de restauración de todas las máquinas virtuales de la infraestructura desde la consola de Veeam.</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](services/hcx_considerations.html)</td>
       <td>El servicio HCX on {{site.data.keyword.cloud_notm}} permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} y al mismo sin realizar ninguna conversión ni cambio.</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](services/addingzertodr.html)</td>
       <td>El servicio Zerto on {{site.data.keyword.cloud_notm}} ofrece funciones de réplica y de recuperación tras desastre, que se pueden integrar en las ofertas de despliegue para proteger y recuperar los datos del entorno virtual VMware en {{site.data.keyword.cloud_notm}}.</td>
    </tr>
   </table>

## Paso 1: Acceso a la consola de IBM Cloud for VMware Solutions

La consola de {{site.data.keyword.vmwaresolutions_short}} es la interfaz con la que solicita y gestiona sus despliegues. Cada despliegue se gestiona como una instancia en la consola. La consola es una interfaz de usuario autónoma, independiente del portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}}.

Para acceder a la consola de {{site.data.keyword.vmwaresolutions_short}}:
1. Vaya a https://console.ng.bluemix.net/infrastructure/vmware-solutions/console.
2. Inicie sesión en la consola con su **IBMid**.

## Paso 2: Configuración de la cuenta de usuario y valores

Antes de solicitar una instancia, debe escribir el nombre de usuario y la clave de API de la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) en la página **Valores** de la consola.

Para obtener información sobre cómo configurar la cuenta de usuario y los valores, consulte [Gestión de cuentas de usuario y valores](vmonic/useraccount.html).

## Paso 3: Solicitud de una instancia

Una vez que haya decidido una oferta de despliegue, que se gestiona como una instancia en la consola, inicie el proceso de solicitud.

Para obtener información sobre cómo solicitar una instancia, consulte los temas siguientes en función de la selección de la oferta de despliegue:
* [Pedido de instancias de vCenter Server](vcenter/vc_orderinginstance.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](vcenter/vc_hybrid_orderinginstance.html)
* [Pedido de instancias de Cloud Foundation](sddc/sd_orderinginstance.html)
* [Solicitud de clústeres nuevos de vSphere](vsphere/vs_orderinginstances.html)
* [Solicitud de instancias de NetApp ONTAP Select](netapp/np_orderinginstances.html)  
* [Solicitud de instancias de VMware Federal](vcenter/vc_fed_orderinginstance.html)

## Paso 4: Visualización de la instancia

Después de colocar un pedido de instancia en el **Paso 3**, el despliegue de la instancia se inicia automáticamente. Puede realizar un seguimiento del estado del despliegue visualizando los detalles de la instancia. Cuando haya finalizado el despliegue de la instancia, puede ver el resumen y la información detallada de la instancia y sus servicios de complemento también en la página de detalles de la instancia.

Para obtener información sobre cómo ver la instancia que ha solicitado, consulte los temas siguientes:
* [Visualización de instancias de vCenter Server](vcenter/vc_viewinginstances.html)
* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](vcenter/vc_hybrid_viewinginstances.html)
* [Visualización de instancias de Cloud Foundation](sddc/sd_viewinginstances.html)
* [Visualización de instancias de NetApp ONTAP Select](netapp/np_viewinginstances.html)
* [Visualización de instancias de VMware Federal](vcenter/vc_fed_viewinginstance.html)

## Paso 5: Gestión de servicios de complemento para la instancia

Si ha solicitado servicios de complemento para su instancia, puede gestionar los servicios también.

Para obtener información sobre cómo gestionar los servicios, consulte los temas siguientes:
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](vcenter/vc_hybrid_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](sddc/sd_addingremovingservices.html)

## Paso siguiente

Gestione la instancia desde la consola de {{site.data.keyword.vmwaresolutions_short}} o desde el cliente web de VMware vSphere.
