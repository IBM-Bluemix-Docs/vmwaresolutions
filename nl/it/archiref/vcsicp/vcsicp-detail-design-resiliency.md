---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Backup, ripristino di emergenza e scalabilità

## Backup e DR

###	Backup VCS

Come parte di {{site.data.keyword.vmwaresolutions_full}}, il software di backup Veeam viene facoltativamente distribuito su una VSI (Virtual Server Instance) {{site.data.keyword.cloud_notm}} utilizzando {{site.data.keyword.cloud_notm}} Endurance Storage al di fuori del cluster VMware. Lo scopo di questo software è di eseguire il backup dei componenti di gestione in questa soluzione.

### Backup NSX

Un corretto backup di tutti i componenti NSX è fondamentale per ripristinare il sistema al suo stato operativo in caso di malfunzionamento. Non è sufficiente per eseguire il backup delle VM NSX, la funzione di backup NSX all'interno di NSX Manager deve essere utilizzata per un backup appropriato. Questo richiede che venga specificato un server FTP o SFTP per il repository dei dati di backup NSX.
Il backup NSX Manager contiene tutta la configurazione NSX, inclusi i controller, le entità di commutazione logica e di instradamento, la sicurezza, le regole del firewall e tutto quello che hai configurato all'interno dell'IU o dell'API NSX Manager. I backup del database vCenter e degli elementi correlati come gli switch virtuali devono essere eseguiti separatamente. La configurazione NSX deve essere sottoposta a backup insieme ad un backup vCenter.

###	Backup e DR per IBM Cloud Private

I backup per una distribuzione ICP sono cruciali per ripristinare il sistema al suo stato di lavoro se si verifica un errore. In un backup VM tradizionale, c'è un punto critico, ogni nodo master ICP esegue etcd e la documentazione etcd indica chiaramente di non utilizzare il backup VM tradizionale per il ripristino.

{{site.data.keyword.cloud_notm}} Private al livello di piattaforma, devi eseguire il backup di questi componenti:

-	**Etcd** — viene utilizzato per archiviare le risorse Kubernetes così come le informazioni di stato di Calico.
-	**Docker Registry** — registro di immagini private utilizzato per archiviare i file dell'immagine contenitore in un repository di immagini.
-	**MongoDB** — database utilizzato dal servizio di misurazione, dal server del repository Helm, dal server dell'API Helm, dalla configurazione LDAP, dal tenant (spazio dei nomi) e dalle configurazioni del ruolo team/user/usergroup.
-	**MariaDB** — database che viene utilizzato da OIDC.
-	**Elasticsearch** — archivia i log del sistema e dell'applicazione.
-	**Prometheus** — archivia i dati per il monitoraggio.
-	**Persistent storage** — utilizzato per i servizi di gestione che utilizzano il volume persistente ICP o Kubernetes e il provider di archiviazione. Puoi utilizzare la tecnologia di backup o ripristino fornita dal provider di archiviazione. Un processo simile può essere esteso anche all'applicazione del tuo utente.

###	Backup e DR per CAM
Il backup per una distribuzione CAM è cruciale per ripristinare il sistema al suo stato di lavoro se si verifica un errore. Il backup di CAM richiede al cliente di eseguire il backup dei seguenti componenti:
-	**Database Mongo** – Il database CAM principale.
-	**Database Maria** - Utilizzato da CAM Blueprint Designer.
-	**NFS/GlusterFS** - I dati CAM risiedono in quattro volumi persistenti.

### Backup e DR per IKS
I backup del database etcd vengono forniti al cliente come parte del servizio gestito, devi eseguire il backup di tutti i dati dell'applicazione.

## Scalabilità

### Scalabilità VCS

Dopo la distribuzione degli host iniziali, l'utente ha la capacità di ridimensionare la capacità di calcolo dall'interno del portale {{site.data.keyword.cloud_notm}} for VMware.

Questo ridimensionamento al di fuori dell'ambiente segue uno di questi tre percorsi:
- Aggiunta di nuovi siti gestiti da vCenter Server separati.
- Aggiunta di nuovi cluster.
- Aggiunta di nuovi host a un cluster esistente.

####	Distribuzioni multisito
VMware on {{site.data.keyword.cloud_notm}} può utilizzare i data center in tutto il mondo di IBM Cloud e il backbone di rete integrato per consentire la distribuzione e il funzionamento di vari casi di utilizzo di più aree geografiche in solo una frazione del tempo necessario a costruire da zero un'infrastruttura di questo tipo.

####	Ridimensionamento con il nuovo cluster
L'utente ha anche l'opzione di ridimensionare la capacità di calcolo creando un nuovo cluster dall'interno della console, ordinando gli host e i nuovi host che vengono automaticamente aggiunti al nuovo cluster. Questa opzione creerà un cluster separato nell'ambiente e fornirà agli utenti la possibilità di suddividere in modo logico e fisico i carichi di lavoro di gestione e di applicazione, la capacità di suddividere i carichi di lavoro in base ad altre caratteristiche (ad esempio, il cluster di database Microsoft SQL) e la capacità di distribuire le applicazioni in topologie ad elevata disponibilità.

####	Ridimensionamento del cluster esistente
L'utente può ridimensionare un cluster esistente ordinando gli host dall'interno della console e i nuovi host che vengono aggiunti automaticamente al cluster. Tieni presente che potresti dover regolare la politica di prenotazione dell'alta disponibilità (HA) per in cluster in base ai loro requisiti di prenotazione.

### Scalabilità ICP
In base alla capacità di calcolo disponibile presso le ubicazioni cloud e in loco, l'utente ha la capacità di ridimensionare l'architettura del nodo dal nodo di avvio inizialmente distribuito.

Il ridimensionamento dell'ambiente permette di:
- Espandere i nodi di lavoro ICP.
- Espandere e utilizzare l'offerta IKS.

####	Espansione ICP
I nodi di lavoro della macchina virtuale ICP vengono ridimensionati per espandere il calcolo e l'applicazione:
  - Il cliente fornisce una nuova macchina virtuale, nella stessa VXLAN in cui viene distribuito ICP.
  - I clienti possono ridimensionare i nodi di lavoro, eseguendo il provisioning di nuove macchine virtuali, accedendo al nodo di avvio ed eseguendo un comando per portare i nuovi nodi nel cluster.
  - Utilizza CAM per automatizzare il provisioning della VM ed eseguire i comandi per l'aggiunta al cluster ICP.


###  Espansione IKS
Gli utenti possono fornire un ambiente IKS tramite il portale {{site.data.keyword.cloud_notm}} per estendere/utilizzare un ambiente contenitore.

Le distribuzioni dell'applicazione in IKS possono essere eseguite tramite:
- I collegamenti/servizi IKS sono sviluppati in CAM e pubblicati nel catalogo ICP.
- Miglioramento futuro di Multi-Cloud Manager per gestire le istanze IKS
- Riga di comando Helm
- Utilizza i cluster a più zone per incrementare l'elevata disponibilità.

### Link correlati
* [Adding or removing cluster nodes](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Aggiunta di nodi di lavoro ridimensionando un pool di nodi di lavoro esistente](../../../../containers/cs_clusters.html#resize_pool)
* [How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [ICP backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
