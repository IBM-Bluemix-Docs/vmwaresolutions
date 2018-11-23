---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---


# Rete e infrastruttura di IBM Cloud

## VRF (Virtual Routing and Forwarding)

Gli account di IBM Cloud possono anche essere configurati come account VRF. Questo fornisce funzionalità simili allo spanning della VLAN, consentendo l'instradamento automatico tra i blocchi di IP della sottorete. Tutti gli account con connessioni Direct-Link devono essere convertiti o creati come account VRF.

## Direct Link

IBM Cloud Direct Link Connect offre l'accesso privato alla tua infrastruttura IBM Cloud e a tutti gli altri cloud collegati al Network Service Provider, tramite il tuo data center IBM Cloud locale. Questa opzione è perfetta per la creazione della connettività a più cloud in un unico ambiente. Colleghiamo i clienti alla rete privata di IBM Cloud, utilizzando una topologia di larghezza di banda condivisa. Come con tutti i prodotti Direct Link, puoi aggiungere l'instradamento globale, che consente il traffico di rete privato a tutte le ubicazioni di IBM Cloud.

## VPN (Virtual Private Network)

### VPN strongSwan

Il servizio VPN strongSwan IPSec fornisce un canale di comunicazione end-to-end sicuro su internet che si basa sulla suite di protocolli standard del settore Internet Protocol Security (IPSec).

### Hybridity (HCX)

Il servizio VCS Hybridity Bundle on IBM Cloud può estendere senza problemi le reti dei data center in loco in IBM Cloud, il che consente la migrazione delle macchine virtuali (VM) da e verso IBM Cloud senza alcuna conversione o modifica.

## Struttura fisica

L'infrastruttura fisica richiesta per la distribuzione di un'istanza di produzione IBM Cloud Private (ICP) in un cluster VMware vCenter Server on IBM Cloud (VCS), richiede la seguente specifica minima.

Tabella 1. Specifica VCS per ICP

| Distribuzione NFS  |  Distribuzione vSAN |
:--|:----:|:----:
Numero di server  |  3 |  4
CPU | 28 Core 2.2 GHz | 28 Core 2.2 GHz
Memoria | 384 GB | 384 GB
Archiviazione | Gestione 2000 GB 2IOPS/GB, Carico di lavoro 2000-GB 4IOPS/GB, ICP 4000 GB 4IOPS/GB | Min 960-GB SSD x 2

Oltre ai requisiti hardware di IBM Cloud Private, devi creare volumi persistenti nell'ambiente ICP per archiviare i dati database e log di Cloud Automation Manager (CAM). Mentre CAM supporta tutti i tipi di volumi persistenti supportati da ICP, le due configurazioni di archiviazione consigliate per CAM sono NFS e GlusterFS.

## Struttura virtuale

Figura 1. Struttura fisica della distribuzione VCS e ICP
![Struttura fisica della distribuzione VCS e ICP](vcsicp-phy-ics-icp-deployment.svg)

All'interno dell'istanza VCS, l'istanza ICP viene distribuita con un gateway dei servizi edge (ESG) dedicato e DLR (Distributed Logical Router). L'installazione ICP viene caricata nella sottorete VXLAN definita nei componenti sopra indicati.

L'ESG è configurato con una regola NAT di origine (SNAT) per consentire il traffico in uscita, consentendo la connettività internet per scaricare i prerequisiti ICP e la connettività a GitHub e Docker o può essere utilizzato un proxy web per fornire la connettività internet. L'ESG è anche configurato per fornire accesso ai servizi DNS e NTP.

L'ESG è anche configurato con una regola NAT di destinazione (DNAT) agli indirizzi IP virtuali Master/Proxy ICP dalla rete IBM Cloud 10.x tramite l'ambiente VXLAN.

### Link correlati

* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
