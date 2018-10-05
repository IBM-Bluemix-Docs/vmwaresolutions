---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-04"

---

# Consideraciones sobre red para instancias de Cloud Foundation

Revise la siguiente información para obtener detalles sobre las consideraciones y requisitos de red para las instancias de Cloud Foundation. Asegúrese de cumplir los requisitos para que la instancia funcione correctamente.

## Componentes de red para instancias de Cloud Foundation

Para revisar los componentes de red que se incluyen en la instancia de Cloud Foundation, consulte [Especificaciones técnicas para instancias de Cloud Foundation](sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Consideraciones sobre cortafuegos

Si utiliza cortafuegos, debe configurar reglas para todas las comunicaciones desde la Instancia de servidor virtual (VSI) de {{site.data.keyword.IBM}} CloudDriver y las máquinas virtuales (VM) de SDDC Manager. Estas reglas deben permitir que todos los protocolos se comuniquen en las direcciones IP `10.0.0.0/8` y `161.26.0.0/16`. Los ejemplos de estos cortafuegos son NSX Distributed Firewalls (DFW) o cortafuegos Vyatta.

## Utilización de VMware NSX con sus VM

Durante el despliegue de la instancia de Cloud Foundation, VMware NSX se solicita, se adquiere una licencia del mismo, se instala y se configura en la instancia. Además, se configuran NSX Manager, controladores NSX y NSX Transport Zone y cada servidor ESXi se configura con componentes de NSX.

Sin embargo, si las VM de carga de trabajo tienen que comunicarse entre sí y acceder a Internet, es su responsabilidad configurar NSX para que las utilicen las VM.

Para obtener más información sobre cómo configurar NSX, consulte los temas siguientes:
* Para una instancia primaria (única) de Cloud Foundation, consulte [Configuración de NSX para VM de carga de trabajo en VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Para una instancia de Cloud Foundation de varios sitios, consulte Conexión segura de sus cargas de trabajo privadas de VMware en {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Consideraciones al cambiar contraseñas para componentes de NSX

Revise las siguientes consideraciones antes de cambiar las contraseñas de NSX Manager, controladores NSX y NSX Edge:
* No cambie la contraseña de NSX Manager. Puede encontrar esta contraseña en la página **Resumen** de la instancia en la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Puede cambiar las contraseñas de los controladores NSX. Para ver instrucciones sobre cómo cambiar las contraseñas de los controladores NSX, consulte [Cambio de la contraseña del controlador](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* No cambie la contraseña del componente VMware NSX Edge Services Gateway (ESG) de gestión.

### Enlaces relacionados

* [Visión general de NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Gestión de reglas de NAT](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
