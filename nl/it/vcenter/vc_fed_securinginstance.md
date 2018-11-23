---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Protezione di istanze VMware Federal

Completa la seguente procedura per proteggere la tua istanza VMware Federal distribuita, ossia, per rimuovere la connessione di gestione aperta per l'accesso in corso all'istanza.

## Prima di iniziare

Consulta le seguenti informazioni per comprendere i risultati della protezione della tua istanza VMware Federal distribuita:

* Registra e salva le credenziali che potrebbero essere necessarie per il tuo ambiente prima di completare questa procedura. Tutte le credenziali relative al tuo ambiente vengono cancellate dal database {{site.data.keyword.vmwaresolutions_full}} e non possono essere recuperate dopo l'avvio dell'azione di protezione.
* Ad eccezione dell'eliminazione completa dell'istanza, tutte le altre funzioni di gestione vengono disabilitate dopo l'avvio dell'azione di protezione.

## Procedura per proteggere le istanze VMware Federal

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da proteggere.
3. Fai clic sull'icona del menu di overflow accanto a **Console vCenter**.
4. Fai clic su **Proteggi istanza**.
5. Fai clic su **OK** per confermare che vuoi disconnettere l'istanza dall'automazione.

  Prima di completare questo passo, assicurati di esaminare le informazioni riportate nella sezione **Prima di iniziare**.
  {:note}

6. Rimuovi il gateway dei servizi edge (ESG) VMware NSX dei servizi di gestione rivolti al pubblico dal tuo ambiente e, facoltativamente, rimuovi il tuo ESG gestito dal client distribuito durante l'automazione.
7. Reimposta le password o le chiavi di tutti gli account utilizzate dall'automazione IBM. Per ulteriori informazioni, vedi [How can I secure my environment to remove access by IBM automation and support?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)

## Risultati

Lo stato dell'istanza viene modificato in **In fase di modifica**.

Una volta che l'istanza è protetta, il suo stato viene modificato in **Protetto** e saranno disponibili solo le proprietà e la cronologia di distribuzione dell'istanza.

### Link correlati

* [Panoramica di VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Ordine di istanze VMware Federal](vc_fed_orderinginstance.html)
* [Visualizzazione delle istanze VMware Federal](vc_fed_viewinginstance.html)
* [Eliminazione di istanze VMware Federal](vc_fed_deletinginstance.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
