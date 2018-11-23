---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di istanze NetApp ONTAP Select

Per distribuire una piattaforma virtualizzata VMware con un'applicazione di archiviazione definita dal software dedicata e altamente disponibile, ordina un'istanza NetApp ONTAP Select.

## Requisiti

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](../vmonic/useraccount.html).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per le istanze NetApp ONTAP Select](np_planning.html).

Non modificare alcun valore impostato durante l'ordine o la distribuzione dell'istanza. La modifica rende inutilizzabile la tua istanza. Ad esempio, se la rete pubblica si interrompe, se i server e le VSI (Virtual Server Instance) vanno dietro una fornitura media di Vyatta o se la VSI di IBM CloudBuilder si arresta o viene eliminata.
{:important}

## Impostazioni di sistema

Quando ordini un'istanza NetApp ONTAP Select, devi specificare le seguenti impostazioni di base.

### Nome istanza

Il nome dell'istanza deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome dell'istanza deve iniziare e terminare con un carattere alfanumerico.
* La lunghezza massima del nome dell'istanza è di 10 caratteri.
* Il nome dell'istanza deve essere univoco all'interno del tuo account.

## Impostazioni dell'interfaccia di rete

Quando ordini un'istanza NetApp ONTAP Select, devi specificare le seguenti impostazioni dell'interfaccia di rete.

### Prefisso nome host

Il prefisso del nome host deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  Il prefisso del nome host deve iniziare e terminare con un carattere alfanumerico.
*  La lunghezza massima del prefisso del nome host è di 10 caratteri.

### Etichetta dominio secondario

L'etichetta del dominio secondario deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  L'etichetta del dominio secondario deve iniziare e terminare con un carattere alfanumerico.
*  La lunghezza massima dell'etichetta del dominio secondario è di 10 caratteri.
*  L'etichetta del dominio secondario deve essere univoca all'interno del tuo account.

### Nome dominio

Il nome del dominio root deve rispettare i seguenti requisiti:
* Il nome del dominio deve essere composto da due o più stringhe separate da un punto (.)
* La prima stringa deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* Tutte le stringhe, eccetto l'ultima, possono includere solo caratteri alfanumerici e trattini (-).
* L'ultima stringa può includere solo caratteri alfabetici.
* La lunghezza dell'ultima stringa deve essere compresa tra 2 e 24 caratteri.

La lunghezza massima del nome di dominio completo (o FQDN, Fully Qualified Domain Name) per gli host e le VM (macchine virtuali) è di 50 caratteri. I nomi di dominio devono essere adattati a questa lunghezza massima.
{:note}

## Impostazioni di licenza

Devi caricare quattro file di licenza NetApp, uno per ciascuno dei quattro {{site.data.keyword.baremetal_short}}. Contatta il tuo team di vendite NetApp per ottenere le licenze appropriate per la tua distribuzione ad alte prestazioni o ad alta capacità.

## Impostazioni di Bare Metal Server

### Ubicazione data center

Devi selezionare il {{site.data.keyword.CloudDataCent_notm}} in cui deve essere ospitata l'istanza.

### Configurazione Bare Metal Server

Seleziona una configurazione Bare Metal Server in base ai tuoi requisiti:
* **Alte prestazioni (Medium)** – Licenza Premium / Dual Intel Xeon E5-2650 v4 (24 core totali, 2,2 GHz) / 128 GB di RAM / Capacità di 22 unità SSD da 1,9 TB per nodo / Capacità effettiva di un cluster a 4 nodi – 59 TB
* **Alte prestazioni (Large)** – Licenza Premium / Dual Intel Xeon E5-2650 v4 (24 core totali, 2,2 GHz) / 128 GB di RAM / Capacità di 22 unità SSD da 3,8 TB per nodo / Capacità effettiva di un cluster a 4 nodi – 118 TB
* **Alta capacità** – Licenza Standard / Dual Intel Xeon E5-2650 v4 (24 core totali, 2,2 GHz) / 64 GB di RAM / Capacità di trentaquattro unità SATA da 4 TB per nodo / Capacità effettiva di un cluster a 4 nodi – 190 TB

Le unità SSD (Solid-State Disk) da 3,8 TB sono supportate quando vengono rese generalmente disponibili in un {{site.data.keyword.CloudDataCent_notm}}.
  {:note}

### Numero di server Bare Metal

Il numero di server ESXi di un'istanza NetApp ONTAP Select è 4 per impostazione predefinita. Non puoi modificare questo valore. Tutti i server ESXi condividono la configurazione.

## Procedura per ordinare le istanze NetApp ONTAP Select

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e quindi su **NetApp ONTAP Select** nella sezione **Data center virtuali**.
2. Nella pagina **NetApp ONTAP Select**, fai clic su **Crea**.
3. Nella pagina **NetApp ONTAP**, immetti il nome dell'istanza.
4. Completa le impostazioni dell'interfaccia di rete immettendo il **Prefisso nome host**, l'**Etichetta sottodominio** e il **Nome dominio**.
5. Completa le impostazioni di licenza facendo clic su **Aggiungi file di licenza** per caricare quattro file di licenza NetApp richiesti dai quattro {{site.data.keyword.baremetal_short}}.
6. Completa le impostazioni di Bare Metal Server:
   1. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.
   2. Seleziona la configurazione di Bare Metal Server.
7. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
    1. Esamina le impostazioni per l'istanza.
    2. Esamina il costo stimato dell'istanza. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** dalla finestra PDF.
    3. Assicurati che l'account da addebitare sia corretto e seleziona quindi la casella di spunta **Accetto che all'account riportato di seguito venga addebitato un corrispettivo**.
    4. Fai clic sul link o sui link dei termini che si applicano al tuo ordine. Assicurati di accettare questi termini e quindi seleziona la casella di spunta **Ho letto e accetto gli accordi di servizio di terze parti elencati di seguito**.
    5. Fai clic su **Fornitura**.

## Risultati

La distribuzione dell'istanza inizia automaticamente. Riceverai la conferma che l'ordine è in fase di elaborazione e puoi controllare lo stato della distribuzione visualizzando i dettagli dell'istanza.

Una volta che l'istanza è stata distribuita correttamente, i componenti descritti in [Specifiche tecniche per le istanze NetApp ONTAP Select](../netapp/np_netappoverview.html#technical-specifications-for-netapp-ontap-select-instances) vengono installati sulla tua piattaforma virtuale VMware.

Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e riceverai una notifica via e-mail.

## Operazioni successive

Visualizza e gestisci l'istanza NetApp ONTAP Select che hai ordinato.

Devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console. Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.
{:important}

**ATTENZIONE:** la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}} (installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza) dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Spegnimento dei componenti

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

### Link correlati

* [Visualizzazione delle istanze NetApp ONTAP Select](np_viewinginstances.html)
* [Eliminazione di istanze NetApp ONTAP Select](np_deletinginstance.html)
* [Centro di documentazione di NetApp ONTAP](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Collega l'archiviazione dedicata alle distribuzioni di NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
