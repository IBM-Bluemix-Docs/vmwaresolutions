---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

# Panoramica sull'architettura

L'offerta IBM Cloud for VMware fornisce l'automazione per distribuire i componenti di tecnologia VMware nei data center di IBM Cloud in tutto il mondo.
L'architettura è costituita da una sola regione cloud e supporta la capacità di estendersi in ulteriori regioni cloud che si trovano in un'altra area geografia e/o in un altro pod di IBM Cloud all'interno dello stesso data center.

I prodotti IBM Cloud Private (ICP) e Cloud Automation Manager (CAM) possono essere distribuiti manualmente nella tua piattaforma di virtualizzazione in loco, abilitando la gestione cloud dalle ubicazioni in loco. In alternativa, ICP e CAM vengono offerti come estensioni del servizio a una distribuzione esistente o nuova di VMware vCenter Server on IBM Cloud (VCS), tramite l'automazione, abilitando la gestione cloud da IBM Cloud.

ICP è una piattaforma dell'applicazione per lo sviluppo e la gestione in loco delle applicazioni inserite nei contenitori. È un ambiente integrato per la gestione dei contenitori che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione e i framework di monitoraggio.

IBM Multi-Cluster Manager (MCM) fornisce la visibilità utente, la gestione incentrata sull'applicazione (politica, distribuzioni, integrità, operazioni) e conformità basata sulle politiche tra i cloud e i cluster. Con MCM, hai il controllo dei tuoi cluster Kubernetes. Puoi assicurarti che i tuoi cluster siano sicuri, funzionanti in modo efficiente, e la distribuzione della piattaforma di gestione dei servizi in esecuzione su ICP che consente agli sviluppatori e agli amministratori di soddisfare le richieste di business.
Cloud Automation Manager Service Composer ti consente di esporre i servizi cloud ibridi nel catalogo ICP.

## Piattaforma di gestione cloud lato IBM Cloud

Figura 1. Gestione cloud dal lato cloud

![Sul cloud - gestione cloud](vcsicp-oncloud-cloudmgt.svg)

Il precedente diagramma rappresenta ICP e CAM distribuiti con l'infrastruttura IBM Cloud, con connessioni al servizio vCenter in loco e al servizio IBM Kubernetes Service (IKS) distribuiti su IBM Cloud. Gli utenti sono in grado di distribuire le macchine virtuali in loco e in un'istanza VCS e i contenitori al cluster ICP e IKS.

Nel diagramma, CAM crea in modo logico le connessioni cloud ai vCenter, ai provider cloud, a ICP e agli ambienti IKS. I cluster ICP dovrebbero essere distribuiti ad ogni ambiente data center/cloud, con MCM che fornisce il meccanismo per collegare i cluster ICP in una sola vista di gestione.

ICP può essere distribuito con i componenti NSX-V o NSX-T. ICP con NSX-V, consente alle macchine virtuali ICP l'esecuzione sulla rete VXLAN e utilizza la rete interna Kubernetes Calico.

ICP con NSX-T, consente agli utenti di controllare e configurare la rete, la sottorete, le politiche dall'IU centrale (NSX-T Manager). Consulta la [Guida di rete di vCenter Server](../vcsnsxt/vcsnsxt-intro.html) per le differenze tra NSX-V e NSX-T.

## Piattaforma di gestione cloud in loco

Figura 2. Gestione cloud dal lato locale
![Gestione cloud in loco](vcsicp-onprem-cloudmgt.svg)

Il precedente diagramma rappresenta ICP e CAM distribuiti nell'infrastruttura in loco, con connessioni a vCenter e IKS distribuiti su IBM Cloud. Gli utenti sono in grado di distribuire le macchine virtuali e i contenitori in loco, le macchine virtuali nell'istanza vCenter Server e i contenitori al cluster IKS.

La VPN strongSwan viene utilizzata per stabilire la connettività con i contenitori IKS distribuiti, eventualmente potrebbe essere sostituita con connettività Direct link.

Nel diagramma, CAM crea in modo logico le connessioni cloud ai vCenter, ai provider cloud, a ICP e agli ambienti IKS. I cluster ICP dovrebbero essere distribuiti ad ogni ambiente data center/cloud, con MCM che fornisce il meccanismo per collegare i cluster ICP in una sola vista di gestione.

### Link correlati

* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
