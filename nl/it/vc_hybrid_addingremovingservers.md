---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle

Puoi espandere o contrarre la capacità della tua istanza VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle in base alle tue esigenze aziendali, aggiungendo o rimuovendo i server ESXi.

Poiché il tuo cluster iniziale ha vSAN come archiviazione, l'aggiunta di uno o più server ESXi dopo la distribuzione può aumentare la capacità di archiviazione del cluster.

## Aggiunta di server ESXi alle istanze vCenter Server with Hybridity Bundle

### Prima di aggiungere i server ESXi

* Non aggiungere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* L'archiviazione vSAN richiede almeno 4 server ESXi.

## Procedura per aggiungere i server ESXi

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere i server ESXi.
5. Nella tabella **Server ESXi**, fai clic su **Aggiungi**.
6. Nella finestra **Aggiungi server**, seleziona il numero di server che vuoi aggiungere, fai clic sul link del prezzo per esaminare il costo stimato e fai quindi clic su **Aggiungi**.

### Risultati dopo l'aggiunta dei server ESXi

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiunta dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi diventa **In fase di modifica**.
3. Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

## Rimozione di server ESXi dalle istanze vCenter Server with Hybridity Bundle

### Prima di rimuovere i server ESXi

* Non rimuovere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* L'archiviazione vSAN richiede almeno 4 server ESXi.
* Prima di rimuovere i server ESXi con il servizio F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installato, devi migrare le VM di F5 BIG-IP e FortiGate in un server ESXi diverso rispetto a quello che ospita le VM.
* Prima di rimuovere i server ESXi con il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} installato, assicurati che non vi siano operazioni di backup o ripristino attive (non riuscite o in corso), poiché queste operazioni attive potrebbero impedire la rimozione dei server ESXi.
* Quando rimuovi i server ESXi, i server vengono messi in modalità di manutenzione e, successivamente, tutte le macchine virtuali (VM) in esecuzione sui server vengono migrate prima di essere rimosse da vCenter Server. Per il massimo controllo sulla ricollocazione delle VM, si consiglia di mettere in modalità di manutenzione i server ESXi da rimuovere e di migrare manualmente le VM in esecuzione sui server utilizzando il client web VMware vSphere. Dopo di che, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_short}}.

## Procedura per rimuovere i server ESXi

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere i server ESXi.
5. Nella tabella **Server ESXi**, seleziona i server che vuoi rimuovere e fai clic su **Rimuovi**.

### Risultati dopo la rimozione dei server ESXi

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare ulteriori modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di rimozione dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi cambia in **In fase di modifica**.
3. I server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
   {:note}

### Link correlati

* [Distinta base di vCenter Server](vc_bom.html)
* [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_planning.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_addingviewingclusters.html)
* [Metti un host in modalità di manutenzione](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
