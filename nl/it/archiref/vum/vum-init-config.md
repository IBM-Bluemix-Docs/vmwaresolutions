---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# Configurazione iniziale

L'automazione di IC4VS configura il VCSA con un gateway predefinito impostato sul BCR (Backend Customer Router) di {{site.data.keyword.cloud}}. Tuttavia, non esiste una rotta a internet tramite il BCR. La rotta standard verso internet dall'istanza VMware vCenter Server on {{site.data.keyword.cloud_notm}} avviene tramite l'ESG di gestione. Poiché non è consigliabile modificare la configurazione di VCSA o dell'ESG di gestione, è più opportuno implementare un server proxy sulla sottorete del cliente per abilitare VUM.

Questo approccio indica che il VCSA o l'ESG di gestione non devono essere riconfigurati, tuttavia è necessario installare una piccola macchina virtuale (VM) o un piccolo dispositivo. Un server proxy è un sistema che si trova tra due dispositivi endpoint e funge da dispositivo intermedio. In questo caso, si trova tra VUM e i server di aggiornamento presso VMware.

Quando VUM richiede una risorsa dal server di aggiornamento su VMware, la richiesta viene prima inviata al server proxy e il server proxy invia quindi la richiesta al server di aggiornamento. Una volta che il server proxy ottiene la risorsa, la invia a VUM. Un server proxy può essere utilizzato per facilitare la sicurezza, i controlli di amministrazione e servizi di cache.

Questo documento descrive l'utilizzo di un server proxy basato su CentOS e Squid. Squid Proxy è un proxy di cache open source per il web e supporta molti protocolli, tra cui HTTP e HTTPS. Sono disponibili numerosi proxy basati su dispositivi e VM, pertanto devi selezionare quello appropriato in base ai requisiti della tua azienda e installarlo e configurarlo seguendo le indicazioni del fornitore. I clienti che scelgono di utilizzare un'implementazione CentOS/Squid possono continuare con il processo descritto qui di seguito.

* Scarica l'ISO CentOS su un server jump
* Crea una libreria vCenter
* Carica l'ISO nella libreria vCenter
* Crea una VM, installa e configura CentOS e installa Squid

Prima di poter iniziare questa attività, devi raccogliere le informazioni per popolare la Tabella 1. Esamina i valori suggeriti e assicurati che siano appropriati per la tua azienda. Questa configurazione è basata su un piccolo proxy per VUM che utilizza solo CentOS-Minimal e Squid.

Tabella 1. Valori di distribuzione

| Parametro | Valori suggeriti | Note |
|:--------- |:-------------- |:------ |
| CPU proxy | 1 vCPU | Squid non ha requisiti minimi |
| RAM proxy | 2 GB | Squid non ha requisiti minimi |
| Disco proxy | 25 | GB	Squid non ha requisiti minimi |
| Nome host | Proxy01 | |
| Indirizzo | proxy ip | Deve essere utilizzato un indirizzo IP di riserva dalla sottorete portatile privata del cliente assegnata durante il processo di provisioning. Solo due indirizzi IP vengono riservati su questa sottorete; uno per il BCR e l'altro per il customer-esg
| Maschera di rete | 255.255.255.192 | |
| Gateway| ip uplink privato customer-nsx-edge | Questa è l'impostazione predefinita del gateway per il server proxy, che è l'indirizzo di uplink privato di customer-nsx-edge. L'indirizzo IP può essere trovato riesaminando la scheda **Settings** per **customer-nsx-edge**. |
| Server DNS | ip AD/DNS | Questo indirizzo IP può essere trovato nella pagina dell'istanza nella console di {{site.data.keyword.vmwaresolutions_short}}, la pagina **Deployed Instances**. |
| IP BCR | ip bcr | Questo è l'indirizzo IP del BCR (Backend Customer Router) di {{site.data.keyword.cloud_notm}} ed è il gateway per 10.0.0.0/8 e 161.26.0.0/16. Questo indirizzo viene utilizzato in una rotta statica nel server proxy in modo che possa raggiungere il VCSA e il server AD/DNS. |

## Configurazione di NSX

Le impostazioni NAT e firewall dell'ESG del cliente NSX sono necessarie per abilitare il traffico del server proxy.

### Firewall

1. Passa a **Home** > **Networking & Security**.
2. Seleziona **NSX Edges**, customer-nsx-edge e quindi **Firewall**.
3. Fai clic sul simbolo **+** e aggiungi una regola del firewall.
4. Fornisci i parametri obbligatori come indicato nella seguente tabella. La nuova regola del firewall deve precedere l'ultima regola, la regola di negazione predefinita.

Tabella 2. Regola del firewall

| Parametro | Valori suggeriti |
|:--------- |:-------------- |
| Nome | Proxy01 in uscita |
| Tipo | Utente |
| Origine | ip server proxy |
| Destinazione | qualsiasi |
| Servizio | HTTP/HTTPS/ICMP Echo |
| Azione | Accetta |

Dopo aver fornito i parametri, fai clic su **Publish Changes**.

### Installazione e configurazione di un server proxy

Il seguente processo distribuisce una VM per ospitare CentOS e Squid dalla libreria di contenuti e comprende i seguenti passi. Si presuppone che tu disponga di una VSI di Windows da utilizzare come jumpbox e che utilizzi un Remote Desktop Protocol per connetterti all'interfaccia pubblica della VSI:

* Scarica il file ISO CentOS-Minimal
* Configura una libreria di contenuti vCenter e inserisci il file ISO CentOS al suo interno
* Configura la VM proxy, installa CentOS e Squid

### Download del file ISO CentOS-Minimal

Utilizzando un browser sul tuo server jump, scarica il file ISO CentOS-Minimal da [CentOS](https://www.centos.org/download/). Nota che {{site.data.keyword.cloud_notm}} mantiene un mirror di diverse distribuzioni Linux diffuse. Questo mirror è disponibile solo sulla rete privata e gli ISO CentOS sono disponibili al seguente indirizzo: `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Configurazione di una libreria di contenuti e inserimento del file ISO CentOS

Crea una libreria di contenuti vCenter locale. La libreria è accessibile solo nell'istanza vCenter Server in cui viene creata. Popola la libreria con i template e gli ISO richiesti per distribuire le VM.

1. Tramite il client web vSphere, passa a **Home** > **Content library** > **Objects** > **Create a new content library** > **Create subscribed library on the vCenter**.
2. Immetti un nome per la libreria di contenuti, ad esempio ISO, e nella casella di testo Notes immetti una descrizione per la libreria, quindi fai clic su **Next**.
3. Seleziona **Local content library** e fai clic su **Next**.
4. Seleziona un archivio dati e fai quindi clic su un archivio dati appropriato, ad esempio vsanDatastore.
5. Esamina le informazioni nella pagina Ready to Complete e fai clic su **Finish**.

### Configurazione della VM proxy, installazione di CentOS e Squid

Questa attività include le seguenti operazioni:

*	Crea una nuova VM
*	Installa CentOS
*	Installa Squid

#### Crea una nuova VM

Questa attività crea una nuova VM pronta per l'uso come server proxy. Per popolare la configurazione, utilizza le impostazioni indicate nella Tabella 1. Valori di distribuzione.

1.	Tramite il client web vSphere, passa a **Home** > **VMs and Templates**.
2.	Nel riquadro di navigazione, fai clic su **datacenter1**, quindi fai clic con il tasto destro del mouse e seleziona **New Virtual Machine** > **New Virtual Machine**.
3.	Seleziona **Create a new Virtual Machine** e fai clic su **Next**.
4.	Immetti un nome per la VM, ad esempio Proxy01, quindi seleziona **datacenter1** e fai clic su **Next**.
5.	Seleziona **cluster1** e fai clic su **Next**.
6.	Seleziona un archivio dati appropriato, ad esempio vsanDatastore, fai clic su **Next** e di nuovo su **Next**.
7.	In **Guest OS Family**, seleziona **Linux** e in **Guest OS version** seleziona **CentOS 7 (64-bit)** e fai clic su **Next**.
8.	Imposta **CPU su 1**, **Memory su 2048 MB** e **New Hard disk su 25 GB**. Seleziona **Content Library ISO File** e poi **CentOS-7-x86_64-Minimal**, fai clic su **OK** e seleziona la casella **Connected**.
9.	Nella casella New device, seleziona **Network** e fai clic su **Add**.
10.	Seleziona la rete **SDDC-DPortGroup-Mgmt**, assicurati che la casella di spunta Connect sia seleziona, quindi fai clic su **Next**.
11.	Esamina le informazioni e fai clic su **Finish**.

#### Installa CentOS

Questa attività installa e configura la VM appena creata pronta per l'installazione di Squid

1.	Nel riquadro di navigazione del client web vSphere, seleziona la **VM** appena creata, Proxy01 e seleziona la **scheda Summary**.
2.	Premi il pulsante **"Play"** per accendere la VM.
3.	La VM verrà ora accesa e avviata dall'ISO CentOS 7. Avvia una **console remota o una console web** nella VM. Tieni presente che è necessario installare la console remota e che il sistema che esegue il browser web deve risolvere gli host vSphere ESXi in base al nome.
4.	Nella schermata iniziale di CentOS 7, seleziona la lingua desiderata e fai clic su **Continue**.
5.	Nella schermata **LOCALIZATION**, fai clic su **DATE & TIME**, seleziona il tuo fuso orario e fai clic su **Done**.
6.	Nella schermata **LOCALIZATION**, fai clic su **KEYBOARD** per modificare l'impostazione predefinita laddove necessario e quindi premi **Done**.
7.	Nella schermata **LOCALIZATION**, fai clic su **INSTALLATION DESTINATION**, fai clic sull'**icona del disco virtuale VMware** e quindi su **Done**.
8.	Nella schermata **LOCALIZATION**, fai clic su **NETWORK & HOSTNAME**, modifica il nome host con quello da te scelto, ad esempio Proxy01.
9.	Fai clic sul pulsante **Configure**, quindi su **IPv4 Settings** e, nella casella **Method**, seleziona **Manual**.
10.	Utilizzando il pulsante **Add**, inserisci la _Maschera di rete dell'indirizzo_ e il _Gateway_ dalla _Tabella 1 – Valori di distribuzione_.
11.	Immetti l'_Indirizzo IP del server DNS_ dalla Tabella 1 – Valori di distribuzione.
12.	Fai clic sul pulsante **Routes** e aggiungi le seguenti rotte statiche: _10.0.0.0/8 e 161.26.0.0/16_ con l'indirizzo IP del gateway di _Indirizzo IP BCR_ indicato dalla Tabella 1. Valori di distribuzione, come gateway. Questa rotta statica consente al server proxy di raggiungere il server DNS.
13.	Fai clic su **Save** e assicurati che l'interfaccia Ethernet sia accesa e mostrata come connessa. Fai clic su **Done** e su **Begin Installation**.
14.	Mentre l'installazione continua, imposta una password root e configura un utente.
15.	Al termine dell'installazione, accedi come utente e immetti il comando _ping vmware.com_. Il nome dovrebbe essere risolto in un indirizzo IP e dovresti ottenere una risposta. Se non ottieni risposte, verifica gli indirizzi IP, le regole del firewall e le impostazioni NAT.

#### Installa e configura Squid

Squid non ha requisiti hardware minimi, ma la quantità di RAM può variare a seconda degli utenti che accedono a internet tramite il tuo proxy e degli oggetti che sono memorizzati nella cache. Poiché al server proxy accede solo VUM e la cache non è abilitata, è stata configurata solo una piccola VM.

1. Utilizzando la console web o la console remota dal client web vSphere Web, accedi al server proxy ed esegui `su` nella root.
2. Prima di installare i pacchetti, si consiglia di aggiornare il sistema e i pacchetti utilizzando il seguente comando:
  `yum -y update`

3. Per installare Squid, devi installare il repository EPEL sul sistema poiché Squid non è disponibile nel repository yum predefinito. Per installare il repository EPEL, immetti il seguente comando:
  `yum -y install epel-release`

4. Esegui l'aggiornamento e l'eliminazione utilizzando i seguenti comandi:

  `yum -y update`
  `yum clean all`

5. Squid viene installato utilizzando il seguente comando: `yum -y install squid`.
6. Una volta installato, avvia Squid immediatamente utilizzando il seguente comando: `systemctl start squid`.
7. Per avviare automaticamente Squid durante la fase di avvio, immetti il seguente comando: `systemctl enable squid`.
8. Assicurati che Squid sia in esecuzione immettendo il seguente comando: `systemctl status squid`.
9. Il firewall CentOS deve consentire l'accesso alla porta Squid, TCP 3128, utilizzando il seguente comando:  `firewall-cmd –add-port=3128/tcp –permanent`.
10.	Per salvare la regola e riavviare il servizio, utilizza il seguente comando: `firewall-cmd –reload`.

## Configurazione iniziale di VUM

Configura VUM per utilizzare il server proxy per l'accesso ai repository su internet.
1. Utilizzando il client web vSphere, passa a **Home** > **Update Manager**. Fai clic sul tuo vCenter Server.
2. Seleziona la **Scheda Manage** e fai clic sul pulsante **Settings**.
3. Seleziona **Download Settings** e quindi, nelle _impostazioni proxy_, fai clic su **Edit**.
4. Spunta la casella **Use Proxy** e immetti l'_indirizzo IP del server proxy_ e la _porta 3128_, quindi fai clic su **OK**. Lo stato di connettività diventa _Validating_ e poi _Connected_.
5. Fai clic su **Download Now**. Nel pannello _Recent Tasks_ dovresti visualizzare questa attività completa.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
