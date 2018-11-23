---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Gestione dell'accesso utente con IAM

L'accesso alle istanze del servizio {{site.data.keyword.vmwaresolutions_full}} per gli utenti nel tuo account è controllato da {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). A ogni utente che accede ai servizi {{site.data.keyword.vmwaresolutions_short}} nel tuo account deve essere assegnata una politica di accesso con un ruolo utente IAM definito.

La politica di accesso determina le azioni che l'utente può eseguire all'interno del contesto del servizio o dell'istanza che selezioni. Le azioni consentite sono personalizzate e definite dal servizio {{site.data.keyword.cloud_notm}} come operazioni che possono essere eseguite sul servizio. Le azioni vengono quindi associate ai ruoli utente IAM.

Le politiche consentono di concedere l'accesso a diversi livelli. Alcune delle opzioni includono i seguenti accessi:

* Accesso a tutte le istanze del servizio nel tuo account
* Accesso a una singola istanza del servizio nel tuo account
* Accesso a una specifica risorsa all'interno di un'istanza
* Accesso a tutti i servizi abilitati a IAM nel tuo account

Dopo aver definito l'ambito della politica di accesso, potrai assegnare un ruolo.

Rivedi le seguenti informazioni che descrivono le azioni consentite da ciascun ruolo all'interno del servizio {{site.data.keyword.vmwaresolutions_short}}.

## Ruoli e autorizzazioni di gestione della piattaforma

I ruoli di gestione della piattaforma consentono agli utenti di eseguire attività sulle risorse del servizio a livello di piattaforma. Ad esempio, assegnare l'accesso utente al servizio, creare o eliminare ID servizio, creare istanze e associare le istanze alle applicazioni.

La seguente tabella fornisce informazioni sulle azioni associate ai ruoli di gestione della piattaforma.

Tabella 1. Ruoli di gestione della piattaforma e azioni consentite

| Ruolo di gestione della piattaforma | Azioni | Azioni di esempio |
|:----------------- |:----------------- |:----------------- |
| Visualizzatore | Azioni di sola lettura | <ul><li>Visualizzare il riepilogo delle istanze</li><li>Visualizzare i dettagli di un'istanza</li></ul>|
| Editor | Aggiornare un'istanza specifica |<ul><li>Aggiungere o rimuovere i server ESXi</li><li>Aggiungere o rimuovere i cluster</li><li>Aggiungere o rimuovere i servizi</li><li>Aggiornare un'istanza a una versione superiore</li></ul> |
| Operatore | Azioni di sola lettura | <ul><li>Elencare le istanze</li><li>Visualizzare i dettagli di un'istanza</li></ul> |
| Amministratore | Accesso alla gestione completa |<ul><li>Creare nuove istanze</li><li>Eliminare istanze</li><li>Concedere l'accesso alla piattaforma ad altri utenti</li></ul>|

Per {{site.data.keyword.vmwaresolutions_short}}, esistono le seguenti azioni:

Tabella 2. Descrizione delle azioni e ruoli richiesti

| Azione | Operazione sul servizio | Ruolo |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Creare nuove istanze | Amministratore |
| vmware-solutions.instances.delete | Eliminare istanze | Amministratore |
| vmware-solutions.instances.view | <ul><li>Elencare le istanze</li><li>Visualizzare i dettagli di un'istanza</li></ul> | Visualizzatore, operatore, editor e amministratore |
| vmware-solutions.instances.update | <ul><li>Aggiungere o rimuovere i server ESXi</li><li>Aggiungere o rimuovere i cluster</li><li>Aggiungere o rimuovere i servizi</li><li>Aggiornare un'istanza a una versione superiore</li></ul> | Editor e amministratore |
| vmware-solutions.account.update | Aggiornare le impostazioni account | Amministratore |

## Gestione dell'accesso per gli utenti

Puoi aggiungere nuovi utenti all'account {{site.data.keyword.cloud_notm}} in modo che questi utenti possano condividere i servizi e le risorse forniti per l'account. Per ulteriori informazioni, vedi [Come invitare gli utenti ad accedere a servizi e risorse](../vmonic/iamuserinvite.html).

Puoi anche gestire l'accesso per gli utenti esistenti, inclusa la modifica dell'accesso esistente, l'assegnazione di un nuovo accesso e la revisione dell'accesso assegnato. Per gestire l'accesso per gli utenti, devi essere il proprietario dell'account o avere il ruolo di gestione della piattaforma di **Amministratore**. Per ulteriori informazioni, vedi [Gestione dell'accesso alle risorse](../../../iam/mngiam.html).

## Migrazione di istanze esistenti agli account IBM Cloud

A causa dell'integrazione di {{site.data.keyword.vmwaresolutions_short}} con IAM, le istanze che sono state distribuite nelle release della V2.5 e successive nel tuo account {{site.data.keyword.cloud}} vengono aggiunte automaticamente al tuo account e sono gestite da IAM.

Le istanze esistenti distribuite nelle release della V2.4 e precedenti possono essere migrate ad account {{site.data.keyword.cloud_notm}} specificati per la gestione abilitata a IAM. Per ulteriori informazioni, consulta i seguenti argomenti:
* [Migrazione di istanze vCenter Server precedenti alla V2.5 agli account IBM Cloud](../vcenter/vc_addinstancetousraccount.html)
* [Migrazione di istanze vCenter Server with Hybridity Bundle precedenti alla V2.5 agli account IBM Cloud](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Migrazione di istanze Cloud Foundation precedenti alla V2.5 agli account IBM Cloud](../sddc/sd_addinstancetousraccount.html)
* [Migrazione di istanze NetApp ONTAP Select precedenti alla V2.5 agli account IBM Cloud](../netapp/np_addinstancetousraccount.html)
* [Migrazione di istanze VMware Federal precedenti alla V2.5 agli account IBM Cloud](../vcenter/vc_fed_addinstancetousraccount.html)

### Link correlati

* [Gestione di identità e accesso](../../../iam/quickstart.html)
* [Gestione di utenti e accesso](../../../iam/iamusermanage.html)
* [Cos'è IAM](../../../iam/index.html)
