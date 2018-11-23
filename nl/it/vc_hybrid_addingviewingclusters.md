---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server with Hybridity Bundle

I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **cluster1** per impostazione predefinita.

Puoi aggiungere cluster alla tua istanza VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle per espandere la capacità di calcolo e archiviazione. All'interno di un cluster, gestisci i server ESXi per una migliore allocazione delle risorse e alta disponibilità. Quando non sono più necessari, elimina i cluster aggiunti dalla tua istanza.

## Aggiunta di cluster alle istanze vCenter Server with Hybridity Bundle

Puoi aggiungere fino a 10 cluster alla tua istanza vCenter Server with Hybridity Bundle.

### Impostazioni di sistema

Quando aggiungi un cluster a un'istanza vCenter Server with Hybridity Bundle, devi specificare le seguenti impostazioni.

#### Nome cluster

Il nome del cluster deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome del cluster deve iniziare e terminare con un carattere alfanumerico.
* La lunghezza massima del nome del cluster è di 30 caratteri.
* Il nome del cluster deve essere univoco all'interno dell'istanza vCenter Server with Hybridity Bundle.

#### Ubicazione data center

L'ubicazione del {{site.data.keyword.CloudDataCent_notm}} del cluster è impostata sul {{site.data.keyword.CloudDataCent_notm}} dell'istanza vCenter Server per impostazione predefinita. Puoi distribuire il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso rispetto a quello dell'istanza distribuita, ma devi assicurarti che la latenza di rete tra i due {{site.data.keyword.CloudDataCents_notm}} sia inferiore a 150 ms. Per controllare la latenza di rete, utilizza uno strumento come [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Se distribuisci il cluster in un diverso {{site.data.keyword.CloudDataCent_notm}} o pod dell'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate altre tre VLAN da utilizzare con i {{site.data.keyword.baremetal_short}} ordinati.

### Impostazioni di Bare Metal Server

Specifica il modello di CPU e la RAM per il Bare Metal Server. Le opzioni disponibili potrebbero variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

#### Skylake

Se selezioni **Skylake**, puoi scegliere la combinazione di CPU e RAM in base alle tue esigenze.

Tabella 1. Opzioni per i server bare metal Skylake

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell

Se selezioni **Broadwell**, puoi scegliere la combinazione di CPU e RAM in base alle tue esigenze.

Tabella 2. Opzioni per i server bare metal Broadwell

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |

#### Numero di server Bare Metal

Per un cluster, sono richiesti almeno due {{site.data.keyword.baremetal_short}}.

Puoi aggiungere fino a 59 {{site.data.keyword.baremetal_short}} per un cluster e puoi aggiungere da 1 a 59 server ESXi alla volta.

Dopo la distribuzione, puoi creare fino a quattro ulteriori cluster. Per l'archiviazione VMware vSAN, sono richiesti quattro server sia per il cluster iniziale che per i cluster di post-distribuzione.

### Impostazioni di archiviazione vSAN

VMware vSAN 6.6 è incluso con il tuo ordine dell'istanza vCenter Server with Hybridity Bundle. Specifica le seguenti opzioni vSAN:
* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona un'opzione per i dischi di capacità di cui hai bisogno.
* **Numero di dischi vSAN**: specifica il numero di dischi di capacità che vuoi aggiungere.
* Se vuoi aggiungere dischi di capacità oltre il limite di otto, seleziona la casella **Alte prestazioni con Intel Optane**. Questa opzione fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità ed è utile per i carichi di lavoro che richiedono meno latenza e una maggiore velocità IOPS. L'opzione **Alte prestazioni con Intel Optane** è disponibile solo per i processori Dual Intel Xeon Gold 5120 e 6140.
* Riesamina i valori di **Tipo di disco per i dischi cache vSAN** e **Numero di dischi cache vSAN**. Questi valori dipendono dalla selezione della casella **Alte prestazioni con Intel Optane**.
* **Licenza vSAN**: seleziona l'edizione della licenza VMware vSAN 6.6 (Advanced o Enterprise).

### Impostazioni di licenza

Licenze fornite da IBM per i seguenti componenti VMware:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Edizione Advanced o Enterprise)

### Impostazioni dell'interfaccia di rete

Le impostazioni della scheda di interfaccia di rete (NIC) si basano sulla tua selezione di **Rete pubblica e privata** o **Solo rete privata**. I seguenti servizi aggiuntivi richiedono NIC pubbliche e non sono disponibili con l'opzione privata:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Riepilogo ordine

In base alla configurazione che hai selezionato per il cluster, il costo stimato viene generato e visualizzato immediatamente nel riquadro **Riepilogo ordine** sulla destra.

## Procedura per aggiungere i cluster alle istanze vCenter Server with Hybridity Bundle

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per visualizzare i cluster al suo interno.

   Assicurati che lo stato dell'istanza sia **Pronto per l'utilizzo**. Altrimenti, non puoi aggiungere i cluster all'istanza.
   {:note}

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra e quindi su **Aggiungi** nell'angolo superiore destro della tabella **CLUSTER**.
4. Nella pagina **Aggiungi cluster**, immetti il nome del cluster.
5. Puoi ospitare il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso da quello in cui è ospitata l'istanza. Per farlo, in **Bare Metal Server**, seleziona la casella di spunta **Seleziona un'ubicazione differente** e scegli il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.
6. Seleziona il **Modello CPU**, la quantità di **RAM** e il **Numero di server Bare Metal** per la configurazione Bare Metal.
7.  Seleziona **Storage vSAN** e specifica i tipi di disco per i dischi di capacità e cache e il numero di dischi. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
8. Seleziona l'edizione della licenza di VMware vSAN per la configurazione della licenza.
9. Seleziona l'impostazione di rete **Rete pubblica e privata** o **Solo rete privata**.
10. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster prima di aggiungerlo.
   1. Esamina le impostazioni per il cluster.
   2. Esamina il costo stimato del cluster. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di aggiungere il cluster.
   4. Fai clic su **Fornitura**.

### Risultati dopo l'aggiunta di cluster alle istanze vCenter Server with Hybridity Bundle

1. La distribuzione del cluster viene avviata automaticamente e lo stato del cluster viene modificato in **Inizializzazione**. Puoi controllare lo stato della distribuzione visualizzando la cronologia di distribuzione nella pagina **Riepilogo** dell'istanza.
2. Quando il cluster è pronto per l'uso, il suo stato viene modificato in **Pronto per l'utilizzo**. Il cluster appena aggiunto viene abilitato con vSphere High Availability (HA) e vSphere Distributed Resource Scheduler (DRS).

Non puoi modificare il nome del cluster. La modifica del nome del cluster potrebbe comportare errori nelle operazioni di aggiunta o rimozione dei server ESXi nel cluster.
{:important}

## Procedura per visualizzare i cluster nelle istanze vCenter Server with Hybridity Bundle

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per visualizzare i cluster al suo interno.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, visualizza il riepilogo dei cluster:
  * **Nome**: il nome del cluster.
  * **Server ESXi**: il numero di server ESXi nel cluster.
  * **CPU**: la specifica CPU dei server ESXi nel cluster.
  * **Dischi vSAN personalizzati**: il numero di dischi vSAN nel cluster, incluso il tipo di disco e la capacità.
  * **Memoria**: la dimensione totale della memoria dei server ESXi nel cluster.
  * **Ubicazione Data Center **: il {{site.data.keyword.CloudDataCent_notm}} in cui è ospitato il cluster.
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
4. Fai clic sul nome di un cluster per visualizzare i dettagli dei server ESXi e di archiviazione:

  * Dettagli dei server ESXi:
     * **Nome**: il nome del server ESXi è nel formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove:

       `host_prefix` è il prefisso del nome host,

       `n` è la sequenza del server,

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
  * Dettagli di archiviazione:
    * **Nome**: il nome dell'archivio dati.
    * **Dimensione**: la capacità di archiviazione.
    * **IOPS/GB**: il livello di prestazioni dell'archiviazione.
    * **Protocollo NFS**: la versione NFS dell'archiviazione.

## Eliminazione di cluster dalle istanze vCenter Server with Hybridity Bundle

Potresti voler eliminare un cluster da un'istanza quando non è più necessario.

### Prima di eliminare

* Puoi eliminare un singolo cluster alla volta. Per eliminare più cluster, devi farlo in sequenza: attendi che il cluster precedente venga eliminato prima di eliminare quello successivo.
* Assicurati che tutti i nodi in un cluster siano accesi e operativi prima di eliminare il cluster.
* Quando elimini un cluster, da questo vengono eliminate anche tutte le VM (macchine virtuali) e non possono essere ripristinate. Se vuoi mantenere le VM, migrale in altri cluster.
* Il cluster predefinito non può essere eliminato.

## Procedura per eliminare i cluster dalle istanze vCenter Server with Hybridity Bundle

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da cui vuoi eliminare i cluster.

   **Nota:** assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. Altrimenti, non potrai rimuovere i cluster dall'istanza.

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, individua il cluster che vuoi eliminare e fai clic sull'icona **Elimina** nella colonna **Azioni**.

### Link correlati

* [Visualizzazione delle istanze vCenter Server with Hybridity Bundle](vc_hybrid_viewinginstances.html)
* [Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
