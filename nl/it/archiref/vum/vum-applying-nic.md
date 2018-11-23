---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Applicazione di driver NIC nativi

ESXi 6.5 contiene molti nuovi driver nativi che sostituiscono i driver vmklinux precedenti. Mentre la maggior parte dei nuovi driver nativi vengono abilitati per impostazione predefinita dopo l'installazione o l'aggiornamento, tre dei nuovi driver nativi sono disabilitati per impostazione predefinita perché non supportano completamente le funzioni dei driver vmklinux corrispondenti.

ixgben è un driver nativo che sostituisce il driver vmklinux net-ixgbe ma non supporta SR-IOV e SW FcOE. L'automazione di ICVS non ha abilitato questo driver quando è stato eseguito il provisioning del tuo host vSphere ESXi. Si consiglia di abilitare questo driver per i benefici prestazionali che offre. La seguente procedura descritta in questa appendice ti mostra come abilitare e disabilitare i driver nativi utilizzando la riga di comando vSphere (vCLI).

Prima di iniziare questa attività, recupera tutti gli indirizzi IP degli host fisici, gli ID di accesso e le password dal [{{site.data.keyword.cloud}}portale dell'infrastruttura](https://control.softlayer.com/devices). Ciò è necessario in caso di ripristino o per controllare l'avanzamento di un aggiornamento, in cui non esiste un accesso di rete diretto all'host.

Per ogni host, effettua le seguenti operazioni in successione:
1. Utilizza il client web vSphere per mettere l'host vSphere ESXi in modalità di manutenzione selezionando **Home** > **Hosts and Clusters**. Nel riquadro di navigazione, seleziona l'host vSphere ESXi, fai clic con il tasto destro del mouse sull'host e seleziona **Maintenance Mode** > **Enter Maintenance Mode**. Poiché l'host fa parte di un cluster DRS automatizzato, le macchine virtuali vengono migrate su host diversi quando l'host entra in modalità di manutenzione.
2. Esegui l'SSH nell'host vSphere ESXi utilizzando i dettagli forniti nella console IC4VS.
3. Immetti il seguente comando della vCLI per abilitare i driver nativi ixgben:
  `esxcli system module set --enabled=true --module=ixgben`
4. Immetti il seguente comando della vCLI per riavviare l'host vSphere ESXi:
  `system shutdown reboot --reason “Install ixgben driver”`
5. Dopo il riavvio dell'host vSphere ESXI, utilizzando SSH accedi nuovamente all'host. Immetti il seguente comando della vCLI e verifica che il driver ixgben sia “caricato” (prima colonna) e “abilitato” (seconda colonna):
  `esxcli system module list |grep ixg`
6. Se i driver sono abilitati, utilizzando il client web vSphere, seleziona l'host nel riquadro di navigazione, fai clic con il tasto destro del mouse e seleziona **Maintenance Mode** > **Exit Maintenance Mode**. Seleziona l'host successivo e abilita i driver finché non vengono terminati tutti gli host.
7. Se la modifica non funziona, per annullare l'operazione, immetti il seguente comando:
  `esxcli system module set --enabled=false --module=ixgben`

8. Se non riesci a connetterti all'host tramite la rete, esegui il comando precedente dalla console IPMI utilizzando la finestra di controllo di {{site.data.keyword.cloud_notm}}.
9. Dopo aver riavviato l'host vSphere ESXi, puoi ora vedere che il driver ixgbe predefinito è stato caricato e abilitato.

Se hai bisogno di ripristinare e non puoi eseguire l'SSH nell'host vSphere ESXi, devi accedere alla console KVM per l'host che richiede il ripristino tramite la finestra di controllo di {{site.data.keyword.cloud_notm}}.

Utilizza l'ID e la password elencati nella finestra di controllo di {{site.data.keyword.cloud_notm}} con l'indirizzo IP IPMI per accedere all'interfaccia web IPMI. Devi essere connesso al data center in cui si trova l'host tramite VPN. Per ulteriori informazioni, vedi [Introduzione a VPN](../../../../infrastructure/iaas-vpn/getting-started.html).

1. Vai alla pagina Device Details, Remote Mgmt per l'host vSphere ESXi e seleziona **Actions** > **KVM Console**. Si aprirà un'altra finestra in cui dovrai immettere utente e password IPMI.
2. Seleziona **Remote Control** > **iKVM/HTML5** e fai clic su **iKVM/HTML5** per riavviare. Potrai ora accedere alla console dell'host vSphere ESXi.
3. Se l'host risponde ai comandi, utilizza **ALT-F1** nella console per accedere alla console dell'host ESXi. Per accedere, utilizza le credenziali dell'host.
4. Se l'host non risponde, utilizza i menu IPMI per spegnere e accendere l'host.
5. Guarda attentamente la console HTML5 mentre l'host si riavvia. Hai solo pochi secondi per passare alla modalità di ripristino quando ESXi inizia a riavviarsi.
6. Premi contemporaneamente i tasti **CMD + R** per accedere alla modalità di ripristino.
7. Digita **“Y”** per accedere alla modalità di ripristino e avviare il server ESXi con la versione precedente.
8. Monitora l'avanzamento tramite la console. Questa operazione può richiedere da 10 a 20 minuti.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
