---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

#	Raccolta di metadati

VUM scarica i metadati relativi ad aggiornamenti, patch o estensioni tramite un processo automatico predefinito che puoi modificare. A intervalli regolari configurabili, VUM contatta VMware o fonti di terze parti per raccogliere i metadati più recenti relativi ad aggiornamenti, patch o estensioni disponibili. Tuttavia, le impostazioni predefinite di VMware sono accettabili per l'utilizzo nell'istanza VMware vCenter Server on {{site.data.keyword.cloud}} e puoi modificarle in base alle tue esigenze aziendali.

VUM visualizza le baseline gestite dal sistema generate da vSAN. Le baseline gestite dal sistema aggiornano automaticamente il loro contenuto su base periodica, il che richiede che VUM abbia accesso costante a internet. Le baseline del sistema vSAN vengono in genere aggiornate ogni 24 ore.

Puoi utilizzare le baseline gestite dal sistema per aggiornare i cluster vSAN alle patch, ai driver, agli aggiornamenti critici consigliati o alla versione host ESXi più recente supportata per vSAN.

Per la maggior parte delle aziende, le impostazioni predefinite di VMware per VUM sono considerate adeguate. Se la tua azienda vuole utilizzare impostazioni diverse, di seguito viene indicato come modificare tali impostazioni.

##	Download Schedule
Gli aggiornamenti sono aggiornamenti di dispositivi virtuali, estensioni e patch di host e, per impostazione predefinita, VUM scarica gli aggiornamenti ogni giorno. Per modificare questa impostazione, accedi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings**, seleziona **Download Schedule** e fai clic su **Edit**.

##	Notification Check Schedule
Le notifiche sono informazioni su richiami di patch, nuove correzioni e avvisi e, per impostazione predefinita, VUM scarica le notifiche su base oraria. Per modificare questa impostazione, accedi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings**, seleziona **Notification Check Schedule** e fai clic su **Edit**.

##	Impostazioni della macchina virtuale
Per modificare le impostazioni della macchina virtuale (VM), accedi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings** e **VM Settings** e fai clic su **Edit**.

##	Host/Cluster Settings
Per modificare le impostazioni di host e cluster, accesi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings** e **Host/Cluster Settings** e fai clic su **Edit**.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
