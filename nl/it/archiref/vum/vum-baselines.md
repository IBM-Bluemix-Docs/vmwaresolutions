---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Creazione di baseline e collegamento agli oggetti di inventario

Le baseline contengono una raccolta di una o più patch, estensioni, service pack, correzioni di bug o aggiornamenti e possono essere classificate come baseline di patch, estensione o aggiornamento. I gruppi di baseline vengono assemblate dalle baseline esistenti. I gruppi di baseline dell'host possono contenere una singola baseline di aggiornamento e varie baseline di patch ed estensione. I gruppi di baseline di macchine virtuali e dispositivi virtuali possono contenere fino a tre baseline di aggiornamento: una baseline di aggiornamento per VMware Tools, una baseline di aggiornamento per l'hardware della macchina virtuale e una baseline di aggiornamento per il dispositivo virtuale.

VUM include baseline predefinite che non possono essere modificate o eliminate. Puoi utilizzare le baseline predefinite oppure creare baseline di patch, estensione e aggiornamento che soddisfino i tuoi criteri. Le baseline personalizzate che crei e le baseline predefinite possono essere combinate in gruppi di baseline.

VUM include baseline predefinite che puoi utilizzare per eseguire la scansione di uno qualsiasi dei seguenti dispositivi per determinare se gli host nel tuo ambiente sono aggiornati con le patch più recenti o se i dispositivi virtuali e le macchine virtuali sono aggiornati alla versione più recente:
* Qualsiasi macchina virtuale
* Qualsiasi dispositivo virtuale
* Qualsiasi host

Le baseline predefinite sono le seguenti:
* **Critical Host Patches (Predefinita)** - Verifica che gli host ESXi siano conformi con tutte le patch critiche.
* **Non-Critical Host Patches (Predefinita)** - Verifica che gli host ESXi siano conformi con tutte le patch facoltative.
* **VMware Tools Upgrade to Match Host (Predefinita)** - Verifica che le macchine virtuali siano conformi con l'ultima versione di VMware Tools sull'host. Update Manager supporta l'aggiornamento di VMware Tools per le macchine virtuali sugli host che eseguono ESXi 5.5.x e versioni successive.
* **VM Hardware Upgrade to Match Host (Predefinita)** - Verifica che l'hardware virtuale di una macchina virtuale sia conforme con l'ultima versione supportata dall'host. Update Manager supporta l'aggiornamento alla versione vmx-13 dell'hardware virtuale sugli host che eseguono ESXi 6.5.
* **VA Upgrade to Latest (Predefinita)** - Verifica che il dispositivo virtuale sia conforme con l'ultima versione rilasciata per il dispositivo.

Per utilizzare le baseline e i gruppi di baseline, devi collegarli agli oggetti di inventario selezionati come, ad esempio, gli oggetti contenitore, le macchine virtuali, i dispositivi virtuali o gli host. Anche se puoi collegare le baseline e i gruppi di baseline ai singoli oggetti, un metodo più efficiente consiste nel collegarli agli oggetti contenitore, come cartelle, vApp, cluster o data center. In questo passo, utilizzeremo le baseline predefinite per gli host nel cluster.

1. Utilizzando il client web vSphere, passa a **Home** > **Hosts and Clusters**.
2. Fai clic sull'oggetto cluster di cui vuoi eseguire la scansione.
3. Fai clic su **Attach Baseline**, seleziona le due baseline di patch predefinite e fai clic su **OK**.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
