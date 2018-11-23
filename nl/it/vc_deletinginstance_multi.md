---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Eliminazione di istanze vCenter Server in una configurazione multisito

Tieni presente le seguenti considerazioni speciali prima di pianificare l'eliminazione delle istanze vCenter Server che fanno parte di una configurazione multisito.

Quando elimini un'istanza vCenter Server, i seguenti componenti vengono rilasciati in modo sequenziale:
1. Tutti i servizi distribuiti
2. Tariffa per supporto e servizi
3. Licenze del prodotto VMware
4. Server ESXi
5. Sottoreti
6. VLAN

A causa delle dipendenze delle risorse, i componenti della tua istanza non vengono rilasciati immediatamente quando elimini l'istanza. Ad esempio, le sottoreti e le VLAN non possono essere eliminate finché i server ESXi non vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud}}, cosa che avviene alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}. Alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni, le sottoreti e le VLAN vengono eliminate e l'eliminazione dell'istanza viene completata.

Per l'istanza eliminata ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
{:note}

## Procedura per eliminare le istanze vCenter Server in una configurazione multisito

1. Rimuovi tutti i servizi dall'istanza secondaria di vCenter Server.
2. Assicurarti che nessun oggetto NSX sia espanso nell'istanza secondaria che vuoi eliminare.
3. Elimina il vCenter e il PSC (Platform Services Controller) secondari dal dominio SSO (Single Sign-On) primario. Per ulteriori informazioni, vedi [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Riduci il livello dell'istanza di servizio virtuale (o VSI, Virtual Service Instance) del controller di dominio locale. Per ulteriori informazioni, vedi [Demoting domain controllers and domains](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Elimina l'istanza secondaria vCenter Server dalla console {{site.data.keyword.vmwaresolutions_short}}.
6. Ripeti i passi da 1 a 5 per tutte le istanze vCenter Server secondarie nella tua configurazione multisito.
7. Dopo aver eliminato tutte le istanze secondarie, puoi anche eliminare l'istanza primaria dalla console {{site.data.keyword.vmwaresolutions_short}}.

### Link correlati

* [Eliminazione di istanze vCenter Server](vc_deletinginstance.html)
* [Ordine, visualizzazione e rimozione dei servizi dalle istanze vCenter Server](vc_addingremovingservices.html)
