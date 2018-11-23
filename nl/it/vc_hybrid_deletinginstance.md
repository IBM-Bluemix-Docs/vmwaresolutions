---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Eliminazione di istanze vCenter Server with Hybridity Bundle

Per rilasciare i componenti che hai ordinato in un'istanza VMware vCenter Server with Hybridity Bundle, elimina l'istanza.

Quando elimini un'istanza vCenter Server with Hybridity Bundle, i seguenti componenti vengono rilasciati in modo sequenziale:
1. Tutti i servizi distribuiti
2. Tariffa per supporto e servizi
3. Licenze del prodotto VMware
4. Server ESXi
5. Sottoreti
6. VLAN

A causa delle dipendenze delle risorse, i componenti della tua istanza non vengono rilasciati immediatamente quando elimini l'istanza. Ad esempio, le sottoreti e le VLAN non possono essere eliminate finché i server ESXi non vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud}}, cosa che avviene alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}. Alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni, le sottoreti e le VLAN vengono eliminate e l'eliminazione dell'istanza viene completata.

Per l'istanza eliminata ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
{:note}

## Procedura per eliminare le istanze dalla pagina Istanze distribuite

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, trova l'istanza da eliminare.
3. Nella colonna **Azioni**, fai clic sull'icona Elimina.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Nella colonna **Azioni**, fai di nuovo clic sull'icona Elimina.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Procedura per eliminare le istanze dalla pagina dei dettagli dell'istanza

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da eliminare.
3. Fai clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Fai di nuovo clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

### Link correlati

* [Eliminazione di istanze vCenter Server with Hybridity Bundle in una configurazione multisito](vc_hybrid_deletinginstance_multi.html)
* [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
* [Visualizzazione delle istanze vCenter Server with Hybridity Bundle](vc_hybrid_viewinginstances.html)
* [Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
