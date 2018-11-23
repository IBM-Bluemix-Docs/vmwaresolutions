---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Contesto di sistema

Figura 1. Diagramma contesto di sistema
![Diagramma contesto di sistema - VCS ICP CAM](vcsicp-syscontext-vcs-icp-cam.svg)

I seguenti sono i componenti principali:

- **Virtualizzazione in loco** - Questo componente è un ambiente VMware ospitato in loco dal client o in un'ubicazione di terze parti e al momento ospita le VM che eseguono le applicazioni che devono essere modernizzate. È l'ambiente di origine per le migrazioni della VM ed è vagamente accoppiato a un'istanza di IBM Cloud tramite VMware Hybridity (HCX).
- **vCenter Server** - VMware vCenter Server on IBM Cloud (VCS) è un'istanza dei servizi IBM Cloud for VMware che è la destinazione delle VM migrate dall'ambiente in loco. Insieme all'ambiente virtualizzato in loco forma un ambiente ibrido che consente alle VM di spostarsi da un sito all'altro.
- **IBM Cloud Kubernetes Service** - IKS utilizza Kubernetes come soluzione di orchestrazione del contenitore. IBM agisce e gestisce il nodo master Kubernetes mentre i nodi di lavoro vengono distribuiti all'infrastruttura gestita dal cliente. IBM fornisce gli strumenti di gestione per la distribuzione della patch del sistema operativo, gli aggiornamenti del motore Docker e le nuove versioni di Kubernetes. IKS fornisce una piattaforma isolata e sicura per la gestione dei contenitori portatili, estensibili e riparabili automaticamente in caso di failover.
- **IBM Cloud Private** - ICP è una piattaforma dell'applicazione per lo sviluppo e la gestione delle applicazioni inserite nei contenitori. È un ambiente integrato che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione, i framework di monitoraggio e un'interfaccia utente grafica che fornisce un'ubicazione centralizzata da cui puoi distribuire, gestire, monitorare e ridimensionare le applicazioni.
- **IBM Cloud Automation Manager** - CAM è una piattaforma di infrastruttura pronta per le imprese come codice (IaC) che fornisce un unico pannello di controllo per eseguire il provisioning di carichi di lavoro basati su VMware insieme a quelli basati su Kubernetes. L'automazione del provisioning del carico di lavoro per le macchine virtuali, i contenitori e i relativi prerequisiti dell'infrastruttura viene abilitata tramite CAM.
- **IBM Multi Cloud Manager** – MCM fornisce la visibilità utente, la gestione incentrata sull'applicazione (politica, distribuzioni, integrità, operazioni) e conformità basata sulle politiche tra i cloud e i cluster. Con MCM, hai il controllo dei tuoi cluster Kubernetes.
- **IBM Cloud Services** - IBM Cloud Services è un'ampia gamma di servizi utilizzabili disponibili, comprese le offerte di analisi, AI e IoT.

## Actor

Tabella 1. Actor

Actor  | Descrizione
--|--
Amministratore di sistema | La risorsa qualificata VMware vSphere che utilizza vCenter Server per gestire la virtualizzazione in loco e l'istanza VCS.
Sviluppatore | La risorsa qualificata del contenitore che utilizza la console CAM per creare e gestire i contenitori. Creano i nuovi servizi come parte della modernizzazione dell'applicazione. Utilizzando CAM lo sviluppatore esegue il provisioning dei carichi di lavoro su VCS, ICP o IKS, crea e orchestra i servizi realizzati con le VM e i contenitori e integra le toolchain DevOps e le soluzioni day-2 ITSM.
Cliente | Attore esterno che consuma i servizi dall'azienda. Per Acme Skateboards, il cliente è uno skater che vuole acquistare i prodotti di skateboarding. Il cliente necessita di un accesso internet sicuro al catalogo.
IBM IKS | La risorsa IBM che gestisce il nodo master IKS per il servizio.

## Sistemi

Tabella 2. Sistemi

Actor | Descrizione
--|--
vCenter Server | Interfaccia primaria che l'amministratore di sistema utilizza per gestire le VM in loco e IBM Cloud nell'istanza VCS.
VM in loco| Server virtualizzati che ospitano le applicazioni destinate alla migrazione in cloud IBM. Migrate inizialmente come VM e riorganizzate da VM in contenitori per la modernizzazione dell'applicazione.
VM IBM Cloud | Server virtualizzati che ospitano le applicazioni migrate dal data center in loco. Nel caso di questa architettura di riferimento e per Acme Skateboards, una delle VM IBM Cloud è un server di database, che fa parte del carico di lavoro presente online.
Catalogo contenuto aziendale | Ubicazione centralizzata da cui puoi sfogliare e installare i pacchetti nel tuo cluster. Il catalogo contiene vari pacchetti IBM utilizzati per creare i contenitori e accedere ai grafici Helm. Helm è uno strumento per la gestione dei grafici Kubernetes. I grafici sono pacchetti di risorse Kubernetes preconfigurate che rendono facile il controllo della versione, l'impacchettamento, la release, la distribuzione, l'eliminazione, l'aggiornamento e anche il rollback delle distribuzioni del contenitore. Helm è il sistema di gestione del pacchetto nativo Kubernetes ed è utilizzato per la gestione dell'applicazione all'interno di un cluster ICP.
Servizi operativi principali | ICP include vari strumenti per raccogliere, archiviare ed eseguire la query dei log e delle metriche. Questi strumenti forniscono un archivio centralizzato per tutti i log e le metriche e offrono prestazioni migliorate e una maggiore stabilità quando si accede ed esegue la query dei log e delle metriche.
Console di gestione | La console di gestione ICP consente di gestire, monitorare e risolvere i problemi delle tue applicazioni e del tuo cluster da una sola console di gestione centralizzata e sicura.
Terraform |  Gestisce il provisioning delle risorse cloud e dell'infrastruttura utilizzando provider come VMware vSphere, IBM Cloud, Microsoft Azure, Amazon Web Services, Google Cloud Platform e OpenStack.
HELM | Gestore del pacchetto per Kubernetes. I grafici Helm vengono utilizzati per definire le risorse di Kubernetes e distribuire le applicazioni.
Chef | Responsabile per la gestione della configurazione e l'automazione della conformità. Chef distribuisce e configura il middleware e le applicazioni dopo che Terraform ha completato il provisioning iniziale.
Servizi |  Rappresenta il Service Composer, che è dove gli amministratori creano, compongono e progettano i servizi creati dalle risorse Kubernetes e da una o più VM.
Applicazioni inserite nel contenitore | Applicazioni che hanno completato il percorso di modernizzazione dell'applicazione e che ora sono in esecuzione come contenitori. Nel caso di questa architettura di riferimento e per Acme Skateboards, una delle applicazioni inserite nel contenitore è un server web, che fa parte del carico di lavoro presente online.
Watson |  Nel caso di questa architettura di riferimento e di Acme Skateboards, Watson rappresenta il servizio AI utilizzato nell'architettura “Concept Car”.

La rete, la sicurezza e la migrazione dell'applicazione sono spesso gli aspetti più impegnativi della modernizzazione dell'applicazione. VMware vCenter Server on IBM Cloud, VMware Hybridity, VMware NSX, IBM Cloud Private e il servizio IBM Cloud Kubernetes affrontano queste sfide e ti consentono di creare applicazioni moderne, robuste, sicure e resilienti.

### Link correlati

* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
