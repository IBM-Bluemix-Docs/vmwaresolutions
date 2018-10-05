---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Más limitaciones y consideraciones

Revise las siguientes consideraciones y limitaciones cuando trabaje con {{site.data.keyword.vmwaresolutions_full}}.

## Instalación automática de actualizaciones de Windows

Microsoft Active Directory (AD) / Domain Name Server (DNS) se configura automáticamente de modo que solo descargue las actualizaciones. No instala estas actualizaciones ni se reinicia automáticamente. Debe instalar manualmente las actualizaciones y reiniciar en un momento planificado que evite cualquier interrupción de la configuración actual del servidor AD y de otros trabajos de copia de seguridad. Para aplicar las actualizaciones de Windows, instale las actualizaciones manualmente.

## Consideraciones al elegir un nombre de dominio raíz de instancias de Cloud Foundation

Cuando elija un nombre de dominio durante el despliegue de una instancia primaria o secundaria de Cloud Foundation, debe verificar que el nombre de host `sddcmanager.<subdomain>` no se resuelva en un dominio externo mediante los mandatos `ping` o `nslookup`.

La estructura del subdominio de la instancia de Cloud Foundation es `<VCF instance name>.<domain name>`. Por ejemplo, si `<domain name>` es `test.local`, y el nombre de la instancia de Cloud Foundation es `mytest`, el nombre de host `sddcmanager.mytest.test.local` no se debe resolver en una dirección IP antes de desplegar la instancia de Cloud Foundation. De lo contrario, el despliegue de la instancia podría fallar.
