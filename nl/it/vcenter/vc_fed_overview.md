---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di VMware Federal on IBM Cloud

Con VMware Federal on {{site.data.keyword.cloud}}, puoi ordinare un'istanza vCenter Server di base oltre a fornire alle agenzie del Governo federale degli Stati Uniti l'opzione per proteggere le istanze vCenter Server distribuite. Quando proteggi un'istanza distribuita, le informazioni sensibili memorizzate relative all'istanza vengono rimosse. Inoltre, viene rimossa la connessione aperta per l'accesso all'istanza, il che significa che le funzioni di gestione, come l'aggiunta e la rimozione di host e cluster, non sono più disponibili. Dopo aver selezionato l'opzione di protezione, l'unica funzione disponibile è l'eliminazione dell'istanza.

Per ulteriori informazioni su vCenter Server on {{site.data.keyword.cloud_notm}} e sull'architettura di vCenter Server, vedi [Panoramica di vCenter Server](vc_vcenterserveroverview.html).

VMware Federal on {{site.data.keyword.cloud_notm}} offre solo un sottoinsieme delle offerte di vCenter Server. La configurazione multisito, BYOL (Bring Your Own License) e l'opzione per ordinare servizi aggiuntivi non sono supportati.
{:note}

## Specifiche tecniche per le istanze VMware Federal on IBM Cloud

Sono inclusi i seguenti componenti:

### Bare Metal Server

Puoi ordinare due o più {{site.data.keyword.baremetal_short}} con una delle seguenti configurazioni:

* 2-CPU Intel Broadwell (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake (Intel Xeon 4100/5100/6100 series)

Per la configurazione dell'archiviazione NFS, il numero consigliato di {{site.data.keyword.baremetal_short}} è impostato sul valore predefinito di tre.

Se selezioni l'archiviazione vSAN, la configurazione richiede quattro {{site.data.keyword.baremetal_short}}.
{:note}

### Rete

Vengono ordinati i seguenti componenti di rete:
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando altre VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle macchine virtuali di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG gestito dal cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Non puoi accedere a questo ESG e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza vCenter Server dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni comporterà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
    {:important}
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata, distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico. Per ulteriori informazioni, vedi [L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-).

  Il gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HTTPS in uscita viene rimosso come parte dell'azione per proteggere la tua istanza VMware Federal distribuita. Per ulteriori informazioni, vedi [Protezione di istanze VMware Federal](vc_fed_securinginstance.html).
  {:note}

### VSI (Virtual Server Instance)

Vengono ordinate le seguenti VSI (Virtual Server Instance):
* Una VSI per IBM CloudBuilder, che viene arrestata al termine della distribuzione dell'istanza.
* (Per le istanze della V2.3 e successive) Puoi scegliere di distribuire una singola VSI di Microsoft Windows Server per Microsoft Active Directory (AD) o due VM Microsoft Windows ad alta disponibilità nel cluster di gestione per migliorare la sicurezza e l'affidabilità.
* (Per le istanze della V2.2) Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) che può essere consultata. Questa VSI funziona come DNS per l'istanza in cui sono registrati gli host e le macchine virtuali.

### Archiviazione

Durante la distribuzione iniziale, puoi scegliere tra le opzioni di archiviazione vSAN e NFS.

#### Archiviazione vSAN

L'opzione vSAN offre configurazioni personalizzate, con varie opzioni per tipo e quantità di dischi:
* Quantità dischi: 2, 4, 6 o 8.
* Disco di archiviazione: SED SSD da 960 GB, SED SSD da 1,9 TB o SED SSD da 3,8 TB.

  Inoltre, vengono ordinati due dischi di cache di 960 GB per ciascun host.
* Opzione Alte prestazioni con Intel Optane, che fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità. Questa opzione dipende dal modello di CPU.

#### Archiviazione NFS

L'opzione NFS offre l'archiviazione a livello di file condivisa personalizzata per carichi di lavoro con varie opzioni per dimensioni e prestazioni:
* Dimensioni: 1, 2, 4, 8 o 12 TB.
* Prestazioni: 2, 4 o 10 IOPS/GB.
* Configurazione individuale per le condivisioni file.

Se scegli l'opzione NFS, viene ordinata una condivisione file da 2 TB con 4 IOPS/GB per i componenti di gestione.

### Licenze fornite da IBM e tariffe

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.4
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6

## Specifiche tecniche per i nodi di espansione VMware Federal on IBM Cloud

Ogni nodo di espansione vCenter Server verrà distribuito e addebitato per i seguenti componenti nel tuo account {{site.data.keyword.cloud_notm}}.

### Hardware per i nodi di espansione

Un Bare Metal Server con la configurazione presentata in [Specifiche tecniche per le istanze VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances).

### Licenze e tariffe per i nodi di espansione

* Un VMware vSphere Enterprise Plus 6.5u1
* Un VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.4
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6

Devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console. Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non vengono sincronizzate con la console.
{:important}

**ATTENZIONE:** la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}}, installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza, dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante l'aggiunta o la rimozione di server ESXi
*  Spegnimento dei componenti

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

### Link correlati

* [Requisiti e pianificazione per le istanze VMware Federal](vc_fed_planning.html)
* [Ordine di istanze VMware Federal](vc_fed_orderinginstance.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze VMware Federal](fed_addviewdeleteclusters.html)
* [Espansione e contrazione della capacità per le istanze VMware Federal](vc_fed_addingremovingservers.html)
* [Protezione di istanze VMware Federal](vc_fed_securinginstance.html)
* [Archiviazione file e blocchi di {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
