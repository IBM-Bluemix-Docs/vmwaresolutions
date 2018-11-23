---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Zerto

Se noti che un host vSphere ESXi non può entrare in modalità di manutenzione durante la correzione, è possibile che Zerto lo stia fermando. Se hai aggiornato Zerto dalla distribuzione iniziale, completa la seguente procedura per correggere questo problema. Se non lo hai aggiornato, segui le istruzioni in  [How to place a host with an associated VRA into maintenance mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Accedi all'interfaccia utente web di Zerto.
2. Seleziona **Site Settings** dal menu a discesa.
3. Seleziona la **scheda Policies** e assicurati che la casella **Allow Zerto to always enter hosts to maintenance mode during remediation** sia selezionata.
4. Disconnettiti da Zerto.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud}} Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
