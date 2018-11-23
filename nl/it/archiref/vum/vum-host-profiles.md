---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

#	Profili host

vCenter ha una funzione denominata Profili host. Questa funzione crea un profilo che cattura una configurazione dell'host di riferimento preconfigurata e convalidata e aiuta un amministratore di sistema a gestire le configurazioni host in un cluster. I profili host forniscono un meccanismo automatizzato e gestito centralmente per la configurazione dell'host e la conformità della configurazione. I profili host consentono di considerare la configurazione come un oggetto gestito, che contiene un catalogo di parametri da configurare, come rete, archiviazione, sicurezza e altri parametri a livello di host. Questi profili host possono essere applicati a singoli host, a un cluster o a tutti gli host e i cluster associati a un profilo host.

Poiché più host VMware vCenter Server on {{site.data.keyword.cloud}} vSphere ESXi vengono distribuiti dall'automazione IC4VS che ha distribuito il cluster iniziale, ci sarà meno deviazione di configurazione rispetto ai metodi manuali di aggiunta degli host. Tuttavia, le azioni dell'amministratore di sistema, al di fuori dell'automazione, possono rendere diversa la configurazione degli host. Ad esempio, è stato aggiunto più spazio di archiviazione NFS o sono state aggiunte altre VLAN. Pertanto, l'utilizzo dei profili host per convalidare la configurazione di un nuovo host mediante il controllo della conformità di questo host rispetto a un host esistente è un caso di utilizzo valido di questo strumento all'interno di {{site.data.keyword.cloud_notm}}.

Per aggiungere altri host al tuo cluster vCenter Server, vedi [Espansione e contrazione della capacità per le istanze vCenter Server](../../vcenter/vc_addingremovingservers.html).

Tieni presente che:
*	Per le istanze distribuite o aggiornate alla V2.1 o superiore, i cluster e i server ESXi appena distribuiti vengono corretti con i recenti aggiornamenti ESXi da VMware, ma non necessariamente con gli aggiornamenti più recenti.
*	Sei responsabile di tutti gli altri aggiornamenti ai componenti VMware, inclusa la garanzia che i cluster e i server ESXi appena distribuiti dispongano di tutti gli aggiornamenti più recenti necessari.

Consigliamo che dopo l'aggiunta di un nuovo host nel cluster, esso venga messo in modalità di manutenzione in modo che possa essere riesaminato per verificare la deviazione di conformità e corretto prima di ospitare qualsiasi carico di lavoro.

Per verificare la conformità è necessaria la seguente sequenza di operazioni:
1.	Creare un profilo host da un host esistente.
2.	Collegare il nuovo host al profilo host.
3.	Verificare la conformità del nuovo host con il profilo host.
4.	Riesaminare gli errori di conformità ed effettuare la correzione.

##	Creazione di un profilo host da un host esistente

1.	Dalla Home del client web vSphere, fai clic su **Policies and Profiles**.
2.	Fai clic su **Host Profiles** e vai alla vista dei profili host.
3.	Fai clic sull'**icona Extract Profile from a Host**.
4.	Seleziona un host esistente che fungerà da host di riferimento e fai clic su **Next**.
5.	Immetti il nome e una descrizione per il nuovo profilo e fai clic su **Next**.
6.	Rivedi le informazioni di riepilogo per il nuovo profilo e fai clic su **Finish**.
7.	Il nuovo profilo viene visualizzato nell'elenco dei profili.

##	Collegamento del nuovo host al profilo host

1.	Dal **Profile List** nella vista principale Host Profiles, seleziona il profilo host precedentemente creato per applicarlo al nuovo host.
2.	Fai clic sull'**icona Attach/Detach a host profile to hosts and clusters**.
3.	Seleziona il nuovo host dall'elenco espanso e fai clic su **Attach**.
4.	Il nuovo host viene aggiunto all'elenco Attached Entities.
5.	Fai clic su **Next** e quindi su **Finish**.

##	Verifica della conformità del nuovo host con il profilo host

1.	Passa al profilo host che è stato precedentemente completato.
2.	Fai clic sull'**icona Check Host Profile Compliance**.
3.	Nella **scheda Objects**, lo stato di conformità viene aggiornato come _Compliant, Unknown o _Non-compliant_. Uno stato non conforme indica che è stata rilevata un'incongruenza specifica tra il profilo e il nuovo host.

##	Riesame degli errori di conformità e correzione

1.	Per visualizzare ulteriori dettagli sugli errori di conformità, seleziona **Host Profile** dalla scheda **Objects** utilizzata nella verifica di conformità.
2.	Per visualizzare dettagli specifici su quali parametri differiscono tra l'host che non ha rispettato la conformità e il profilo host, fai clic sulla **scheda Monitor** e seleziona la **vista Compliance**.
3.	Espandi la gerarchia degli oggetti e seleziona l'host in errore.
4.	I parametri che differiscono vengono visualizzati nella finestra Compliance, sotto la gerarchia.
5.	Esamina i parametri e comprendi il motivo per cui il nuovo host può variare dall'host di riferimento. Per i parametri in cui la conformità non è accettabile, ad esempio quando la deviazione di configurazione è stata provocata dall'azione dell'amministratore di sistema, correggi prima di spostare il nuovo host dalla modalità di manutenzione.

### Link correlati

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demo)
