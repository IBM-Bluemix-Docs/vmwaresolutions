---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Gestione delle notifiche di sistema

Puoi controllare le notifiche per verificare lo stato delle operazioni di sistema o dell'utente. Puoi anche utilizzare le informazioni per analizzare i problemi che potrebbero verificarsi.

## Visualizzazione delle notifiche

1. Dalla console {{site.data.keyword.vmwaresolutions_full}}, fai clic su **Notifiche** nel riquadro di navigazione a sinistra.
2. Visualizza il riepilogo su tutte le notifiche.

   Tabella 1. Cronologia delle notifiche

    <table>
      <tr>
        <th>Colonna</th>
        <th>Descrizione</th>
      </tr>
      <tr>
        <td>Severità</td>
        <td>La severità dell'evento segnalato dalla notifica.
          <dl class="dl">
          <dt class="dt dlterm">Critico</dt>
          <dd class="dd">Un evento critico potrebbe influire sull'intero sistema o servizio.</dd>
          <dt class="dt dlterm">Errore</dt>
          <dd class="dd">Si verifica un evento di errore durante un'operazione che potrebbe richiedere l'intervento dell'amministratore o dell'utente.</dd>
          <dt class="dt dlterm">Avvertenza</dt>
          <dd class="dd">Un componente produce errori o non funziona correttamente. Tuttavia, l'errore non interrompere il processo in corso del componente.</dd>
            <dt class="dt dlterm">Informativo</dt>
            <dd class="dd">È stata completata un'operazione di sistema o utente. In genere, i seguenti eventi segnalano notifiche informative:
              <ul class="ul">
                <li class="li">Un servizio è stato installato.</li>
                <li class="li">Un servizio è stato aggiornato.</li>
                <li class="li">Un servizio è stato rimosso.</li>
                <li class="li">Tutti i servizi sono stati riconfigurati per i server ESXi aggiunti.</li>
                <li class="li">Tutti i servizi sono stati riconfigurati per i server ESXi rimossi.</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>Tipo</td>
         <td>Il tipo di componente a cui è correlato l'evento segnalato:<ul><li>Istanze vCenter Server</li><li>Istanze Cloud Foundation</li><li>Servizi</li><li>Sistema</li></ul></td>
       </tr>
       <tr>
         <td>Risorsa</td>
         <td>Il nome dell'istanza o del servizio che invia la notifica.</td>
       </tr>
       <tr>
         <td>Descrizione</td>
         <td>Una breve descrizione della notifica.</td>
       </tr>
       <tr>
         <td>Data</td>
         <td>La data e ora in cui la notifica è stata inviata.</td>
       </tr>
    </table>                                       

3. Fai clic su una riga di notifica per visualizzarne i dettagli.

## Filtraggio delle notifiche

Per impostazione predefinita, vengono visualizzate tutte le notifiche non lette. Puoi filtrare le notifiche per stato, severità e tipo. Per filtrare le notifiche, seleziona le caselle di spunta solo per gli elementi che vuoi visualizzare negli elenchi **Stato**, **Severità** o **Tipo**.

### Link correlati

* [Domande frequenti](faq.html)
* [Account utente e impostazioni](useraccount.html)
