---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Invitación de usuarios para acceder a servicios y recursos

{{site.data.keyword.vmwaresolutions_full}} se integra con {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) para la colaboración entre varios usuarios. Después de registrarse para una cuenta de {{site.data.keyword.cloud_notm}} e iniciar sesión en la consola de {{site.data.keyword.vmwaresolutions_short}}, puede añadir usuarios a la cuenta de {{site.data.keyword.cloud_notm}}. Estos usuarios añadidos pueden compartir los servicios y recursos que se han suministrado para la cuenta.

## Antes de empezar

* Asegúrese de que es el propietario de la cuenta o de que el rol de gestión de plataforma para el servicio **Soluciones de VMware** sea **Administrador**.
* Asegúrese de que ha revisado los roles de usuario y los permisos en [Gestión del acceso de usuario con Identity and Access Management](iam.html).

## Procedimiento

1. En el lado izquierdo de la cabecera, pulse **Gestionar > Seguridad > Identidad y acceso**.
2. En la página **Usuarios**, pulse **Invitar usuarios**.
3. En la página **Invitar usuarios**, en la sección **Usuarios**, especifique las direcciones de correo electrónico de los usuarios que desea invitar en el campo **Dirección de correo electrónico**.
4. En la sección **Acceso**, expanda **Servicios** y, a continuación, complete las tareas siguientes:
   1. Seleccione **Recurso** en la lista **Asignar acceso a**.
   2. Seleccione **VMware Solutions** en la lista **Servicios**.
   3. Seleccione el rol de acceso de la plataforma que desea asignar a los usuarios. Puede ser **Administrador**, **Editor**, **Operador** o **Visor**.
5. Pulse **Invitar a usuarios**.

## Resultados

Después de que los usuarios añadidos acepten la invitación, pueden iniciar sesión en la consola {{site.data.keyword.vmwaresolutions_short}} y conmutar a la cuenta. Para ello, en sus valores de perfil, los usuarios pulsan su icono de cuenta de usuario desde el banner de la consola de {{site.data.keyword.vmwaresolutions_short}}. A continuación, los usuarios añadidos pueden colaborar y compartir los servicios y los recursos disponibles en la cuenta especificada.

### Enlaces relacionados

* [Invitación de usuarios y asignación de acceso](../../../iam/iamuserinv.html)
* [Gestión de identidad y acceso](../../../iam/quickstart.html)
* [Gestión de usuarios y acceso](../../../iam/iamusermanage.html)
* [¿Qué es IAM?](../../../iam/index.html)
* [Migración de instancias anteriores a V2.5 vCenter Server a cuentas de IBM Cloud](../vcenter/vc_addinstancetousraccount.html)
* [Migración de vCenter Server anterior a V2.5 con las instancias del paquete híbrido (Hybridity) en cuentas de IBM Cloud](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Migración de instancias anteriores a V2.5 Cloud Foundation a cuentas de IBM Cloud](../sddc/sd_addinstancetousraccount.html)
* [Migración de instancias anteriores a V2.5 NetApp ONTAP Select a cuentas de IBM Cloud](../netapp/np_addinstancetousraccount.html)
* [Migración de instancias anteriores a V2.5 VMware Federal a cuentas de IBM Cloud](../vcenter/vc_fed_addinstancetousraccount.html)
