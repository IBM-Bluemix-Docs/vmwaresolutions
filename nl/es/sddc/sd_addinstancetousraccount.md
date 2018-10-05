---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Migración de instancias anteriores a V2.5 Cloud Foundation a cuentas de IBM Cloud

Las instancias de VMware Cloud Foundation desplegadas en V2.5 y releases posteriores en la cuenta de {{site.data.keyword.cloud}} se añaden automáticamente a la cuenta y se gestionan mediante {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

Para las instancias que se han desplegado en V2.4 y releases anteriores, puede migrarlas a cuentas de {{site.data.keyword.cloud_notm}} especificadas para la gestión de usuarios habilitada para IAM.

## Antes de empezar

Asegúrese de que la cuenta de {{site.data.keyword.cloud_notm}} a la que desea migrar la instancia no sea una cuenta de IaaS-only. Una cuenta de IaaS-only es una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) que no está enlazada a una cuenta de {{site.data.keyword.cloud_notm}}.

Para obtener más información sobre cómo enlazar su cuenta de Iaas-only con su cuenta de PaaS, consulte [Siga estos pasos para enlazar sus cuentas de IaaS y PaaS](https://www.ibm.com/blogs/bluemix/2018/03/follow-steps-link-iaas-paas-accounts/).

## Procedimiento para migrar instancias

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En el banner de la consola, pulse el icono de cuenta de usuario y, a continuación, pulse el campo **Cuenta** para seleccionar la cuenta de usuario a la que desea migrar la instancia.
3. En la tabla **Instancias de Cloud Foundation**, busque la instancia anterior a V2.5.
4. En la columna **Acciones**, pulse el icono de menú de desbordamiento y, a continuación, pulse **Migrar instancia a la cuenta**.
5. En la ventana **Migrar instancia a la cuenta**, confirme la cuenta a la que va a migrar la instancia y, a continuación, pulse **Migrar**.

## Resultados

1. Se obtiene una notificación de consola en la que se acepta la solicitud para migrar la instancia a la cuenta {{site.data.keyword.cloud_notm}} especificada.
2. Cuando se completa la migración de la instancia, la instancia se visualiza en la página **Instancias desplegadas** bajo la cuenta a la que se ha migrado. La instancia migrada ya no se visualiza en la cuenta original desde la que se ha migrado.

### Enlaces relacionados

* [Gestión de acceso de usuario con IAM](../vmonic/iam.html)
* [Invitación de usuarios para acceder a servicios y recursos](../vmonic/iamuserinvite.html)
* [Qué es IBM Cloud IAM](https://console.stage1.bluemix.net/docs/iam/index.html#iamoverview)
