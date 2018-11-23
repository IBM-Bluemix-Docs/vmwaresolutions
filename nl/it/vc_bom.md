---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Distinta base di vCenter Server

Esamina le informazioni relative alla distinta base (Diba) per le istanze VMware vCenter Server.

## Diba di VLAN per le istanze vCenter Server

La seguente tabella mostra in dettaglio le informazioni sulla Diba per le VLAN di vCenter Server.

Tabella 1. Diba per le VLAN nelle istanze vCenter Server

| VLAN       | Tipo       | Dettagli       |
|:---------- |:---------- |:------------- |
| VLAN1     | Pubblica, Primaria | Assegnata ai server ESXi fisici per l'accesso alla rete pubblica. Non utilizzata dopo la distribuzione iniziale. Disponibile per l'accesso a Internet. |
| VLAN2     | Privata A, Primaria | Assegnata da {{site.data.keyword.cloud}} ai server ESXi fisici. Utilizzata dall'interfaccia di gestione per il traffico di gestione VMware vSphere.<br><br>Assegnata alle VM (macchine virtuali) che funzionano come componenti di gestione.<br><br>Assegnata al VTEP (VXLAN Tunnel Endpoint) VMware NSX |
| VLAN3     | Privata B, Portatile | Assegnata a VMware vSAN, se utilizzato.<br><br>Assegnata a VMware NFS, se utilizzato.<br><br>Assegnata a VMware vSphere vMotion. |

## Diba di software per le istanze vCenter Server

La seguente tabella mostra in dettaglio le informazioni sulla Diba per i componenti software di vCenter Server.

Tabella 2. Diba per i componenti software nelle istanze vCenter Server

| Produttore  | Componente                      | Versione       |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.5 Aggiornamento 2c (fino al livello di patch ESXi650-201808001) |
| VMware       | vCenter Server Appliance        | 6.5 Aggiornamento 2c |
| VMware       | Platform Services Controller    | 6.5 Aggiornamento 2c |
| VMware       | vSAN                            | 6.6.1        |
| VMware       | NSX per vSphere                 | 6.4.1        |
| Microsoft    | Windows Server Standard edition | 2012R2       |

VMware vSAN è un componente facoltativo.
{:note}

## Impostazioni di configurazione avanzate per i server ESXi

Esamina la seguente tabella per una panoramica delle impostazioni di configurazione avanzate che vengono applicate ai server ESXi. Queste impostazioni variano a seconda che l'istanza vCenter Server sia distribuita nella V2.2 o successive o aggiornata alla V2.2 o successive dalla V2.1 o precedenti.

Le impostazioni si applicano alle nuove istanze e ai nuovi cluster nelle nuove istanze della V2.2 o successive. Le impostazioni non si applicano ai nuovi cluster nelle istanze esistenti della V2.1 o precedenti o nelle istanze esistenti aggiornate alla V2.2 o successive.

Tabella 3. Impostazioni di configurazione avanzate dei server ESXi per le istanze e i cluster vCenter Server

| Impostazione di configurazione | Se appena distribuita nella V2.2 o successiva  | Se aggiornata dalla V2.1 o precedente |
|:------------- |:------------- |:------------- |
| Numero massimo di volumi | **MaxVolumes** = 256 | Entrambi **/NFS/MaxVolumes** e **/NFS41/MaxVolumes** = 256 |
| Numero massimo di errori heartbeat | **HeartbeatMaxFailures** = 10 | Non impostato |
| Frequenza heartbeat | **HeartbeatFrequency** = 12 | Non impostato |
| Timeout heartbeat | **HeartbeatTimeout** = 5 | Non impostato |
| Profondità massima della coda | **MaxQueueDepth** = 64 | Non impostato |
| Dimensione campione completa della coda | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Soglia completa della coda | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| Dimensione heap TCP/IP | **TcpipHeapSize** = 32 | Non impostato |
| Numero massimo di heap TCP/IP | **TcpipHeapMax** = 1536 | Non impostato |

**Note:**
* L'impostazione **MaxVolumes** è obbligatoria per il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} perché il servizio potrebbe utilizzare più del numero predefinito di montaggi NFS sul server ESXi.
* Il valore **Non impostato** per un'impostazione di configurazione indica che la nuova impostazione non viene applicata automaticamente perché richiede il riavvio dei server ESXi, il che potrebbe causare un'interruzione.

  Si consiglia di modificare le impostazioni di configurazione **Non impostato** nei nuovi valori per garantire coerenza tra tutte le istanze e per consentire il supporto adeguato per l'espansione dell'archiviazione. IBM prevede di eseguire test solo con queste nuove impostazioni per tutte le release di {{site.data.keyword.vmwaresolutions_short}} V2.2 e versioni successive.

  Per ulteriori informazioni, vedi [Increasing the default value that defines the maximum number of NFS mounts on an ESXi host](https://kb.vmware.com/s/article/2239).

## Impostazioni di configurazione di NSX e del gruppo di porte

Esamina la seguente tabella per una panoramica delle impostazioni di configurazione di VMware NSX e del gruppo di porte per le istanze vCenter Server e le differenze tra le release.

Le impostazioni si applicano alle nuove istanze e ai nuovi cluster nelle nuove istanze della V2.2 o successive. Le impostazioni non si applicano ai nuovi cluster nelle istanze esistenti della V2.1 o precedenti o nelle istanze esistenti aggiornate alla V2.2 o successive.

Tabella 4. Impostazioni di configurazione di NSX e del gruppo di porte per le istanze vCenter Server

| Impostazione di configurazione | V2.1 o precedente  | V2.2 o successiva |   
|:------------- |:------------- |:------------- |
| Politica gruppo cluster VXLAN NSX | Failover | Bilanciamento del carico - SRCID |
| VTEP cluster VXLAN NSX | 1 | 2 |
| Pool ID segmento per istanza primaria | 6000-8000 | 6000-7999 |  
| Pool ID segmento per una o più istanze secondarie successive | 6000-8000 | Dall'intervallo finale precedente nella configurazione multisito + 1 all'intervallo finale precedente nella configurazione multisito + 2000 |  
| Gruppo di porte SDDC-DPortGroup-VSAN (se applicabile) | **Active uplinks** impostato su **uplink1** e **Standby uplinks** impostato su **uplink2** | **Active uplinks** impostato su **uplink2** e **Standby uplinks** impostato su **uplink1** |  
| Gruppo di porte SDDC-DPortGroup-Mgmt | **Port binding** impostato su **Ephemeral - no binding** e **Load balancing** impostato su **Route based on originating virtual port** | **Port binding** impostato su **Static binding** e **Load balancing** impostato su **Route based on physical NIC load** |  
| Gruppo di porte SDDC-DPortGroup-External | **Port binding** impostato su **Ephemeral - no binding** | **Port binding** impostato su **Static binding** |

## Impostazioni di configurazione MTU della rete

Il cluster vSphere utilizza due vDS (vSphere Distributed Switch), uno per la connettività di rete pubblica e l'altro per la connettività di rete privata.

Le connessioni alla rete privata sono configurate per utilizzare la MTU (Maximum Transmission Unit) dei frame Jumbo con la dimensione di 9000, che migliora le prestazioni per i trasferimenti di dati di grandi dimensioni come l'archiviazione e VMware vMotion. Questo valore è la MTU massima consentita in VMware e da {{site.data.keyword.cloud_notm}}.

Nella V2.1 o successive, le connessioni alla rete pubblica utilizzano una MTU Ethernet standard di 1500. Questa impostazione di 1500 deve essere mantenuta; eventuali modifiche potrebbero causare la frammentazione dei pacchetti su Internet.

Riesamina la seguente tabella per una panoramica delle impostazioni di configurazione MTU della rete applicate al DVS (Distributed Virtual Switch) pubblico e privato, a seconda che l'istanza vCenter Server sia distribuita nella V2.1 o successive.

Tabella 5. Impostazioni di configurazione MTU per le istanze e i cluster vCenter Server a seconda della versione dell'istanza

| vDS | V2.1 o successive  | V2.0 o precedenti (o aggiornati dalla V2.0 o precedenti) |
|:-------------- |:-------------- |:------------- |
| Switch pubblico  | 1500 (predefinito) | 9000 (Frame Jumbo) |
| Switch privato | 9000 (Frame Jumbo) | 9000 (Frame Jumbo) |

Le impostazioni si applicano alle nuove istanze e ai nuovi cluster delle istanze distribuite nella V2.1 o successive. Le impostazioni si applicano anche ai nuovi cluster tra i {{site.data.keyword.CloudDataCents_notm}} dalle istanze aggiornate alla V2.1 o successive.

Le impostazioni non si applicano ai nuovi cluster nello stesso {{site.data.keyword.CloudDataCent_notm}}, per le istanze esistenti della V2.0 o precedenti o per le istanze esistenti aggiornate alla V2.1 o successive.

Per le istanze che sono state distribuite nella V2.0 o precedenti, si consiglia di aggiornare l'impostazione MTU dello Switch pubblico su 1500.

### Aggiornamento dell'impostazione MTU dello Switch pubblico

Per aggiornare l'impostazione MTU per lo Switch pubblico, completa la seguente procedura nel client web VMware vSphere:
1. Fai clic con il tasto destro del mouse su vDS e seleziona **Modifica impostazioni**.
2. Nella **scheda Proprietà**, seleziona l'opzione **Avanzate**.
3. Assicurati che il valore **MTU massima** sia impostato su 1500.

   **Nota:** quando si modifica la dimensione MTU in un vDS, gli uplink collegati (NIC fisiche) vengono disattivati e riattivati. Di conseguenza, si verifica una breve interruzione per le VM che utilizzano l'uplink. Pertanto, si consiglia si pianificare l'aggiornamento dell'impostazione MTU durante i tempi di inattività pianificati.

### Link correlati

* [Build numbers and versions of VMware ESXi and ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827)
* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [Panoramica di vCenter Server](vc_vcenterserveroverview.html)
* [Pianificazione per le istanze vCenter Server](vc_planning.html)
