---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# Supresión de instancias de Cloud Foundation en una configuración de varios sitios

Antes de planificar la supresión de instancias de Cloud Foundation en una configuración de varios sitios, revise las consideraciones siguientes.

Cuando suprima una instancia de Cloud Foundation, los siguientes componentes se liberarán en esta secuencia:
1. Todos los servicios desplegados
2. Cuota de soporte y servicios
3. Licencias del producto VMware
4. Servidores ESXi
5. Subredes
6. VLAN

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y las VLAN y se completa la supresión de la instancia.

**Atención**: se le facturará por la instancia suprimida hasta el final del ciclo de facturación de {{site.data.keyword.cloud_notm}}.

## Procedimiento

1. Elimine todos los servicios desde la instancia secundaria de Cloud Foundation.
2. Asegúrese de que no tiene ningún objeto NSX ampliado en la instancia secundaria que desea suprimir.
3. Suprima el vCenter secundario y el PSC (Platform Services Controller) del dominio SSO (inicio de sesión único) primario. Para obtener más información, consulte [Eliminación del registro de vCenter Server de un inicio de sesión único](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Disminuya el nivel de la VSI (instancia de servicio virtual) del controlador de dominio local. Para obtener más información, consulte [Disminución del nivel de controladores de dominio y de dominios](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Suprima la instancia secundaria de Cloud Foundation de la consola de {{site.data.keyword.vmwaresolutions_short}}.
6. Repita los pasos 1 a 5 para todas las instancias secundarias de Cloud Foundation en una configuración de varios sitios.
7. Después de suprimir todas las instancias secundarias, también puede suprimir la instancia secundaria desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

### Enlaces relacionados

* [Supresión de instancias de Cloud Foundation](sd_deletinginstance.html)
* [Solicitud, visualización y eliminación de servicios de instancias de Cloud Foundation](sd_addingremovingservices.html)
