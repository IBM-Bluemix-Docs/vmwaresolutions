---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle

Esamina i seguenti requisiti prima di ordinare la tua istanza VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Pianifica la tua istanza in base all'ubicazione del {{site.data.keyword.CloudDataCent_notm}}, ai requisiti di capacità del tuo carico di lavoro e ai requisiti di servizi aggiuntivi.

## Requisiti dell'account IBM Cloud

L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti per l'account {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilità dei data center IBM Cloud

La distribuzione di vCenter Server with Hybridity Bundle ha requisiti rigorosi sull'infrastruttura fisica. Pertanto, puoi distribuire le istanze solo nei {{site.data.keyword.CloudDataCents_notm}} che soddisfano i requisiti. Per la distribuzione di vCenter Server with Hybridity Bundle sono disponibili i seguenti {{site.data.keyword.CloudDataCents_notm}}:

Tabella 1. {{site.data.keyword.CloudDataCents_notm}} disponibili per le istanze vCenter Server with Hybridity Bundle

| {{site.data.keyword.CloudDataCent_notm}} | Ubicazione | Regione |
|:-----|:----------------|
| AMS03 | Amsterdam | Europa |
| CHE01 | Chennai | Asia Pacifico |
| DAL09 | Dallas | Nord America meridionale |
| DAL10 | Dallas | Nord America meridionale |
| DAL12 | Dallas | Nord America meridionale |
| DAL13 | Dallas | Nord America meridionale |
| FRA02 | Francoforte | Europa |
| FRA04 | Francoforte | Europa |
| HKG02 | Hong Kong | Asia Pacifico |
| LON02 | Londra | Europa |
| LON04 | Londra | Europa |
| LON06 | Londra | Europa |
| MEL01 | Melbourne | Asia Pacifico |
| MEX01 | Queretaro | Nord America meridionale |
| MIL01 | Milano | Europa |
| MON01 | Montreal | Nord America orientale |
| OSL01 | Oslo | Europa |
| PAR01 | Parigi | Europa |
| SAO01 | San Paolo | Sud America |
| SEO01 | Seul | Asia Pacifico |
| SJC03 | San Jose | Nord America occidentale |
| SJC04 | San Jose | Nord America occidentale |
| SNG01 | Singapore | Asia Pacifico |
| SYD01 | Sydney | Asia Pacifico |
| SYD04 | Sydney | Asia Pacifico |
| TOK02 | Tokyo | Asia Pacifico |
| TOR01 | Toronto | Nord America orientale |
| WDC04 | Washington, DC | Nord America orientale |
| WDC06 | Washington, DC | Nord America orientale |
| WDC07 | Washington, DC | Nord America orientale |

A seconda della disponibilità e della fornitura di inventario, i {{site.data.keyword.CloudDataCents_notm}} potrebbero visualizzare un indicatore di stato nella console {{site.data.keyword.vmwaresolutions_short}} per aiutarti a pianificare le tue distribuzioni.

Tabella 2. Indicatori di stato per i {{site.data.keyword.CloudDataCents_notm}} quando ordini le istanze vCenter Server with Hybridity Bundle

| Stato | Dettagli sullo stato |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | Il {{site.data.keyword.CloudDataCent_notm}} non è attualmente disponibile. |
| Temporarily Out of Inventory  | Il {{site.data.keyword.CloudDataCent_notm}} al momento non ha disponibilità. |
| Limited Inventory             | Il {{site.data.keyword.CloudDataCent_notm}} ha una disponibilità limitata e l'ordine potrebbe non essere completato. |

## Backup dei componenti di gestione

Sei responsabile del mantenimento e della verifica della disponibilità di tutti i componenti dell'istanza. Si consiglia vivamente di pianificare il backup o l'alta disponibilità di tutti i componenti di gestione. Per ulteriori informazioni, vedi [Backup dei componenti](../archiref/solution/solution_backingup.html).

## Servizi per le istanze vCenter Server with Hybridity Bundle

L'istanza vCenter Server with Hybridity Bundle include la licenza di VMware Hybrid Cloud Extension (HCX) che ti dà diritto al servizio VMware HCX on {{site.data.keyword.cloud_notm}}. Questo servizio può estendere senza problemi le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione delle macchine virtuali (VM) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.

Quando distribuisci questo servizio, completa le seguenti impostazioni:
* Specifica il **Tipo di interconnessione HCX** selezionando una delle seguenti opzioni:
  * **Rete pubblica**: HCX crea una connessione crittografata tra i siti sulla rete pubblica.
  * **Rete privata**: HCX crea una connessione crittografata tra i siti sulla rete privata.
* Specifica il **Tipo di certificato endpoint pubblico**. Se selezioni **Certificato CA**, configura le seguenti impostazioni:
  * **Contenuto del certificato**: immetti il contenuto del certificato CA.
  * **Chiave privata**: immetti la chiave privata del certificato CA.
  * (Facoltativo) **Password**: immetti la password per la chiave privata, se è crittografata.
  * (Facoltativo) **Immettere nuovamente la password**: immetti di nuovo la password per la chiave privata.
  * (Facoltativo) **Nome host**: immetti il nome host da associare al nome comune (CN) del certificato CA. HCX on {{site.data.keyword.cloud_notm}} richiede che il certificato CA sia in un formato accettato da Edge NSX. Per ulteriori informazioni sui formati dei certificati Edge NSX, vedi [Importazione di certificati SSL](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

Puoi ordinare altri servizi aggiuntivi per la tua istanza in base alle tue esigenze, come ad esempio il ripristino di emergenza. Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html).

## Considerazioni sulla capacità

Per ulteriori informazioni relative alle considerazioni sulla capacità, vedi [Ridimensionamento della capacità](../archiref/solution/solution_scaling.html).

### Link correlati

* [Panoramica di vCenter Server with Hybridity Bundle](vc_hybrid_overview.html)
* [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
* [Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html)
