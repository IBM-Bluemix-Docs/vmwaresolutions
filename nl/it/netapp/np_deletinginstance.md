---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Eliminazione di istanze NetApp ONTAP Select

Se elimini un'istanza NetApp ONTAP Select, i seguenti componenti vengono rilasciati in modo sequenziale:
1. Le VM (macchine virtuali) organizzate in cluster NetApp ONTAP distribuite e la VM di distribuzione NetApp ONTAP Select
2. Tariffa per supporto e servizi
3. Licenze del prodotto VMware
4. Server ESXi
5. Sottoreti
6. VLAN

A causa delle dipendenze delle risorse, i componenti della tua istanza non vengono rilasciati immediatamente quando elimini l'istanza. Ad esempio, le sottoreti e le VLAN non possono essere eliminate finché i server ESXi non vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud}}, cosa che avviene alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}. Alla fine del ciclo di fatturazione, che in genere è di 30 giorni, le sottoreti e le VLAN vengono recuperate e l'eliminazione dell'istanza viene completata.

Per l'istanza eliminata ti vengono addebitati costi fino alla fine del ciclo di fatturazione.
{:note}

## Procedura per eliminare le istanze dalla pagina Istanze distribuite

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze di NetApp ONTAP Select**, trova l'istanza da eliminare.
3. Nella colonna **Azioni**, fai clic sull'icona Elimina.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza viene eliminata correttamente e il suo stato viene modificato in **Eliminato**, fai di nuovo clic sull'icona di eliminazione nella colonna **Azioni**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Nella colonna **Azioni**, fai di nuovo clic sull'icona Elimina.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Procedura per eliminare le istanze dalla pagina dei dettagli dell'istanza

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze di NetApp ONTAP Select**, fai clic sull'istanza da eliminare.
3. Fai clic sull'icona del menu di overflow accanto a **Console NetApp** e quindi su **Elimina istanza**.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Fai di nuovo clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

### Link correlati

* [Ordine di istanze NetApp ONTAP Select](np_orderinginstances.html)
* [Visualizzazione delle istanze NetApp ONTAP Select](np_viewinginstances.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
