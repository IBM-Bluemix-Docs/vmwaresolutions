---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

# Panoramica di Mission Critical VMware on IBM Cloud

Mission Critical VMware on {{site.data.keyword.cloud}} offre un'architettura a più zone per aiutare le aziende ad evitare il tempo di inattività delle applicazioni cloud e ad automatizzare i failover in una regione cloud.

Con questa architettura cloud, i clienti possono raggiungere una maggiore disponibilità e una percentuale di successo di failover rispetto a quella che la maggior parte dei client VMware possono raggiungere con gli ambienti in loco o con le piattaforme cloud concorrenti.

Questa architettura supporta i carichi di lavoro esistenti di importanza critica e legacy, incluse le applicazioni native non cloud, ad una disponibilità aggregata mirata del 99,99%. Le regioni di IBM Cloud a più zone sono progettate per mantenere i carichi di lavoro di importanza critica online se si verifica un'interruzione del sito. I carichi di lavoro in un sito malfunzionante vengono riavviati automaticamente quasi in tempo reale, mentre i carichi di lavoro nei siti adiacenti rimangono online e disponibili.

L'architettura comprende vari servizi aziendali, tra cui reti, archiviazione, resilienza e altri strumenti creati per il monitoraggio e la risoluzione dei problemi delle applicazioni basate sul cloud. Inoltre, questa architettura può essere integrata con IBM Services Platform with Watson, creata su {{site.data.keyword.cloud_notm}}, per consentire un più ampio utilizzo dei servizi. Utilizzando le funzionalità cognitive della piattaforma, i client possono estrarre i dati in modo più efficace per le nuove informazioni aziendali per aiutare a mantenere le operazioni continue.

## Specifiche tecniche per Mission Critical VMware on IBM Cloud

L'architettura Mission Critical VMware on {{site.data.keyword.cloud_notm}} è un'architettura di riferimento end-to-end che fornisce il failover automatizzato per i carichi di lavoro del cliente. Utilizza una regione a più zone {{site.data.keyword.cloud_notm}} on un servizio gestito da IBM che comprende i seguenti componenti:

* Architettura di calcolo (VMware vSphere)
* Architettura di rete (al momento NSX-V)
* Architettura di archiviazione (VMware vSAN)
* Integrazione con IBM Services Platform with Watson per abilitare l'utilizzo dei servizi
* Strumenti per il monitoraggio, la risoluzione dei problemi, le prestazioni e la gestione della capacità:
  * Modello di suite vRealize (Operations, Log Insight e Network Insight)
  * Modello Active Directory
  * Integrazione con Netcool/Bluecare per la creazione di ticket automatica, l'avvivo e l'arricchimento di eventi
  * Modelli di resilienza (backup e ripristino)

Mission Critical VMware on {{site.data.keyword.cloud_notm}} è disponibile nelle seguenti regioni:
* America: Nord America meridionale - Tutti i data center IBM Cloud in Dallas e in Nord America orientale: tutti i data center IBM Cloud in Washington, DC
* Europa: tutti i data center IBM Cloud in Francoforte e Londra
* Asia Pacifico: tutti i data center IBM Cloud in Sydney e Tokyo

### Specifiche dell'architettura dell'infrastruttura di base

L'infrastruttura di base ha le seguenti specifiche:
* Ogni sito ha il proprio cluster di gestione e edge dedicato
* Il cluster della risorsa è un cluster esteso vSphere + vSAN
* Il sito di controllo contiene un host ESXi di controllo
* Architettura singolo vCenter e NSX Manager
* vCenter Server Appliance con Platform Services Controller (PSC) integrato che utilizza vCenter High Availability (HA) su un'architettura di rete L3
* Il ripristino NSX Manager sta utilizzando una metodologia Hot/Standby che sincronizza i file di backup

### Specifiche dell'architettura dell'infrastruttura dello strumento e della tecnologia

L'architettura dello strumento e della tecnologia ha le seguenti specifiche:
* vRealize Operations, vRealize Log Insight e vRealize Network Insight per fornire le funzionalità di gestione e operative specifiche per i prodotti VMware che stai utilizzando, ad esempio NSX, vSAN e vSphere
* IBM Software Defined Environment Automation Tool Health Check (SAT HC) per la convalida delle distribuzioni con le procedure consigliate e le politiche di sicurezza
* Ripristino di emergenza (DR) facoltativo a un sito {{site.data.keyword.cloud_notm}} della regione
* Fortigate Security Appliance o simile per garantire un accesso a internet sicuro e per facilitare l'integrazione di rete attiva-attiva con la rete in loco

### Specifiche dell'architettura cluster estesa vSphere + vSAN

L'architettura cluster estesa vSphere + vSAN ha le seguenti specifiche:
* Il cluster fornisce le funzionalità di archiviazione e di calcolo che si estendono su due siti per fornire una maggiore disponibilità.
* Le richieste di scrittura da macchine virtuali (VM) sono scritte in modo sincrono su entrambi i siti incorrendo nella latenza della rete site-to-site.
* Le richieste di lettura dalle VM sono realizzate localmente nell'ubicazione fisica in cui è ubicata la VM, evitando ulteriore latenza.
* Il sito e l'host di controllo agiscono come split brain/quorum.
* La codifica nativa vSAN (per la crittografia inattiva) può essere utilizzata insieme a questa architettura.

### Specifiche dell'architettura di rete

L'architettura di rete ha le seguenti specifiche:
* Edge/DLR/VXLAN in combinazione con l'instradamento basato sulla metrica BGP per facilitare un progetto di sito attivo-attivo con il failover automatico.
* Ogni sito ha il concetto del proprio insieme Edge/DLR e VXLAN.
* In circostanze normali, qualsiasi VM connessa a DLR-A, ad esempio VM-A sarà nella zona di disponibilità {{site.data.keyword.cloud_notm}} #1 e il traffico sarà sia in entrata che in uscita localmente.
* Durante un'attività vMotion per VM-A, il traffico continuerà ad entrare ed uscire tramite la zona di disponibilità {{site.data.keyword.cloud_notm}} #1.
* Durante un malfunzionamento del sito o dell'edge, il traffico sarà instradato al sito disponibile rimanente.

### Link correlati

* [Richiesta di Mission Critical VMware on IBM Cloud](managing_mcv.html)
