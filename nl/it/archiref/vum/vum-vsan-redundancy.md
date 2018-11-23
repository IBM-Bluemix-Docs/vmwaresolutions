---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Ridondanza vSAN della macchina virtuale

Quando metti un host vSphere ESXi in modalità di manutenzione su un cluster vSAN, ti viene richiesto di selezionare una modalità di rimozione dei dati. La selezione della modalità può avere un impatto sulle macchine e sui dispositivi virtuali che utilizzano l'archivio dati vSAN:
* Una **migrazione completa dei dati** rimuove tutti i dati dall'host e li trasferisce agli altri host vSphere ESXi nel cluster vSAN. Questa modalità di rimozione comporta la maggiore quantità di trasferimento dati e consuma più tempo e risorse. Tutti i componenti presenti sull'archiviazione locale dell'host selezionato vengono migrati altrove nel cluster. Quando l'host entra in modalità di manutenzione, tutte le macchine e i dispositivi virtuali hanno accesso ai loro componenti di archiviazione e sono ancora conformi alle politiche di archiviazione assegnate. La rimozione completa dei dati può richiedere molto tempo e prolungare la durata della finestra di manutenzione per un aggiornamento.
* La modalità **ensure accessibility data evacuation** è l'opzione predefinita e quando l'host vSphere ESXi viene messo in modalità di manutenzione, vSAN garantisce che tutte le macchine o dispositivi virtuali accessibili sull'host rimangano accessibili. Poiché si verifica solo la rimozione parziale dei dati, la macchina o il dispositivo virtuale potrebbe non essere più pienamente conforme a una politica di archiviazione della VM durante la rimozione e potrebbe non avere accesso a tutte le sue repliche. Se si verifica un errore mentre l'host è in modalità di manutenzione e il livello primario di errori da tollerare è impostato su 1, si verificherà una perdita di dati e la macchina o il dispositivo virtuale potrebbe non essere disponibile.
* Nella modalità **no data migration**, vSAN non rimuove alcun dato dall'host quando entra in modalità di manutenzione. Mentre questo riduce il tempo per entrare in modalità di manutenzione e quindi riduce la durata della finestra di manutenzione, alcune macchine o dispositivi virtuali potrebbero diventare inaccessibili.

Questa sezione crea una nuova politica di archiviazione della VM che consente di selezionare la modalità **ensure accessibility data evacuation** per ridurre le finestre di manutenzione, ma riduce il rischio che un errore di un host mentre un altro è un modalità di manutenzione renda inaccessibile una macchina o un dispositivo virtuale. Per qualsiasi macchina o dispositivo virtuale, laddove non sia accettabile che diventi non ridondante quando un host vSAN viene messo in modalità di manutenzione, completa il seguente processo prima di eseguire eventuali azioni di correzione. Sarà richiesto un cluster con almeno 6 host.

1. Crea un nuovo profilo vSAN con le impostazioni di RAID 5/6 e FTT =2 (RAID 6) e applica quindi questa politica sulle macchine o sui dispositivi virtuali.

2. Attendi che vSAN abbia completato la sincronizzazione prima di avviare qualsiasi azione di correzione. Lo stato di completamento può essere verificato passando alla **pagina vSAN Virtual Objects monitoring** per il cluster ed esaminando il **Completion Status**.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
