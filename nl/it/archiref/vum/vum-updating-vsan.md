---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# Aggiornamento dei cluster vSAN

vSAN genera baseline e gruppi di baseline di sistema da utilizzare con VUM e puoi utilizzare queste baseline consigliate per aggiornare software, patch ed estensioni per gli host vSphere ESXi nella tua istanza vCenter Server che utilizza vSAN. vSAN 6.6.1 e versioni successive genera consigli di build automatizzata per i cluster vSAN. vSAN combina le informazioni contenute nella Guida alla compatibilità VMware e nel catalogo delle release di vSAN con le informazioni sulle release vSphere ESXi installate.

Questi aggiornamenti consigliati forniscono la migliore release disponibile per mantenere il tuo hardware in uno stato supportato.
* **Baseline del sistema vSAN** - I consigli di build vSAN vengono forniti attraverso le baseline del sistema vSAN per VUM. vSAN genera un gruppo di baseline per ogni cluster vSAN e vengono elencate nel riquadro Baselines della scheda Baselines and Groups. VUM esegue automaticamente la scansione di ciascun cluster vSAN per verificare la conformità rispetto al gruppo di baseline. Tuttavia, per aggiornare il tuo cluster vSAN, devi correggere manualmente la baseline del sistema tramite VUM; puoi correggere la baseline del sistema vSAN su un singolo host o sull'intero cluster.
* **Catalogo delle release vSAN** - Il catalogo delle release di vSAN conserva informazioni sulle versioni disponibili, l'ordine delle preferenze per le release e le patch critiche necessarie per ogni release. vSAN richiede la connessione a internet per accedere al catalogo delle release. Non è necessario essere iscritti al programma per il miglioramento dell'esperienza del cliente (Customer Experience Improvement Program, CEIP) per vSAN per accedere al catalogo delle release.
* Utilizzo dei **consigli di build vSAN** - VUM controlla le release vSphere ESXi installate rispetto all'elenco HCL (Hardware Compatibility List) nella Guida alla compatibilità VMware. Determina il percorso di aggiornamento corretto per ogni cluster vSAN, in base al catalogo delle release vSAN corrente. vSAN include anche i driver e gli aggiornamenti di patch necessari per la release consigliata nella sua baseline del sistema. I consigli di build vSAN assicurano che ciascun cluster vSAN rimanga allo stato di compatibilità hardware corrente o migliore. Se l'hardware nel cluster vSAN non è incluso nell'elenco HCL, vSAN consiglia un aggiornamento all'ultima release.

L'aggiornamento dei cluster vSAN procede nella seguente sequenza di attività:
* **Abilita il flusso di lavoro di vSAN Online Health** – Questo flusso di lavoro abilita le baseline vSAN in VUM in modo che gli aggiornamenti possano essere riesaminati e corretti. Deve essere eseguito inizialmente solo per abilitare vSAN con VUM
* **Prerequisiti** – Comprendi i prerequisiti, il processo e le restrizioni
* **Aggiorna vCenter Server Appliance**. Per ulteriori informazioni, vedi [Aggiornamento di VCSA e vCenter collegati a SSO](vum-updating-vcsa.html).
* **Aggiorna gli host vSphere ESXi** – Per ulteriori informazioni, vedi  [Creazione di baseline e collegamento a oggetti di inventario](vum-baselines.html).
* **Aggiorna il formato del disco vSAN** - Fai riferimento ad Aggiorna il formato del disco vSAN. L'aggiornamento del formato del disco è facoltativo, ma per ottenere risultati migliori, aggiorna gli oggetti per utilizzare la versione più recente. Il formato su disco espone il tuo ambiente alle funzioni complete di vSAN.

## Abilita il flusso di lavoro di vSAN Online Health

Eseguendo le attività indicate in questa sezione si rendono disponibili le baseline vSAN in VUM. vSAN 6.6.1 e versioni successive fornisce un processo di aggiornamento automatico trasparente per garantire che un cluster vSAN sia aggiornato con la migliore release disponibile per mantenere la tua istanza VMware vCenter Server on {{site.data.keyword.cloud}} in uno stato supportato con:
* **Consigli di versione vSAN** - generati automaticamente utilizzando le informazioni della Guida alla compatibilità VMware, il catalogo delle release vSAN e la rilevazione della configurazione hardware sottostante. Include anche i driver e gli aggiornamenti di patch necessari per la release consigliata nella sua baseline del sistema.
* **Consigli di build vSAN** - assicurano che i cluster rimangano allo stato di compatibilità hardware corrente o migliore.

Prima di continuare, assicurati che VCSA sia vCenter 6.5 Patch 2 o versione più recente, in quanto vengono risolti alcuni problemi di utilizzo del proxy. Per ulteriori informazioni, vedi [Aggiornamento di VCSA e vCenter collegati a SSO](vum-updating-vcsa.html).

Per vedere gli aggiornamenti vSAN in VUM viene seguito il flusso di lavoro di vSAN Online Health. Pertanto, vSAN Online Health deve connettersi ai siti `vcsa.vmware.com` e `vmware.com` per eseguire questi controlli di integrità online; per abilitare il flusso di lavoro di vSAN Online Health dobbiamo:
* Configurare il VCSA per utilizzare il proxy.
* Configurare vSAN per utilizzare il proxy.
* Abilitare il programma per il miglioramento dell'esperienza del cliente (Customer Experience Improvement Program, CEIP).
* Eseguire un caricamento di prova e convalidare che il caricamento abbia funzionato.

Il primo passo consiste nell'aggiungere le tue credenziali di my.vmware.com al motore di vSAN Build Recommendation. Dopo aver eseguito correttamente l'accesso, vSAN genererà un gruppo di baseline di aggiornamenti consigliati per ogni cluster vSAN. Le baseline del sistema vSAN vengono elencate nel riquadro Baselines della scheda Baselines and Groups.

### Configura il VCSA per utilizzare il proxy

1.	Dal browser web del tuo server jump, connettiti all'interfaccia di gestione VCSA `https://<vCenter ip>:5480`
2.	Utilizzando le credenziali della console IC4VS, accedi all'interfaccia di gestione VCSA come root.
3.	Nell'interfaccia di gestione di vCenter Server Appliance, fai clic su **Networking** e su **Manage**.
4.	Per configurare un server proxy, nel riquadro Proxy Settings, fai clic su **Edit**.
5.	Seleziona **Use a Proxy Server**, immetti le impostazioni del server proxy e fai clic su **OK**.

Nota che ci sono dei report in cui sembra che le informazioni sul proxy siano impostate solo per HTTP ma non per HTTPS. Per poter configurare le informazioni sul proxy anche per il traffico HTTPS, è necessario prima abilitarlo. Dopo aver effettuato l'accesso a VCSA tramite SSH, utilizza il comando proxy.get per visualizzare la configurazione e confermare che i parametri HTTPS non sono impostati.

Se i parametri HTTPS non sono impostati, utilizza il seguente comando:
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### Configura vSAN per utilizzare il proxy
1. Passa a **Home** > **Hosts and Clusters**, seleziona il **Cluster vSAN** nel riquadro di navigazione, seleziona la **scheda Configure** e passa a **vSAN** e quindi a **General**. Scorri fino alla sezione **Internet Connectivity** e fai clic su **Edit**.
2. Immetti l'indirizzo IP e il numero di porta del proxy e fai clic su **OK**.

### Abilita il programma per il miglioramento dell'esperienza del cliente (Customer Experience Improvement Program, CEIP)

Questo passo è facoltativo. Utilizzando il client web vSphere, passa a **Home** > **Administration** > **Customer Experience Improvement Program** e fai quindi clic su **Join**.

### Esegui un caricamento di prova e convalida che il caricamento abbia funzionato
1. Utilizzando il client web vSphere, passa a **Home** > **Hosts and Clusters**. Seleziona il cluster richiesto, seleziona la **scheda Monitor** e la pagina **vSAN**, quindi fai clic su **Health**. Fai clic su **Enable Online Health**.
2. Fai clic sul pulsante **Retest** e attendi il completamento del processo.
3. In Health viene visualizzato un nuovo controllo chiamato _"Online health connectivity"_ e il pulsante Enable Online Health cambia in Retest with Online Health.
4. Fai clic sul pulsante **Retest with Online Health** per attivare il primo caricamento e attendi il completamento del processo, esaminando lo stato nel riquadro Recent Tasks. Il nome del test dovrebbe cambiare in Online health (Last check: just now).
5. Al termine, nella finestra Health, scorri ed espandi la sezione vSAN Build Recommendation e fai clic su **vSAN Build Recommendation Engine Health**.
6. Fai clic su **Login to my.vmware.com** e immetti le tue credenziali. Al termine del processo, lo stato di **Test Result** diventa **Passed**.
7. Fai clic sulla **scheda Update Manager** e dovresti ora vedere che il cluster vSAN è stato aggiunto alle baseline.

## Prerequisiti

Prima di avviare il processo di aggiornamento vSAN, assicurati che siano soddisfatti i seguenti requisiti:
* Esamina gli articoli della Knowledge Base di VMware e verifica eventuali problemi di compatibilità noti tra la versione vSAN corrente e la versione vSAN di destinazione desiderata
* **L'ambiente vSphere è aggiornato**:
  - Il VCSA deve essere a un livello di patch uguale o superiore rispetto agli host vSphere ESXi. Aggiorna il VCSA secondo necessità
  - Tutti gli host devono eseguire la stessa build di ESXi. Se le versioni degli host vSphere ESXi non corrispondono, esegui l'aggiornamento
* **Tutti i dischi vSAN devono essere integri**:
  - Nessun disco deve essere guasto o assente. Questo può essere determinato tramite la vista **vSAN Disk Management** nel client web vSphere. **Home** > **Hosts and Clusters**, seleziona il **Cluster vSAN** e fai clic sulla **scheda vSAN** e su **Physical Disks**. Scorri tutti i dischi ed esamina lo stato di integrità di vSAN.
  - Non ci devono essere oggetti vSAN inaccessibili. Questo può essere verificato con il **vSAN Health Service** facendo clic su **Home** > **Hosts and Clusters** e selezionando quindi il **Cluster vSAN**. Fai clic sulla **scheda Monitor**, **vSAN** e su **Health**. Esamina i risultati del test.
  - Non ci deve essere alcuna risincronizzazione attiva all'inizio del processo di aggiornamento facendo clic **Home** > **Hosts and Clusters**, seleziona quindi il **Cluster vSAN**, fai clic sulla **scheda vSAN** e su **Resync Components**. _Il conteggio di risincronizzazione dei componenti dovrebbe essere 0_. Nota che alcune attività di risincronizzazione sono previste durante il processo di aggiornamento, poiché i dati devono essere sincronizzati dopo il riavvio dell'host.
* **Preparazione dell'host vSphere ESXi** - Quando sposti un host in modalità di manutenzione in un cluster vSAN, sono disponibili tre opzioni:
  - **No data migration** - Se selezioni questa opzione, vSAN non rimuove alcun dato da questo host. Se spegni o rimuovi l'host dal cluster, alcune macchine virtuali (VM) potrebbero diventare inaccessibili.
  - **Ensure availability** - Se selezioni questa opzione, vSAN ti consente di spostare l'host in modalità di manutenzione più velocemente rispetto alla migrazione completa dei dati e consente l'accesso alle VM nell'ambiente.
  - **Full data migration**
* **Uscita dalla modalità di manutenzione e risincronizzazione** - Quando l'host vSphere ESXi viene aggiornato e tolto dalla modalità di manutenzione, si verificherà una risincronizzazione che puoi vedere tramite il server web. Assicurati che questa operazione venga completata prima di passare al prossimo host. Una risincronizzazione si verifica in quanto l'host che è stato aggiornato può ora contribuire di nuovo all'archivio dati vSAN. È fondamentale attendere fino al termine della risincronizzazione per garantire che non ci siano perdite di dati.
* **Dopo aver avviato un aggiornamento del cluster vSAN**:
  - Non tentare di aggiornare un cluster introducendo nuove versioni nel cluster e migrando i carichi di lavoro.
  - Se introduci nuovi host, assicurati che siano della stessa versione iniziale e aggiornali insieme al resto del cluster.
  - Se aggiungi o sostituisci i dischi durante un aggiornamento, assicurati che siano formattati con la versione di formato su disco legacy appropriata, laddove applicabile.
  - Alcune modifiche di comportamento di vSAN sono controllate dal formato su disco, pertanto è importante che le versioni più recenti del formato su disco non vengano introdotte in un cluster a versione mista.

## Aggiorna vCenter Server Appliance

Per ulteriori informazioni, vedi [Aggiornamento di VCSA e vCenter collegati a SSO](vum-updating-vcsa.html).

##	Aggiorna gli host vSphere ESXi

Per ulteriori informazioni, vedi [Creazione di baseline e collegamento a oggetti di inventario](vum-baselines.html).

##	Aggiorna il formato del disco vSAN

RVC (Ruby vSphere Console) è un'interfaccia della riga di comando basata su Ruby per vSphere e può essere utilizzata per gestire VMware vSphere ESXi e vCenter. L'inventario di vSphere viene presentato in una struttura ad albero, che ti consente di navigare ed eseguire comandi sugli oggetti vCenter.

Molte attività amministrative di base possono essere eseguite in modo molto più efficiente rispetto al clic nel client vSphere. RVC è completamente implementata in VCSA e utilizza una connessione SSH al dispositivo.
1. Esegui l'SSH in VCSA e accedi utilizzando root e password forniti nella console ICVS.
2. Nel prompt, digita:
  `rvc Administrator@vsphere.local@localhost` e premi **Invio**.
3. Immetti la password dell'amministratore fornita sulla console ICVS. Ora sarai alla radice del file system virtuale, digita ls e quindi premi **Invio**; dovresti visualizzare quanto segue:
  `0 /
  1 localhost/``

5. Digita `cd 1`, immetti `ls` e premi **Invio**. Dovresti visualizzare quanto segue:
  `0 / datacenter1 (datacenter)`

6. Digita `cd 0`, immetti `ls` e premi **Invio**. Dovresti visualizzare quanto segue:

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. Digita `cd 1`, premi **Invio**, immetti `ls` e premi **Invio**. Dovresti visualizzare il tuo cluster:
  `0 cluster1 (cluster)``

8. Ora useremo i comandi VSAN su questo cluster. Per controllare lo stato del disco, digita `vsan.disks_stats 0` e premi **Invio**.

9. Assicurati che lo stato di integrità per tutti i dischi sia OK. Quindi, avvia l'aggiornamento digitando `vsan.ondisk_upgrade 0` e premendo quindi **Invio**.

10. A seconda della dimensione vSAN, questa attività potrebbe richiedere molto tempo. Una volta completata, digita `vsan.objstatusreport 0` e premi **Invio** per verificare che le versioni dell'oggetto siano aggiornate al nuovo formato su disco.

11. L'aggiornamento del cluster VSAN è ora completato. Digita `exit` e premi **Invio** per uscire da RVC.

### Link correlati

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
