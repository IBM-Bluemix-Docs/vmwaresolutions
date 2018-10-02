---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-13"

---

# Conception de gestion d'infrastructure

La gestion d'infrastructure fait référence aux composants qui gèrent l'infrastructure VMware. Cette conception utilise une seule instance PSC (Platform Services Controller) externe et une seule instance vCenter Server :
* vCenter Server est la plateforme centralisée dédiée à la gestion des environnements vSphere ; il s'agit de l'un des composants fondamentaux de cette solution.
* Le contrôleur PSC est optimisé dans cette solution pour fournir un ensemble de services d'infrastructure, y compris VMware vCenter Single Sign On, un service de licence, un service de consultation et l'autorité de certification VMware.

Les instances PSC et les instances vCenter Server sont des machines virtuelles distinctes.

## Conception de PSC

Cette conception déploie une seule instance PSC externe en tant que dispositif virtuel sur un sous-réseau portable, sur le VLAN privé qui est associé aux machines virtuelles de gestion. Le routeur BCR (Back-end Customer Router) lui sert de passerelle par défaut. Le dispositif virtuel est configuré avec les spécifications décrites dans le tableau suivant.

**Remarque** : ces valeurs sont définies au moment du déploiement et elles ne peuvent pas être modifiées.

Tableau 1. Spécifications PSC (Platform Services Controller)

| Attribut                    | Spécification                  |
|------------------------------|--------------------------------|
| Contrôleur PSC (Platform Services Controller) | Dispositif virtuel              |
| Nombre d'unités centrales virtuelles              | 2                              |
| Mémoire                       | 4 Go                           |
| Disque                         | 114 Go sur le magasin de données VMFS local |
| Type de disque                    | A allocation dynamique               |

Le domaine SSO par défaut `vsphere.local` est affecté au contrôleur PSC situé dans l'instance principale.

## Conception de vCenter Server

vCenter Server est également déployé en tant que dispositif virtuel. En outre, vCenter Server est installé sur un sous-réseau portable, sur le VLAN privé qui est associé aux machines virtuelles de gestion. L'adresse IP affectée sur le routeur BCR pour ce sous-réseau spécifique lui sert de passerelle par défaut. Le dispositif virtuel est configuré avec les spécifications décrites dans le tableau suivant.

Tableau 2. Spécifications vCenter Server Appliance

| Attribut                    | Spécification                       |
|------------------------------|-------------------------------------|
| vCenter Server               | Dispositif virtuel                   |
| Taille d'installation du dispositif  | Moyenne (jusqu'à 400 hôtes, 4 000 machines virtuelles) |
| Contrôleur PSC (Platform Services Controller) | Externe                            |
| Nombre d'unités centrales virtuelles              | 8                                   |
| Mémoire                       | 24 Go                               |
| Disque                         | 400 Go sur magasin de données local           |
| Type de disque                    | A allocation dynamique                    |

### Base de données vCenter Server

La configuration de vCenter Server utilise une base de données PostgreSQL imbriquée locale qui est incluse avec le dispositif. La base de données imbriquée est utilisée pour retirer les dépendances sur les bases de données externes et l'octroi de licence.

### Spécification de cluster vCenter Server

Cette conception vous permet de regrouper en cluster les hôtes vSphere ESXi qui sont mis à disposition via la solution. Toutefois, avant les clusters, un objet de centre de données est créé afin de signifier l'emplacement des hôtes vSphere ESXi, ainsi que celui du pod dans le centre de données. Un cluster est créé une fois l'objet de centre de données créé. L cluster est déployé avec la haute disponibilité VMware vSphere et le planificateur DRS (Distributed Resource Scheduler) VMware vSphere activés.

### Planificateur DRS (Distributed Resource Scheduler) vSphere

Cette conception utilise la planification DRS (Distributed Resource Scheduling) vSphere dans le cluster initial pour placer les machines virtuelles et dans les autres clusters pour faire migrer dynamiquement des machines virtuelles afin d'obtenir des clusters équilibrés. La valeur "Fully Automated" est affectée au paramètre Automation Level, par conséquent, les recommandations de placement initial et de migration sont automatiquement exécutées par vSphere. En outre, le seuil de migration défini est modéré, ainsi, vCenter appliquera les recommandations de priorité 1, 2, 3 pour obtenir au moins une amélioration décente de l'équilibrage de charge du cluster.

**Remarque :** la gestion de l'alimentation via la fonction **Distributed Power Management** n'est pas utilisée dans cette conception.

### Haute disponibilité vSphere

Cette conception utilise la haute disponibilité vSphere dans le cluster initial et les autres clusters pour détecter les pannes de traitement et récupérer les machines virtuelles qui s'exécutent dans un cluster. La haute disponibilité vSphere dans cette conception est configurée avec les options de **surveillance hôte** et de **contrôle d'admission** activées dans le cluster. De plus, le cluster initial réserve les ressources d'un noeud comme capacité de secours pour la règle de contrôle d'admission.

**Remarque** : vous êtes chargé d'ajuster la règle de contrôle d'admission lorsque le cluster est développé ou réduit par la suite.

Par défaut, une valeur moyenne est affectée à l'option de **priorité de redémarrage des machines virtuelles** et l'option de **réponse d'isolement hôte** est désactivée. De plus, l'option de **surveillance des machines virtuelles** est désactivée et la fonction de **pulsation de magasin de données** est configurée pour inclure n'importe lequel des magasins de données de cluster. Cette approche utilise les magasins de données NAS éventuellement présents.

## Automatisation

L'automatisation est l'élément central de ces solutions. Elle offre les avantages suivants :
* Elle réduit la complexité du déploiement
* Elle réduit le temps de déploiement
* Elle assure un déploiement cohérent de l'instance VMware

Les machines virtuelles {{site.data.keyword.IBM}} CloudBuilder, IBM CloudDriver et SDDC Manager fonctionnent conjointement pour fournir une nouvelle instance VMware et effectuer des fonctions de gestion de cycle de vie.

### IBM CloudBuilder et IBM CloudDriver

Les instances de serveur virtuel IBM CloudBuilder et IBM CloudDriver sont des composants développés par IBM auxquels vous ne pouvez pas accéder.
* IBM CloudBuilder est une instance de serveur virtuel {{site.data.keyword.cloud_notm}} temporaire qui amorce le déploiement, la configuration et la validation des composants de solution dans les hôtes ESXi bare metal mis à disposition.
* L'instance de serveur virtuel IBM CloudDriver est déployée pour la création d'instance, puis régulièrement, selon les besoins, avec le dernier code {{site.data.keyword.cloud_notm}} pour VMware pour les opérations, telles que le déploiement de noeuds, de clusters ou de services supplémentaires. IBM CloudDriver communique avec la console {{site.data.keyword.vmwaresolutions_short}} via une passerelle VMware NSX ESG (Edge Services Gateway) déployée exclusivement à des fins de gestion d'instance, et agit en tant qu'agent chargé de gérer l'instance. IBM CloudDriver est responsable des actions en cours, telles que l'ajout de nouveaux hôtes bare metal au cluster et le déploiement de services complémentaires dans l'instance. Pour les instances Cloud Foundation, IBM CloudDriver communique avec la machine virtuelle VMware SDDC Manager pour effectuer des fonctions, telles que l'ajout d'hôtes et l'application de modules de correction à des hôtes.

L'utilisateur peut supprimer ou endommager les machines virtuelles décrites dans les sections ci-dessous. Lorsqu'une machine virtuelle est retirée, arrêtée ou lorsqu'elle devient inutilisable, les opérations Cloud Foundation ou vCenter Server suivantes sur la console {{site.data.keyword.vmwaresolutions_short}} sont interrompues :
* Affichage de l'état de l'hôte ou de l'instance
* Ajout ou retrait de clusters
* Ajout ou retrait d'hôtes ESXi
* Ajout ou retrait de services
* Application de correctif

### SDDC Manager

Pour les instances Cloud Foundation, la machine virtuelle SDDC Manager est un composant qui est développé et géré par VMware. Il continue de faire partie de l'instance tout au long de son cycle de vie. Il est responsable des fonctions de cycle de vie suivantes pour les instances :
* Gestion des composants VMware : vCenter Server, Platform Services Controller (PSC), vSAN et NSX, y compris l'allocation d'adresse IP et la résolution de nom d'hôte
* Développement et rétraction d'hôtes ESXi dans le cluster, y compris les services concernés, tels que NSX VTEP, vSAN et les pools de ressources

Pour les instances vCenter Server, ces activités sont effectuées par IBM CloudDriver en l'absence de gestionnaire SDDC Manager.

### Flux d'automatisation

La procédure suivante décrit l'ordre dans lequel les événements se déroulent lorsqu'une instance VMware est commandée via la console {{site.data.keyword.vmwaresolutions_short}} :
1.  Commande de VLAN et de sous-réseaux pour la mise en réseau à partir d'{{site.data.keyword.cloud_notm}}
2.  Commande de serveurs bare metal avec vSphere Hypervisor installé
3.  Le cas échéant, commande de l'instance de serveur virtuel Microsoft Windows qui servira de contrôleur de domaine Active Directory
4.  Validation du matériel mis en réseau et déployé
5.  Le cas échéant, configuration initiale d'un réseau de stockage virtuel de noeud unique
6.  Le cas échéant, déploiement et configuration de deux machines virtuelles Microsoft Windows qui serviront de contrôleurs de domaine Active Directory
7.  Déploiement et configuration de vCenter, PSC et NSX
8.  Regroupement en cluster des autres noeuds ESXi, développement de vSAN, le cas échéant, et configuration des composants NSX (VTEP)
9.  Déploiement de machine virtuelle DDC Manager VMware Cloud Foundation, le cas échéant, et de l'instance de serveur virtuel IBM CloudDriver
10.  Validation de l'installation et de la configuration de l'environnement
11. Retrait de l'instance de serveur virtuel CloudBuilder
12. Déploiement de services facultatifs, tels que le serveur de sauvegarde et le stockage

### Liens connexes

* [Conception d'infrastructure physique](design_physicalinfrastructure.html)
* [Conception d'infrastructure virtuelle](design_virtualinfrastructure.html)
* [Conception des services communs](design_commonservice.html)
