---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configurazione della rete per utilizzare l'ESG NSX gestito dal cliente con le tue VM

Configura la rete per le tue macchine virtuali in modo da poter usufruire del gateway dei servizi edge (ESG) VMware NSX che viene distribuito nelle tue istanze VMware vCenter Server. Per ulteriori informazioni sulle misure di sicurezza implementate per ridurre al minimo il rischio di sicurezza, vedi [L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX è una piattaforma di virtualizzazione di rete che consente la virtualizzazione di reti isolate e fornisce numerosi servizi
di rete come switch, instradamento e firewall. Per ulteriori informazioni su NSX, vedi [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Come parte del processo di ordine per la tua istanza di vCenter Server, le seguenti azioni vengono completate per tuo conto:
* Una sottorete del cliente privata viene ordinata per essere utilizzata dalle tue VM (macchine virtuali) per accedere alla rete privata dell'infrastruttura {{site.data.keyword.cloud}}.
* Una sottorete del cliente pubblica viene ordinata per consentire alla tue VM di accedere a Internet.
* NSX viene distribuito e configurato nella tua istanza vCenter Server.
* Uno switch logico NSX di esempio viene distribuito per essere utilizzato dalle VM del carico di lavoro del cliente.
* Un DLR (Distributed Logical Router) NSX di esempio viene distribuito per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2).
* Un dispositivo Edge NSX viene distribuito e configurato per eseguire la conversione degli indirizzi di rete (NAT) dall'intervallo di indirizzi IP
dello switch logico del carico di lavoro a un indirizzo IP pubblico sulle regole NAT.
* Se hai installato il servizio Veeam on {{site.data.keyword.cloud_notm}}, NSX Manager è configurato per eseguire un backup giornaliero delle configurazioni NSX. Per ulteriori informazioni, vedi [Considerazioni sull'istallazione di Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html#considerations-when-you-install-veeam-on-ibm-cloud).

## Procedura per configurare le impostazioni di rete per le tue VM

Per usufruire di NSX per le tue VM del carico di lavoro, devi configurare una serie di impostazioni completando le seguenti operazioni quando crei le VM:

1. Imposta l'adattatore di rete della VM sullo switch logico del carico di lavoro:
   1. Nella casella di dialogo **Nuova macchina virtuale**, fai clic sulla scheda **Personalizza hardware**.
   2. Nel menu **nuovo dispositivo**, seleziona **Rete** e fai clic su **Aggiungi**.
   3. Sull'adattatore di rete appena aggiunto, seleziona lo switch logico del carico di lavoro dal menu. Un nome di esempio per lo switch logico del carico di lavoro
   è **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   Assicurati di non selezionare lo switch **Workload Transit**.
   {:important}

2. Identifica un indirizzo IP disponibile per la VM:
   *  L'indirizzo IP deve essere compreso nell'intervallo `192.168.10.0/24`. Nota che l'indirizzo IP `192.168.10.1` è riservato (vedi il **Passo 3**).
   *  Quando configuri la rete del sistema operativo che viene eseguito sulla VM, utilizza l'indirizzo IP selezionato e la maschera di rete
   `255.255.255.0`.

   Sei responsabile della gestione dell'intervallo di indirizzi IP a cui hai assegnato le tue VM.
   {:note}

3. Assegna il gateway predefinito della VM come `192.168.10.1`. Questo è l'indirizzo IP del DLR NSX sullo stesso switch logico delle VM del carico di lavoro.

## Procedura per abilitare la regola SNAT

Se vuoi che le tue VM del carico di lavoro abbiano accesso in uscita a Internet, devi abilitare la regola SNAT (Source Network Address Translation) associata. L'abilitazione della regola SNAT consente di convertire l'accesso Internet dalle tue VM in un unico indirizzo IP pubblico. Completa la seguente procedura nel client web VMware vSphere:

1. Fai clic su **Home > Rete & Sicurezza**.
2. Nel riquadro di navigazione, fai clic su **Edge NSX** e doppio clic sull'edge denominato **customer-nsx-edge**.
3. Fai clic su **Gestione > NAT** per aprire la scheda **NAT**.
4. Seleziona la regola SNAT predefinita nella tabella e fai clic sul segno di spunta verde sopra la tabella per abilitare la regola.

Per ulteriori informazioni sulle regole NAT dell'edge NSX, vedi [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Procedura per identificare i dettagli delle sottoreti del cliente

L'edge **customer-nsx-edge** è destinato al tuo utilizzo personale, quindi puoi modificarlo per definire più regole NAT per il traffico in entrata o in uscita. Queste regole devono utilizzare solo gli indirizzi IP sulle sottoreti del cliente pubbliche o private ordinate a tuo nome.

Per identificare i dettagli per le sottoreti del cliente in modo da poter utilizzare gli indirizzi IP ordinati, completa la seguente procedura nel client web VMware vSphere:

1. Fai clic su **Home > Rete & Sicurezza**.
2. Nel riquadro di navigazione, fai clic su **Edge NSX** e doppio clic sull'**edge customer-nsx-edge**.
3. Nella scheda **Riepilogo** relativa a questo edge, esamina la descrizione che contiene gli identificativi di sottorete per le sottoreti del cliente pubbliche e private.

Inoltre, puoi trovare ulteriori dettagli sulle sottoreti del cliente completando la seguente procedura nel 	{{site.data.keyword.slportal}}:

1. Fai clic su **Rete > Gestione IP > Sottoreti**.
2. Fai clic sul menu del filtro e nel campo della sottorete immetti l'identificativo come mostrato nella descrizione dell'edge **customer-nsx-edge** sulla scheda **Riepilogo** nel client web VMware vSphere.
3. Riesamina le note che vengono visualizzate per gli indirizzi IP. Queste note identificano quali sottoreti e indirizzi IP vengono ordinati e utilizzati durante la configurazione iniziale.

   **Avvertenza:** non utilizzare gli indirizzi IP che vengono ordinati e utilizzati durante la configurazione iniziale. Puoi comunque utilizzare altri indirizzi IP
   su queste sottoreti in base ai tuoi requisiti. Per configurare ulteriori regole NAT (network address translation), vedi [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

### Link correlati

* [Risoluzione dei problemi](../vcenter/vcenter_chg_impact.html)
* [Domande frequenti](../vmonic/faq.html)
* [Gateway dei servizi edge NSX](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
