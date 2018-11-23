---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Preparazione e correzione

Le patch e le estensioni possono essere facoltativamente preparate prima della correzione per garantire che vengano scaricate da VUM sull'host vSphere ESXi senza applicarle immediatamente. Durante la correzione, VUM applica le patch, le estensioni e gli aggiornamenti agli oggetti di inventario. La preparazione di patch ed estensioni accelera il processo di correzione in quanto le patch e le estensioni sono già disponibili localmente sugli host.

Se durante il processo di correzione un qualsiasi host non entra in modalità di manutenzione, VUM segnalerà un errore e il processo di correzione si interrompe e avrà esito negativo. Gli host vSphere ESXi che sono già stati corretti rimangono al livello aggiornato.

Affinché il processo di correzione funzioni correttamente, è consigliabile disabilitare alcune delle funzioni del cluster come DPM, il controllo di ammissione HA, la tolleranza di errore e disconnettere qualsiasi dispositivo rimovibile dalle macchine virtuali (VM) in modo che DRS non debba affrontare alcun problema durante la migrazione delle VM ad altri host.
Inoltre, durante l'esecuzione della procedura guidata di correzione, puoi generare report per verificare che non siano presenti impostazioni incongruenti a livello di host/VM che possono causare errori nel processo di correzione.

1.	Utilizzando il client web vSphere, seleziona **Home** > **Hosts and Clusters**.
2.	Fai clic con il tasto destro del mouse su un data center, sul cluster o su un host e seleziona **Stage Patches**.
3.	Nella pagina di selezione della baseline (Baseline Selection) della procedura guidata di preparazione (Stage), seleziona le baseline di patch ed estensioni da preparare.
4.	Seleziona gli host in cui verranno applicate le patch e le estensioni e fai clic su **Next**. Se hai selezionato di preparare patch ed estensioni in un singolo host, questo è selezionato per impostazione predefinita.
5.	Facoltativamente, deseleziona le patch e le estensioni da escludere dall'operazione di preparazione. Per ricercare all'interno dell'elenco di patch ed estensioni, inserisci il testo nella casella di testo della casella di filtro. Fai clic su **Avanti**.
6.	Esamina la pagina Ready to Complete e fai clic su **Finish**.

Il numero di patch ed estensioni preparate per l'host specifico è visualizzato nelle colonne Patches e Extensions nel riquadro inferiore della scheda Update Manager. Una volta completata una correzione, tutte le patch ed estensioni preparate, installate o meno durante la correzione, verranno eliminate dall'host.
La correzione è il processo in cui VUM applica patch, estensioni e aggiornamenti agli host vSphere ESXi, alle VM o ai dispositivi virtuali al termine di una scansione e rende conformi gli oggetti selezionati. Puoi correggere gli host, le VM o i dispositivi virtuali singolarmente o a livello di cartella, cluster o data center. VUM supporta la correzione per i seguenti oggetti di inventario utilizzando la correzione manuale o la correzione pianificata:
*	Host ESXi per la correzione di patch, estensioni e aggiornamenti.
*	VM accese, sospese o spente e template per l'aggiornamento di VMware Tools e dell'hardware della VM.
*	Dispositivi virtuali accesi creati con VMware Studio 2.0 e successive, per l'aggiornamento del dispositivo virtuale.

Se l'aggiornamento lo richiede, gli host vengono messi in modalità di manutenzione prima della correzione. VCSA migra le VM su altri host all'interno dell'istanza VMware vCenter Server on {{site.data.keyword.cloud}} prima che l'host venga messo in modalità di manutenzione.

## Per gli host in un cluster vSAN
Tieni presente il seguente comportamento per gli host che fanno parte di un cluster vSAN:
* Il completamento del processo di correzione dell'host potrebbe richiedere molto tempo.
* In base alla progettazione, solo un host da un cluster VSAN può essere in una modalità di manutenzione in un determinato momento.
* VUM corregge gli host che fanno parte di un cluster VSAN in modo sequenziale anche se imposti l'opzione per correggere gli host in parallelo.
* Per qualsiasi VM sull'host che utilizza una politica di archiviazione della VM con un'impostazione per "Numero di errori da tollerare=0", l'host potrebbe riscontrare dei ritardi insoliti quando entra in modalità di manutenzione. Il ritardo si verifica perché vSAN deve migrare i dati della VM da un disco a un altro nel cluster dell'archivio dati vSAN e questo può richiedere molte ore. Puoi aggirare questo problema impostando il "Numero di errori da tollerare=1" per la politica di archiviazione della VM, che comporta la creazione di due copie dei file della VM nell'archivio dati vSAN.
* Per qualsiasi VM sull'host che utilizza una politica di archiviazione della VM con un'impostazione per "Numero di errori da tollerare=1", la VM diventerà non ridondante quando l'host entra in modalità di manutenzione. Se questo non è accettabile, vedi [Ridondanza vSAN della macchina virtuale](vum-vsan-redundancy.html).

Per correggere host e cluster, completa la seguente procedura:
1.	Utilizzando il client web vSphere, seleziona **Home** > **Hosts and Clusters**.
2.	Dal navigatore di oggetti di inventario, seleziona un data center, un cluster o un host, fai clic sulla scheda **Update Manager** e quindi su **Remediate**. Se hai selezionato un oggetto contenitore, vengono corretti tutti gli host sotto l'oggetto selezionato. Si apre quindi la procedura guidata di correzione.
3.	Seleziona **Patch Baselines** o **Extension Baselines** a seconda del tipo di aggiornamento che vuoi eseguire sull'host. Nella pagina di selezione della baseline (Select baseline) della procedura guidata di correzione (Remediate), seleziona il **gruppo di baseline** e le **baseline** da applicare.
4.	Seleziona gli host di destinazione che vuoi correggere e fai clic su **Next**. Se hai scelto di correggere un singolo host e non un oggetto contenitore, l'host è selezionato per impostazione predefinita.
5.	Facoltativamente, nella pagina **Patches and Extensions**, deseleziona specifiche patch o estensioni da escludere dal processo di correzione e fai clic su **Next**.
6.	Facoltativamente, nella pagina **Advanced options**, seleziona l'opzione per pianificare la correzione da eseguire in un secondo momento e specifica un nome univoco e una descrizione facoltativa per l'attività. L'ora che imposti per l'attività pianificata corrisponde all'ora in VCSA. Facoltativamente, seleziona l'opzione per ignorare le avvertenze relative ai dispositivi non supportati sull'host o all'archivio dati VMFS non più supportato per continuare con la correzione. Fai clic su **Avanti**.
7.	Nella pagina **Remediation Options** dell'host, dal menu a discesa **VM Power state**, puoi selezionare la modifica dello stato di alimentazione delle VM e dei dispositivi virtuali in esecuzione sugli host da correggere. Un host non può entrare in modalità di manutenzione fino a quando le VM sull'host non vengono spente, sospese o migrate con vMotion su altri host in un cluster DRS. Alcuni aggiornamenti richiedono che un host entri in modalità di manutenzione prima della correzione. Le macchine e i dispositivi virtuali non possono essere eseguiti quando un host è in modalità di manutenzione. Per ridurre i tempi di inattività della correzione degli host a scapito della disponibilità della VM, puoi scegliere di spegnere o sospendere le VM e i dispositivi virtuali prima del processo di correzione. In un cluster DRS, se non spegni le VM, la correzione richiede più tempo ma le VM sono disponibili durante l'intero processo di correzione poiché vengono migrate con vMotion su altri host. Le selezioni sono le seguenti:

  - **Spegni le macchine virtuali** - Spegni tutte le VM e i dispositivi virtuali prima della correzione.
  - **Sospendi macchine virtuali** - Sospendi tutte le VM e i dispositivi virtuali in esecuzione prima della correzione.
  - **Non modificare lo stato di alimentazione delle VM** - Lascia le VM e i dispositivi virtuali nello stato di alimentazione corrente.

8.	Facoltativamente, seleziona **Disable any removable media devices connected to the virtual machine on the host**. VUM non corregge gli host su cui le VM hanno unità CD, DVD o minidisco collegate. Negli ambienti cluster, i dispositivi multimediali collegati potrebbero impedire vMotion se l'host di destinazione non dispone di un dispositivo identico o di un'immagine ISO montata corrispondente, il che a sua volta impedisce all'host di origine di entrare in modalità di manutenzione. Dopo la correzione, VUM ricollega i dispositivi multimediali rimovibili nel caso in cui siano ancora disponibili.
9.	Facoltativamente, seleziona **Retry entering maintenance mode in case of failure**, specifica il numero di tentativi e il tempo di attesa tra i tentativi. VUM attende il periodo di ritardo dei tentativi e riprova a mettere l'host in modalità di manutenzione tutte le volte che indichi nel campo Number of retries.
10.	In un'istanza vCenter Server non è richiesto di selezionare la casella di spunta sotto le impostazioni di patch ESXi per consentire a Update Manager di applicare patch agli host accesi avviati da PXE.
11.	Fai clic su **Avanti**.
12.	Se correggi gli host in un cluster, modifica le opzioni di correzione del cluster. La pagina **Cluster remediation options** è disponibile solo quando correggi i cluster. È possibile selezionare le seguenti opzioni:

*	**Disabilita DPM (Distributed Power Management)** se è abilitato per uno qualsiasi dei cluster selezionati – VUM non corregge i cluster con DPM attivo. DPM monitora l'utilizzo di risorse delle VM in esecuzione nel cluster. Se esiste una capacità in eccesso sufficiente, DPM consiglia di spostare le VM su altri host nel cluster e di collocare l'host originale in modalità standby per risparmiare energia. L'inserimento degli host in modalità standby potrebbe interrompere la correzione.
*	**Disabilita il controllo di ammissione HA (High Availability)** se è abilitato per uno qualsiasi dei cluster selezionati - VUM non corregge i cluster con il controllo di ammissione HA attivo. Il controllo di ammissione è una politica utilizzata da VMware HA per garantire la capacità di failover in un cluster. Se il controllo di ammissione HA è abilitato durante la correzione, le VM all'interno di un cluster potrebbero non migrare con vMotion.
*	**Disabilita la tolleranza di errore (FT)** se è abilitata. Questo influisce su tutte le VM a tolleranza d'errore nei cluster selezionati - Se la tolleranza di errore è attiva per una qualsiasi delle VM su un host, VUM non corregge tale host. Perché la tolleranza di errore sia abilitata, gli host su cui vengono eseguite le VM primarie e secondarie devono essere della stessa versione e devono avere le stesse patch installate. Se applichi patch diverse a questi host, la tolleranza di errore non può essere riabilitata.
*	**Abilita correzione in parallelo per gli host nei cluster selezionati** - Consente di correggere gli host nei cluster in modo parallelo. Se l'impostazione non è selezionata, VUM corregge gli host in un cluster in modo sequenziale. Per la correzione in parallelo puoi selezionare una delle seguenti opzioni:
    - Puoi consentire a VUM di valutare continuamente il numero massimo di host che può correggere contemporaneamente senza bloccare le impostazioni DRS.
    - Puoi specificare un limite per il numero di host che vengono corretti contemporaneamente in ciascun cluster che correggi. Nota che VUM corregge contemporaneamente solo gli host su cui le VM sono spente o sospese. Puoi scegliere di spegnere o sospendere le VM dal menu VM Power State nel riquadro Maintenance Mode Options della pagina Host Remediation Options. In base alla progettazione, solo un host da un cluster VSAN può essere in una modalità di manutenzione in un determinato momento. VUM corregge gli host che fanno parte di un cluster vSAN in modo sequenziale anche se selezioni l'opzione per correggerli in parallelo.
*	**Migra le macchine virtuali spente e sospese sugli altri host nel cluster**, se un host deve entrare in modalità di manutenzione. Update Manager migra le VM sospese e spente dagli host che devono entrare in modalità di manutenzione su altri host nel cluster. Puoi scegliere di spegnere o sospendere le VM prima della correzione nel riquadro **Maintenance Mode Settings**.
13.	Nella pagina Ready to complete, puoi facoltativamente fare clic su **Pre-check Remediation** per generare un report sulle opzioni di correzione del cluster e fare clic su **OK**. Viene visualizzata una finestra di dialogo con il report sulle opzioni di correzione del cluster. Puoi esportare questo report o copiare le voci per il tuo proprio record e fare clic su **Next**.
14.	Esamina la pagina Ready to Complete e fai clic su **Finish**.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
