---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Considerazioni sulla modifica delle risorse vCenter Server

La modifica di utenti, risorse o sottoreti riservati a {{site.data.keyword.vmwaresolutions_full}} può influire sulle operazioni di gestione.

**Importante:** non modificare le autorizzazioni globali del gruppo **ic4v-vCenter** nella pagina **Utenti e gruppi** del client web VMware vSphere. Tali modifiche includono la modifica del nome utente, l'eliminazione dell'utente o la modifica della sua password.

## ID automazione

L'ID **automazione** è un account utente che viene utilizzato dalle operazioni automatizzate fornite nella console {{site.data.keyword.vmwaresolutions_short}}.

Gli utenti e le password per le operazioni automatizzate nella console non devono essere modificati perché le operazioni della console che dipendono da quelle credenziali potrebbero non riuscire.

## Account utente specifici del servizio

Ogni servizio crea un account utente interno in vCenter Server. Questo account è necessario affinché le operazioni di gestione associate a un servizio possano connettersi a vCenter Server per eseguire le operazioni sul servizio.

**Importante:** per evitare interruzioni e problemi di connessione, se modifichi le impostazioni di ID utente, password o scadenza password per questo account utente, assicurati di aggiornare le informazioni anche nel servizio associato.

L'ID utente per questo account è nel formato `<service_name>-<truncated service_uuid>@test.local` o `<service_name>-<truncated service_uuid>@example-domain.local`. Ad esempio, l'ID utente utilizzato dal servizio Veeam on {{site.data.keyword.cloud_notm}} per connettersi a vCenter Server per eseguire backup pianificati è `Veeam-<Veeam_uuid>@test.local`.

**Nota:** il `<service_name>` insieme al `<service_uuid>` viene troncato a 20 caratteri.

## Risorse VMware per le istanze vCenter Server (V1.9 e successive)

Per le istanze distribuite nella V1.9 e successive, se l'istanza vCenter Server è nello stato **Pronto per l'utilizzo**, puoi modificare il data center virtuale VMware, il cluster, gli switch, i gruppi di porte e i nomi di archivio dati del cliente dal client web VMware vSphere. Tuttavia, non devi modificare il nome dell'archivio dati di gestione dal suo valore predefinito: **vsanDatastore** per le istanze vSAN e **management-share** per le istanze NFS (Network File System).

## Risorse VMware per le istanze vCenter Server (V1.8 e precedenti)

La seguente tabella elenca le operazioni che potrebbero essere interessate se l'amministratore SSO modifica le risorse VMware vCenter Server all'esterno della console {{site.data.keyword.vmwaresolutions_short}}. Se disponibile, verrà fornita anche una soluzione per il recupero.

Questa tabella è applicabile alle istanze distribuite nella V1.8 e precedenti, oltre alle istanze distribuite nella V1.8 e precedenti e quindi aggiornate alla V1.9 o successive.

Tabella 1. Operazioni interessate dalla modifica delle risorse VMware

| Tentativo di modifica  | Operazioni interessate  | Severità  | Metodo di recupero  |
|:------------- |:------------- |:--------------|:--------------|
| Modifica del nome del data center virtuale VMware. | L'aggiunta di un data center virtuale VMware potrebbe non riuscire perché il nuovo server ESXi non può raggiungere il data center virtuale modificato. | Importante | Modifica di nuovo il nome del data center virtuale VMware con il nome originale. |
| Modifica dei nomi dei gruppi di porte.    | L'aggiunta di un server ESXi potrebbe non riuscire. | Importante | Modifica di nuovo il nome del gruppo di porte con il nome originale. |
| Modifica del nome del cluster. | L'aggiunta di un server ESXi potrebbe non riuscire. | Importante | Modifica di nuovo il nome del cluster con il nome originale.
| Modifica del nome del DVS (Distributed Virtual Switch) pubblico o privato. | L'aggiunta di un server ESXi potrebbe non riuscire. | Importante | Modifica di nuovo il nome del DVS (Distributed Virtual Switch) pubblico o privato con il nome originale.
| Modifica del nome dell'archivio dati vSAN nell'istanza che utilizza vSAN. | L'aggiunta di un server ESXi potrebbe non riuscire.<br><br>L'aggiornamento dell'istanza potrebbe non riuscire. | Importante | Modifica di nuovo il nome dell'archivio dati vSAN con il nome originale, **vsanDatastore**.
| Modifica del nome dell'archivio dati NFS di gestione nell'istanza che utilizza NFS. | L'aggiunta di un server ESXi potrebbe non riuscire.<br><br>L'aggiornamento dell'istanza potrebbe non riuscire. | Importante | Modifica di nuovo il nome dell'archivio dati di gestione NFS con il nome originale, **management-share** e rimonta l'archivio dati NFS in modalità di sola lettura sul server ESXi.

La seguente tabella elenca le operazioni che potrebbero essere interessate se viene disabilitato l'accesso shell o SSH per molte risorse.

Tabella 2. Operazioni interessate dall'accesso shell e SSH (locale)

| Tentativo di modifica  | Operazioni interessate  | Severità  | Metodo di recupero  |
|:------------- |:------------- |:--------------|:--------------|
| Disabilita l'accesso SSH o shell per vCenter Server o PSC.    | L'accoppiamento di un istanza primaria e secondaria potrebbe non riuscire.    | Importante    | N/A    |
| Disabilita l'accesso SSH o shell per ESXi.    | L'aggiunta e la rimozione degli host, dei servizi e della memoria di rete per l'istanza potrebbe non riuscire.    | Importante    | N/A    |

Se scegli di disabilitare l'accesso shell o SSH, puoi riabilitarlo temporaneamente prima di eseguire le operazioni indicate.

## Sottoreti di gestione per le istanze vCenter Server

Le seguenti informazioni trattano le sottoreti ordinate da {{site.data.keyword.vmwaresolutions_short}} e forniscono opzioni per ordinare sottoreti aggiuntive per uso personale.

**ATTENZIONE:** non utilizzare questi componenti per altri scopi altrimenti la stabilità del tuo ambiente sarà gravemente compromessa.

Con ogni ordine di Bare Metal Server {{site.data.keyword.cloud_notm}}, vengono ordinati i seguenti intervalli di indirizzi IP per impostazione predefinita:
*  Un intervallo pubblico primario di 32 indirizzi IP
*  Un intervallo privato primario di 64 indirizzi IP

Inoltre, a {{site.data.keyword.vmwaresolutions_short}} sono anche riservate le seguenti sottoreti di gestione:
*  Due sottoreti private portatili di 64 indirizzi IP sulla prima VLAN: una per la gestione e l'altra per VTEPS
*  Due sottoreti private portatili di 64 indirizzi IP sulla seconda VLAN: una per VMotion e una per vSAN
*  Una sottorete portatile pubblica di 16 indirizzi IP sulla VLAN pubblica

Se hai bisogno di utilizzare più sottoreti, puoi ottenere gli indirizzi IP da utilizzare in uno dei seguenti modi:
*  **Opzione 1 (consigliata)**: utilizza le sovrapposizioni della rete virtuale VMware NSX. Viene fornito un template VXLAN di esempio al momento dell'ordine. Questo template VXLAN può essere utilizzato come punto di partenza per la creazione di SDN (Software-Defined Networking). Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'edge NSX gestito dal cliente](vc_esg_config.html).
*  **Opzione 2**: ordina le tue proprie sottoreti pubbliche o private portatili per ottenere gli indirizzi IP. Per distinguere le sottoreti che ordini da quelle di gestione, puoi aggiungere delle note a tutte le sottoreti che stai ordinando.
