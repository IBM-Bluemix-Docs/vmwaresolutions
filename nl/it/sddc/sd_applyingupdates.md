---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Applicazione di aggiornamenti alle istanze Cloud Foundation

La console {{site.data.keyword.vmwaresolutions_full}} rileva ed elenca periodicamente gli aggiornamenti software disponibili che puoi applicare al tuo ambiente virtuale VMware.

Un aggiornamento disponibile è un record nell'elenco di aggiornamenti software dell'istanza, che può essere applicato immediatamente o pianificato per un secondo momento. L'aggiornamento è un bundle che contiene uno o più pacchetti per l'aggiornamento dei componenti di gestione IBM e dei componenti VMware.

A partire dalla V2.5, gli aggiornamenti di IBM CloudDriver non sono più elencati perché sono abilitati gli aggiornamenti automatici. Azioni come l'aggiunta di un host, l'aggiunta di un cluster e l'ordine di un servizio aggiornano automaticamente l'istanza all'ultima versione. Per ulteriori informazioni sugli aggiornamenti automatici, consulta la sezione *Resilienza di IBM CloudDriver* in [Note sulla release per la V2.5](../vmonic/relnotes_v25.html).
{:note}

## Prima di iniziare

Prima di tentare di applicare un aggiornamento, espandi la voce di aggiornamento facendo clic sulla freccia in giù e verifica le seguenti informazioni:
* La versione dell'aggiornamento. Devi applicare gli aggiornamenti in sequenza cronologica, dalla più antica alla più recente. Assicurati di aver applicato tutti gli aggiornamenti precedenti prima di applicare quello più recente. Ad esempio, devi applicare l'aggiornamento V2.4 prima di tentare di applicare l'aggiornamento V2.5.
* Se è necessario un tempo di inattività.
* Il tempo totale stimato per completare l'aggiornamento.
* L'impatto dell'aggiornamento sull'ambiente virtuale VMware. La tabella 1 mostra come i diversi livelli di impatto degli aggiornamenti sul sistema.
* I dettagli dell'aggiornamento.

Tabella 1. Livelli di aggiornamento e impatto

<table>
  <tr>
    <th>Livello di aggiornamento</th>
    <th>Impatto</th>
  </tr>
  <tr>
    <td>Basso</td>
    <td>Questo aggiornamento non influisce su alcun sistema. Non devi applicarlo durante i tempi di inattività
    pianificati.</td>
  </tr>
  <tr>
    <td>Medio</td>
  <td>Questo aggiornamento potrebbe influire su alcuni sistemi. Si consiglia di applicarlo durante i tempi di inattività
    pianificati.</td>
  </tr>
    <tr>
    <td>Maggiore</td>
  <td>Questo aggiornamento influisce su alcuni o tutti i sistemi. Devi applicarlo durante i tempi di inattività pianificati.</td>
  </tr>
</table>

## Procedura per applicare aggiornamenti alle istanze Cloud Foundation

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza da aggiornare.
3. Nella pagina **Riepilogo**, verifica che tutti i dettagli dell'istanza siano visualizzati correttamente. Quindi, fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra per verificare i dettagli nella pagina **Infrastruttura**.
   Se i dettagli non vengono visualizzati, potrebbe indicare un problema di connettività con la VSI (Virtual Server Instance) IBM CloudDriver, a seguito di una regola del firewall o di altri problemi di rete. Risolvi il problema prima di continuare con il passo successivo, altrimenti l'aggiornamento potrebbe non riuscire.
4. Fai clic su **Aggiorna e applica patch** nel riquadro di navigazione a sinistra.
5. Fai clic sulla freccia in giù per espandere l'aggiornamento che vuoi applicare e quindi completa uno dei seguenti passi:
   *  Per avviare immediatamente l'aggiornamento, fai clic sull'icona del menu di overflow nella colonna **Azioni** della voce di aggiornamento, quindi fai clic su **Aggiorna ora**.
   *  Per pianificare un aggiornamento futuro, fai clic sull'icona del menu di overflow nella colonna **Azioni** della voce di aggiornamento, quindi fai clic su **Pianifica aggiornamento**. Seleziona la data, l'ora e il fuso orario in cui vuoi avviare l'aggiornamento. Fai clic su **OK**.
6. Se applichi aggiornamenti alle istanze Cloud Foundation nella configurazione di distribuzione multisito, viene visualizzata una sezione intitolata **Passi necessari per l'aggiornamento**, che elenca le operazioni di aggiornamento richieste per tutte le istanze nella distribuzione multisito. Devi completare i passi in sequenza facendo clic su **Applica aggiornamento** per ciascun passo. Devi attendere il completamento del passo precedente prima di iniziare il passo successivo.

## Risultati

1. Prima che venga avviata un'operazione di aggiornamento, viene completato un controllo di integrità dell'istanza. Se il controllo di integrità non riesce, verrai avvisato in modo da poter risolvere il problema prima di applicare l'aggiornamento.
2. Durante gli aggiornamenti che includono aggiornamenti dei componenti VMware, potrebbe essere necessario eseguire la migrazione delle VM dai server ESXi per passare alla modalità di manutenzione. La migrazione della VM potrebbe essere impedita se in una VM è montato un archivio dati o CD-ROM locale.
3. Durante il provisioning di un nuovo ambiente, {{site.data.keyword.vmwaresolutions_short}} crea l'ID **automationuser** che viene utilizzato per la gestione dell'istanza, incluso per l'applicazione degli aggiornamenti. Non modificare la password per questo ID utente. La modifica della password potrebbe causare un errore nell'aggiornamento.

4. Dopo aver applicato un aggiornamento, viene visualizzato un record nell'elenco di stato degli aggiornamenti software, in cui puoi visualizzare l'avanzamento dettagliato e lo stato dell'aggiornamento. Al termine dell'aggiornamento, viene visualizzato un record nell'elenco degli aggiornamenti software installati.

  Per recuperare lo stato più recente per un lavoro di aggiornamento, fai clic sull'icona di aggiornamento nella parte superiore destra della pagina.
  {:tip}

5. Per ulteriori informazioni sugli stati di aggiornamento, consulta la seguente tabella.

   Tabella 2. Dettagli degli stati di aggiornamento

    <table>
      <tr>
        <th>Stato</th>
        <th>Dettagli</th>
      </tr>
      <tr>
        <td>Disponibile</td>
        <td>L'aggiornamento è disponibile per l'applicazione. Non puoi selezionare un aggiornamento disponibile finché non vengono applicati tutti gli aggiornamenti precedenti.</td>
      </tr>
      <tr>
        <td>In corso</td>
      <td>Il lavoro di aggiornamento è iniziato ma non è ancora terminato. Non puoi applicare altri aggiornamenti finché non viene completato il lavoro di aggiornamento corrente. </td>
      </tr>
        <tr>
        <td>Installato</td>
      <td>Il lavoro di aggiornamento è completato. Il componente corrispondente della piattaforma VMware è aggiornato.</td>
      </tr>
        <tr>
        <td>Non riuscito</td>
      <td>Il lavoro di aggiornamento non riesce. La console segnala un errore di aggiornamento. Esamina l'errore e correggi il problema segnalato prima di riapplicare l'aggiornamento.</td>
      </tr>
          <tr>
        <td>Pianificato</td>
      <td>Il lavoro di aggiornamento è pianificato per un secondo momento. Il lavoro di aggiornamento si avvia automaticamente all'ora pianificata.</td>
      </tr>
          <tr>
        <td>Sconosciuto</td>
      <td>Non è possibile ottenere lo stato del lavoro di aggiornamento. Contatta il supporto IBM per assistenza.</td>
      </tr>
    </table>

6. Se il processo di aggiornamento non riesce in un passo specifico, [contatta il supporto IBM](../vmonic/trbl_support.html) per assistenza. Ti verrà comunicato come risolvere il problema e sarai guidato a riavviare l'aggiornamento dal passo non riuscito.

### Link correlati

* [Panoramica di Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
