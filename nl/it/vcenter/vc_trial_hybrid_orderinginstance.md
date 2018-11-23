---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine ed eliminazione della versione di prova a singolo nodo di VMware vCenter Server sulle istanze di IBM Cloud

La versione di prova a singolo nodo di VMware vCenter Server su {{site.data.keyword.cloud}} è un cloud privato ospitato a singolo tenant che fornisce lo stack VMware vSphere come servizio. Mentre l'ambiente gestito dal client viene normalmente distribuito con un minimo di tre nodi, questa versione di prova a singolo nodo fornisce un percorso a basso costo per sperimentare i vantaggi di un'implementazione cloud ibrida.

Questa versione di prova è ideale per una prova di utilizzo che illustra la velocità dell'automazione avanzata di IBM per la distribuzione iniziale e la facilità di spostamento di carichi di lavoro semplici non di produzione nel cloud. Utilizzando VMware Hybrid Cloud Extension (HCX), puoi estendere in modo sicuro la tua rete di data center in loco nel {{site.data.keyword.CloudDataCent_notm}} riducendo la complessità di rete della configurazione dell'interconnessione. HCX estrae le risorse di rete sottostanti per il tunnel tramite internet pubblicamente in modo da poter spostare facilmente i carichi di lavoro bidirezionalmente senza dover reinserire l'IP delle macchine virtuali (VM). Con HCX, non c'è bisogno che VMware NSX sia installato in locale ed è compatibile con le versioni più vecchie di vSphere.  

La versione di prova a singolo nodo è solo per una prova di utilizzo. Non eseguire i carichi di lavoro di produzione su questo ambiente. Le funzioni di gestione come l'aggiunta o la rimozione degli host e dei cluster, l'ordine di ulteriori servizi di componenti aggiuntivi e l'applicazione degli aggiornamenti non sono supportate.
{:important}

Questa versione di prova è destinata ad essere utilizzata per un massimo di 90 giorni. Quando hai terminato con la versione di prova, puoi eliminare questo ambiente e quindi eseguire il provisioning di un ambiente ad alta disponibilità che soddisfi le tue esigenze di capacità. Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html).

## Specifiche tecniche per la versione di prova a singolo nodo per le istanze di vCenter Server

I seguenti componenti sono inclusi nella tua versione di prova a singolo nodo dell'istanza di vCenter Server:

La disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.
{:note}

### Bare Metal Server

Un processore Dual Intel Xeon Gold 5120 (28 core, 2.20 GHz) con 384 GB RAM.

### Rete

Vengono ordinati i seguenti componenti di rete:
*  Doppi uplink di rete privata e pubblica da 10 Gbps
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando ulteriori VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle VM di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG gestito dal cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Non puoi accedere a questo ESG e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire la versione di prova a singolo nodo dell'istanza vCenter Server dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, tieni presente che l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni causerà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
    {:important}
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata, distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico. Per ulteriori informazioni, vedi [L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

Per ulteriori informazioni sui componenti di rete ordinati quando si distribuisce il servizio HCX on {{site.data.keyword.cloud_notm}}, vedi [Panoramica di HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### VSI (Virtual Server Instance)

Vengono ordinate le seguenti VSI (Virtual Server Instance):

* Una VSI per IBM CloudBuilder, che viene arrestata al termine della distribuzione dell'istanza.
* Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) che può essere consultata. La VSI funziona come DNS per l'istanza in cui sono registrati gli host e le VM.

### Licenze fornite da IBM e tariffe

Le seguenti licenze sono incluse nella tua versione di prova a singolo nodo dell'ordine dell'istanza di vCenter Server:

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

La versione di prova a singolo nodo delle istanze di vCenter Server non supporta BYOL (Bring Your Own License).
{:note}

Possono essere applicate ulteriori tariffe per supporto e servizi.

## Specifiche tecniche per VMware HCX on IBM Cloud

versione di prova a singolo nodo per vCenter Server include HCX on {{site.data.keyword.cloud_notm}}. Per informazioni sulle specifiche tecniche e sulle considerazioni per HCX su {{site.data.keyword.cloud_notm}}, consulta [Panoramica di VMware HCX on IBM Cloud](../services/hcx_considerations.html).

## Requisiti e pianificazione per ordinare la versione di prova a singolo nodo delle istanze di vCenter Server

Assicurati di confermare i seguenti requisiti e di completare le seguenti attività:
* Prerequisiti per le istanze HCX in loco:
 * Richiede VMware vSphere e vCenter 5.5 o superiore.
 * L'ambiente vSphere deve disporre di switch distribuiti per il VMx che saranno migrati a {{site.data.keyword.cloud_notm}}.
 * Il dispositivo virtuale HCX Manager deve poter essere distribuito su una rete privata nell'ambiente in loco e deve essere autorizzato ad accedere a internet pubblico.
* L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti per l'account {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).
*  Configura le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](../vmonic/useraccount.html).
* Controlla i requisiti del nome dell'istanza:  
 * Sono consentiti solo caratteri alfanumerici e trattini (-).
 * Il nome dell'istanza deve iniziare e terminare con un carattere alfanumerico.
 * La lunghezza massima del nome dell'istanza è di 10 caratteri.
 * Il nome dell'istanza deve essere univoco all'interno del tuo account.
* Controlla che il {{site.data.keyword.CloudDataCents_notm}} soddisfi i requisiti per l'infrastruttura fisica. Per ulteriori informazioni, consulta la sezione *Disponibilità di {{site.data.keyword.CloudDataCent_notm}}* in [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability).

## Procedura per ordinare la versione di prova a singolo nodo delle istanze di vCenter Server

1. Nella pagina **Single-node Trial for VMware vCenter Server on  {{site.data.keyword.cloud_notm}}**, fai clic sulla scheda **vCenter Server** e quindi su **Continue**.
2. Nella pagina **Single-node Trial for VMware vCenter Server**, completa le istruzioni per richiedere un account dell'infrastruttura {{site.data.keyword.cloud_notm}} o fornisci i tuoi **Nome utente** e **Chiave API** esistenti e fai clic su **Retrieve**.

 Questa sezione è nascosta se la chiave API già esiste.
 {:note}
3. Immetti il nome dell'istanza.
4. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.  

 Il {{site.data.keyword.CloudDataCent_notm}} è pre-selezionato. Seleziona un'ubicazione {{site.data.keyword.CloudDataCent_notm}} diversa, se necessario.
 {:note}
5. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
   1. Esamina le impostazioni per l'istanza.
   2. Esamina il costo stimato dell'istanza. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di ordinare l'istanza.
   4. Fai clic su **Fornitura**.

### Risultati

La distribuzione dell'istanza inizia automaticamente e viene ordinata la chiave di attivazione del servizio HCX on {{site.data.keyword.cloud_notm}}.

#### Processo di distribuzione per HCX on IBM Cloud

La distribuzione di HCX on {{site.data.keyword.cloud_notm}} è automatizzata. Le seguenti istruzioni vengono completate dal processo automatico di {{site.data.keyword.vmwaresolutions_short}}:
1. Dall'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate tre sottoreti per HCX:
   * Due sottoreti portatili private per la gestione HCX.
   * Una sottorete portatile pubblica per l'attivazione e la manutenzione con VMware. Questa sottorete viene utilizzata anche per le interconnessioni HCX.

   Gli indirizzi IP nelle sottoreti ordinate per HCX devono essere gestiti dall'automazione di VMware on {{site.data.keyword.cloud_notm}}. Questi indirizzi IP non possono essere assegnati alle risorse VMware, come VM ed Edge NSX, create da te. Se hai bisogno di ulteriori indirizzi IP per le tue risorse VMware, devi ordinare le tue proprie sottoreti da {{site.data.keyword.cloud_notm}}.
   {:important}
3. Vengono creati tre pool di risorse e cartelle VM per HCX, necessari per interconnessioni HCX, componenti HCX locali e componenti HCX remoti.
4. Viene distribuita e configurata una coppia di gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HCX:
   * Le interfacce di uplink pubblico e privato vengono configurate utilizzando le sottoreti ordinate.
   * Gli ESG vengono configurati come una coppia di dispositivi edge di grandi dimensioni con l'alta disponibilità (HA) abilitata.
   * Le regole del firewall e le regole NAT (Network Address Translation) vengono configurate per consentire il traffico HTTPS in entrata e in uscita da e verso HCX Manager.
   * Vengono configurate le regole di bilanciamento del carico e i pool di risorse. Le regole e i pool di risorse sono utilizzati per inoltrare il traffico in entrata correlato a HCX ai dispositivi virtuali appropriati di HCX Manager, vCenter Server e PSC (Platform Services Controller).
   * Viene applicato un certificato SSL per crittografare il traffico HTTPS in entrata correlato a HCX che arriva tramite gli ESG.

   L'edge di gestione HCX è dedicato al traffico di gestione HCX tra i componenti HCX in loco e i componenti HCX lato cloud. Non modificare l'edge di gestione HCX o utilizzarlo per le estensioni di rete HCX. Crea, invece, edge separati per le estensioni di rete. Inoltre, l'utilizzo di un firewall o la disabilitazione delle comunicazioni dell'edge di gestione HCX ai componenti di gestione IBM privati o all'Internet pubblico potrebbe influire negativamente sulla funzionalità di HCX.
   {:important}

5. HCX Manager on {{site.data.keyword.cloud_notm}} viene distribuito, attivato, e configurato:
   * HCX Manager viene registrato con vCenter Server.
   * Vengono configurati HCX Manager, vCenter Server, PSC e NSX Manager.
   * Viene configurata la flotta HCX.
   * Vengono configurati i contenitori di distribuzione HCX locali e remoti.
6. Il nome host e l'indirizzo IP di HCX Manager vengono registrati con il server DNS di VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualizzazione dei dettagli dell'istanza

Puoi controllare lo stato della distribuzione visualizzando i dettagli dell'istanza. Per informazioni sulla visualizzazione dei dettagli dell'istanza, vedi:

* [Visualizzazione delle istanze vCenter Server](vc_viewinginstances.html)
* [Visualizzazione delle istanze VMware HCX on IBM Cloud in loco](../services/standalone_viewingserviceinstances.html)

Una volta che l'istanza è stata distribuita correttamente, i componenti descritti nelle sezioni *Specifiche tecniche* di questo argomento sono installati sulla tua piattaforma virtuale VMware e sull'HCX in loco sulla chiave di attivazione del servizio {{site.data.keyword.cloud_notm}} disponibile nell'HCX in loco nella pagina dei dettagli di {{site.data.keyword.cloud_notm}}.

Lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e ricevi una notifica per email.

### Operazioni successive

Installa HCX Enterprise Manager in loco e configura la connessione alla tua istanza HCX on {{site.data.keyword.cloud_notm}}.

1. Individua la chiave di attivazione in loco nella pagina **Istanze distribuite**.
  1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** dal riquadro di navigazione a sinistra.
  2. Nella tabella **Istanze di vCenter Server**, controlla la colonna **Tipo** per individuare l'istanza della versione di prova a singolo nodo e prendi nota del nome dell'istanza.
  3. Scorri fino alla tabella **Istanze HCX in loco** e controlla la colonna **Nome** per individuare l'istanza che ha lo stesso nome dell'istanza a singolo nodo. Al nome dell'istanza viene accodato *-OnPrem*.
  4. Prendi nota della chiave nel campo **Chiave di attivazione**.
2. Ottieni il HCX Enterprise Manager Open Virtual Appliance (OVA) dalla console HCX on {{site.data.keyword.cloud_notm}} HCX Manager.
  1. Collegati alla console HCX Cloud.
    1. Nella tabella **Istanze vCenter Server**, fai clic sulla versione di prova a singolo nodo dell'istanza per visualizzarne i dettagli.
    2. In **Informazioni di accesso**, individua e prendi nota delle credenziali vCenter.
    3. Fai clic su **Servizi** dal riquadro di navigazione a sinistra.
    4. Nella pagina **Servizi**, fai clic su **Servizi installati**.
    5. Nella pagina dei dettagli **HCX on IBM Cloud**, individua e prendi nota dell'**HCX Cloud IP**.
    6. Assicurati di essere collegato alla VPN per accedere alla tua rete privata {{site.data.keyword.cloud_notm}}.
    7. Fai clic su **Visualizza console cloud HCX**.
  2. Nella **Console cloud HCX**, completa la seguente procedura:
      1. Fai clic sulla scheda **Amministrazione**.
      2. Nella scheda **Aggiornamenti di sistema**, fai clic su **RICHIEDI LINK DI DOWNLOAD**.
      3. Fai clic su **COPIA LINK** e utilizza quindi questo link per scaricare HCX Enterprise Client in un ambiente in loco con accesso al tuo ambiente vSphere in loco.
3. Nel client web VMware vSphere, distribuisci HCX Enterprise Client come dispositivo virtuale HCX Manager nel tuo ambiente in loco. Per ulteriori informazioni, consulta [Installazione di HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    Devi distribuire l'HCX Manager in loco su una rete privata e consentirgli l'accesso alla rete pubblica. Puoi utilizzare un gateway Edge NSX, Vyatta o simile per consentire l'accesso Internet all'HCX Manager in loco. Se i gateway utilizzati per l'accesso alla rete privata e l'accesso alla rete pubblica sono diversi, si consiglia di utilizzare il gateway predefinito per consentire l'accesso alla rete pubblica e la **Console di gestione HCX Manager** per creare una rotta statica per l'accesso alla rete privata.  
    {:note}
4. Utilizza la chiave di attivazione in loco annotata nel passo 1 per attivare la tua VM HCX Enterprise Manager.
  1. Accedi alla tua VM HCX Enterprise Manager in loco utilizzando le credenziali specificate durante la distribuzione dell'OVA.
  2. Immetti la chiave di attivazione quando richiesto.

  Per ulteriori informazioni, vedi [HCX Activation and Initial Configuration](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. Un certificato SSL autofirmato è stato generato dal servizio HCX on {{site.data.keyword.cloud_notm}}. Devi importare il certificato nell'HCX Manager in loco completando le seguenti istruzioni:
    1. Nella **Console di gestione HCX Manager** in loco, fai clic sulla scheda **Amministrazione**.
    2. Dal riquadro di navigazione a sinistra, fai clic su **Certificato CA attendibile** e quindi su **IMPORTA** sulla destra.
    3. Fai clic su **URL** e immetti l'URL del certificato che vuoi applicare, ossia l'**IP cloud HCX** (``https://<cloud-side public IP>``), che puoi trovare nella pagina dei dettagli del servizio HCX on {{site.data.keyword.cloud_notm}} nella console {{site.data.keyword.vmwaresolutions_short}}.
    4. Fai clic su **APPLICA**.
6. Continua la configurazione iniziale e crea l'interconnessione. Per ulteriori informazioni, vedi [Installing and Configuring VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Estendi le reti in VMware HCX dal locale a {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, consulta [Extending Networks with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migra le VM tra i locale e {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, consulta [Migrating Virtual Machines with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

Devi gestire i componenti dell'infrastruttura {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console.
Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console e il tuo ambiente potrebbe diventare instabile.
{:important}

## Procedura per eliminare la versione di prova a singolo nodo delle istanze di vCenter Server

Per rilasciare i componenti che hai ordinato in una versione di prova a singolo nodo dell'istanza vCenter Server, elimina l'istanza.

Per ulteriori informazioni, vedi [Eliminazione delle istanze vCenter Server](vc_deletinginstance.html).

### Link correlati

* [Registrazione di un account {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Glossario dei termini HCX](../services/hcx_glossary.html)
* [Documentazione di VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Obtaining the HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
* [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
