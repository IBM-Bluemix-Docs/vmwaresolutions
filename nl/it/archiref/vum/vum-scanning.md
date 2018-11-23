---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Scansione e revisione

Quando esegui la scansione di host, macchine virtuali (VM) e dispositivi virtuali, li valuti rispetto alle baseline e ai gruppi di baseline per determinarne il livello di conformità. Gli oggetti di inventario vengono sottoposti a scansione e i risultati vengono esaminati per determinare la loro conformità alle baseline e ai gruppi di baseline. I risultati della scansione possono essere filtrati mediante ricerca di testo, selezione del gruppo, selezione della baseline e selezione dello stato di conformità. Puoi avviare le seguenti scansioni:
*	**Avviare manualmente una scansione di host vSphere ESXi** - Puoi eseguire la scansione degli host vSphere ESXi nell'inventario di vSphere in base alle baseline e ai gruppi di baseline collegati.
*	**Avviare manualmente una scansione di macchine virtuali e dispositivi virtuali** - Puoi eseguire la scansione di macchine e dispositivi virtuali nell'inventario di vSphere in base alle baseline e ai gruppi di baseline collegati.
*	**Avviare manualmente una scansione di un oggetto contenitore** - Avvia una scansione simultanea di host, VM e dispositivi virtuali, eseguendo la scansione di un oggetto contenitore che sia un data center o una cartella del data center.
*	**Pianificare una scansione** - Puoi configurare il client web vSphere per eseguire la scansione di VM, dispositivi virtuali e host ESXi in momenti specifici o a intervalli appropriati.

## Avvio manuale di una scansione degli host vSphere ESXi

1. Fai clic su **Scan for Updates** e seleziona **Patches and Extensions and Upgrades**, quindi fai clic su **OK**.
2. Al termine della scansione, seleziona **Critical Host Patches**. Nel pannello in basso, controlla i dettagli della patch per ciascun host facendo clic sul numero in **Number of Patches**. Una finestra mostra le informazioni sulla patch.
3. Esamina i dettagli e ripeti per le **Non-Critical Patches**.

  I file di log di VUM sono ubicati in _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

## Avvio manuale di una scansione di macchine virtuali e dispositivi virtuali

Puoi eseguire la scansione di VM e dispositivi virtuali nell'inventario di vSphere in base alle baseline e ai gruppi di baseline collegati. Le macchine e i dispositivi virtuali selezionati vengono scansionati rispetto alle baseline collegate, a seconda delle opzioni che selezioni. Vengono scansionati anche tutti gli oggetti figlio, quindi quanto più grande è l'infrastruttura virtuale e più in alto nella gerarchia di oggetti di cui avvii la scansione, tanto più tempo impiegherà la scansione e più accurata sarà la vista di conformità.

1.	Utilizzando il client web vSphere, seleziona **Home** > **VMs and Templates**.
2.	Fai clic con il tasto destro su una _macchina virtuale_, un _dispositivo virtuale_ o una _cartella di macchine e dispositivi virtuali_ e fai clic su **Scan for Updates**.
3.	Seleziona i tipi di aggiornamenti da sottoporre a scansione. Le opzioni sono: _aggiornamenti dispositivo virtuale, aggiornamenti hardware VM_ e _aggiornamenti VMware Tools_.
4.	Fai clic su **Scan**.

##	Avvio manuale di una scansione di un oggetto contenitore

Avvia una scansione simultanea di host, VM e dispositivi virtuali, eseguendo la scansione di un oggetto contenitore che sia un data center o una cartella del data center.
1.	Utilizzando il client web vSphere, seleziona **Home** > **VMs and Templates**.
2.	Fai clic con il tasto destro su un _datacenter_ o una _cartella del datacenter_ e fai clic su **Scan for Updates**.
3.	Seleziona i tipi di aggiornamenti da sottoporre a scansione. Le opzioni sono: _aggiornamenti dispositivo virtuale, aggiornamenti hardware VM_ e _aggiornamenti VMware Tools_.
4.	Fai clic su **Scan**.

##	Pianificazione di una scansione

Puoi configurare il client web vSphere per eseguire la scansione di VM, dispositivi virtuali e host vSphere ESXi in momenti specifici o a intervalli appropriati.

1.	Utilizzando il client web vSphere, seleziona un oggetto dall'inventario. Vengono scansionati anche tutti gli oggetti figlio dell'oggetto selezionato.
2.	Seleziona la **scheda Monitor** e fai clic su **Task & Events**.
3.	Seleziona **Scheduled Tasks** e fai clic su **Schedule a New Task**.
4.	Seleziona **Scan for Updates** dall'elenco a discesa che viene visualizzato. Viene visualizzata la procedura guidata Scan for Updates.
5.	Nella pagina Edit Settings, seleziona i tipi di aggiornamenti per la scansione dell'oggetto di inventario. Devi selezionare almeno un tipo di scansione. Nella pagina Scheduling options, descrivi e pianifica l'attività di scansione.
6.	Immetti un nome univoco e, facoltativamente, una descrizione per l'attività di scansione. Fai clic su **Change** per impostare la frequenza e l'ora di inizio dell'attività di scansione. Fai clic su **OK**.
7.	L'attività di scansione viene elencata nella vista Scheduled Tasks del client web vSphere.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
