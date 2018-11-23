---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Gestione di VMware HCX on IBM Cloud

## Accesso alle console di gestione HCX on IBM Cloud

Per gestire il servizio HCX on {{site.data.keyword.cloud}}, devi accedere alla console cloud HCX o alla console di gestione HCX Manager:
1. Utilizza la VPN dell'infrastruttura {{site.data.keyword.cloud_notm}} o un server jump per consentire l'accesso all'indirizzo IP del dispositivo virtuale HCX Manager. Puoi trovare l'indirizzo IP nella pagina dei dettagli del servizio HCX on {{site.data.keyword.cloud_notm}} nella console {{site.data.keyword.vmwaresolutions_short}}.
2. Per accedere alla console cloud HCX, fai clic su **Visualizza console cloud HCX** nella pagina dei dettagli del servizio HCX on {{site.data.keyword.cloud_notm}} ed esegui quindi l'accesso utilizzando le credenziali di vCenter Server.
3. Per accedere alla console di gestione HCX Manager, fai clic su **Visualizza console di gestione HCX Manager** nella pagina dei dettagli del servizio HCX on {{site.data.keyword.cloud_notm}} ed esegui quindi l'accesso utilizzando le credenziali di HCX Manager elencate nella stessa pagina dei dettagli del servizio.

Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html).

## Applicazione degli aggiornamenti a HCX on IBM Cloud

HCX on {{site.data.keyword.cloud_notm}} viene distribuito con l'ultima build testata della tecnologia VMware Hybrid Cloud Extension. VMware invia regolarmente aggiornamenti a queste build, che includono correzioni importanti e nuove funzioni. Queste build vengono trasmesse automaticamente alle installazioni di HCX on {{site.data.keyword.cloud}}, incluse le istallazioni di HCX in loco.

Per applicare eventuali correzioni di manutenzione trasmesse al tuo ambiente, devi utilizzare la console di gestione HCX Manager nel tuo data center in loco e nella tua istanza vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle.

Se non vedi un aggiornamento di build previsto, hai problemi con HCX o vuoi che l'ultima build di HCX venga trasmessa immediatamente al tuo sistema, apri un ticket di supporto seguendo la procedura in [Come contattare il supporto IBM](../vmonic/trbl_support.html).

### Link correlati

* [Panoramica di HCX on {{site.data.keyword.cloud_notm}}](hcx_considerations.html)
* [Glossario dei termini HCX](hcx_glossary.html)
* [Panoramica di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentazione di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
