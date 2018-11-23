---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-076"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione di FortiGate Security Appliance on IBM Cloud

Dopo aver installato correttamente il servizio FortiGate Security Appliance on {{site.data.keyword.cloud}}, puoi gestire e configurare le regole del firewall per FSA dalla console FortiGate.

Devi assicurarti che le regole del firewall FSA siano definite per consentire le comunicazioni HTTPS in uscita (porta TCP 443) che vengono avviate dai componenti di gestione come Zerto Virtual Manager per comunicare con il database di gestione esterno sull'infrastruttura {{site.data.keyword.cloud_notm}} tramite Internet. Le comunicazioni HTTPS in uscita (porta TCP 443) hanno origine dall'indirizzo IP pubblico del gateway dei servizi edge (ESG) VMware NSX dei servizi di gestione nella tua istanza.
{:important}

## Accesso alla console FortiGate serie 300

Per gestire il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, devi accedere alla console FortiGate® serie 300 in uno dei seguenti modi:
* Accedi al client web FortiOS utilizzando le credenziali che puoi trovare nella pagina dei dettagli del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.
* Accedi alla console tramite una connessione SSH utilizzando le credenziali che puoi trovare nella pagina dei dettagli del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)

### Link correlati

* [Panoramica di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_considerations.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web fortinet.com](https://www.fortinet.com/)
* [Documentazione tecnica di Fortinet](http://docs.fortinet.com/fortigate/admin-guides)
