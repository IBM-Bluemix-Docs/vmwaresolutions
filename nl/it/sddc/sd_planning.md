---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Requisiti e pianificazione per le istanze Cloud Foundation

Esamina i seguenti requisiti prima di ordinare le tue istanze VMware Cloud Foundation. Pianifica la tua istanza in base all'ubicazione del {{site.data.keyword.CloudDataCent}}, ai requisiti di capacità del tuo carico di lavoro e ai requisiti del servizio.

## Requisiti dell'account IBM Cloud

L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti per l'account {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilità dei data center IBM Cloud

La distribuzione di Cloud Foundation ha requisiti rigorosi sull'infrastruttura fisica. Pertanto, puoi distribuire le istanze solo nei {{site.data.keyword.CloudDataCents_notm}} che soddisfano i requisiti. Per la distribuzione di Cloud Foundation sono disponibili i seguenti {{site.data.keyword.CloudDataCents_notm}}:

Tabella 1. {{site.data.keyword.CloudDataCents_notm}} e configurazioni di Bare Metal Server {{site.data.keyword.cloud_notm}} disponibili per le istanze Cloud Foundation

| {{site.data.keyword.CloudDataCent_notm}} | Ubicazione | Regione | Configurazioni server |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europa | Skylake, Broadwell |
| CHE01 | Chennai | Asia Pacifico | Skylake, Broadwell |
| DAL09 | Dallas | Nord America meridionale | Skylake, Broadwell |
| DAL10 | Dallas | Nord America meridionale | Skylake, Broadwell |
| DAL12 | Dallas | Nord America meridionale | Skylake, Broadwell |
| DAL13 | Dallas | Nord America meridionale | Skylake, Broadwell |
| FRA02 | Francoforte | Europa | Skylake, Broadwell |
| FRA04 | Francoforte | Europa | Skylake, Broadwell |
| HKG02 | Hong Kong | Asia Pacifico | Skylake, Broadwell |
| LON02 | Londra | Europa | Skylake, Broadwell |
| LON04 | Londra | Europa | Skylake, Broadwell |
| LON06 | Londra | Europa | Skylake, Broadwell |
| MEL01 | Melbourne | Asia Pacifico | Skylake, Broadwell |
| MEX01 | Queretaro | Nord America meridionale | Skylake, Broadwell |
| MIL01 | Milano | Europa | Skylake, Broadwell |
| MON01 | Montreal | Nord America orientale | Skylake, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Broadwell |
| PAR01 | Parigi | Europa | Skylake, Broadwell |
| SAO01 | San Paolo | Sud America | Skylake, Broadwell |
| SEO01 | Seul | Asia Pacifico | Skylake, Broadwell |
| SJC03 | San Jose | Nord America occidentale | Skylake, Broadwell |
| SJC04 | San Jose | Nord America occidentale | Skylake, Broadwell |
| SNG01 | Singapore | Asia Pacifico | Skylake, Broadwell |
| SYD01 | Sydney | Asia Pacifico | Skylake, Broadwell |
| SYD04 | Sydney | Asia Pacifico | Skylake, Broadwell |
| TOK02 | Tokyo | Asia Pacifico | Skylake, Broadwell |
| TOR01 | Toronto | Nord America orientale | Skylake, Broadwell |
| WDC04 | Washington, DC | Nord America orientale | Skylake, Broadwell |
| WDC06 | Washington, DC | Nord America orientale | Skylake, Broadwell |
| WDC07 | Washington, DC | Nord America orientale | Skylake, Broadwell |

A seconda della disponibilità e della fornitura di inventario, i {{site.data.keyword.CloudDataCents_notm}} potrebbero visualizzare un indicatore di stato nella console {{site.data.keyword.vmwaresolutions_short}} per aiutarti a pianificare le tue distribuzioni.

Tabella 2. Indicatori di stato per i {{site.data.keyword.CloudDataCents_notm}} quando ordini istanze Cloud Foundation

| Stato | Dettagli sullo stato |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | Il {{site.data.keyword.CloudDataCent_notm}} non è attualmente disponibile. |
| Temporarily Out of Inventory  | Il {{site.data.keyword.CloudDataCent_notm}} al momento non ha disponibilità. |
| Limited Inventory             | Il {{site.data.keyword.CloudDataCent_notm}} ha una disponibilità limitata e l'ordine potrebbe non essere completato. |

## Backup dei componenti di gestione

Sei responsabile del mantenimento e della verifica della disponibilità di tutti i componenti dell'istanza. Si consiglia di pianificare il backup o l'alta disponibilità di tutti i componenti di gestione. Per ulteriori informazioni, vedi [Backup dei componenti](../archiref/solution/solution_backingup.html).

## Servizi per le istanze Cloud Foundation

Puoi ordinare servizi aggiuntivi per la tua istanza in base alle tue esigenze, ad esempio il ripristino di emergenza. Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](sd_addingremovingservices.html).

## Considerazioni sulla capacità

Per ulteriori informazioni sulla capacità, vedi [Ridimensionamento della capacità](../archiref/solution/solution_scaling.html).

### Link correlati

* [Panoramica di Cloud Foundation](sd_cloudfoundationoverview.html)
* [Ordine di istanze Cloud Foundation](sd_orderinginstance.html)
* [Espansione e contrazione della capacità per le istanze Cloud Foundation](sd_addingremovingservers.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](sd_addingremovingservices.html)
