---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aggiunta, visualizzazione ed eliminazione di cluster per le istanze VMware Federal

I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **cluster1** per impostazione predefinita.

Puoi aggiungere cluster alle tue istanze VMware Federal per espandere la capacità di calcolo e archiviazione. All'interno di un cluster, puoi gestire i server ESXi per una migliore allocazione delle risorse e alta disponibilità. Quando non sono più necessari, puoi eliminare i cluster aggiunti dalle tue istanze.

**Disponibilità:** la funzione di aggiunta ed eliminazione dei cluster è disponibile solo per le istanze che sono state distribuite o aggiornate alle release della V2.3 e successive.

## Aggiunta di cluster alle istanze VMware Federal

Puoi aggiungere fino a 10 cluster a un'istanza. Quando aggiungi un cluster a un'istanza VMware Federal, devi specificare le seguenti impostazioni.

### Impostazioni di sistema

Quando aggiungi un cluster a un'istanza VMware Federal, devi specificare le seguenti impostazioni.

#### Nome cluster

Il nome del cluster deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome del cluster deve iniziare e terminare con un carattere alfanumerico.
* La lunghezza massima del nome del cluster è di 30 caratteri.
* Il nome del cluster deve essere univoco all'interno dell'istanza VMware Federal.

#### Ubicazione data center

Il data center del cluster è impostato sul data center dell'istanza VMware Federal per impostazione predefinita.

### Impostazioni di Bare Metal Server

#### Skylake

Specifica il modello di CPU e la RAM per il Bare Metal Server. Le opzioni disponibili potrebbero variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

Tabella 1. Opzioni per Skylake {{site.data.keyword.baremetal_short}}

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell

Specifica il modello di CPU e la RAM per il Bare Metal Server. Le opzioni disponibili potrebbero variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

Tabella 2. Opzioni per Broadwell {{site.data.keyword.baremetal_short}}

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |

#### Numero di server Bare Metal

Per un cluster, è richiesto un minimo di 2 {{site.data.keyword.baremetal_short}}.

Per le istanze VMware Federal distribuite nella V2.3 o successive, puoi aggiungere fino a 59 {{site.data.keyword.baremetal_short}} per un cluster e aggiungere da 1 a 59 server ESXi alla volta.

Dopo la distribuzione, puoi creare fino a quattro ulteriori cluster. Per le impostazioni di archiviazione vSAN, sono richiesti quattro server sia per il cluster iniziale che per i cluster di post-distribuzione.

### Impostazioni di archiviazione

Le impostazioni di archiviazione si basano sulla tua selezione della configurazione Bare Metal Server e sul tipo di archiviazione.

#### Archiviazione vSAN

Specifica le seguenti opzioni vSAN:
* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona un'opzione per i dischi di capacità di cui hai bisogno.
* **Numero di dischi vSAN**: specifica il numero di dischi di capacità che vuoi aggiungere.
* Se vuoi aggiungere dischi di capacità oltre il limite di otto, seleziona la casella **Alte prestazioni con Intel Optane**. Questa opzione fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità ed è utile per i carichi di lavoro che richiedono meno latenza e una maggiore velocità IOPS. L'opzione **Alte prestazioni con Intel Optane** è disponibile solo per i processori Dual Intel Xeon Gold 5120 e 6140.
* Riesamina i valori di **Tipo di disco per i dischi cache vSAN** e **Numero di dischi cache vSAN**. Questi valori dipendono dalla selezione della casella **Alte prestazioni con Intel Optane**.
* **Licenza vSAN**: seleziona l'edizione della licenza VMware vSAN 6.6 (Advanced o Enterprise).

Se il tuo cluster iniziale è stato aggiunto come cluster vSAN, tutti gli ulteriori cluster vSAN utilizzano la stessa licenza vSAN e la stessa configurazione del cluster vSAN iniziale. Questo vale anche se in qualsiasi cluster (iniziale o aggiuntivo) dell'istanza è stato scelto di distribuire vSAN. La prima volta che aggiungi un cluster, ti viene richiesta la licenza vSAN e l'edizione. La prossima volta che selezioni vSAN per un nuovo cluster, viene riutilizzata qualsiasi cosa tu abbia scelto inizialmente.

#### Archiviazione NFS

Se selezioni **Storage NFS**, puoi aggiungere l'archiviazione condivisa a livello di file per la tua istanza in cui tutte le condivisioni utilizzano le stesse impostazioni o puoi specificare impostazioni di configurazione diverse per ogni condivisione file. Specifica le seguenti opzioni NFS:

Il numero di condivisioni file deve essere compreso tra 1 e 32.
{:note}

* **Configura le condivisioni singolarmente**: seleziona questa opzione per specificare diverse impostazioni di configurazione per ogni condivisione file.
* **Numero di condivisioni**: quando utilizzi la stessa impostazione di configurazione per ogni condivisione file, specifica il numero di condivisioni file per l'archiviazione condivisa NFS che vuoi aggiungere.
* **Dimensione**: seleziona la capacità che soddisfa le tue esigenze di archiviazione condivisa.
* **Prestazioni**: seleziona l'IOPS (Input/output Operations Per Second) per GB in base ai tuoi requisiti del carico di lavoro.
* **AGGIUNGI NFS**: seleziona questa opzione per aggiungere singole condivisioni file con diverse impostazioni di configurazione.

Tabella 3. Opzioni del livello di prestazioni NFS

| Opzione        | Dettagli       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Questa opzione è progettata per i carichi di lavoro più generici. Applicazioni di esempio includono: hosting di piccoli database, backup di applicazioni web o immagini disco di macchine virtuali per un hypervisor. |
  | 4 IOPS/GB | Questa opzione è progettata per i carichi di lavoro ad alta intensità che hanno un'alta percentuale di dati attivi alla volta. Applicazioni di esempio includono: database transazionali. |
  | 10 IOPS/GB | Questa opzione è progettata per i tipi di carichi di lavoro più impegnativi, come l'analisi. Applicazioni di esempio includono: database ad alte transazioni e altri database sensibili alle prestazioni. Questo livello di prestazioni è limitato a una capacità massima di 4 TB per condivisione file.|

### Impostazioni di licenza

Licenze fornite da {{site.data.keyword.IBM}} per i seguenti componenti VMware:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Edizione Base, Advanced o Enterprise)
  * (Per i cluster vSAN) vSAN 6.6 (Edizione Advanced o Enterprise)

### Riepilogo ordine

In base alla configurazione che hai selezionato per il cluster, il costo stimato viene generato e visualizzato immediatamente nel riquadro **Riepilogo ordine** sulla destra.

## Procedura per aggiungere i cluster alle istanze VMware Federal

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanza vCenter Server**, fai clic sull'istanza a cui vuoi aggiungere i cluster.

   Assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. In caso contrario, non potrai aggiungere i cluster all'istanza.
   {:note}
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra e quindi su **Aggiungi** nell'angolo superiore destro della tabella **CLUSTER**.
4. Nella pagina **Aggiungi cluster**, immetti il nome del cluster.
5. Seleziona il **Modello CPU**, la quantità di **RAM** e il **Numero di server Bare Metal** per la configurazione Bare Metal.
6. Completa la configurazione di archiviazione.
  * Se selezioni **Storage vSAN**, specifica i tipi di disco per i dischi di capacità e cache e il numero di dischi. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le stesse impostazioni in tutte le condivisioni file, specifica il **Numero di condivisioni**, la **Dimensione** e le **Prestazioni**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le condivisioni file singolarmente, seleziona **Configura condivisioni singolarmente**, quindi fai clic sull'icona **+** accanto all'etichetta **Aggiungi NFS** e seleziona la **Dimensione** e le **Prestazioni** per ogni singola condivisione file. Devi selezionare almeno una condivisione file.
7. Seleziona l'edizione della licenza di VMware vSAN per la configurazione della licenza.
8. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster prima di aggiungerlo.
   1. Esamina le impostazioni per il cluster.
   2. Esamina il costo stimato del cluster. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nell'angolo superiore destro della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di aggiungere il cluster.
   4. Fai clic su **Fornitura**.

## Risultati dopo l'aggiunta dei cluster alle istanze VMware Federal

1. La distribuzione del cluster viene avviata automaticamente e lo stato del cluster viene modificato in **Inizializzazione**. Puoi controllare lo stato della distribuzione visualizzando la cronologia di distribuzione dalla pagina di riepilogo dell'istanza.
2. Quando il cluster è pronto per l'uso, il suo stato viene modificato in **Pronto per l'utilizzo**. Il cluster appena aggiunto viene abilitato con vSphere High Availability (HA) e vSphere Distributed Resource Scheduler (DRS).

Non puoi modificare il nome del cluster. La modifica del nome del cluster potrebbe comportare errori nelle operazioni di aggiunta o rimozione dei server ESXi nel cluster.
{:important}

## Procedura per visualizzare i cluster nelle istanze VMware Federal

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic su un'istanza per visualizzare i cluster al suo interno.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, visualizza il riepilogo dei cluster:
   * **Nome**: il nome del cluster.
   * **Server ESXi**: il numero di server ESXi nel cluster.
   * **CPU**: la specifica CPU dei server ESXi nel cluster.
   * **Dischi vSAN personalizzati**: il numero di dischi vSAN nel cluster, incluso il tipo di disco e la capacità.
   * **Memoria**: la dimensione totale della memoria dei server ESXi nel cluster.
   * **Ubicazione Data Center**: il data center in cui è ospitato il cluster.
   * **Pod**: il pod in cui è distribuito il cluster.
   * **Stato**: lo stato del cluster. Lo stato può assumere uno dei seguenti valori:
     <dl class="dl">
         <dt class="dt dlterm">Inizializzazione</dt>
         <dd class="dd">Il cluster è in fase di creazione e configurazione.</dd>
         <dt class="dt dlterm">In fase di modifica</dt>
         <dd class="dd">Il cluster è in fase di modifica.</dd>
         <dt class="dt dlterm">Pronto per l'utilizzo</dt>
         <dd class="dd">Il cluster è pronto per l'uso.</dd>
         <dt class="dt dlterm">In fase di eliminazione</dt>
         <dd class="dd">Il cluster è in fase di eliminazione.</dd>
         <dt class="dt dlterm">Eliminato</dt>
         <dd class="dd">Il cluster è stato eliminato.</dd>
     </dl>
   * **Azioni**: fai clic sull'icona **Elimina** per eliminare il cluster.
4. Fai clic sul nome di un cluster per visualizzare i dettagli del server ESXi, di archiviazione e di licenza.

### Server ESXi

   * **Nome**: il nome del server ESXi è nel formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove:

      `host_prefix` è il prefisso del nome host,
      `n` è la sequenza del server ESXi,
      `subdomain_label` è l'etichetta del dominio secondario e
      `root_domain` è il nome del dominio root.

   * **Versione**: la versione del server ESXi.
   * **Credenziali**: il nome utente e la password per accedere al server ESXi.
   * **IP privato**: l'indirizzo IP privato del server ESXi.
   * **Stato**: lo stato del server ESXi, che può assumere uno dei seguenti valori:
        <dl class="dl">
        <dt class="dt dlterm">Aggiunto</dt>
        <dd class="dd">Il server ESXi è stato aggiunto ed è pronto per l'uso. </dd>
        <dt class="dt dlterm">In fase di aggiunta</dt>
        <dd class="dd">Il server ESXi è in fase di aggiunta. </dd>
        <dt class="dt dlterm">In fase di eliminazione</dt>
        <dd class="dd">Il server ESXi è in fase di eliminazione.</dd>
        </dl>

### Archiviazione

   * **Nome**: il nome dell'archivio dati.
   * **Dimensione**: la capacità di archiviazione.
   * **IOPS/GB**: il livello di prestazioni dell'archiviazione.
   * **NFS/Portale**: la versione NFS dell'archiviazione.
   * **Stato**: lo stato dell'archiviazione, che può assumere uno dei seguenti valori:
        <dl class="dl">
        <dt class="dt dlterm">Aggiunto</dt>
        <dd class="dd">Il server ESXi è stato aggiunto ed è pronto per l'uso. </dd>
        <dt class="dt dlterm">In fase di aggiunta</dt>
        <dd class="dd">Il server ESXi è in fase di aggiunta. </dd>
        <dt class="dt dlterm">In fase di eliminazione</dt>
        <dd class="dd">Il server ESXi è in fase di eliminazione.</dd>
        </dl>

### Licenze

   * **Licenza**: il tipo di licenza.
   * **Tipo di ordine**: la licenza è fornita da IBM o fornita dall'utente.
   * **Edizione della licenza**: la versione e l'edizione della licenza.
   * **Chiave di licenza**: la chiave di licenza.
   * **Capacità totale (CPU)**: la quantità totale di capacità della CPU per la licenza.
   * **Capacità libera (CPU)**: la quantità di capacità della CPU disponibile per la licenza.

## Eliminazione di cluster dalle istanze VMware Federal

Potresti voler eliminare un cluster da un'istanza quando non è più necessario.

Utilizza questa procedura per rimuovere i cluster dalle istanze che sono state distribuite o aggiornate alle release della V2.3 e successive.
{:note}

### Prima di eliminare

* Utilizza questa procedura per eliminare i cluster dalle istanze distribuite nelle release della V2.3 o successive.
* Per i cluster distribuiti nelle istanze della V2.2 o precedenti, devi aggiornare l'istanza alla V2.3 per poter eliminare i cluster che hai aggiunto all'istanza.
* Puoi eliminare un singolo cluster alla volta. Per eliminare più cluster, devi farlo in sequenza: attendere che il cluster precedente venga eliminato prima di tentare di eliminare quello successivo.
* Assicurati che tutti i nodi in un cluster siano accesi e operativi prima di eliminare il cluster.
* Quando elimini un cluster, da questo vengono eliminate anche tutte le VM (macchine virtuali) e non possono essere ripristinate. Se vuoi mantenere le VM, migrale in altri cluster.
* Non è possibile eliminare il cluster predefinito.

## Procedura per eliminare i cluster dalle istanze VMware Federal

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da cui vuoi eliminare i cluster.

   Assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. Altrimenti, non potrai eliminare i cluster dall'istanza.
   {:note}

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, individua il cluster che vuoi eliminare e fai clic sull'icona **Elimina** nella colonna **Azioni**.

### Link correlati

* [Visualizzazione delle istanze VMware Federal](vc_fed_viewinginstance.html)
* [Espansione e contrazione della capacità per le istanze VMware Federal](vc_fed_addingremovingservers.html)
