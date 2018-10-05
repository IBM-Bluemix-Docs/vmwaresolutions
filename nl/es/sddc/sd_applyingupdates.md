---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

{:tip: .tip}

# Aplicación de actualizaciones a instancias de Cloud Foundation

La consola de {{site.data.keyword.vmwaresolutions_full}} detecta y muestra periódicamente las actualizaciones de software disponibles que puede aplicar a su entorno virtual VMware.

Una actualización disponible es un registro de la lista de actualizaciones de software de la instancia, que se puede aplicar de inmediato o se puede planificar para un momento posterior. La actualización es un paquete que a su vez contiene uno o varios paquetes para actualizar los componentes de gestión de IBM y los componentes de VMware.

## Antes de empezar

Antes de intentar aplicar una actualización, expanda la entrada de la actualización pulsando la flecha hacia abajo y verifique la información siguiente:
* La versión de la actualización. Debe aplicar las actualizaciones en secuencia cronológica, es decir, desde la primera hasta la más reciente. Asegúrese de haber aplicado todas las actualizaciones anteriores antes de aplicar la más reciente. Por ejemplo, debe aplicar la actualización de V2.4 antes de intentar aplicar la actualización de V2.5.
* Si se requiere tiempo de inactividad.
* El tiempo total estimado para completar la actualización.
* El impacto de la actualización sobre el entorno virtual VMware. La Tabla 1 muestra cómo afectan al sistema distintos niveles de impacto.
* Los detalles de la actualización.

Tabla 1. Niveles de actualización e impacto

<table>
  <tr>
    <th>Nivel de actualización</th>
    <th>Impacto</th>
  </tr>
  <tr>
    <td>Bajo</td>
    <td>Esta actualización no afecta a ningún sistema. No es necesario que la aplique durante un tiempo de inactividad planificado.</td>
  </tr>
  <tr>
    <td>Medio</td>
  <td>Esta actualización puede afectar a algunos sistemas. Se recomienda aplicarla durante un tiempo de inactividad planificado.</td>
  </tr>
    <tr>
    <td>Grave</td>
  <td>Esta actualización afecta a algunos o a todos los sistemas. Debe aplicarla durante un tiempo de inactividad planificado.</td>
  </tr>
</table>

## Procedimiento

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de Cloud Foundation**, pulse la instancia que desea actualizar.
3. En la página **Resumen**, verifique que todos los detalles de la instancia se muestren correctamente. A continuación, pulse **Infraestructura** en el panel de navegación de la izquierda para verificar los detalles en la página **Infraestructura**.
   Si no se visualizan los detalles, esto podría indicar un problema de conectividad con la IBM CloudDriver Virtual Server Instance (VSI), como resultado de una regla de cortafuegos u otro problema de red. Resuelva el problema antes de continuar con el siguiente paso; de lo contrario, la actualización puede fallar.
4. Pulse **Actualización y parche** en el panel de navegación izquierdo.
5. Pulse la flecha hacia abajo para ampliar la actualización que desea aplicar y luego siga uno de los pasos siguientes:
   *  Para comenzar la actualización de inmediato, pulse el icono de menú de desbordamiento en la columna **Acciones** de la entrada de la actualización y pulse **Actualizar ahora**.
   *  Para planificar una actualización futura, pulse el icono de menú de desbordamiento en la columna **Acciones** de la entrada de la actualización y pulse **Planificar actualización**. Seleccione la fecha, la hora y el huso horario en que desea que comience la actualización. Pulse **Aceptar**.
6. Si está aplicando actualizaciones a instancias de Cloud Foundation en la configuración de despliegue de varios sitios, aparecerá una sección titulada **Pasos necesarios para actualizar**, que lista las operaciones de actualización que son necesarias para todas las instancias en el despliegue de varios sitios. Debe completar los pasos en secuencia pulsando **Aplicar actualización** para cada paso. Debe esperar a que finalice el paso anterior antes de iniciar el paso siguiente.

## Resultados

1. Antes de que se inicie una operación de actualización, se realiza una comprobación del estado de la instancia. Si la comprobación de estado falla, se le notificará para que pueda solucionar el problema antes de aplicar la actualización.
2. Durante las actualizaciones que incluyen actualizaciones de componentes de VMware, es posible que tenga que migrar las VM de los servidores ESXi para ir a la modalidad de mantenimiento. Es posible que la migración de VM se evite si una VM tiene un almacén de datos o un CD-ROM montado.
3. Durante el suministro de un nuevo entorno, {{site.data.keyword.vmwaresolutions_short}} crea el ID **automationuser** que se utiliza para la gestión de la instancia, incluida la aplicación de actualizaciones. No cambie la contraseña de este ID de usuario. Si cambia la contraseña, la actualización podría fallar.

4. Después de aplicar una actualización, aparece un registro en la lista de estado de actualización de software, donde puede ver el progreso detallado y el estado de la actualización. Cuando la actualización finaliza correctamente, aparece un registro en la lista de actualizaciones de software instaladas.

  Para recuperar el estado más reciente de un trabajo de actualización, pulse el icono de renovación de la parte superior derecha de la página.
  {:tip}

5. Para obtener más información sobre los estados de una actualización, consulte la tabla siguiente.

   Tabla 2. Detalles de los estados de actualización

    <table>
      <tr>
        <th>Estado</th>
        <th>Detalles</th>
      </tr>
      <tr>
        <td>Disponible</td>
        <td>La actualización está lista para se aplicada. No puede seleccionar una actualización disponible hasta que se hayan aplicado sus actualizaciones anteriores.</td>
      </tr>
      <tr>
        <td>En curso</td>
      <td>El trabajo de actualización se ha iniciado pero todavía no ha finalizado. No puede aplicar ninguna otra actualización hasta que finalice el trabajo de actualización actual. </td>
      </tr>
        <tr>
        <td>Instalado</td>
      <td>El trabajo de actualización ha finalizado. El componente correspondiente de la plataforma VMware se ha actualizado.</td>
      </tr>
        <tr>
        <td>Fallido</td>
      <td>El trabajo de actualización ha fallado. La consola muestra un error correspondiente a la anomalía de actualización. Revise el error y solucione el problema antes de aplicar la actualización.</td>
      </tr>
          <tr>
        <td>Planificado</td>
      <td>El trabajo de actualización está planificado para un momento posterior. El trabajo de actualización se inicia automáticamente en el momento planificado.</td>
      </tr>
          <tr>
        <td>Desconocido</td>
      <td>No se puede obtener el estado del trabajo de actualización. Póngase en contacto con el servicio de soporte de IBM para obtener ayuda.</td>
      </tr>
    </table>

6. Si el proceso de actualización falla en un paso específico, [póngase en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html) para obtener ayuda. Se le informará sobre cómo resolver el problema y se le guiará para que rearranque la actualización desde el paso que ha dado el error.

### Enlaces relacionados

* [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Visión general de Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
