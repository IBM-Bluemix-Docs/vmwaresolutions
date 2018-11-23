---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-09"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Rimozione di Hybridity Bundle da un'istanza vCenter Server

Per rimuovere la licenza di Hybridity Bundle dalla tua istanza vCenter Server, devi sostituire le chiavi di licenza a noleggio di VMware NSX e VMware vSAN con le chiavi BYOL (Bring Your Own License) nel client web VMware vSphere. Inoltre, devi aprire un ticket di supporto per annullare i costi per le licenze a noleggio.

Il downgrade della tua licenza potrebbe causare errori nell'istanza vCenter Server. Puoi scegliere di effettuare il downgrade di una licenza a tuo proprio rischio, ma prima considera le funzioni che non sono disponibili quando esegui il downgrade. Per ulteriori informazioni, vedi [Tabella di confronto per le edizioni dei componenti VMware](../archiref/solution/appendix.html).
{:important}

## Considerazioni importanti prima di rimuovere Hybridity Bundle da un ambiente multisito

Esamina le seguenti considerazioni prima di rimuovere Hybridity Bundle da un ambiente multisito:

* Devi applicare le licenze BYOL a tutte le distribuzioni multisito prima di rimuovere le licenze a noleggio.
* Devi combinare le licenze VMware NSX e avere una capacità sufficiente da utilizzare in tutte le distribuzioni multisito.
* Devi creare un unico ticket di supporto per rimuovere Hybridity Bundle da tutte le distribuzioni multisito.

Mentre si rimuove Hybridity Bundle da un ambiente multisito, vengono applicate le licenze BYOL. Per tutti i siti in una configurazione multisito, la licenza NSX viene automaticamente ripristinata nell'edizione di licenza più bassa tra tutti i siti. Devi assicurarti che le edizioni di licenza siano coerenti su tutti i siti nella configurazione multisito.
{:note}

## Prima di rimuovere Hybridity Bundle

Verifica i seguenti requisiti prima di rimuovere Hybridity Bundle:

* Hai un'istanza vCenter Server V2.4 o versioni successive con Hybridity Bundle abilitato.
* Non hai il servizio VMware HCX on {{site.data.keyword.cloud_notm}} installato sulla tua istanza vCenter Server.
* Disponi dell'accesso come amministratore al client web VMware vSphere.
* Se non già applicate, hai a disposizione le chiavi BYOL da applicare per VMware NSX e per ogni cluster VMware vSAN.
* Facoltativamente e se non già applicate, hai a disposizione le chiavi BYOL da applicare per le licenze di VMware vCenter Server e VMware vSphere Enterprise Plus.

## Procedura per rimuovere Hybridity Bundle

1. Accedi come **Amministratore** al client web VMware in cui vuoi rimuovere Hybridity Bundle.
2. Fai clic su **Home > Administration > Licensing > Licenses**.
3. Fai clic sulla scheda **Assets**.
4. Completa la seguente procedura per installare una BYOL VMware NSX:
   1. Fai clic sulla scheda **Solutions**.
   2. Seleziona NSX for vSphere e fai clic su **All Actions > Assign license**.
   3. Fai clic sull'icona **Add** e immetti la chiave di licenza. Fai clic su **Avanti**.
   4. Digita il nome per la licenza e fai clic su **Next**. Fai clic su **Finish** per aggiungere la licenza.
   5. Seleziona la nuova chiave di licenza.
   6. Annota le chiavi di licenza complete per la licenza che viene applicata e la licenza che viene sostituita.

   Devi avere a disposizione i dettagli della licenza da utilizzare in seguito in questa procedura.
   {:important}
   7. Fai clic su **OK** per assegnare la licenza.
5. Completa la seguente procedura per installare una BYOL VMware vSAN:
   1. Fai clic sulla scheda **Clusters**.
   2. Completa la seguente procedura per ogni cluster vSAN associato alla tua istanza vCenter Server:
    1. Seleziona un cluster vSAN e fai clic su **All Actions > Assign license**.
    2. Fai clic sull'icona **Add** e immetti la chiave di licenza. Fai clic su **Avanti**.
    3. Digita il nome per la licenza e fai clic su **Next**. Fai clic su **Finish** per aggiungere la licenza.
    4. Seleziona la nuova chiave di licenza.
    5. Annota il nome del cluster e le chiavi di licenza complete per la licenza che viene applicata e la licenza che viene sostituita.

    Devi avere a disposizione i dettagli della licenza da utilizzare in seguito in questa procedura.
    {:important}
    6. Fai clic su **OK** per assegnare la licenza.
6. Facoltativamente, completa la seguente procedura per installare una BYOL VMware vCenter Server:
   1. Fai clic sulla scheda **vCenter Server systems**.
   2. Seleziona vCenter Server e fai clic su **All Actions > Assign license**.
   3. Fai clic sull'icona **Add** e immetti la chiave di licenza. Fai clic su **Avanti**.
   4. Digita il nome per la licenza e fai clic su **Next**. Fai clic su **Finish** per aggiungere la licenza.
   5. Seleziona la nuova chiave di licenza.
   6. Annota le chiavi di licenza complete per la licenza che viene applicata e la licenza che viene sostituita.

   Devi avere a disposizione i dettagli della licenza da utilizzare in seguito in questa procedura.
   {:important}

   7. Fai clic su **OK** per assegnare la licenza.
7. Facoltativamente, completa la seguente procedura per installare una BYOL VMware vSphere Enterprise Plus:
  1. Fai clic sulla scheda **Hosts**.
  2. Completa la seguente procedura per ogni cluster associato alla tua istanza vCenter Server o per tutti i cluster contemporaneamente se viene applicata la stessa licenza a tutti i cluster associati al tuo server vCenter:
    1. Seleziona tutti gli host associati al cluster e fai clic su **All Actions > Assign license**.
    2. Fai clic sull'icona **Add** e immetti la chiave di licenza. Fai clic su **Avanti**.
    3. Digita il nome per la licenza e fai clic su **Next**. Fai clic su **Finish** per aggiungere la licenza.
    4. Seleziona la nuova chiave di licenza.
    5. Annota il nome del cluster e le chiavi di licenza complete per la licenza che viene applicata e la licenza che viene sostituita.

    Devi avere a disposizione i dettagli della licenza da utilizzare in seguito in questa procedura. Se le chiavi di licenza non sono uguali per tutti i cluster, assicurati di annotare il nome del cluster associato a ogni chiave di licenza.
    {:important}

    6. Fai clic su **OK** per assegnare la licenza.
8. Rimuovi le licenze a noleggio.
   1. Fai clic sulla scheda **Licenses**.
   2. Seleziona le licenze che hai sostituito nei passi 4 - 7.
   3. Fai clic sull'icona **Remove Licenses**.
9. Apri un ticket di supporto e fornisci le seguenti informazioni per annullare i costi per le licenze a noleggio:
  * Il nome della/e tua/e istanza/e vCenter Server.
  * L'ID associato alla/e tua/e istanza/e vCenter Server.
  * Un elenco delle chiavi di licenza BYOL che hai installato in questa procedura. Laddove applicabile, fornisci il nome dell'istanza e del cluster con le chiavi di licenza per i cluster vSphere e vSAN.
  * Un elenco delle chiavi di licenza a noleggio che hai rimosso in questa procedura. Laddove applicabile, fornisci il nome dell'istanza e del cluster con le chiavi di licenza per i cluster vSphere e vSAN.

  I team di supporto e operazioni IBM accedono al livello di gestione vCenter del tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) per verificare che le licenze a noleggio siano state rimosse prima di annullare i costi della licenza a noleggio di Hybridity Bundle.
  {:note}

### Link correlati

* [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
* [Visualizzazione delle istanze vCenter Server with Hybridity Bundle](vc_hybrid_viewinginstances.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
