---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di vCenter Server

VMware vCenter Server on {{site.data.keyword.cloud}} è un cloud privato ospitato che fornisce lo stack VMware vSphere come servizio. L'ambiente VMware è costruito su un minimo di due (tre consigliati) {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}}, offre opzioni di archiviazione collegata alla rete condivisa e archiviazione definita dal software dedicata e include la distribuzione e configurazione automatizzata di un firewall edge logico di facile gestione con tecnologia VMware NSX.

In molti casi, l'intero ambiente può essere fornito in meno di un giorno e l'infrastruttura bare metal può ridimensionare rapidamente ed elasticamente la capacità di calcolo a seconda delle necessità.

Dopo la distribuzione, puoi aumentare l'archiviazione condivisa ordinando altre condivisioni file NFS (Network File System) dal {{site.data.keyword.slportal}} e collegandole manualmente a tutti i server ESXi in un cluster. Se hai bisogno dell'archiviazione dedicata, [NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}](../netapp/np_netappoverview.html) è offerto sia in configurazioni ad alte prestazioni (tutti gli SSD) che ad alta capacità (tutti i SATA).

VMware vSAN è anche disponibile come opzione di archiviazione dedicata. Per aumentare la capacità di archiviazione basata su vSAN di un cluster vSAN, puoi aggiungere altri server ESXi dopo la distribuzione.

Se hai acquistato la licenza VMware fornita da IBM, puoi aggiornare l'edizione di base di VMware NSX all'edizione Advanced o Enterprise e puoi acquistare ulteriori componenti VMware, come ad esempio VMware vRealize Operations.

Puoi aggiungere i servizi gestiti IBM se vuoi scaricare le operazioni quotidiane e la manutenzione dei livelli di virtualizzazione, sistemi operativi guest o applicazioni. Il team {{site.data.keyword.cloud_notm}} Professional Services è anche disponibile per aiutarti ad accelerare il tuo viaggio verso il cloud con servizi di migrazione, implementazione, pianificazione e incorporazione.

## Architettura di vCenter Server

Il seguente grafico illustra l'architettura di alto livello e i componenti di una distribuzione vCenter Server a tre nodi.

Figura 1. Architettura di alto livello di vCenter Server per un cluster a tre nodi
![Architettura di vCenter Server](vc_architecture.svg "Architettura di alto livello di vCenter Server per un cluster a tre nodi")

### Infrastruttura fisica

Questo livello fornisce l'infrastruttura fisica (risorse di calcolo, archiviazione e rete) che deve essere utilizzata dall'infrastruttura virtuale.

### Infrastruttura di virtualizzazione (calcolo e rete)

Questo livello virtualizza l'infrastruttura fisica attraverso diversi prodotti VMware:
* VMware vSphere virtualizza le risorse di calcolo fisiche.
* VMware NSX è la piattaforma di virtualizzazione di rete che fornisce componenti di rete logica e reti virtuali.

### Gestione della virtualizzazione

Questo livello comprende il dispositivo vCenter Server Appliance (vCSA), NSX Manager, due ESG NSX, tre controller NSX, il dispositivo virtuale PSC (Platform Services Controller) e la VSI (Virtual Server Instance) IBM CloudDriver. La VSI CloudDriver viene distribuita su richiesta in base alle esigenze per determinate operazioni, ad esempio l'aggiunta di host all'ambiente.

L'offerta di base viene distribuita con un dispositivo vCenter Server dimensionato per supportare un ambiente con un massimo di 400 host e 4000 VM. Gli stessi strumenti e script compatibili con l'API vSphere possono essere utilizzati per gestire l'ambiente VMware ospitato da IBM.

In totale, l'offerta di base richiede 38 vCPU e 67 GB di vRAM che sono riservati per il livello di gestione della virtualizzazione. La capacità host rimanente per le tue macchine virtuali dipende da diversi fattori, come la percentuale di sottoscrizione eccedente, il dimensionamento della VM e i requisiti delle prestazioni del carico di lavoro.

Per ulteriori informazioni sull'architettura, vedi [Riferimento all'architettura di {{site.data.keyword.vmwaresolutions_short}}](../archiref/solution/solution_overview.html).

## Specifiche tecniche per le istanze vCenter Server

Nella tua istanza vCenter Server sono inclusi i seguenti componenti.

La disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.
{:note}

### Bare Metal Server

Puoi ordinare tre o più {{site.data.keyword.baremetal_short}} con una delle seguenti configurazioni:
* **Skylake**: server di generazione 2-CPU Intel Skylake (Intel Xeon 4100/5100/6100 series) con i tuoi modello CPU e dimensione RAM selezionati.  
* **Certificato SAP**: {{site.data.keyword.baremetal_short}} con il modello CPU da te selezionato.
  * Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 192 GB RAM
  * Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 384 GB RAM
  * Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 768 GB RAM
* **Broadwell**: server di generazione 2-CPU Intel Broadwell (Intel Xeon E5-2600 v4 series) con i tuoi modello CPU e dimensione RAM selezionati.  
     Se intendi utilizzare l'archiviazione vSAN, la configurazione richiede quattro {{site.data.keyword.baremetal_short}}.
     {:note}
     
### Rete

Vengono ordinati i seguenti componenti di rete:
*  Doppi uplink di rete privata e pubblica da 10 Gbps
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando ulteriori VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle macchine virtuali di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG gestito dal cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Questo ESG è denominato **mgmt-nsx-edge**, non puoi accedervi e usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza vCenter Server dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni potrebbe comportare l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
    {:important}
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata. Questo gateway è distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico. Per ulteriori informazioni, vedi [L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

### VSI (Virtual Server Instance)

Vengono ordinate le seguenti VSI (Virtual Server Instance):
* Una VSI per IBM CloudBuilder, che viene arrestata al termine della distribuzione dell'istanza.
* (Per le istanze della V2.2 e successive) Puoi scegliere di distribuire una singola VSI di Microsoft Windows Server per Microsoft Active Directory (AD) o due VM Microsoft Windows ad alta disponibilità nel cluster di gestione per migliorare la sicurezza e la solidità.
* (Per le istanze dalla V1.9 alla V2.1) Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) che può essere consultata. La VSI funziona come DNS per l'istanza in cui sono registrati gli host e le macchine virtuali.
* (Per le istanze della V1.8 e precedenti) Una VSI per il backup basato su istantanea dei componenti di gestione, che continua l'esecuzione dopo il completamento della distribuzione dell'istanza.

### Archiviazione

Durante la distribuzione iniziale, puoi scegliere tra le opzioni di archiviazione vSAN e NFS.

#### Archiviazione vSAN

L'opzione vSAN offre configurazioni personalizzate, con varie opzioni per tipo, dimensione e quantità di dischi:
* Quantità dischi: 2, 4, 6 o 8
* Disco di archiviazione: SED SSD da 960 GB, SED SSD da 1,9 TB o SED SSD da 3,8 TB.

  Inoltre, vengono ordinati anche due dischi di cache di 960 GB per ciascun host.

  Le unità SSD (Solid State Disk) da 3,8 TB saranno supportate una volta rese generalmente disponibili in un data center.
  {:note}
* Opzione Alte prestazioni con Intel Optane, che fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità. Questa opzione dipende dal modello di CPU.

#### Archiviazione NFS

L'opzione NFS offre l'archiviazione a livello di file condivisa personalizzata per carichi di lavoro con varie opzioni per dimensioni e prestazioni:
* Dimensioni: 1, 2, 4, 8 o 12 TB
* Prestazioni: 2, 4 o 10 IOPS/GB.
* Configurazione individuale delle condivisioni file.

Se scegli l'opzione NFS, viene ordinata una condivisione file da 2 TB e 4 IOPS/GB per i componenti di gestione.

### Licenze (fornite da IBM o BYOL) e tariffe

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.4
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6
* Tariffa per supporto e servizi (una licenza per nodo)

## Specifiche tecniche per i nodi di espansione vCenter Server

Ogni nodo di espansione vCenter Server verrà distribuito e addebitato per i seguenti componenti nel tuo account {{site.data.keyword.cloud_notm}}.

### Hardware per i nodi di espansione

Un Bare Metal Server con la configurazione presentata in [Specifiche tecniche per le istanze vCenter Server](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

### Licenze e tariffe per i nodi di espansione

* Un VMware vSphere Enterprise Plus 6.5u1
* Un VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.4
* Una tariffa per supporto e servizi
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6

Devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console. Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.
La gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}}, installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza, dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante l'aggiunta o la rimozione di server ESXi
*  Spegnimento dei componenti
*  Riavvio dei servizi
   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.
   {:important}

### Link correlati

* [Distinta base del software vCenter Server](vc_bom.html)
* [Pianificazione per le istanze vCenter Server](vc_planning.html)
* [Ordine di istanze vCenter Server](vc_orderinginstance.html)
* [Archiviazione file e blocchi di {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
