---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visualizzazione delle istanze VMware Federal

Visualizza il riepilogo e le informazioni dettagliate delle istanze VMware Federal fornite per account utente diversi.

## Procedura per visualizzare il riepilogo delle istanze VMware Federal

Per visualizzare un riepilogo di tutte le istanze VMware Federal fornite per un account utente, completa la seguente procedura:
1. Nella console {{site.data.keyword.vmwaresolutions_full}}, fai clic su **Istanze distribuite** dal riquadro di navigazione a sinistra.
2. Dal banner della console, fai clic sull'icona del tuo account utente e quindi sul campo **Account** per selezionare l'account utente per il quale vuoi controllare le istanze.
3. Nella tabella **Istanze di vCenter Server**, visualizza l'elenco delle istanze fornite nell'account utente selezionato.

Tabella 1. Elementi dell'istanza VMware Federal

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Nome | Il nome dell'istanza. |
| Versione | La versione di release in cui è stata distribuita o aggiornata l'istanza. |  
| Ubicazione | Il {{site.data.keyword.CloudDataCent_notm}} in cui è ospitata l'istanza. |  
| Ora di creazione | La data e ora di creazione dell'istanza. |
| Stato | Lo stato dell'istanza. |

L'istanza può avere una serie di stati.

Tabella 2. Descrizioni dello stato delle istanze nel data center VMware Federal

| Stato        | Descrizione       |
|:------------- |:------------- |
| In fase di creazione | L'istanza è in fase di creazione. |
| In fase di build | L'istanza è in fase di configurazione. |
| Pronto per l'utilizzo | L'istanza è pronta per l'uso. |
| In fase di modifica | L'istanza è in fase di modifica. |
| Protetto | L'istanza distribuita viene disconnessa da una connessione di gestione aperta e dall'automazione.
| Non riuscito | Il processo di creazione, configurazione o modifica non è riuscito. |
| In fase di eliminazione | L'istanza è in fase di eliminazione. |
| Errore di eliminazione | Si è verificato un errore durante l'eliminazione dell'istanza. |
| Eliminato | L'istanza è stata eliminata. |

## Procedura per visualizzare i dettagli delle proprietà delle istanze VMware Federal

Per visualizzare i dettagli delle proprietà di un'istanza:

1. Nella tabella **Istanze vCenter Server**, fai clic sul nome di un'istanza.
2. In **Proprietà**, visualizza i dettagli dell'istanza.

Tabella 3. Proprietà dell'istanza VMware Federal

| Proprietà        | Descrizione       |
|:------------- |:------------- |
| Nome | Il nome dell'istanza. |
| ID | L'ID dell'istanza. |
| Ubicazione | Il {{site.data.keyword.CloudDataCent_notm}} in cui è ospitata l'istanza. |
| Versione corrente |  La versione corrente di {{site.data.keyword.vmwaresolutions_short}}. |
| Versione vCenter | La versione di VMware vCenter Server.<br><br>**Nota:** esiste una leggera variazione tra la versione di vCenter Server visualizzata nella console {{site.data.keyword.vmwaresolutions_short}} e nel client web VMware vSphere. Entrambe sono corrette. |
| NSX per vSphere | La versione del prodotto VMware NSX per vSphere. |
| Edizione licenza NSX | La versione e l'edizione della licenza di VMware NSX. |
| Dominio root DNS | Il nome del dominio root è il nome del dominio DNS (Domain Name System) e il nome root dell'insieme di strutture Microsoft Active Directory (AD). |
| Dominio SSO DNC | Il dominio SSO è il dominio vSphere Single Sign-On. Il nome del dominio SSO viene fissato per tutte le istanze distribuite di vCenter Server con il valore <samp class="ph codeph">vsphere.local</samp>. |
| Dominio secondario DNS | Il dominio secondario è il nome del dominio secondario DNS del nome di dominio root in cui risiedono i nomi host delle istanze vCenter Server locali. Il nome del dominio secondario è nel formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Stato | Lo stato dell'istanza. |

## Procedura per visualizzare le informazioni di accesso per le istanze VMware Federal

In **Informazioni sull'accesso**, visualizza le informazioni di accesso per i componenti relativi all'istanza. Le password visualizzate sono le password iniziali generate dal sistema. Se le modifichi all'esterno della console {{site.data.keyword.vmwaresolutions_short}}, non vengono aggiornate nella pagina di riepilogo dell'istanza.

Tabella 4. Informazioni di accesso per i componenti relativi all'istanza

| Componente        | Descrizione       |
|:------------- |:------------- |
| IP AD/DNS | Gli indirizzi IP dei due server AD. |
| Nomi di dominio completo AD/DNS | I nomi di dominio completi del server AD/DNS.<br><br>**Nota:** è possibile utilizzare la stessa password amministratore per connettersi a tutti i server AD/DNS utilizzando una connessione al desktop remoto. |
| ADMIN AD/DNS (Desktop remoto)  | Per le istanze primarie, visualizza il nome utente e la password per accedere al server AD tramite una connessione al desktop remoto.
| IP NSX Manager  | L'indirizzo IP di NSX Manager.  |
| Nome di dominio completo NSX Manager  | Il nome di dominio completo di NSX Manager.  |
| HTTP NSX Manager  | Il nome utente e la password utilizzati per accedere alla console web di NSX Manager. |
| IP PSC  | L'indirizzo IP del PSC (Platform Services Controller).  |
| Nome di dominio completo PSC  | Il nome di dominio completo del PSC.  |    
| ADMIN PSC  | Il nome utente e la password di VMware vCenter Single Sign-On che puoi utilizzare per accedere alla console web PSC.  |
| SSH PSC  | Il nome utente e la password che puoi utilizzare per accedere alla VM PSC tramite una connessione SSH.  |
| IP vCenter  | L'indirizzo IP di vCenter Server.  |
| Nome di dominio completo vCenter  | Il nome di dominio completo di vCenter Server.  |
| ADMIN vCenter  | Il nome utente e la password di VMware vCenter Single Sign-On che puoi utilizzare per accedere a vCenter Server utilizzando il client web vSphere.  |
| SSH vCenter  | Il nome utente e la password che puoi utilizzare per accedere alla VM di vCenter Server tramite una connessione SSH.  |

## Procedura per visualizzare la cronologia di distribuzione per le istanze VMware Federal

Fai clic su **Cronologia distribuzione** dal riquadro di navigazione a sinistra per visualizzare la cronologia di distribuzione per l'istanza.

Tabella 5. Cronologia di distribuzione delle istanze VMware Federal

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Data | La data e l'ora in cui lo stato dell'istanza è stato modificato. |
| Riepilogo | I dettagli della modifica. |

## Cosa fare se si verificano errori

Se si verificano degli errori durante la distribuzione o l'eliminazione dell'istanza, il team di supporto {{site.data.keyword.cloud_notm}} viene automaticamente informato. Per informazioni sullo stato del tuo ticket, puoi [contattare il supporto IBM](../vmonic/trbl_support.html).

## Operazioni successive

Gestisci le tue istanze dalla console {{site.data.keyword.vmwaresolutions_short}} o dal client web VMware vSphere.

Prima di fare clic su **Console vCenter** nella pagina di riepilogo dell'istanza per passare al client web vSphere e iniziare a gestire i tuoi server ESXi, devi accedere al portale VPN del {{site.data.keyword.CloudDataCent_notm}}. Passa con il mouse sul pulsante **Console vCenter** e segui le istruzioni per assicurarti di soddisfare tutti i requisiti e di aver completato i passi necessari prima di accedere al client web vSphere.
{:important}

Rivedi i seguenti argomenti per informazioni utili per completare le istruzioni di accesso:
*  Per i requisiti e i passi necessari prima di accedere al client web vSphere, vedi [Timeout raggiunto durante la connessione al client web vSphere](../vmonic/trbl_timeout_vc_console.html).
*  Per un elenco di punti di accesso per accedere alla rete privata dell'infrastruttura {{site.data.keyword.cloud_notm}} utilizzando la VPN, vedi [Accesso VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Se hai dei problemi durante la distribuzione di un file OVF (Open Virtualization Format) utilizzando il client web vSphere, vedi [Distribuzione di un file OVF mediante il client web vSphere](../vmonic/trbl_deploy_ovf.html).

### Link correlati

* [Panoramica di VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Ordine di istanze VMware Federal](vc_fed_orderinginstance.html)
* [Eliminazione di istanze VMware Federal](vc_fed_deletinginstance.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
