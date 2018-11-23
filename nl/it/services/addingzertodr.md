---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Zerto on IBM Cloud

Il servizio Zerto on {{site.data.keyword.cloud}} integra le funzionalità di replica e ripristino di emergenza nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}.

Questo servizio è disponibile solo per le istanze distribuite nella V1.2 o successive. La versione corrente di Zerto installata è la 6.0 aggiornamento 3.
{:note}

## Specifiche tecniche per Zerto on IBM Cloud

Nel servizio Zerto on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

I componenti Zerto Virtual Replication Appliance (VRA) vengono distribuiti solo nel cluster predefinito.
{:note}

### VSI

* Una VSI (Virtual Service Instance) - Zerto Virtual Manager
* Core 2 x 2,0 GHz
* 4 GB di RAM
* Windows Server 2016 Standard Edition (64 bit)

### Archiviazione

Disco da 100 GB (SAN)

### Rete

* Un indirizzo IP primario privato
* Uplink di rete privata da 1 Gbps

### Licenze e tariffe

Licenza di Zerto Replication V6.0 aggiornamento 3

### Link correlati

* [Informazioni su {{site.data.keyword.vmwaresolutions_short}}](../vmonic/prod_overview.html)
* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Richiesta di servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
