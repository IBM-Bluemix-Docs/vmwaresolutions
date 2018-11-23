---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Progettazione dettagliata

## Componenti di servizi comuni
I servizi comuni forniscono i servizi che vengono utilizzati da altri servizi nella piattaforma di gestione cloud. Questo include i servizi di identità e di accesso, i servizi di nome dominio, i servizi NTP.

Figura 1. Servizi comuni ICP

![Servizi comuni ICP](vcsicp-icp-commonservices.svg)

### Servizi di identità e accesso
Come parte dell'automazione VCS, viene utilizzato una Microsoft Active Directory (AD) per la gestione dell'identità. Viene distribuita una sola VSI (Virtual Server Instance) AD. Il vCenter è configurato per utilizzare l'autenticazione MS AD e anche ICP può essere configurato per l'autenticazione LDAP.

###	DNS (Domain Name Services)
La distribuzione VCS utilizza il le VSI Microsoft Active Directory (AD) distribuite come server DNS per l'istanza. Tutti i componenti distribuiti (vCenter, PSC, NSX, host ESXi) sono configurati in modo da puntare a MS AD come proprio server DNS predefinito.

###	Servizi NTP
La distribuzione VCS utilizza i server NTP dell'infrastruttura {{site.data.keyword.cloud}}. Tutti i componenti distribuiti saranno configurati per utilizzare questi server NTP. Per il corretto funzionamento dei certificati e dell'autenticazione MS AD è fondamentale che tutti i componenti all'interno della progettazione utilizzino gli stessi server NTP.

## Rete

### Rete NSX-V

NSX-V è progettata in modo che una sola piattaforma del gestore NSX-V sia collegata ad una sola istanza vCenter Server. Fornisce i servizi di rete alle applicazioni in esecuzione all'interno di un ambiente vSphere.

Utilizzando la rete NSX-V inclusa nella distribuzione VCS, possiamo distribuire ICP in una rete di sovrapposizione VXLAN.

ICP è distribuito con lo stack di rete Calico predefinito per Kubernetes, che fornisce l'isolamento di rete all'interno del tuo cluster.

Figura 2. ICP con rete NSX-V

![ICP con rete NSX-V](vcsicp-nsxv-networking.svg)

For more information, see [Guida di rete di vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

### Rete NSX-T

NSX-T è progettata in modo che una sola piattaforma di rete possa connettersi a qualsiasi tipo di applicazione, basata su macchina virtuale o contenitore, in esecuzione all'interno o all'esterno di un ambiente vSphere.

ICP fornisce un'opzione per sostituire la rete di Calico con un'istanza NSX-T, fornendo una sola ubicazione per la gestione della rete e della sicurezza.

Figura 3. ICP con rete NSX-T

![ICP con rete NSX-T](vcsicp-icp-nsxt-networking.svg)

### Link correlati

* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
