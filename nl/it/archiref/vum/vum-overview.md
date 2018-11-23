---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Panoramica di VMware Update Manager

VMware Update Manager (VUM) utilizza un processo a più fasi per aggiornare gli oggetti vSphere e applicare patch o estensioni. Questo processo consente una procedura di aggiornamento uniforme con un tempo di inattività minimo del sistema. Prima di esaminare questo processo, dobbiamo comprendere i seguenti termini:
* **Oggetto di inventario** - Un oggetto all'interno di vCenter come, ad esempio, la macchina virtuale, i dispositivi virtuali o l'host vSphere ESXi.
* **Baseline** - Le baseline contengono una raccolta di una o più patch, estensioni, service pack, correzioni di bug o aggiornamenti e possono essere classificate come baseline di patch, estensione o aggiornamento. Esistono due classificazioni di baseline: host e VM/VA che hanno entrambe baseline predefinite da VMware ed è possibile aggiungere quelle personalizzate secondo necessità:
  - Baseline host predefinite:
    - Critical Host Patches
    - Non-Critical Host Patches

  - Baseline VM/VA predefinite:
    - VA Upgrade to Latest
    - VM Hardware Upgrade to Match Host
    - VMware Tools Upgrade to Match Host

* **Gruppo di baseline** - Un insieme di baseline non conflittuali, che combina diversi tipi di baseline e che in base alle quali scansiona e corregge un oggetto di inventario nel complesso. Se il gruppo di baseline contiene sia baseline di aggiornamento che di patch o estensione, l'aggiornamento viene eseguito per primo.
* **Scansione** - La scansione è il processo in cui uno o più oggetti di inventario vengono valutati in base alla baseline o al gruppo di baseline.
* **Preparazione** - La preparazione garantisce che le patch e le estensioni vengano scaricate negli host vSphere ESXi prima della correzione ed è un passo facoltativo per ridurre al minimo il tempo in cui gli host restano in modalità di manutenzione.
* **Correzione** - La correzione è il processo in cui VUM applica patch, estensioni e aggiornamenti a uno o più oggetti di inventario.

Pertanto, il processo di VUM è il seguente:
* Un oggetto di inventario o un gruppo di oggetti viene sottoposto a scansione per verificarne la conformità rispetto a una baseline o a un gruppo di baseline.
* Dopo una revisione, le patch e le estensioni possono essere facoltativamente preparate, prima di correggerle.

Il download di aggiornamenti, patch di host, estensioni e metadati correlati è un processo automatico predefinito che può essere modificato. Per impostazione predefinita, a intervalli regolari configurabili, VUM contatta VMware o fonti di terze parti per raccogliere le seguenti informazioni su aggiornamenti, patch o estensioni disponibili:

* Metadati relativi a tutte le patch di ESXi 5.5 e ESXi 6.x indipendentemente dal fatto che nel tuo ambiente siano presenti host di tali versioni.
* Metadati relativi alle patch di ESXi 5.5 e ESXi 6.x nonché alle estensioni provenienti da indirizzi URL di fornitori di terze parti.
* Notifiche, avvisi e richiami di patch per gli host ESXi 5.5 e ESXi 6.x.
* Metadati relativi agli aggiornamenti per i dispositivi virtuali.

VUM supporta il richiamo di patch per host che eseguono ESXi 5.0 o versioni successive. Una patch viene richiamata se la patch rilasciata presenta problemi o potenziali problemi. Dopo aver eseguito la scansione degli host nell'istanza VMware vCenter Server on {{site.data.keyword.cloud}}, VUM ti avvisa se la patch richiamata è stata installata su un determinato host. Le patch richiamate non possono essere installate sugli host con VUM. VUM inoltre elimina tutte le patch richiamate dal repository di patch. Dopo che viene rilasciata una patch che corregge il problema, VUM scarica la nuova patch nel suo repository di patch. Se hai già installato la patch problematica, VUM ti avvisa che è stata rilasciata una correzione e ti chiede di applicare la nuova patch.

L'interfaccia del client VUM fornisce due viste principali:
*	Vista di amministrazione (Administration)
*	Vista di compatibilità (Compliance)

##	Vista di amministrazione (Administration)
Per accedere alla vista di amministrazione, passa a **Home** > **Update Manager** e seleziona l'indirizzo IP dell'istanza Update Manager. Nella vista di amministrazione, puoi effettuare le seguenti attività:
*	Configurare le impostazioni di Update Manager
*	Creare e gestire baseline e gruppi di baseline
*	Visualizzare gli eventi di Update Manager
*	Esaminare il repository di patch e gli aggiornamenti dei dispositivi virtuali disponibili
*	Esaminare e controllare le notifiche
*	Importare immagini ESXi

##	Vista di compatibilità (Compliance)
Per accedere alla vista di conformità di un oggetto di inventario selezionato, passa a **Hosts and Clusters** o **VMs and Templates** e fai clic sulla **scheda Update Manager**. Nella vista di conformità di Update Manager, puoi effettuare le seguenti attività:
*	Visualizzare la conformità ed eseguire la scansione dei risultati per ogni oggetto di inventario selezionato
*	Collegare e scollegare baseline e gruppi di baseline da un oggetto di inventario selezionato
*	Eseguire la scansione di un oggetto di inventario selezionato
*	Preparare patch o estensioni negli host
*	Correggere un oggetto di inventario selezionato

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
