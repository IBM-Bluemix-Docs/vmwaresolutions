---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-09"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica su IBM Cloud Private Hosted

Il servizio {{site.data.keyword.cloud}} Private Hosted distribuisce automaticamente {{site.data.keyword.cloud_notm}} Private Hosted nelle tue istanze VMware vCenter Server. Questo servizio porta la potenza dei microservizi e dei contenitori al tuo ambiente VMware su {{site.data.keyword.cloud_notm}}. Con questo servizio, puoi estendere lo stesso modello operativo e gli stessi strumenti VMware e {{site.data.keyword.cloud_notm}} Privato con cui hai dimestichezza da una situazione in loco a {{site.data.keyword.cloud_notm}}.

Questo servizio è disponibile per le seguenti istanze:
* Istanze vCenter Server distribuite in o aggiornate alla V2.5 e successive
* Istanze vCenter Server with Hybridity Bundle distribuite in o aggiornate alla V2.7 e successive
{:note}

## Specifiche tecniche per IBM Cloud Private Hosted

La seguente tabella elenca i requisiti minimi per ordinare il servizio IBM Cloud Private Hosted per l'ambiente **Pronto per la produzione** e **Sviluppo/Test**.

Tabella 1. Requisiti minimi per gli ambienti Pronto per la produzione e Sviluppo/Test

|Ambiente | Core | Memoria (GB) | Host | Memoria (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| Pronto per la produzione | 52 | 640 | 3 | 8.000 |
| Sviluppo/Test | 30 | 200 | 3 | 4.000 |

### Requisiti della risorsa di IBM Cloud Private Hosted

Le seguenti tabelle elencano i requisiti della risorsa del servizio {{site.data.keyword.cloud_notm}} Private Hosted negli ambienti Pronto per la produzione e Sviluppo/Test.

Tabella 2. Requisiti della risorsa di {{site.data.keyword.cloud_notm}} Private Hosted nell'ambiente Pronto per la produzione

| Tipo di nodo  | Core CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Numero di VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Avvio       | 12 | 24 | 100 | 1 | 1 |   
| Gestione | 8 | 64 | 500 | 3 | 3 |
| Master     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Di lavoro     | 4 | 16 | 200 | 300 | 6 |
| Controllo vulnerabilità | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Server NFS | 8 | 4  | 350 | 1 | 1 |
| Gateway dei servizi edge NSX | 2 | 1 | 0.5 | 0.5 | 2 |
| Vincoli documentati | 52 | 640 |  | 8.000 |   |

Tabella 3. Requisiti della risorsa di {{site.data.keyword.cloud_notm}} Private Hosted nell'ambiente Sviluppo/Test

| Tipo di nodo  | Core CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Numero di VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Avvio       | 12 | 24 | 100 | 1 | 1 |   
| Gestione | 8 | 16 | 150 | 1 | 1 |
| Master     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Di lavoro     | 4 | 16 | 200 | 300 | 3 |
| Controllo vulnerabilità | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Server NFS | 8 | 4  | 350 | 1 | 1 |
| Gateway dei servizi edge NSX | 2 | 1 | 0.5 | 0.5 | 2 |
| Vincoli documentati | 30 | 200 |  | 4.000 |  |

### Formule per il calcolo dei requisiti di spazio di IBM Cloud Private Hosted

Le seguenti formule vengono utilizzate per calcolare i requisiti di spazio di IBM Cloud Private e le spese generali di gestione.

#### Formula 1

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

Tabella 4. Descrizione delle variabili nella formula 1

| Variabili	| Descrizione |	Unità |	Esempio vSAN | Esempio NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	Il numero di core effettivi disponibili per i carichi di lavoro e i servizi nell'ambiente |	Core |	38	| 43 |
| HostCount	| Il numero di host nel cluster predefinito	| Host | 4	| 4 |
| HostCoreCount	| Il numero di core non elaborati disponibili in ogni host nel cluster predefinito |	Core |	16 | 16 |
| HostOverheadCores	| Il numero di core riservati dal server ESXi come sovraccarico, che equivale a 0,1 core	| Core	| 0.1 |	0.1 |
| MgmtOverheadCores | Il numero di core riservati dai componenti di gestione vCenter Server (vCenter Server, PSC, AD/DNS, Edge), che corrisponde a cinque core	| Core	| 5	| 5 |
| vSphereHAHostTolerance |	Il numero di host da tollerare nella configurazione vSphere HA, che equivale a un host |	Host	 | 1 | 1 |
| HostVsanOverheadCorePercentage | La percentuale di core di un host utilizzata da vSAN, che è uguale al 10% o al 0% se l'host non è vsan	| % | 10% |	0% |

#### Formula 2

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

Tabella 5. Descrizione delle variabili nella formula 2

| Variabili	| Descrizione |	Unità |	Esempio vSAN | Esempio NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| Il numero di GB di memoria disponibili per i carichi di lavoro e i servizi nell'ambiente | GB | 	693	| 860 |
| HostCount	| Il numero di host nel cluster predefinito | Host | 6	| 6 |
| HostMemory |	Il numero di GB non elaborati disponibili in ogni host nel cluster predefinito |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | Il numero di GB di una capacità di ogni disco SSD di capacità vSAN su questo host, che è uguale a 960, 1.946 o 3.891, o uguale a 0 GB se non VSAN | GB |	960 | 0 |
| HostOverheadMemory |	 Il numero di GB di memoria riservati dal server ESXi come sovraccarico, che equivale a 4,6 GB	|	GB	| 4.6 |	4.6 |
| MgmtOverheadMemory |	Il numero di GB di memoria riservati dai componenti di gestione vCenter Server (vCenter Server, PSC, AD/DNS, Edge), che corrisponde a 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance |Il numero di host da tollerare nella configurazione vSphere HA, che equivale a un host |Host	 | 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | Il numero di GB di memoria riservati dalla gestione vSAN (rappresentata come percentuale di uno dei dischi vSAN di capacità), che equivale al 2,75% |	% | 2.75%	| 2.75% |
| HostVsanOverheadMemory | Il numero di GB di memoria riservati dalla gestione vSAN indipendentemente dallo spazio disco, che è equivalente a 7 GB o a 0 GB se non VSAN| GB |  7	| 0 |

## Considerazioni quando installi IBM Cloud Private Hosted

* Ottieni la licenza richiesta prima di installare il servizio {{site.data.keyword.cloud_notm}} Private Hosted. Ti consigliamo di assicurarti che la tua licenza possa supportare non solo la distribuzione iniziale di {{site.data.keyword.cloud_notm}} Private Hosted, ma anche l'espansione futura della dimensione di {{site.data.keyword.cloud_notm}} Private Hosted nella tua infrastruttura.
* Per le distribuzioni {{site.data.keyword.cloud_notm}} Private Hosted nell'ambiene pronto per la produzione, 64 GB RAM per host non è supportato. Pertanto, devi selezionare un'opzione che sia superiore a 64 GB di **RAM**.
* Prima che il servizio {{site.data.keyword.cloud_notm}} Private Hosted sia installato nel tuo ambiente, viene eseguito un controllo sulla capacità disponibile del cluster predefinito nell'ambiente per garantire che i componenti del servizio possano essere installati. Se il controllo della capacità ha esito negativo, il servizio non viene installato e il suo stato viene impostato su **Capacity Validation Failed** nella console. Inoltre, viene visualizzato un messaggio della console con maggiori dettagli e ti viene invata una notifica per email. Per installare il servizio, devi aumentare la capacità nel tuo cluster predefinito aggiungendo più host o liberando RAM, CPU o spazio su disco e quindi aggiungere nuovamente il servizio nella console. Dopo di che, puoi rimuovere il servizio esistente nello stato **Capacity Validation Failed** facendo clic sull'icona **Delete** accanto a esso.

## Considerazioni quando rimuovi IBM Cloud Private Hosted

* {{site.data.keyword.cloud_notm}} elimina solo le macchine virtuali (VM) che sono state distribuite durante l'installazione iniziale del servizio {{site.data.keyword.cloud_notm}} Private Hosted. Tutti i nodi che sono stati distribuiti dopo l'installazione non saranno eliminati.
* {{site.data.keyword.cloud_notm}} eliminerà la VXLAN, il DLR e il gateway edge creati durante la distribuzione iniziale del servizio {{site.data.keyword.cloud_notm}} Private Hosted. Le VM che hai distribuito su VXLAN perderanno la connettività una volta avviata la rimozione del servizio {{site.data.keyword.cloud_notm}} Private Hosted.

### Link correlati

* [Ordine di IBM Cloud Private Hosted](../services/icp_ordering.html)
* [Guida di vCenter Server e IBM Cloud Private](../archiref/vcsicp/vcsicp-intro.html)
* [Apri un ticket per IBM Cloud privato](https://www.ibm.com/mysupport/s/?language=en_US)
