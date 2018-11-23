---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visualizzazione delle istanze NetApp ONTAP Select

Visualizza il riepilogo e le informazioni dettagliate delle istanze NetApp ONTAP Select fornite per account utente diversi.

## Procedura per visualizzare il riepilogo delle istanze NetApp ONTAP Select

Per visualizzare un riepilogo di tutte le istanze NetApp ONTAP Select fornite per un account utente, completa la seguente procedura:

1. Dalla console {{site.data.keyword.vmwaresolutions_full}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Dal banner della console, fai clic sull'icona del tuo account utente e quindi sul campo **Account** per selezionare l'account utente per il quale vuoi controllare le istanze.
3. Nella tabella **Istanze di NetApp ONTAP Select**, visualizza l'elenco delle istanze fornite nell'account utente selezionato.

Tabella 1. Elementi dell'istanza NetApp ONTAP Select

| Elemento        | Descrizione       |  
|:------------- |:--------------- |
| Nome | Il nome dell'istanza. |
| Versione | La versione dell'istanza. |  
| Ubicazione | Il data center in cui è ospitata l'istanza. |
| Ora di creazione | La data e ora di creazione dell'istanza. |   
| Stato | Lo stato dell'istanza. Lo stato può assumere uno dei seguenti valori:<ul><li>In fase di creazione: l'istanza è in fase di creazione.</li><li>In fase di build: l'istanza è in fase di configurazione.</li><li>Pronto per l'utilizzo: l'istanza è pronta per l'uso.</li><li>In fase di modifica: l'istanza è in fase di modifica.</li><li>Non riuscito: il processo di creazione, configurazione o modifica non è riuscito.</li><li>In fase di eliminazione: l'istanza è in fase di eliminazione.</li><li>Errore di eliminazione: si è verificato un errore durante l'eliminazione dell'istanza.</li><li>Eliminato: l'istanza è stata eliminata.</li></ul>|

## Procedura per visualizzare i dettagli delle proprietà delle istanze NetApp ONTAP Select

Per visualizzare i dettagli delle proprietà di un'istanza:

1. Nella tabella **Istanze di NetApp ONTAP Select**, fai clic sul nome di un'istanza.
2. In **Proprietà**, visualizza i dettagli dell'istanza.

Tabella 2. Proprietà dell'istanza NetApp ONTAP Select

| Proprietà        | Descrizione       |
|:--------------- |:----------------- |
| Nome | Il nome dell'istanza. |
| ID | L'ID dell'istanza. |
| Ubicazione | Il data center in cui è ospitata l'istanza. |
| Versione distribuita | La versione distribuita di {{site.data.keyword.vmwaresolutions_short}}. |
| Versione vCenter | La versione di VMware vCenter Server.<br><br>**Nota**: esiste una leggera variazione tra la versione di vCenter Server visualizzata nella console {{site.data.keyword.vmwaresolutions_short}} e nel client web VMware vSphere. Entrambe sono corrette. |
| NSX per vSphere | La versione del prodotto VMware NSX per vSphere. |
| Edizione licenza NSX | La versione e l'edizione della licenza di VMware NSX. |
| Versione NetApp | La versione di NetApp ONTAP Select. |
| Tipo di licenza NetApp | Il tipo di licenza per NetApp ONTAP Select. |
| DNS, Dominio root | Il nome del dominio root è il nome del dominio DNS (Domain Name System) e il nome root dell'insieme di strutture Microsoft Active Directory (AD) per l'istanza. |
| DNS, Dominio SSO | Il dominio SSO è il dominio vSphere Single Sign-On. Il nome del dominio SSO viene impostato per tutte le istanze distribuite di NetApp ONTAP Select con il valore `vsphere.local`. |
| DNS, Domino secondario | Il dominio secondario è il nome del dominio secondario DNS del nome di dominio root in cui risiedono i nomi host delle istanze NetApp ONTAP Select locali. Il nome del dominio secondario è nel formato `<subdomain_label>.<root_domain>`. |
| Stato | Lo stato dell'istanza. |

## Procedura per visualizzare le informazioni di accesso per le istanze NetApp ONTAP Select

In **Informazioni sull'accesso**, visualizza le informazioni di accesso per i componenti relativi all'istanza. Queste password sono password iniziali generate dal sistema. Se le modifichi all'esterno della console {{site.data.keyword.vmwaresolutions_short}}, non vengono aggiornate nella pagina di riepilogo dell'istanza.

Tabella 3. Informazioni di accesso per i componenti relativi alle istanze NetApp ONTAP Select

| Componente        | Descrizione       |
|:---------------- |:----------------- |
| IP AD/DNS | Gli indirizzi IP dei due server AD. |
| Nome di dominio completo AD/DNS | Il nome di dominio completo del server AD/DNS. |
| ADMIN AD/DNS (Desktop remoto) | Il nome utente e la password che puoi utilizzare per accedere al server AD tramite una connessione al desktop remoto. |
| IP NSX Manager | L'indirizzo IP di NSX Manager. |
| Nome di dominio completo NSX Manager | Il nome di dominio completo di NSX Manager. |
| HTTP NSX Manager | Il nome utente e la password che puoi utilizzare per accedere alla console web di NSX Manager. |
| IP cluster NetApp | L'indirizzo IP del cluster NetApp ONTAP Select. |
| Nome di dominio completo cluster NetApp | Il dome di dominio completo del cluster NetApp ONTAP. |
| HTTPS cluster NetApp | Il nome utente e la password che puoi utilizzare per accedere al cluster NetApp ONTAP Select. |
| IP strumento di distribuzione NetApp | L'indirizzo IP della macchina virtuale di distribuzione NetApp ONTAP Select. |
| Nome di dominio completo strumento di distribuzione NetApp | Il nome di dominio completo della macchina virtuale di distribuzione NetApp ONTAP Select. |
| HTTPS strumento di distribuzione NetApp | Il nome utente e la password che puoi utilizzare per accedere alla macchina virtuale di distribuzione NetApp ONTAP Select. |
| IP PSC | L'indirizzo IP del PSC (Platform Services Controller). |
| Nome di dominio completo PSC | Il nome di dominio completo del PSC. |
| ADMIN PSC | Il nome utente e la password di VMware vCenter Single Sign-On che puoi utilizzare per accedere alla console web PSC. |
| SSH PSC | Il nome utente e la password che puoi utilizzare per accedere alla VM PSC tramite una connessione SSH. |
| IP vCenter | L'indirizzo IP di vCenter Server. |
| Nome di dominio completo vCenter | Il nome di dominio completo di vCenter Server. |
| ADMIN vCenter | Il nome utente e la password di VMware vCenter Single Sign-On che puoi utilizzare per accedere a vCenter Server utilizzando il client web vSphere. |
| SSH vCenter | Il nome utente e la password che puoi utilizzare per accedere alla VM di vCenter Server tramite una connessione SSH. |

## Procedura per visualizzare la cronologia di distribuzione per le istanze NetApp ONTAP Select

Fai clic su **Cronologia distribuzione** dal riquadro di navigazione a sinistra per visualizzare la cronologia di distribuzione per l'istanza.

Tabella 4. Cronologia di distribuzione delle istanze NetApp ONTAP Select

| Elemento        | Descrizione       |  
|:------------|:------------- |
| Data | La data e l'ora in cui lo stato dell'istanza è stato modificato |
| Riepilogo | I dettagli della modifica |

Se si verificano degli errori durante la distribuzione o l'eliminazione dell'istanza, il team di supporto {{site.data.keyword.cloud_notm}} viene automaticamente informato. Per informazioni sullo stato del tuo ticket, puoi [contattare il supporto IBM](../vmonic/trbl_support.html).

## Visualizzazione dei cluster NetApp ONTAP Select

1. Fai clic su **Infrastruttura** dal riquadro di navigazione a sinistra.
2. In **CLUSTER**, visualizza il riepilogo dei cluster NetApp ONTAP Select.

	Tabella5. Elementi dei cluster NetApp ONTAP Select

	 <table>
	   <tr>
	     <th>Elemento</th>
	     <th>Descrizione</th>
	   </tr>
	   <tr>
	     <td>Nome</td>
	     <td>Il nome del cluster.</td>
	   </tr>
	   <tr>
	     <td>Server ESXi</td>
	     <td>Il numero di server ESXi nel cluster.</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>La specifica CPU dei server ESXi nel cluster.</td>
	   </tr>
	   <tr>
	      <td>Archiviazione effettiva</td>
	      <td>La capacità totale del disco dei server ESXi nel cluster.</td>
	   </tr>
	   <tr>
	      <td>Memoria</td>
	      <td>La dimensione totale della memoria dei server ESXi nel cluster.</td>
	   </tr>
	   <tr>
	      <td>Ubicazione data center</td>
	      <td>Il data center in cui è ospitato il cluster. È uguale all'ubicazione del data center per l'istanza.</td>
	   </tr>
		 <tr>
		   <td>Pod</td>
			 <td>Il pod in cui è stato creato il cluster.</td>
		 </tr>
		 <tr>
		  <td>Stato</td>
			<td>Lo stato del cluster. Lo stato può assumere uno dei seguenti valori:<ul><li>Inizializzazione: il cluster è in fase di creazione e configurazione.</li><li>In fase di modifica: il cluster è in fase di modifica.</li><li>Pronto per l'utilizzo: il cluster è pronto per l'uso.</li></ul></td>
		 </tr>
		 <tr>
		  <td>Azioni</td>
			<td>Fai clic sull'icona **Elimina** per eliminare il cluster.</td>
		 </tr>
	 </table>

3. Fai clic sul nome del cluster per visualizzare i dettagli del server ESXi.

Tabella 6. Dettagli del server ESXi di un cluster NetApp ONTAP Select

| Elemento        | Descrizione       |  
|:------------|:----------------- |
| Nome | Il nome del server ESXi nel formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove:<br><br>`host_prefix` è il prefisso del nome host, `n` è la sequenza del server, `subdomain_label` è l'etichetta del dominio secondario e `root_domain` è il nome del dominio root. |
| Versione | La versione del server ESXi. |
| Credenziali | Il nome utente e la password per accedere al server ESXi. |
| IP privato | L'indirizzo IP privato del server ESXi. |
| Stato | Lo stato del server ESXi, che può assumere uno dei seguenti valori:<ul><li>Attivo: il server ESXi è pronto per l'uso.</li><li>In fase di eliminazione: il server ESXi è in fase di eliminazione.</li></ul> |

## Operazioni successive

Gestisci le tue istanze dalla console {{site.data.keyword.vmwaresolutions_short}}, dal client web VMware vSphere o dalla console NetApp.

Prima di fare clic su **Console vCenter** nella pagina di riepilogo dell'istanza per passare al client web vSphere e iniziare a gestire i tuoi server ESXi, devi accedere al portale VPN del {{site.data.keyword.CloudDataCent_notm}}. Passa con il mouse sul pulsante **Console vCenter** e segui le istruzioni per assicurarti di soddisfare tutti i requisiti e di aver completato i passi necessari prima di accedere al client web vSphere.
{:important}

Per ulteriori informazioni che ti consentono di completare le istruzioni di accesso, consulta i seguenti argomenti:

*  Per i requisiti e i passi necessari prima di accedere al client web vSphere, vedi [Timeout raggiunto durante la connessione al client web vSphere](../vmonic/trbl_timeout_vc_console.html).
*  Per un elenco di punti di accesso per accedere alla rete privata dell'infrastruttura {{site.data.keyword.cloud_notm}} tramite VPN, vedi [Accesso VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Se hai dei problemi durante la distribuzione di un file OVF (Open Virtualization Format) utilizzando il client web vSphere, vedi [Distribuzione di un file OVF mediante il client web vSphere](../vmonic/trbl_deploy_ovf.html).

### Link correlati

* [Ordine di istanze NetApp ONTAP Select](np_orderinginstances.html)
* [Eliminazione di istanze NetApp ONTAP Select](np_deletinginstance.html)
* [Collega l'archiviazione dedicata alle distribuzioni di NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
