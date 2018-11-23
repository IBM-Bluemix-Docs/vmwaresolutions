---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-09"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di F5 on IBM Cloud

Il servizio F5 on {{site.data.keyword.cloud}} (F5 BIG-IP® Virtual Edition) fornisce servizi intelligenti di bilanciamento del carico L4-L7 e di gestione del traffico su scala locale e globale, una solida protezione firewall per reti e applicazioni web e accesso sicuro e federato alle applicazioni.

Puoi installare più di un'istanza di questo servizio a seconda delle necessità.

Questo servizio è disponibile solo per le istanze distribuite nella V1.9 o successive. La versione BIG-IP VE corrente installata è la v13.1.1.2.
{:note}

## Specifiche tecniche per F5 on IBM Cloud

Con il servizio F5 on {{site.data.keyword.cloud_notm}} sono inclusi i seguenti componenti:

### Macchine virtuali
* Due macchine virtuali (VM) con tutte le opzioni disponibili.
* 2, 4 o 8 vCPU per macchina virtuale in base all'opzione di licenza.
* 4, 8 o 16 GB di RAM per macchina virtuale in base all'opzione di licenza.

### Rete
* VXLAN (Virtual Extensible LAN) privata per la sincronizzazione ad alta disponibilità (HA).
* Accesso a TMSH (Traffic Management Shell) e alla Console di gestione tramite la rete di gestione privata.

### Licenze e tariffe
Le tariffe della licenza per ciascuna VM vengono applicate a ciascun ciclo di fatturazione in base all'opzione di licenza (Buono, Migliore o Massimo) e alla larghezza di banda selezionata.

Non puoi modificare il livello di licenza dopo l'installazione del servizio. Per modificare il livello di licenza, devi rimuovere il servizio esistente e reinstallare il servizio utilizzando un'opzione di licenza diversa.
{:important}

## Considerazioni sull'installazione per F5 on IBM Cloud

Prima di installare il servizio F5 on {{site.data.keyword.cloud_notm}}, esamina le seguenti considerazioni.

In base al modello di licenza e alla larghezza di banda che selezioni, vengono distribuite due VM (macchine virtuali) di BIG-IP VE con la seguente configurazione:

Tabella 1. distribuzioni di CPU e RAM per diverse selezioni di larghezza di banda e modello di licenza

| Larghezza di banda massima | Modello di licenza: Buono | Modello di licenza: Migliore | Modello di licenza: Massimo |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbps           | 2 vCPU, 4 GB di RAM    | 4 vCPU, 8 GB di RAM      | 8 vCPU, 16 GB di RAM   |
| 200 Mbps          | 2 vCPU, 4 GB di RAM    | 4 vCPU, 8 GB di RAM      | 8 vCPU, 16 GB di RAM   |
| 1 Gbps            | 2 vCPU, 4 GB di RAM    | 4 vCPU, 8 GB di RAM      | 8 vCPU, 16 GB di RAM   |
| 3 Gbps            | 8 vCPU, 16 GB di RAM   | 8 vCPU, 16 GB di RAM     | 8 vCPU, 16 GB di RAM   |
| 5 Gbps            | 8 vCPU, 16 GB di RAM   | 8 vCPU, 16 GB di RAM     | 8 vCPU, 16 GB di RAM   |
| 10 Gbps           | 8 vCPU, 16 GB di RAM   | 8 vCPU, 16 GB di RAM     | 8 vCPU, 16 GB di RAM   |

### Ulteriori considerazioni

* F5 BIG–IP limita la velocità effettiva dell'applicazione in base alla larghezza di banda massima scelta. Poiché le prestazioni della rete sono influenzate da molti fattori, non tutte le configurazioni e topologie possono essere in grado di raggiungere la larghezza di banda massima scelta.
* La coppia HA (alta disponibilità) di VM BIG-IP VE verrà distribuita solo nel cluster predefinito.

  Inoltre, viene prenotato anche il 100% di CPU e RAM per le due VM BIG-IP VE perché queste VM si trovano nel piano dati delle comunicazioni di rete ed è fondamentale che per loro siano ancora disponibili risorse.

  Per calcolare la prenotazione di CPU e RAM per una singola VM BIG-IP VE, utilizza la seguente formula:

  `Prenotazione CPU = velocità CPU del server ESXi * numero di vCPU` (dalla tabella 1)

  `Prenotazione RAM = dimensione RAM` (dalla tabella 1)

### Considerazioni sulla pianificazione
Per evitare errori con F5 on {{site.data.keyword.cloud_notm}}, devi soddisfare i seguenti requisiti:
* Sono disponibili almeno due server ESXi attivi per le due VM BIG-IP VE da distribuire con la regola di anti-affinità di mantenere le VM su server separati.
* I due server ESXi attivi hanno sufficienti risorse disponibili in modo che una VM BIG-IP VE possa essere ospitata su ciascun server ESXi con prenotazione del 100% di CPU e RAM.
* VMware vSphere HA dispone di risorse sufficienti per ospitare due VM BIG-IP con il 100% di CPU e RAM.

A causa di questi requisiti, devi pianificare lo spazio che serve per F5 on {{site.data.keyword.cloud_notm}}. Se necessario, prima di ordinare F5 on {{site.data.keyword.cloud_notm}}, aggiungi 1-2 server ESXi alla tua istanza e/o riduci la prenotazione di CPU di vSphere HA per il failover.

## Esempio di ordine di F5 on IBM Cloud

Ordini un'istanza **Small** di VMware vCenter Server con 2 server ESXI con la seguente configurazione: sedici core a 2,10 GHz ciascuno con 128 GB di RAM. Per F5 on {{site.data.keyword.cloud_notm}}, selezioni il modello di licenza **Massimo** e un valore di 5 Gbps per **Larghezza di banda massima**.

In questo caso, una singola VM BIG-IP richiede, su ciascun server:
* 2,1 GHz * 8 vCPU = 16,8 GHz di CPU e
* 16 GB di RAM

In totale, si tratta di 33,6 GHz di CPU e 32 GB di RAM per due VM BIG-IP.

Ogni server ESXi ha una capacità di 16 core * 2,1 GHz = 33,6 GHz, quindi soddisfiamo i primi due requisiti se entrambi i server sono attivi e ci sono almeno 16,8 GHz di CPU e 16 GB di RAM disponibili su ciascun server.

Tuttavia, per impostazione predefinita, vSphere HA riserva il 50 percento di CPU e RAM per il failover sulle istanze vCenter Server che sono state inizialmente distribuite con 2 server ESXi. Per questo esempio, è disponibile quanto segue:

`50% di 2 * 16 core * 2,1 GHz = 33,6 GHz disponibili`

Poiché ci saranno altri carichi di lavoro presenti sui server ESXi, ad esempio, VMware vCenter Server, Controller VMware NSX, VMware NSX Edge, utilizzando queste risorse non possiamo soddisfare il terzo requisito, perché abbiamo bisogno di 33,6 GHz di CPU e 32 GB di RAM per le due VM BIG-IP.

In questo caso, l'installazione di F5 on {{site.data.keyword.cloud_notm}} potrebbe non riuscire, a meno che almeno un server ESXi venga aggiunto all'ambiente e le prenotazioni di failover di vSphere HA vengano aggiornate in modo appropriato per garantire che ci siano risorse sufficienti per due VM BIG-IP VE. Se sono necessarie risorse aggiuntive per eseguire il servizio F5 on {{site.data.keyword.cloud_notm}}, puoi aggiungere altri server ESXi prima di installare F5 on {{site.data.keyword.cloud_notm}}.

## Considerazioni sulla rimozione di F5 on IBM Cloud

Prima di rimuovere il servizio F5 on {{site.data.keyword.cloud_notm}}, assicurati che la configurazione esistente di BIG-IP VE sia stata rimossa correttamente. In particolare, il traffico di rete deve essere instradato attorno a BIG-IP VE anziché tramite BIG-IP VE. In caso contrario, il traffico di dati esistente dal tuo ambiente potrebbe essere influenzato.

### Link correlati

* [Ordine di F5 on {{site.data.keyword.cloud_notm}}](f5_ordering.html)
* [Gestione di F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web F5](https://f5.com/){:new_window}
