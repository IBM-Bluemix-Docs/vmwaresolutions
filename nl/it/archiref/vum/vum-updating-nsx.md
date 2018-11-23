---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Aggiornamento di NSX

Questa sezione è stata aggiunta a questo documento per darti un'idea del processo di aggiornamento di NSX. Per il processo di aggiornamento della versione NSX che vuoi aggiornare, devi fare riferimento alla guida di VMware.

Se devi aggiornare sia NSX che vSphere, VMware consiglia di completare prima l'aggiornamento di NSX e quindi di completare l'aggiornamento di vSphere poiché i VIB NSX sono specifici della versione di ESXi installata sull'host. Tuttavia, si consiglia di utilizzare VUM come specificato in questo documento; se eseguito manualmente, utilizza il seguente flusso di lavoro, un host alla volta:

1. **Aggiorna ESXi** - Al termine dell'aggiornamento di ESXi, l'host esce dalla modalità di manutenzione, tuttavia non puoi spostare sull'host le VM connesse agli switch logici finché non viene completato il passo successivo.
2. **Aggiorna VIB NSX** - Una volta che i VIB sono stati aggiornati e l'host è stato rimosso dalla modalità di manutenzione, puoi spostare sull'host le VM connesse agli switch logici.

NSX viene aggiornato aggiornando NSX Manager utilizzando un download da _my.vmware.com_. Quindi, hai bisogno di un account per scaricare l'aggiornamento. Se utilizzi la licenza di sottoscrizione {{site.data.keyword.cloud}} con la tua istanza VMware vCenter Server on {{site.data.keyword.cloud_notm}}, non potrai scaricare gli aggiornamenti con il tuo account **my.vmware.com**. Pertanto, devi [contattare il supporto IBM](../../vmonic/trbl_support.html).

Prima di iniziare l'aggiornamento, controlla le note sulla release NSX che contengono informazioni sui problemi noti di aggiornamento e soluzioni temporanee. Utilizzando le note sulla release, verifica che vCenter soddisfi i nuovi requisiti di sistema per NSX.

Se hai installato un software aggiuntivo dai partner VMware, consulta la documentazione del partner per i dettagli di compatibilità e aggiornamento. Se disponi di istanze vCenter Server primarie e secondarie e di un ambiente Cross-vCenter NSX, fai riferimento alla note sulla release per il processo di aggiornamento corretto.

In un ambiente Cross-vCenter NSX, il dispositivo NSX Manager primario viene aggiornato per primo, seguito da tutti i dispositivi NSX Manager secondari.
**I downgrade non sono supportati**, pertanto esegui un backup di NSX Manager prima di procedere con un aggiornamento; tutte le configurazioni NSX Edge, i router logici e i gateway dei servizi edge vengono sottoposti a backup come parte del backup di NSX Manager.

Una volta aggiornato correttamente NSX Manager, NSX non può essere sottoposto a downgrade. È consigliabile che tutte le attività di manutenzione vengano eseguite in una finestra di manutenzione concordata, quindi, segui le indicazioni della tua azienda. Si consiglia di aggiornare tutti i componenti NSX in un'unica finestra di interruzione per ridurre i tempi di inattività e i problemi di funzionalità. Il processo di aggiornamento di NSX può richiedere del tempo, quindi è importante comprendere l'ordine di aggiornamento della distribuzione NSX:
* NSX Manager
* Cluster controller NSX
* Cluster host NSX
* I gateway dei servizi edge possono essere aggiornati in qualsiasi momento dopo l'aggiornamento di NSX Manager
* Guest Introspection, se utilizzato segui le istruzioni nelle note sulla release

Il flusso di lavoro è il seguente:
1. Accedi al tuo server jump e apri un browser.
2. Utilizzando le tue credenziali di _my.vmware.com_, passa alla sezione di download e cerca _NSX for vSphere_.
3. Seleziona la versione richiesta.
4. Nella pagina di download, seleziona **Upgrade Bundle, Download Now**.
5. Esegui il download in una cartella appropriata.
6. **Aggiorna NSX Manager**:
  - Accedi al dispositivo virtuale NSX Manager utilizzando l'indirizzo IP e le credenziali documentate nella console IC4VS e fai clic sul pulsante Upgrade nella home page.
  - Accedi a NSX Manager.
  - In **Appliance Management**, fai clic su **Backups & Restore**.
  - Fai clic su Backup e immetti un nome file appropriato. Nota che VMware consiglia di reinstallare il dispositivo NSX Manager prima di ripristinare i dati di NSX Manager. Anche se un'operazione di ripristino su un dispositivo NSX Manager esistente potrebbe funzionare, non è ufficialmente supportata. È consigliabile prendere nota delle impostazioni IP per il dispositivo NSX Manager in modo che possano essere utilizzate per specificare le informazioni sull'IP e sull'ubicazione di backup per il dispositivo NSX Manager appena distribuito.
  - Nell'angolo superiore destro, fai clic su **Upload Bundle** e carica il file che hai scaricato da _my.vmware.com_.
  - Leggi le informazioni sull'aggiornamento e scegli se abilitare SSH e partecipare al programma per il miglioramento dell'esperienza del cliente VMware.
  - Fai clic su **Upgrade**.
  - Al termine del caricamento, verrai reindirizzato alla pagina di accesso di NSX Manager. Accedi nuovamente e verifica che la versione corrente del software sia corretta.
7. **Aggiorna il cluster controller NSX**:
  - Apri il client web vSphere e accedi al VCSA.
  - Passa a **Home** > **Networking & Security** > **Installation**, seleziona la **scheda Management** e fai clic su **Upgrade Available** nella colonna Controller Cluster Status.
  - I controller nel tuo ambiente vengono aggiornati e riavviati uno alla volta. Dopo aver avviato l'aggiornamento, il sistema scarica il file di aggiornamento e aggiorna, riavvia e modifica lo stato di aggiornamento di ciascun controller.
8. **Aggiorna i cluster host NSX**:
  - Dopo aver aggiornato NSX Manager e i controller NSX, i cluster host vengono aggiornati con i VIB NSX sugli host vSphere ESXi.
  - Nel client web vSphere, passa a **Home** > **Networking & Security** > **Installation** e seleziona la **scheda Host Preparation**. Per ogni cluster che vuoi aggiornare, fai clic su **Upgrade available**. Lo stato di installazione è Installing.
  - Lo stato di installazione del cluster è _Not Ready_. Fai clic su **Not Ready** per visualizzare ulteriori informazioni e fai clic su **Resolve all** per tentare di completare l'installazione di VIB. L'host viene messo in modalità di manutenzione e riavviato, se necessario, per completare l'aggiornamento. La colonna dello stato di installazione mostra Installing. Al completamento dell'aggiornamento, la colonna dello stato di installazione visualizza un segno di spunta verde e la versione NSX aggiornata.
9. **Gateway dei servizi edge**:
  - Durante il processo di aggiornamento, viene distribuito un nuovo dispositivo virtuale Edge insieme a quello esistente. Quando il nuovo Edge è pronto, le vNIC del vecchio Edge vengono disconnesse e le vNIC del nuovo Edge vengono connesse. Il nuovo Edge invia quindi pacchetti ARP gratuiti (GARP) per aggiornare la cache ARP degli switch connessi. Quando viene distribuita l'HA, il processo di aggiornamento viene eseguito due volte. Questo processo può influire temporaneamente sull'inoltro dei pacchetti.
  - Nel client web vSphere, seleziona **Networking & Security** > **NSX Edges**. Per ogni istanza edge NSX, seleziona **Upgrade Version** dal menu **Actions**.
  - Dopo che l'edge NSX è stato aggiornato correttamente, lo stato diventa Deployed e la colonna della versione visualizza la nuova versione NSX. Se un Edge non si aggiorna e non torna alla versione precedente, fai clic sull'icona **Redeploy NSX Edge** e ritenta l'aggiornamento.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
