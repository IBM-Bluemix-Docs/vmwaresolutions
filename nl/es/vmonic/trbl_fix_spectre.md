---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Soluciones para las vulnerabilidades Spectre y Meltdown

Para solucionar las vulnerabilidades Spectre y Meltdown, debe aplicar varios parches en un orden específico.

## Actualización del firmware

Para obtener información más reciente sobre la actualización del firmware, consulte [Protección frente a vulnerabilidades de seguridad recientes](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Actualización de instancias desplegadas en V2.0 o posteriores

Las instancias de V2.0 o posterior se han desplegado con VMware vSphere 6.5 y VMware vCenter Server 6.5. Hay que aplicar parches a estos dos componentes de software.

### Instancias de vCenter Server desplegadas en V2.0 o posteriores

#### Para VMware vSphere 6.5

* Para todas las nuevas instancias de V2.6, vSphere se desplegará con los parches siguientes aplicados: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG y ESXi650-201808403-BG.
* Para todas las instancias existentes desplegadas antes de V2.5, pero actualizadas a V2.5, todos los nuevos clústeres y servidores ESXi se actualizarán con los parches siguientes: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG y ESXi650-201808403-BG.
* Para todos los servidores ESXi existentes, y para los clústeres o servidores ESXi que siga desplegando antes de actualizar a V2.5, debe aplicar los parches siguientes: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG y ESXi650-201808403-BG desde el [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch).

#### Para VMware vCenter Server 6.5

* Para todas las nuevas instancias de V2.6, vCenter Server se desplegará con los parches acumulativos de vCenter 6.5 U2c aplicados.
* Para todas las instancias existentes desplegadas antes de V2.6, debe aplicar el parche vCenter 6.5 U2c desde el [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch).

### Instancias de Cloud Foundation desplegadas en V2.0 o posteriores

Para aplicar los parches necesarios a VMware vSphere 6.5 y VMware vCenter Server 6.5, debe actualizar las instancias de Cloud Foundation al paquete de parches de VMware más reciente. Para todas las instancias y servidores ESXi existentes, se le solicitará que aplique los parches en la página **Actualización y parche** desde la consola de {{site.data.keyword.vmwaresolutions_full}}. Para obtener más información, consulte [Aplicación de actualizaciones a instancias de Cloud Foundation](../sddc/sd_applyingupdates.html).

### Clústeres de VMware vSphere desplegados en V2.0 o posteriores

Para todos los nuevos clústeres de VMware vSphere 6.5 y servidores ESXi, debe aplicar los siguientes parches: ESXi650-201808401-BG, ESXi650-201808402-BG y ESXi650-201808403-BG, desde el [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch).

Para todos los clústeres de VMware vSphere 6.5 existentes, debe aplicar los siguientes parches: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG y ESXi650-201808403-BG, desde el [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch).

Para VMware vCenter Server 6.5, debe aplicar el parche vCenter 6.5 U2c del [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch) a todos los servidores de vCenter, tanto a los recién desplegados como a los existentes.

## Instancias desplegadas en la V1.9 o anteriores

Las instancias de Cloud Foundation y de vCenter Server, y los clústeres de VMware vSphere de la V1.9 o anteriores, se han desplegado con VMware vSphere 6.0 y VMware vCenter Server 6.0.

### Instancias de vCenter Server desplegadas en V1.9 o anteriores

Para VMware vSphere 6.0 y para VMware vCenter Server 6.0, debe aplicar los parches (ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG y ESXi600-201808403-BG para vSphere y vCenter 6.0 U3h para vCenter Server) del [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch) a todas las instancias y servidores ESXi, tanto a los recién desplegados como a los existentes.

### Instancias de Cloud Foundation desplegadas en V1.9 o anteriores

Las actualizaciones para estas instancias estarán disponibles cuando salgan al mercado las actualizaciones necesarias de los proveedores de los que dependen estas instancias.

### Clústeres de VMware vSphere desplegados en V1.9 o anteriores

Para VMware vSphere 6.0 y para VMware vCenter Server 6.0, debe aplicar los parches (ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG y ESXi600-201808403-BG para vSphere y vCenter 6.0 U3h para vCenter Server) del [sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch) a todos los clústeres vSphere y servidores ESXi, tanto a los recién desplegados como a los existentes.

### Enlaces relacionados

* [Aplicación de actualizaciones a instancias de Cloud Foundation](../sddc/sd_applyingupdates.html)
* [Protección frente a vulnerabilidades de seguridad recientes](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Sitio de parches del producto VMware](https://my.vmware.com/group/vmware/patch)
