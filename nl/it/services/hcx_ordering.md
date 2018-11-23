---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di VMware HCX on IBM Cloud

Puoi ordinare il servizio VMware HCX on {{site.data.keyword.cloud}} mentre ordini una nuova istanza VMware vCenter Server with Hybridity Bundle con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di VMware HCX on IBM Cloud per una nuova istanza

Per ordinare una nuova istanza VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle con VMware HCX on {{site.data.keyword.cloud_notm}}, seleziona **VMware HCX on IBM Cloud** nella sezione **Servizi** quando ordini l'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}.


## Ordine di VMware HCX on IBM Cloud per un'istanza esistente

Per aggiungere il servizio VMware HCX on {{site.data.keyword.cloud_notm}} in un'istanza esistente di VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.

## Configurazione di VMware HCX on IBM Cloud

Per installare HCX on {{site.data.keyword.cloud_notm}}, completa le seguenti impostazioni:
1. Specifica il **Tipo di interconnessione HCX** selezionando una delle seguenti opzioni:
  * **Rete pubblica:** HCX crea una connessione crittografata tra i siti sulla rete pubblica. La registrazione e la misurazione della licenza vengono eseguite sulla rete pubblica.
  * **Interconnessione privata:** HCX crea una connessione crittografata tra i siti sulla rete privata. La registrazione e la misurazione della licenza vengono eseguite sulla rete pubblica.
  * **Rete privata:** HCX crea una connessione crittografata tra i siti sulla rete privata. La registrazione e la misurazione della licenza vengono eseguite sulla rete privata tramite il proxy HTTP.
3. Se selezioni **Rete privata**, completa i seguenti campi:
  * **Indirizzo proxy:** l'indirizzo IPv4 del server proxy.
  * **Porta proxy:** la porta del server proxy. Il numero di porta è in genere 8080 o 3128.
  * **Nome utente:** il nome utente se è richiesta l'autenticazione proxy.
  * **Password:** la password se è richiesta l'autenticazione proxy.
  * **Immettere nuovamente la password:** immetti di nuovo la password per la convalida dell'autenticazione proxy.
2. Specifica il **Tipo di certificato endpoint pubblico**. Se selezioni **Certificato CA**, configura le seguenti impostazioni:
  * **Contenuto del certificato:** immetti il contenuto del certificato CA.
  * **Chiave privata:** immetti la chiave privata del certificato CA.
  * (Facoltativo) **Password:** immetti la password per la chiave privata, se è crittografata.
  * (Facoltativo) **Immettere nuovamente la password:** immetti di nuovo la password per la chiave privata.
  * (Facoltativo) **Nome host:** il nome host da associare al nome comune (CN) del certificato CA. HCX on {{site.data.keyword.cloud_notm}} richiede che il formato del certificato CA sia accettato da Edge NSX. Per ulteriori informazioni sui formati dei certificati Edge NSX, vedi [Importazione di certificati SSL](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Processo di distribuzione per HCX on IBM Cloud

La distribuzione di HCX on {{site.data.keyword.cloud_notm}} è automatizzata. Sia che tu scelga di ordinare un'istanza vCenter Server with Hybridity Bundle con il servizio incluso o di distribuire il servizio nella tua istanza in un secondo momento, i seguenti passi sono completati dal processo di automazione {{site.data.keyword.vmwaresolutions_short}}:
1. Dall'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate tre sottoreti per HCX:
   * Una sottorete portatile privata per la gestione HCX.
   * Una sottorete portatile privata per le interconnessioni HCX. Questa sottorete viene utilizzata se per **Tipo di interconnessione HCX** si seleziona l'opzione **Rete privata**.
   * Una sottorete portatile pubblica per l'attivazione e la manutenzione con VMware. Se per **Tipo di interconnessione HCX** si seleziona l'opzione **Rete pubblica**, questa sottorete viene utilizzata anche per le interconnessioni HCX.

   Gli indirizzi IP nelle sottoreti ordinate per HCX devono essere gestiti dall'automazione di VMware on {{site.data.keyword.cloud_notm}}. Questi indirizzi IP non possono essere assegnati alle risorse VMware, come VM ed Edge NSX, create da te. Se hai bisogno di ulteriori indirizzi IP per le tue risorse VMware, devi ordinare le tue proprie sottoreti da {{site.data.keyword.cloud_notm}}.
   {:important}
2. Se per il **Tipo di interconnessione HCX** è stata selezionata la **Rete privata**, viene creato un gruppo di porte denominato **SDDC-DPortGroup-HCX-Private** sul DVS (Distributed Virtual Switch) privato.
3. Viene ordinata una chiave di attivazione HCX da VMware.
4. Vengono creati tre pool di risorse e cartelle VM per HCX, necessari per interconnessioni HCX, componenti HCX locali e componenti HCX remoti.
5. Viene distribuita e configurata una coppia di gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HCX:
   * Le interfacce di uplink pubblico e privato vengono configurate utilizzando le sottoreti ordinate.
   * Gli ESG vengono configurati come una coppia di dispositivi edge di grandi dimensioni con l'alta disponibilità (HA) abilitata.
   * Le regole del firewall e le regole NAT (Network Address Translation) vengono configurate per consentire il traffico HTTPS in entrata e in uscita da e verso HCX Manager.
   * Vengono configurate le regole di bilanciamento del carico e i pool di risorse. Le regole e i pool di risorse sono utilizzati per inoltrare il traffico in entrata correlato a HCX ai dispositivi virtuali appropriati di HCX Manager, vCenter Server e PSC (Platform Services Controller).
   * Viene applicato un certificato SSL per crittografare il traffico HTTPS in entrata correlato a HCX che arriva tramite gli ESG.

   L'edge di gestione HCX è dedicato al traffico di gestione HCX tra i componenti HCX in loco e i componenti HCX lato cloud. Non modificare l'edge di gestione HCX o utilizzarlo per le estensioni di rete HCX. Crea, invece, edge separati per le estensioni di rete. Inoltre, l'utilizzo di un firewall o la disabilitazione delle comunicazioni dell'edge di gestione HCX ai componenti di gestione IBM privati o all'Internet pubblico potrebbe influire negativamente sulla funzionalità di HCX.
   {:important}

6. HCX Manager on {{site.data.keyword.cloud_notm}} viene distribuito, attivato, e configurato:
   * HCX Manager viene registrato con vCenter Server.
   * Vengono configurati HCX Manager, vCenter Server, PSC e NSX Manager.
   * Viene configurata la flotta HCX.
   * Vengono configurati i contenitori di distribuzione HCX locali e remoti.
7. Il nome host e l'indirizzo IP di HCX Manager vengono registrati con il server DNS di VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

### Link correlati

* [Panoramica di HCX on {{site.data.keyword.cloud_notm}}](hcx_considerations.html)
* [Gestione di HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Glossario dei termini HCX](hcx_glossary.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Panoramica di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentazione di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
