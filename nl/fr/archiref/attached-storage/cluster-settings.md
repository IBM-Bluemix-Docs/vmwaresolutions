---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# Paramètres de cluster

Avant l'ajout du stockage connecté, la solution vCenter Server n'activait pas de fonctions avancées, telles que vSphere Distributed Resource Scheduler (DRS) et vSphere High Availability (HA). Avec l'ajout de l'unité de stockage connecté NFS, ces fonctions sont activées sur le cluster avec les paramètres répertoriés dans les sections ci-dessous.

## vSphere Distributed Resource Scheduler

Deux fonctions principales sont activées en même temps que la fonction vSphere DRS sur un cluster, il s'agit de l'équilibrage de charge et de la gestion de l'alimentation.

### Equilibrage de charge

Avec l'équilibrage de charge, la distribution et l'utilisation des ressources d'unité centrale et de mémoire pour tous les hôtes et toutes les machines virtuelles du cluster sont surveillées en permanence. La fonction DRS compare ces métriques à une utilisation de ressource idéale en fonction des attributs des pools de ressources et des machines virtuelles du cluster, de la demande en cours et de la cible de déséquilibre. Ensuite, elle effectue (ou recommande d'effectuer) des migrations de machine virtuelle en conséquence.

Lorsqu'une machine virtuelle est mise sous tension dans le cluster pour la première fois, la fonction DRS tente de maintenir un équilibrage de charge adéquat en plaçant la machine virtuelle sur un hôte approprié ou en effectuant une recommandation. Les paramètres de placement ou de recommandation sont définis dans la section DRS Automation des paramètres du cluster.

Dans cette conception, DRS est entièrement automatisé (valeur "Fully Automated" affectée au paramètre Automation Level), ainsi, lorsque des machines virtuelles sont mises sous tension, elles sont automatiquement placées sur des hôtes ayant une capacité suffisante. Les machines virtuelles sont également migrées automatiquement depuis un hôte vers un autre afin d'équilibrer la charge sur le cluster. De plus, le seuil de migration du cluster DRS défini est à mi-chemin entre modéré et intense de sorte que les recommandations de priorité 1, priorité 2 et priorité 3 soient appliquées. Cela signifie que vCenter Server apporte au moins de bonnes améliorations à l'équilibrage de charge du cluster.

Le tableau suivant présente les paramètres du cluster vSphere DRS dans le client Web VMware vSphere :

Tableau 1. Paramètres d'automatisation DRS pour le cluster vSphere DRS

| Paramètre             | Valeur  |
|:------------------- |:------ |
| Turn ON vSphere DRS | Sélectionné |
| Automation Level | Fully Automated |
| Migration Threshold | Apply priority 1, priority 2, and priority 3 recommendations |
| Enable individual machine automation levels | Sélectionné, valeur définie : 15 ms |

Pour plus d'informations sur la configuration de ces paramètres dans le client Web vSphere, voir [Set a Custom Automation Level for a Virtual Machine in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

Outre le niveau d'automatisation et le seuil de migration du cluster, cette conception active l'automatisation des machines virtuelles de manière à vous permettre de définir des substitutions pour les machines virtuelles individuelles. Cela permet un contrôle granulaire plus précis des machines virtuelles et vous donne la possibilité de définir des priorités pour l'équilibrage de charge des machines virtuelles.

### Gestion de l'alimentation

Lorsque la fonction VMware Distributed Power Management est activée, DRS compare la capacité de niveau cluster et de niveau hôte aux demandes des machines virtuelles du cluster, y compris la demande historique récente. Elle place (ou recommande de placer) des hôtes en mode d'alimentation de secours si une capacité excédentaire suffisante est trouvée ou de mettre des hôtes sous tension si de la capacité est nécessaire. En fonction des recommandations d'état d'alimentation d'hôte obtenues, il peut également s'avérer nécessaire de faire migrer des machines virtuelles vers et depuis les hôtes.
Dans cette conception, la gestion de l'alimentation est désactivée car il n'y a aucun avantage d'ordre opérationnel ou financier à mettre sous tension puis hors tension les hôtes présents dans le cluster.

## vSphere High Availability

vSphere fournit la haute disponibilité pour les machines virtuelles en regroupant dans un cluster ces dernières ainsi que les hôtes sur lesquels elles résident. Les hôtes présents dans le cluster sont surveillés et, si un incident se produit, les machines virtuelles présentes sur un hôte défaillant sont redémarrées sur d'autres hôtes.
Dans cette conception, vSphere High Availability est activé avec la surveillance d'hôte et la surveillance de machine virtuelle sur le cluster.

### Surveillance d'hôte

La surveillance d'hôte permet à des hôtes présents dans le cluster d'échanger des signaux de présence de réseau et permet à vSphere HA de réagir lorsqu'il détecte des incidents. Cette fonction est activée dans cette conception.

### Surveillance de machine virtuelle

La fonction de surveillance de machine virtuelle utilise les informations de pulsation capturées par les outils VMware comme un proxy pour la disponibilité du système d'exploitation invité. Cela permet à vSphere HA de réinitialiser ou redémarrer automatiquement des machines virtuelles individuelles ayant perdu leur capacité à activer un signal de présence. Cette conception active la surveillance de machine virtuelle et la surveillance d'application.

#### Conditions d'incident et réponses des machines virtuelles

Les conditions d'incident définissent la manière dont les machines virtuelles échouent et la réponse renvoyée pour chaque incident. Dans cette conception, le paramètre VM Restart Priority a pour valeur Medium ; il est vivement recommandé de vérifier cette valeur et d'ajuster les paramètres en conséquence de sorte que la priorité de redémarrage corresponde à l'importance de la charge de travail. De plus, le paramètre Response for Host Isolation a pour valeur "Power off and restart VMs" de sorte que les machines virtuelles ne soient pas affectées par un hôte isolé du cluster. Les autres valeurs de ce paramètre sont les valeurs par défaut.

Le tableau suivant présente les paramètres du cluster vSphere HA dans le client Web VMware vSphere :

Tableau 2. Conditions d'incident et paramètres de réponse des machines virtuelles pour le cluster vSphere HA

| Paramètre             | Valeur  |
|:------------------- |:------ |
| VM Restart Priority | Medium |
| Response for Host Isolation | Power off and restart VMs |
| Response for Datastore with Permanent Device Loss (PDL) | Désactivé |
| Response for Datastore with All Paths Down (APD) | Désactivé |
| Response for APD recovery after APD timeout | Désactivé |
| VM monitoring sensitivity | Custom |
| Failure interval | 50 s |
| Minimum uptime | 90 s |
| Maximum per-VM resets | 10 |
| Maximum resets time window | Within 1 hrs |

Pour plus d'informations sur la configuration de ces paramètres dans le client Web vSphere, voir [Configure Virtual Machine Responses](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Contrôle d'admission

vCenter Server utilise le contrôle d'admission pour s'assurer qu'il y a suffisamment de ressources disponibles dans un cluster pour fournir la protection par basculement et faire en sorte que les réservations de ressource de machine virtuelle soient respectées. Dans cette conception, la capacité de basculement est réservé en spécifiant un pourcentage des ressources de cluster. La capacité de basculement définie correspond à 25 % de l'unité centrale et à 25 % de la mémoire.

#### Fonction des signaux de présence de magasin de données

vSphere HA utilise la fonction des signaux de présence de magasin de données pour faire la distinction entre les hôtes qui ont échoué et ceux qui résident sur une partition de réseau. La fonction des signaux de présence de magasin de données permet à vSphere HA de surveiller des hôtes lorsqu'une partition de réseau de gestion survient et de continuer à répondre aux incidents qui se produisent. Dans cette conception, le paramètre Heartbeat Datastore Selection Policy a pour valeur "Automatically select datastores accessible from the host".

### Liens connexes

* [Présentation de la solution](../solution/solution_overview.html)
