---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Copia de seguridad de los componentes

Usted es responsable de la configuración, la gestión y la supervisión de todos los componentes de software, incluida la copia de seguridad y la disponibilidad de la infraestructura de gestión y las cargas de trabajo.

Como parte de la solución, puede desplegar opcionalmente los servicios complementarios {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}. Veeam e IBM Spectrum Protect Plus pueden ayudar a satisfacer el requisito de realizar copia de seguridad de los componentes de gestión.

Estos servicios complementarios se despliegan junto con el almacenamiento de Resistencia de {{site.data.keyword.cloud_notm}}. Los servicios le ayudan a realizar copia de seguridad de las cargas de trabajo y de los componentes de gestión. La [Visión general de la arquitectura de IBM Spectrum Protect Plus](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} y la [Visión general de la arquitectura de Veeam](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window} proporcionan una guía útil sobre la planificación y el dimensionamiento del despliegue. También puede solicitar [servicios gestionados](https://console.bluemix.net/infrastructure/vmware-solutions/console/gettingstarted/veeam/vcs/managed) para el despliegue de Veeam.

Distintos componentes de solución requieren distintas estrategias para la copia de seguridad. Algunos componentes están protegidos mediante la copia de seguridad a nivel de imagen, y otros componentes están protegidos mediante la copia de seguridad basada en archivos para su configuración y datos.

## Servidor de archivos para copia de seguridad basada en archivos

Algunos componentes, como por ejemplo VMware vCenter Server, Platform Services Controller (PSC) y VMware NSX, requieren la copia de seguridad de su configuración en un servidor de archivos.

Para alojar estas copias de seguridad, despliegue un servidor de archivos de Linux en el clúster utilizando los pasos siguientes:

1. Solicite una subred portátil privada desde la infraestructura de {{site.data.keyword.cloud_notm}} y ubíquela en la misma VLAN que los componentes de sistema. Se trata de la VLAN privada en la que residen las direcciones IP de gestión para los hosts.
2. Suba una imagen del sistema operativo al almacén de datos de gestión de VMware, como por ejemplo [Ubuntu Server 18.04 LTS](http://mirrors.service.softlayer.com/ubuntu-releases/ubuntu-server/bionic/daily-live/current/){:new_window} desde el duplicado privado de {{site.data.keyword.cloud_notm}}.
3. Despliegue esta máquina virtual (VM) en el clúster en el grupo de puertos de gestión utilizando una dirección IP portátil privada que se ha solicitado anteriormente. Asegúrese de que la máquina virtual esté configurada para apuntar a los servidores de AD/DNS y, opcionalmente, añadir la máquina virtual al DNS del subdominio.
4. Cree un ID de usuario de copia de seguridad no root en este servidor y asegúrese de que todos los servicios necesarios estén configurados e iniciados para las transferencias de archivos. Por ejemplo, FTP o SSH.
5. Asegúrese de que esta máquina virtual esté incluida en el trabajo de copia de seguridad de gestión de Veeam o IBM Spectrum Protect Plus.

## Copia de seguridad basada en archivos de vCenter

VMware vCenter Server y PSC proporcionan una [interfaz de usuario de gestión de dispositivos y una API para exportar la base de datos y la configuración a un servidor de archivos](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window} utilizando varios protocolos. VMware documenta un ejemplo de cómo puede configurar esto para [ejecutarlo periódicamente como un trabajo cron](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window} directamente en el vCenter Server Appliance y PSC, que puede adaptar para su uso.

Debe realizar una copia de seguridad de vCenter Server Appliance y de PSC por separado utilizando esta técnica. Familiarícese con y tenga en cuenta las consideraciones y limitaciones documentadas por VMware. Además, planifique una rotación y caducidad regular de las copias de seguridad de archivos en el servidor de archivos. Tenga en cuenta que VMware requiere que la ubicación de la copia de seguridad sea una carpeta vacía, por lo que debe planificar la rotación o la automatización de la copia de seguridad para dejar la ubicación vacía para cada trabajo de copia de seguridad subsiguiente.

## Copia de seguridad basada en archivos NSX

La copia de seguridad adecuada de todos los componentes de NSX es crucial para restaurar el sistema a su estado de trabajo si se produce una anomalía. El diseño requiere que configure la copia de seguridad de NSX a través de la función de copia de seguridad del gestor de NSX. Con este fin, puede [configurar el gestor de NSX para realizar copias de seguridad de forma regular](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window} en el servidor de archivos. Asegúrese de que el servidor de archivos o sus datos estén copiados correctamente, y de garantizar la rotación de las copias de seguridad de NSX antiguas.

## Copia de seguridad basada en imágenes de máquinas virtuales de gestión

Después de haber desplegado la instancia y de haber desplegado el servicio de IBM Spectrum Protect Plus o el servicio de copia de seguridad de Veeam, configure un trabajo de copia de seguridad para las máquinas virtuales de gestión. Planifique la copia de seguridad de las máquinas virtuales siguientes con al menos 7 días de copias de seguridad diarias:

* Si está presente, VMware SDDC Manager
* Si está presente, los servidores de Active Directory
* Servidor de copia de seguridad de archivos

Planifique asignar suficientes licencias de Veeam o IBM Spectrum Protect Plus para realizar copia de seguridad de estas máquinas virtuales, y planifique al menos 2 TB de almacenamiento de copia de seguridad para las máquinas virtuales.

## Servicios complementarios

Si despliega componentes de solución de complemento en la instancia, también debe planificar la copia de seguridad de estos componentes como parte de la estrategia de copia de seguridad de gestión:

* Zerto Virtual Replication: El sistema Zerto Virtual Manager (ZVM) se despliega como una instancia de servidor virtual (VSI) de {{site.data.keyword.cloud_notm}} y su copia de seguridad no está soportada por Veeam ni IBM Spectrum Protect Plus. Si la estrategia de recuperación tras desastre requiere que recupere el ZVM sin realizar una migración tras error del sitio, debe utilizar la solución de copia de seguridad de Windows preferida para realizar una copia de seguridad y restaurar el ZVM.
* F5 BIG-IP: F5 recomienda [copia de seguridad basada en archivos de la configuración de F5](https://support.f5.com/csp/article/K13132){:new_window}, que puede dirigir al servidor de archivos.
* FortiGate Security Appliance o VM: Fortinet recomienda [copia de seguridad basada en archivos de la configuración de FortiGate](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}, que puede dirigir al servidor de archivos.
* HyTrust Cloud Control y Data Control: HyTrust soporta tanto la imagen como la copia de seguridad basada en archivos de los dispositivos del servidor HyTrust. Para obtener más información, consulte las guías de administración de HyTrust.
* VMware HCX: La interfaz de gestión de dispositivos HCX le permite crear y descargar una copia de seguridad basada en archivos de la configuración del gestor HCX similar a la de vCenter Server Appliance.

## Consideraciones adicionales

Si elige desplegar el servidor de AD/DNS como una instancia de servidor virtual (VSI) de {{site.data.keyword.cloud_notm}}, no puede respaldarlo utilizando Veeam ni IBM Spectrum Protect Plus. En este caso, utilice la solución de copia de seguridad de Windows preferida para las operaciones de copia de seguridad y de restauración, o planifique el despliegue de la instancia utilizando las VM de AD/DNS dentro del clúster de VMware, que puede realizar una copia de seguridad de Veeam o IBM Spectrum Protect Plus.

A partir de VMware vCenter 6.5u2, VMware da soporte a la copia de seguridad de la base de datos de vCenter Postgres utilizando copias de seguridad basadas en imágenes, con scripts integrados de suspensión y de reanudación para la base de datos durante la ventana de copia de seguridad para asegurar la integridad de la base de datos. Si actualiza la instancia de VMware a vCenter 6.5u2, puede elegir utilizar Veeam o IBM Spectrum Protect Plus para hacer una copia de seguridad de vCenter Server y de PSC en lugar de utilizar copias de seguridad basadas en archivos. Si lo hace, debe utilizar la característica de desactivación de Veeam o IBM Spectrum Protect Plus para garantizar la integridad de la base de datos.

## Restauración de la copia de seguridad

Hay varias consideraciones especiales al restaurar las copias de seguridad de gestión:

* Para vCenter y PSC, VMware proporciona un instalador que puede desplegar un nuevo dispositivo virtual y restaurar la configuración a partir de la copia de seguridad.
* Al restaurar un dispositivo a partir de la copia de seguridad, el instalador detecta el tipo de dispositivo (vCenter Server o PSC) en función de la información de copia de seguridad que proporcione.
* Puesto que se despliega directamente en uno de los hosts, es posible que no pueda desplegar en un conmutador o grupo de puertos distribuidos. Es posible que tenga que crear un conmutador estándar temporal y un grupo de puertos para desplegar los dispositivos recuperados y migrar uno de los vmnics temporalmente a este conmutador para proporcionar conectividad de red para las máquinas virtuales. Después del despliegue, puede migrar las máquinas virtuales al grupo de puertos distribuidos y devolver el vmnic a dvSwitch.
* Para NSX, es posible que tenga que volver a desplegar el NSX Manager y los controladores antes de restaurar la configuración a partir de la copia de seguridad.
* Asegúrese de que se familiarice con las consideraciones y limitaciones de VMware para la copia de seguridad y la restauración de vCenter.

## Resumen

Con la planificación apropiada, puede asegurarse de que la instancia de VMware puede sufrir la pérdida de sus componentes de gestión y recuperarse correctamente. Asegúrese de supervisar regularmente el éxito de los trabajos de copia de seguridad y de la disponibilidad de los datos de copia de seguridad y asegurarse de probar el plan de copia de seguridad y de restauración de forma regular, tanto para la infraestructura de gestión como para las cargas de trabajo.

### Enlaces relacionados

* [Visión general de la solución](solution_overview.html)
* [Visión general del diseño](design_overview.html)
* [Capacidad de escalado](solution_scaling.html)
