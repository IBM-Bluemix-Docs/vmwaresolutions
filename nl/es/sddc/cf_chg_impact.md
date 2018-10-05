---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# Consideraciones sobre el cambio de artefactos de Cloud Foundation

El cambio de usuarios, recursos o subredes reservados para {{site.data.keyword.vmwaresolutions_full}} puede afectar a las operaciones de gestión de las instancias de VMware Cloud Foundation.

**Importante:** No cambie los permisos globales del grupo **ic4v-vCenter** en la página **Usuarios y grupos** en el cliente web de VMware vSphere. Los ejemplos siguientes son cambios de permiso global: cambiar el nombre de usuario, suprimir el usuario o cambiar su contraseña.

## Cuentas de usuario específicas de servicio

Cada servicio crea una cuenta de usuario interna en vCenter Server. Esta cuenta es necesaria para que las operaciones de gestión que están asociadas a un servicio se puedan conectar con vCenter Server para realizar las operaciones en el servicio.

**Importante**: Para evitar interrupciones y problemas de conexión, si cambia el ID de usuario, la contraseña o los valores de caducidad de contraseña de esta cuenta de usuario, asegúrese de actualizar también la información en el servicio asociado.

El ID de usuario de esta cuenta está en el formato `<service_name>-<truncated service_uuid>@test.local` o `<service_name>-<truncated service_uuid>@example-domain.local`. Por ejemplo, el ID de usuario que utiliza el servicio Veeam on {{site.data.keyword.cloud_notm}} para conectarse a vCenter Server para realizar copias de seguridad planificadas es `Veeam-<Veeam_uuid>@test.local`.

**Nota**: `<service_name>` junto con `<service_uuid>` se trunca a 20 caracteres.

## Recursos de VMware correspondientes a instancias de Cloud Foundation

En la tabla siguiente se muestran las operaciones que podrían verse afectadas si cambia los recursos de VMware fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}. Si se dispone de una solución de recuperación, también se muestra.

Tabla 1. Operaciones que se ven afectadas para el administrador de SSO (cliente)

| Cambio intentado  | Operaciones afectadas  | Gravedad  | Método recuperación  |
|:------------- |:------------- |:--------------|:--------------|
| Cambiar el nombre del centro de datos virtual de VMware. | La adición de un centro de datos de VMware puede fallar porque el nuevo servidor ESXi no se puede unir al centro de datos modificado. | Importante | Vuelva a cambiar el nombre del centro de datos virtual de VMware por el nombre original. |
| Cambiar cualquier nombre de grupo de puertos.    | La adición de un servidor ESXi puede fallar. | Importante | Vuelva a cambiar el nombre del grupo de puertos por el nombre original. |
| Cambiar el nombre de clúster. | La adición de un servidor ESXi puede fallar. | Importante | Vuelva a cambiar el nombre del clúster por el nombre original.
| Cambiar el nombre del conmutador virtual distribuido (DVS) público o privado. | La adición de un servidor ESXi puede fallar. | Importante | Vuelva a cambiar el nombre del DVS por el nombre original.
| Cambie el nombre del almacén de datos de VSAN. | La adición de un servidor ESXi puede fallar.<br><br>La actualización de la instancia puede fallar. | Importante | Vuelva a cambiar el nombre del almacén de datos de VSAN por el nombre original, **vsanDatastore**.
| Cambiar el nombre de la instancia o el nombre del dominio. | La instancia no se puede utilizar. | Crítico | N/D

## Gestión de subredes correspondientes a instancias de Cloud Foundation

En la siguiente información se describen las subredes solicitadas por {{site.data.keyword.vmwaresolutions_short}} y se muestran opciones para que pueda solicitar subredes adicionales para su propio uso.

**ATENCIÓN**: no utilice estos componentes para otros fines o la estabilidad del entorno se verá seriamente comprometida.

Con cada pedido de servidor nativo de {{site.data.keyword.cloud_notm}}, se solicitan de forma predeterminada los siguientes rangos de direcciones IP:

*  Un rango público primario de 32 direcciones IP
*  Un rango privado primario de 64 direcciones IP

Además, las siguientes subredes de gestión también están reservadas para {{site.data.keyword.vmwaresolutions_short}}:

*  Dos subredes privadas portátiles de 64 direcciones IP en la primera VLAN: uno para la gestión y la otra para VTEPS.
*  Dos subredes privadas portátiles de 64 direcciones IP en la segunda VLAN: uno para vMotion y una para vSAN.
*  Una subred pública portátil de 16 direcciones IP en la VLAN pública.

Si necesita utilizar más subredes, puede obtener las direcciones IP que puede utilizar de una de las siguientes formas:

* **Opción 1 (recomendada)**: utilice superposiciones de red virtual VMware NSX. Se proporciona una plantilla de VXLAN de muestra cuando se realiza el pedido. Esta plantilla de VXLAN se puede utilizar como punto de partida para crear SDN.
* **Opción 2**: solicite sus propias redes públicas o privadas portátiles para obtener direcciones IP. Para distinguir las subredes que solicita de las subredes de gestión, puede añadir notas a todas las subredes que solicite.
