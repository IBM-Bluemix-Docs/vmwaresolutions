---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Problema de configuración de la consola de vSphere al añadir un clúster HA

## Problema
Cuando se añade una configuración de clúster HA (alta disponibilidad) con una sola compartición de archivos, aparece el siguiente problema de configuración en los hosts ESXi:

`The number of heartbeat datastores for host is 1, which is less than required: 2 (El número de almacenes de datos de latido para el host es 1, que es menor que el necesario: 2)`

## Solución
Este problema se produce cuando no hay redundancia en el almacenamiento compartido para permitir el control de latido del almacén de datos.

Para obtener más información y ver los pasos a seguir para solucionar el problema, consulte [Error de HA: "El número de almacenes de datos de latido para el host es 1, que es menor que el necesario: 2" (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
