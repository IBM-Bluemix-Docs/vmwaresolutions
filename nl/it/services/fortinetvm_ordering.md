---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di FortiGate Virtual Appliance on IBM Cloud

Puoi ordinare il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud}} quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per una nuova istanza

Puoi ordinare una nuova istanza con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **FortiGate Virtual Appliance on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **FortiGate Virtual Appliance on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di FortiGate Virtual Appliance on IBM Cloud per un'istanza esistente

Puoi aggiungere il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **FortiGate Virtual Appliance on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

## Configurazione del servizio FortiGate Virtual Appliance on IBM Cloud

Quando ordini il servizio, fornisci le seguenti impostazioni.

### Connessione di rete FortiGuard

Seleziona **Rete pubblica** o **Rete privata** per FortiGuard. Se il cluster di destinazione è configurato con interfacce di rete solo private, è disponibile solo l'opzione **Rete privata**. Questa selezione determina come FortiGuard contatterà il server di licenza Fortinet per attivare la licenza e per scaricare le patch di sicurezza e non influirà sul piano di dati del carico di lavoro.

Se selezioni **Rete privata**, specifica le seguenti impostazioni:
* **Indirizzo IP proxy**: l'indirizzo IPv4 del server proxy.
* **Numero porta proxy**: il numero di porta del server proxy, di solito 8080 o 3128.
* **Nome utente proxy**: se hai bisogno dell'autenticazione proxy, immetti il nome utente del server proxy.
* **Password proxy**: se hai bisogno dell'autenticazione proxy, immetti la password del server proxy.

### Nome

Immetti il nome del servizio.

### Dimensione distribuzione

{{site.data.keyword.cloud_notm}} fornisce le seguenti opzioni di dimensioni della distribuzione:
* Small (2 vCPU / 4 GB di RAM)
* Medium (4 vCPU / 6 GB di RAM)
* Large (8 vCPU / 12 GB di RAM)

### Modello di licenza

Il modello di licenza per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} offre le seguenti opzioni:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">Questo bundle include Filtraggio stateful dei pacchetti, Protezione VLAN e registrazione avanzata, Regole firewall in entrata e in uscita, Terminazione VPN SSL/IPSec e supporto e supporto 24 x 7.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">Questo bundle include tutti i servizi firewall standard oltre al servizio Advanced Malware Protection (AMP) (tra cui Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, FortiSandbox Cloud, Virus Outbreak Protection Service e Content Disarm & Reconstruct), nonché i servizi Web Filtering, IPS, Antispam, Application Control e FortiCare.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">Questo bundle include tutti i servizi firewall standard e i servizi UTM oltre ai seguenti servizi:<ul><li>Cloud Access Security Broker (CASB): Questo servizio fornisce visibilità, conformità, sicurezza dei dati e protezione delle minacce per i servizi basati sul cloud.</li><li>Industrial Security: Questo servizio fornisce firme per i protocolli ICS/SCADA comuni.</li><li>Security Rating: Questo servizio fornisce funzionalità di controllo per identificare le vulnerabilità critiche e le debolezze della configurazione e implementare i suggerimenti delle procedure consigliate.</li></ul></dd>
</dl>

Nel terzo quadrimestre del 2018, Fortinet ha aggiunto tre nuovi servizi (CASB, Industrial Security, e Security Rating) al proprio bundle aziendale. Questi servizi sono disponibili solo su FortiGate 6.0.
{:note}

Non puoi modificare il modello di licenza dopo l'installazione del servizio. Per modificare il modello di licenza, devi rimuovere il servizio esistente e reinstallare il servizio selezionando un'opzione di licenza diversa.
{:important}

### Link correlati

* [Panoramica di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_considerations.html)
* [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
