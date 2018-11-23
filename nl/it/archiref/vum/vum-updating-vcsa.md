---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# Aggiornamento di VCSA e vCenter collegati a SSO

## Aggiornamento di VCSA

VUM non aggiorna il VCSA, pertanto in questa sezione viene descritto il processo di aggiornamento di questo dispositivo. Il VCSA distribuito in un'istanza VMware vCenter Server on {{site.data.keyword.cloud}} non ha accesso a Internet, quindi il bundle di aggiornamento deve essere prima scaricato su un server jump.

Il VCSA viene aggiornato mediante la console di gestione del dispositivo, non con il client web vSphere. È possibile accedere alla console di gestione del dispositivo VCSA utilizzando un browser, l'indirizzo IP VCSA e la porta 5480.

Prima di eseguire l'aggiornamento, devi avviare un'istantanea del dispositivo o un backup di VCSA. Assicurati che tutto funzioni come previsto, quindi rimuovi l'istantanea entro pochi giorni per evitare una riduzione delle prestazioni. Inoltre, esamina le note sulla release prima di tentare qualsiasi aggiornamento.

Per aggiornare il VCSA, completa la seguente procedura:
1. Puoi scaricare gli aggiornamenti andando alla pagina di VMware Patch [Download Center](https://my.vmware.com/group/vmware/patch#search), effettuando l'accesso e scegliendo VC dal menu **Search by Product**. Seleziona la patch appropriata e fai clic su **Download**.
2. Utilizzando il client web vSphere, carica il file ISO nel repository dell'archivio chiavi di vCenter.
3. Monta il file ISO di aggiornamento in vCenter Server.
4. Fai un'istantanea del tuo vCenter Server.
5. Accedi alla console di gestione del dispositivo vCenter all'indirizzo: `https://vcenterip:5480`
6. Vai alla sezione **Update**, seleziona **Check Updates** e quindi **Check CDROM**. L'aggiornamento dovrebbe essere elencato.
7. Seleziona **Install Updates** e fai clic su **Accept** per accettare l'EULA. L'aggiornamento viene installato.
8. Al termine dell'aggiornamento, devi tornare alla console di gestione del dispositivo e riavviare la console.
9. Accedi di nuovo al client web vSphere e verifica eventuali errori. Esegui una scansione manuale di VUM, fai clic su **Home** > **Hosts and Cluster**, seleziona un data center o un cluster, seleziona la **scheda Update Manager** e fai quindi clic su **Scan for Updates**. Se questo produce un errore, consulta l'articolo [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Dopo il test, se devi annullare le modifiche, ripristina l'istantanea o ripristina il vCenter con un backup precedente.

## vCenter collegati a SSO

Se hai istanze vCenter Server primarie e secondarie, i tuoi VCSA vengono configurati in un singolo dominio SSO (Single Sign-On) di vCenter. Ogni VCSA avrà un'istanza VUM distribuita. Le proprietà di configurazione che modifichi vengono applicate solo all'istanza VUM specificata e non vengono propagate alle altre istanze nel gruppo.

Puoi specificare un'istanza VUM selezionando il nome del VCSA con il quale è registrata l'istanza VUM dalla barra di navigazione. Puoi anche gestire le baseline e i gruppi di baseline nonché scansionare e correggere solo gli oggetti di inventario gestiti dal VCSA con cui è registrata l'istanza VUM.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
