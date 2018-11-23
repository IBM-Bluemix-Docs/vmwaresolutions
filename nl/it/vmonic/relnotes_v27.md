---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# Note sulla release per la V2.7

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Supporto server 6140 certificato SAP

A partire dalla release V2.7, i seguenti nuovi modelli CPU {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} sono disponibili per la distribuzione delle istanze e dei cluster di di VMware vCenter Server on {{site.data.keyword.cloud_notm}} e di VMware vSphere on {{site.data.keyword.cloud_notm}}:
* Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 192 GB RAM
* Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.2 GHz / 384 GB RAM
* Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 768 GB RAM

Per ulteriori informazioni, vedi la sezione *Impostazioni di {{site.data.keyword.baremetal_short_sing}}* in:
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [Ordine di nuovi cluster vSphere](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Aggiornamenti per i servizi aggiuntivi

### IBM Cloud Private Hosted

Il servizio {{site.data.keyword.cloud_notm}} Private Hosted è ora disponibile per le istanze VMware vCenter Server with Hybridity Bundle, oltre che per le istanze VMware vCenter Server distribuite nella (o aggiornate alla) V2.5 e nelle release successivi. Puoi ora ordinare un'istanza vCenter Server o un'istanza vCenter Server with Hybridity Bundle con il servizio incluso. Puoi inoltre aggiungere il servizio a un'istanza vCenter Server o vCenter Server with Hybridity Bundle esistente dopo la distribuzione iniziale.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [{{site.data.keyword.cloud_notm}}Panoramica su Private Hosted](../services/icp_overview.html)
* [Ordine di {{site.data.keyword.cloud_notm}} Private Hosted](../services/icp_ordering.html)

### Mission Critical VMware on IBM Cloud

Il servizio Mission Critical VMware on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze che sono distribuite o aggiornate alla V2.7 o alle release successive.

Mission Critical VMware on {{site.data.keyword.cloud_notm}} offre un'architettura a più zone per aiutare le aziende ad evitare il tempo di inattività delle applicazioni cloud e ad automatizzare i failover in una regione cloud. Con questa architettura cloud, puoi raggiungere una maggiore disponibilità e una percentuale di successo di failover rispetto a quella che la maggior parte dei client VMware possono raggiungere con gli ambienti in loco o con le piattaforme cloud concorrenti.

Per ulteriori informazioni, vedi [Panoramica di Mission Critical VMware on {{site.data.keyword.cloud_notm}}](../services/mcv_overview.html).

### F5 on IBM Cloud

Ora quando ordini il servizio F5 on {{site.data.keyword.cloud_notm}}, puoi selezionare se desideri che F5 applichi la licenza sulla rete pubblica o sulla rete privata con un server proxy. Per ulteriori informazioni, vedi [Ordine di F5 on {{site.data.keyword.cloud_notm}}](../services/f5_ordering.html).

### FortiGate Virtual Appliance on IBM Cloud

Nel terzo quadrimestre del 2018, Fortinet ha modificato i propri pacchetti di sottoscrizione. Per ulteriori informazioni, vedi [Ordine di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_ordering.html).

Per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} distribuito nelle istanze Cloud Foundation e vCenter Server della V2.1 e successive, viene fornito FortiOS 6.0.3.

Quando ordini FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, puoi selezionare se desideri che FortiGuard applichi la licenza e gli aggiornamenti di sicurezza sulla rete pubblica o sulla rete privata con un server proxy. Per ulteriori informazioni, vedi [Ordine di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_ordering.html).

### Aggiornamenti dei componenti del servizio Zerto on IBM Cloud

Per il servizio Zerto on {{site.data.keyword.cloud_notm}} distribuito nelle istanze Cloud Foundation e vCenter Server della V2.1 e successive, viene fornito Zerto Virtual Replication 6.0 aggiornamento 3. Per ulteriori informazioni, vedi [Panoramica di Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html).

### Integrazione di KMIP for VMware on IBM Cloud con il programma di traccia dell'attività IBM Cloud

In aggiunta agli eventi dell'istanza VMware, gli eventi di KMIP for VMware on {{site.data.keyword.cloud_notm}}, come la creazione, l'eliminazione e l'accesso alla chiave, sono ora integrati con la tua istanza del programma di traccia dell'attività {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni su KMIP for WMware on {{site.data.keyword.cloud_notm}}, vedi [Panoramica di KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html).

## Documentazione nuova e aggiornata

### Documentazione dell'architettura di riferimento

La seguente documentazione tecnica è ora disponibile nella sezione *Riferimento* della documentazione dell'utente:

* [Architettura della soluzione NSX Edge Services Gateway](../archiref/nsx/nsx_overview.html)
* [Guida di VMware Update Manager](../archiref/vum/vum-intro.html)
* [Guida di rete di vCenter Server](../archiref/vcsnsxt/vcsnsxt-intro.html)
* [Guida di vCenter Server e {{site.data.keyword.cloud_notm}} Private](../archiref/vcsicp/vcsicp-intro.html)
* [Guida del servizio vCenter Server e IBM Kubernetes](../archiref/vcsiks/vcsiks-intro.html)
* [Guida di VMware e Skate Advisor Concept Car](../archiref/vcscar/vcscar-intro.html)
* [VMware - Percorso di modernizzazione di Stock Trader](../archiref/vcscontent/vcscontent-modjourney.html)

I documenti dell'architettura di riferimento sono disponibili solo in inglese.

## Aggiornamenti e miglioramenti dell'interfaccia utente

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* La scheda **Personalizzato** in cui si specifica il modello CPU e la RAM per le impostazioni di {{site.data.keyword.baremetal_short_sing}} quando ordini le istanze è ora suddivisa nelle schede **Skylake** e **Broadwell** in base al tipo di server per facilitarti nella selezione del server.
* Le opzioni **Preconfigurate**della configurazione di Bare Metal Server non sono più disponibili.
* La colonna **Tipo** è ora inclusa nella tabella **Istanze vCenter Server** nella pagina **Istanze distribuite** per identificare le istanze vCenter Server, vCenter Server with Hybridity Bundle e vCenter Limited Test Drive.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.
