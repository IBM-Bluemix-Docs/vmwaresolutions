---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione di Zerto on IBM Cloud

Dopo aver distribuito il servizio Zerto on {{site.data.keyword.cloud}} nella tua istanza, puoi configurare o aggiornare Zerto Virtual Replication e distribuire più dispositivi Virtual Replication Appliance ai server ESXi appena aggiunti.

## Utilizzo del tuo certificato per Zerto

Come procedura consigliata, utilizza il tuo certificato SSL per Zerto Virtual Manager (ZVM). Dopo aver distribuito Zerto on {{site.data.keyword.cloud_notm}}, sostituisci il certificato SSL per ZVM con il tuo certificato. Per ulteriori informazioni, vedi [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Gestione della configurazione delle repliche Zerto

Per gestire la configurazione delle repliche Zerto, accedi alla console di Zerto Virtual Replication utilizzando le credenziali di vCenter con autorizzazioni di amministratore. Ad esempio, la riassociazione delle istanze Zerto o la configurazione dei gruppi di protezione virtuali per replicare le macchine virtuali.

Se esegui la replica tra istanze {{site.data.keyword.cloud_notm}} Zerto diverse, puoi configurare la replica direttamente tra le istanze Zerto. Se esegui la replica tra l'istanza {{site.data.keyword.cloud_notm}} Zerto e il tuo proprio data center, devi installare tu stesso Zerto nel tuo data center. Questa istanza può autorizzarsi automaticamente quando la associ all'istanza {{site.data.keyword.cloud_notm}} Zerto.

La replica di Zerto non supporta l'attraversamento NAT (Network Address Translation). Stabilire la connettività tra l'istanza di {{site.data.keyword.cloud_notm}} Zerto e il tuo data center potrebbe richiedere la personalizzazione delle rotte sui dispositivi Zerto Virtual Manager (ZVM) o Zerto Virtual Replication Appliance (VRA) su entrambi i lati. Stabilire la connettività potrebbe richiedere anche un tunneling sicuro tra i siti. Quando configuri o riconfiguri le rotte sui dispositivi ZVM, devi assicurarti che tutti questi dispositivi possano connettersi correttamente a `zerto.com` per la segnalazione di utilizzo. Puoi verificare questa connessione aprendo una sessione del browser in `https://www.zerto.com` dal dispositivo ZVM.

L'ESG (Edge Services Gateway) VMware NSX di gestione delle istanze Cloud Foundation e vCenter Server on {{site.data.keyword.cloud_notm}} è preconfigurato per consentire le comunicazioni HTTPS in uscita (porta TCP 443) originate da ZVM.
{:note}

## Aggiornamento di Zerto Virtual Replication

Per aggiornare Zerto Virtual Replication, accedi alla console di Zerto Virtual Replication.

## Distribuzione di VRA ai server ESXi appena aggiunti

Quando aggiungi o rimuovi i server ESXi per il cluster primario della tua istanza, i VRA vengono distribuiti o rimossi automaticamente. I VRA non vengono distribuiti automaticamente ai server ESXi nei cluster secondari della tua istanza. Puoi distribuire i VRA autonomamente utilizzando la console di Zerto Virtual Replication.

### Link correlati

* [Panoramica di Zerto on {{site.data.keyword.cloud_notm}}](addingzertodr.html)
* [Richiesta di servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Ripristino di emergenza Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Spiegazione degli avvisi di Zerto Virtual Replication](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
