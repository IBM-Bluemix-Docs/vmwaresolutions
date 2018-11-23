---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Applicazione di aggiornamenti alle istanze vCenter Server with Hybridity Bundle

Il processo di applicazione di patch e aggiornamenti alle istanze vCenter Server with Hybridity Bundle è automatizzato solo per i componenti di gestione. Gli aggiornamenti di VMware devono essere applicati manualmente.

## Prima di iniziare

A partire dalla V2.5, gli aggiornamenti di IBM CloudDriver non sono più elencati perché sono abilitati gli aggiornamenti automatici. Azioni come l'aggiunta di un host, l'aggiunta di un cluster e l'ordine di un servizio aggiornano automaticamente l'istanza all'ultima versione. Per ulteriori informazioni sugli aggiornamenti automatici, consulta la sezione *Resilienza di IBM CloudDriver* in [Note sulla release per la V2.5](../vmonic/relnotes_v25.html).
{:note}

Prima di tentare di applicare un aggiornamento, espandi la voce di aggiornamento facendo clic sulla freccia in giù e verifica le seguenti informazioni:
* La versione dell'aggiornamento. Devi applicare gli aggiornamenti in sequenza cronologica, dalla più antica alla più recente. Assicurati di aver applicato tutti gli aggiornamenti precedenti prima di applicare quello più recente. Ad esempio, devi applicare l'aggiornamento alla V2.3 prima di tentare di applicare l'aggiornamento alla V2.4.
* Se è necessario un tempo di inattività.
* Il tempo totale stimato per completare l'aggiornamento.
* L'impatto dell'aggiornamento sull'ambiente virtuale VMware.
* I dettagli dell'aggiornamento.

La seguente tabella mostra come i diversi livelli di impatto influiscono sul sistema.

Tabella 1. Livelli di aggiornamento e impatto

| Livello di aggiornamento  | Impatto        |  
|:------------- |:------------- |
| Basso    | Questo aggiornamento non influisce su alcun sistema. Non devi applicarlo durante i tempi di inattività
    pianificati. |  
| Medium | Questo aggiornamento potrebbe influire su alcuni sistemi. Si consiglia di applicarlo durante i tempi di inattività
    pianificati. |  
| Maggiore  | Questo aggiornamento influisce su alcuni o tutti i sistemi. Devi applicarlo durante i tempi di inattività pianificati. |  

## Procedura per applicare aggiornamenti alle istanze vCenter Server with Hybridity Bundle

1. Dalla console {{site.data.keyword.vmwaresolutions_full}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da aggiornare.
3. Nella pagina **Riepilogo**, verifica che tutti i dettagli dell'istanza siano visualizzati correttamente. Quindi, fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra per verificare i dettagli nella pagina **Infrastruttura**.
   Se i dettagli non vengono visualizzati, ciò potrebbe indicare un problema di connettività con la VSI (Virtual Server Instance) IBM CloudDriver, a causa di una regola del firewall o di altri problemi di rete. Risolvi il problema prima di continuare con il passo successivo, altrimenti l'aggiornamento potrebbe non riuscire.
4. Fai clic su **Aggiorna e applica patch** nel riquadro di navigazione a sinistra.

   La pagina **Aggiorna e applica patch** contiene solo i pacchetti per l'aggiornamento dei componenti di gestione IBM e non gli aggiornamenti di VMware. {{site.data.keyword.vmwaresolutions_short}} applica gli aggiornamenti di VMware per le seguenti operazioni:
   * Quando viene distribuita una nuova istanza vCenter Server.
   * Quando vengono aggiunti nuovi server ESXi, viene eseguito il provisioning dei nuovi server ESXi con gli aggiornamenti VMware, ma i server ESXi esistenti non vengono aggiornati.
   * Quando vengono aggiunti nuovi cluster, viene eseguito il provisioning dei nuovi cluster con gli aggiornamenti VMware, ma i cluster esistenti non vengono aggiornati.
   {:note}

5. Per gli aggiornamenti della licenza, fai clic su **Aggiorna**. Dall'elenco, seleziona l'edizione a cui vuoi aggiornare e fai clic su **Aggiorna**. I downgrade dell'edizione della licenza non sono disponibili.

   L'aggiornamento della licenza sostituisce tutte le licenze NSX esistenti sull'istanza. Potrebbero essere addebitati costi aggiuntivi derivanti da una sovrapposizione di vecchie e nuove licenze se esegui l'aggiornamento nel mezzo di un ciclo di fatturazione. Per evitare costi aggiuntivi, si consiglia di aggiornare la licenza alla fine del ciclo di fatturazione.
   {:note}

6. Per gli aggiornamenti software, fai clic sulla freccia in giù per espandere l'aggiornamento che vuoi applicare e quindi completa uno dei seguenti passi:
   *  Per avviare immediatamente l'aggiornamento, fai clic sull'icona del menu di overflow nella colonna **Azioni** della voce di aggiornamento, quindi fai clic su **Aggiorna ora**.
   *  Per pianificare un aggiornamento futuro, fai clic sull'icona del menu di overflow nella colonna **Azioni** della voce di aggiornamento, quindi fai clic su **Pianifica aggiornamento**. Seleziona la data, l'ora e il fuso orario in cui vuoi avviare l'aggiornamento. Fai clic su **OK**.
7. Se applichi aggiornamenti alle istanze vCenter Server nella configurazione di distribuzione multisito, viene visualizzata una sezione intitolata **Passi necessari per l'aggiornamento**. Questa sezione elenca le operazioni di aggiornamento richieste per tutte le istanze nella distribuzione multisito. Devi completare i passi in sequenza facendo clic su **Applica aggiornamento** per ciascun passo. Devi attendere il completamento del passo precedente prima di iniziare il passo successivo.   

## Risultati

2. Dopo aver applicato un aggiornamento, viene visualizzato un record nell'elenco di stato degli aggiornamenti software, in cui puoi visualizzare l'avanzamento dettagliato e lo stato dell'aggiornamento. Al termine dell'aggiornamento, viene visualizzato un record nell'elenco degli aggiornamenti software installati.

  Per recuperare lo stato più recente per un lavoro di aggiornamento, fai clic sull'icona di aggiornamento nella parte superiore destra della pagina.
  {:tip}

3. Per i dettagli sugli stati degli aggiornamenti, consulta il seguente elenco:
<dl class="dl">
<dt class="dt dlterm">Disponibile</dt>
<dd class="dd">L'aggiornamento è disponibile per l'applicazione. Non puoi selezionare un aggiornamento disponibile finché non vengono applicati tutti gli aggiornamenti precedenti.
</dd>
<dt class="dt dlterm">In corso</dt>
<dd class="dd">Il lavoro di aggiornamento è iniziato ma non è ancora terminato. Non puoi applicare altri aggiornamenti finché non viene completato il lavoro di aggiornamento
corrente.</dd>
<dt class="dt dlterm">Installato</dt>
<dd class="dd">Il lavoro di aggiornamento è completato. Il componente corrispondente della piattaforma VMware è aggiornato.</dd>
<dt class="dt dlterm">Non riuscito</dt>
<dd class="dd">Il lavoro di aggiornamento non riesce. La console segnala un errore di aggiornamento. Esamina l'errore e correggi il problema segnalato prima
di riapplicare l'aggiornamento.</dd>
<dt class="dt dlterm">Pianificato</dt>
<dd class="dd">Il lavoro di aggiornamento è pianificato per un secondo momento. Il lavoro di aggiornamento si avvia automaticamente all'ora pianificata.</dd>
<dt class="dt dlterm">Sconosciuto</dt>
<dd class="dd">Non è possibile ottenere lo stato del lavoro di aggiornamento. Contatta il supporto IBM per assistenza.</dd>
</dl>

4. Se il processo di aggiornamento non riesce in un passo specifico, [contatta il supporto IBM](../vmonic/trbl_support.html) per assistenza. Ti verrà comunicato come risolvere il problema e sarai guidato a tentare nuovamente l'aggiornamento dal passo non riuscito.

### Link correlati

* [Panoramica di vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
