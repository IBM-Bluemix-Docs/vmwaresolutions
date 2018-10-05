---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Valores de almacenamiento

Este diseño da soporte a la conexión del almacenamiento compartido mediante NFS v3 únicamente. NFS v4 y v4.1 no están soportados.

**Nota**: Todo el almacenamiento adjunto para este diseño se limita al almacenamiento de {{site.data.keyword.cloud_notm}} disponible en el mismo {{site.data.keyword.CloudDataCent_notm}} que la solución vCenter Server. Además, de forma predeterminada todos los discos virtuales que se almacenan en el almacén de datos son de aprovisionamiento ligero.

La arquitectura especifica que los almacenes de datos NFS v3 se adjuntan utilizando el nombre de DNS del almacenamiento de {{site.data.keyword.cloud_notm}} para conectarse a la compartición. Además, el recurso compartido NFS se conecta a todos los hosts del clúster de vCenter Server y se coloca en un clúster de almacén de datos con el DRS de almacenamiento habilitado.

## Planificador de recursos distribuidos de almacenamiento (DRS de almacenamiento) de vSphere

DRS de almacenamiento le permite gestionar los recursos agregados de un clúster de almacén de datos. Cuando DRS de almacenamiento está habilitado, proporciona recomendaciones sobre la ubicación de disco de la máquina virtual (VM) y la migración para equilibrar el espacio y los recursos de E/S entre los almacenes de datos del clúster de almacén de datos.

Las siguientes características están disponibles cuando el DRS de almacenamiento está activado:
* Equilibrio de carga de espacio entre los almacenes de datos dentro de un clúster de almacén de datos
* Equilibrio de carga de E/S entre los almacenes de datos dentro de un clúster de almacén de datos
* Colocación inicial de los discos virtuales en función del espacio y de la carga de trabajo de E/S.

En este diseño, el DRS de almacenamiento se habilita con el nivel de automatización establecido en **Totalmente automatizado**. Como resultado, los archivos se migran automáticamente para optimizar el uso de recursos en el clúster de datos. Puesto que el clúster está totalmente automatizado, todas las demás opciones de DRS de almacenamiento se establecen en **Utilizar valores de clúster**.

## Valores de tiempo de ejecución de DRS de almacenamiento para NFS v3

La agresividad del DRS de almacenamiento se determina especificando umbrales para el espacio que se utiliza y la latencia de E/S. El DRS de almacenamiento recopila información de uso de recursos para los almacenes de datos en un clúster de almacén de datos. vCenter Server utiliza esta información para generar recomendaciones sobre la colocación de discos virtuales en almacenes de datos.

Cuando se ha establecido un nivel de agresividad bajo para un clúster del almacén de datos, el DRS de almacenamiento solo recomienda migraciones de vMotion de almacenamiento cuando es necesario, por ejemplo cuando la carga de E/S, la utilización de espacio o el desequilibrio son altos. Cuando se ha establecido un nivel de agresividad alto para un clúster del almacén de datos, el DRS de almacenamiento recomienda migraciones siempre que el clúster del almacén de datos se puede beneficiar del espacio o del equilibrio de la carga de E/S.

Están disponibles las siguientes categorías de umbral en el clúster de almacén de datos:

* Utilización de espacio: el DRS de almacenamiento genera recomendaciones o realiza migraciones cuando el porcentaje de utilización de espacio en el almacén de datos es mayor que el umbral que ha establecido en el cliente web de vSphere.
* Latencia de E/S: el DRS de almacenamiento genera recomendaciones o realiza migraciones cuando el percentil 90 de latencia de E/S durante un día correspondiente al almacén de datos es mayor que el umbral.

En este diseño, los valores de tiempo de ejecución del DRS de almacenamiento están habilitados y los umbrales conservan sus respectivos valores predeterminados. Es muy recomendable cambiar estos valores en función de los requisitos de E/S de carga de trabajo y de la sensibilidad a la latencia.

En la tabla siguiente se muestran los valores en el cliente web de VMware vSphere.

Tabla 1. Valores de tiempo de ejecución de DRS de almacenamiento

| Parámetro       | Valor  |
|:--------------- |:------ |
| Habilitar métrica de E/S para recomendaciones de SDRS | Seleccionado |
| Espacio utilizado | Seleccionado, establecidos en 80% |
| Umbral de latencia de E/S | 15 ms |

Para obtener más información sobre la configuración de estos valores en el cliente web de vSphere, consulte [Establecimiento de reglas de tiempo de ejecución de DRS de almacenamiento en el cliente web de vSphere](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

## Control de E/S de almacenamiento para NFS v3

Si SIOC (Control de E/S de almacenamiento, Storage I/O Control) está habilitado en el entorno, cambia la longitud de la cola de dispositivos para la máquina virtual única. El cambio en la longitud de cola del dispositivo reduce la cola de matriz de almacenamiento para todas las máquinas virtuales en una proporción igual y regula la cola de almacenamiento. SIOC solo interviene si los recursos están restringidos y la latencia de E/S del almacenamiento es superior a un umbral definido.

Para que SIOC determine si un dispositivo de almacenamiento está restringido o congestionado, necesita un umbral definido. La latencia del umbral de congestión es distinto para los diferentes tipos de almacenamiento. En este diseño se recomienda y se implementa una latencia de umbral de 10 milisegundos.

También puede limitar los discos virtuales individuales para máquinas virtuales individuales u otorgarles distintas comparticiones con SIOC. Limitar los discos y otorgar distintas comparticiones le permite alinear el entorno a la carga de trabajo con el número de IOPS de volumen de almacenamiento de archivos adquirido. El límite lo establece IOPS y es posible establecer un peso o comparticiones diferentes.

Las comparticiones de discos virtuales establecidas en **Alto** (2.000 comparticiones) reciben el doble de E/S que un disco establecido en **Normal** (1.000 comparticiones) y cuatro veces el de uno establecido en **Bajo** (500 comparticiones). **Normal** es el valor predeterminado para todas las máquinas virtuales, por lo que es necesario ajustar los valores **Normal** para las máquinas virtuales que lo requieran.

## Almacenamiento adicional para NFS v3

Cuando sea necesario añadir almacenamiento adicional al entorno por falta de espacio o por latencia alta, puede solicitar otra compartición NFS de la consola. Una vez solicitada la compartición, adjunte la exportación a los hosts vSphere ESXi del clúster y colóquela en el clúster de almacenamiento. El hecho de colocar la nueva compartición NFS en el clúster de almacenamiento permite escalar de forma efectiva y sin interrupciones el almacenamiento asociado al entorno sin sobrecargarle con migraciones de nivel de almacenamiento.

## Parámetros de configuración avanzada

Este diseño añade parámetros de configuración avanzados recomendados por {{site.data.keyword.cloud_notm}}. Como resultado, se establecen los siguientes parámetros en cada host ESXi de vSphere que está conectado a la unidad compartida NFS de {{site.data.keyword.cloud_notm}}.

Tabla 2. Parámetros de configuración avanzada de NFS

| Parámetro       | Valor  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### Enlaces relacionados

* [Visión general de la solución](../solution/solution_overview.html)
