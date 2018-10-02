---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Paramètres de stockage

Cette conception prend en charge la connexion de stockage partagé via NFS v3 uniquement. NFS v4 et v4.1 ne sont pas pris en charge. 

**Remarque** : tout le stockage connecté pour cette conception est limité au stockage {{site.data.keyword.cloud_notm}} disponible dans le même {{site.data.keyword.CloudDataCent_notm}} que la solution vCenter Server. De plus, tous les disques virtuels qui sont stockés dans le magasin de données sont par défaut alloués de manière dynamique. 

L'architecture indique que les magasins de données NFS v3 sont connectés à l'aide du même nom DNS à partir du stockage {{site.data.keyword.cloud_notm}} pour la connexion au partage. De plus, le partage NFS est connecté à tous les hôtes dans le cluster vCenter Server et placé dans un cluster de magasins de données pour lequel la fonction Storage DRS est activée.

## vSphere Storage Distributed Resource Scheduler (Storage DRS)

Storage DRS vous permet de gérer les ressources agrégées d'un cluster de magasins de données. Lorsque la fonction Storage DRS est activée, elle fournit des recommandations relatives au placement et à la migration des disques de machine virtuelle afin d'équilibrer l'espace et les ressources d'E-S entre les magasins de données du cluster de magasins de données.

Les fonctions suivantes sont disponibles lorsque la fonction Storage DRS est activée :
* Equilibrage de charge de l'espace entre les magasins de données d'un cluster de magasins de données
* Equilibrage de charge des entrées-sorties entre les magasins de données d'un cluster de magasins de données
* Placement initial des disques virtuels en fonction de la charge de travail de l'espace et des entrées-sorties

Dans cette conception, Storage DRS est entièrement automatisé (valeur **Fully Automated** affectée au paramètre Automation Level). Par conséquent, les fichiers sont migrés automatiquement afin d'optimiser l'utilisation des ressources sur le cluster de données. Dans la mesure où le cluster est entièrement automatisé, toutes les autres options Storage DRS ont pour valeur **Use cluster settings**.

## Paramètres d'exécution de Storage DRS pour NFS v3

L'intensité de Storage DRS est déterminé en spécifiant des seuils relatifs à l'espace qui est utilisé et le temps d'attente des entrées-sorties. Storage DRS collecte des informations d'utilisation de ressource pour les magasins de données d'un cluster de magasins de données. vCenter Server utilise ces informations pour générer des recommandations relatives au placement des disques virtuels sur les magasins de données.

Lorsqu'un faible niveau d'intensité est défini pour un cluster de magasins de données, Storage DRS recommande d'effectuer des migrations Storage vMotion uniquement lorsque cela est nécessaire, par exemple, si la charge des entrées-sorties, l'utilisation de l'espace ou leur déséquilibre est élevé. Lorsqu'un niveau d'intensité élevé est défini pour un cluster de magasins de données, Storage DRS recommande d'effectuer des migrations chaque fois que le cluster de magasins de données peut bénéficier de l'équilibrage de charge de l'espace ou des entrées-sorties.

Les catégories de seuil suivantes sont disponibles dans le cluster de magasins de données :

* Utilisation de l'espace : Storage DRS génère des recommandations ou effectue des migrations lorsque le pourcentage d'utilisation de l'espace sur le magasin de données est supérieur au seuil que vous avez défini dans le client Web vSphere.
* Temps d'attente des entrées-sorties : Storage DRS génère des recommandations ou effectue des migrations lorsque le temps d'attente des entrées-sorties 90ème percentile mesuré sur une journée pour le magasin de données est supérieur au seuil.

Dans cette conception, les paramètres d'exécution de Storage DRS sont activés et les valeurs par défaut respectives des seuils sont conservées. Il est vivement recommandé de modifier ces valeurs en fonction des exigences des entrées-sorties de la charge de travail et de la sensibilité de temps d'attente.

Le tableau suivant présente les paramètres du client Web VMware vSphere :

Tableau 1. Paramètres d'exécution de Storage DRS

| Paramètre       | Valeur  |
|:--------------- |:------ |
| Enable I/O metric for SDRS recommendations | Sélectionné |
| Utilized space | Sélectionné, valeur définie : 80% |
| I/O latency threshold | 15 ms |

Pour plus d'informations sur la configuration de ces paramètres dans le client Web vSphere, voir [Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

## Paramètre Storage I/O Control pour NFS v3

Lorsque le paramètre SIOC (Storage I/O Control) est activé dans l'environnement, il modifie la longueur de la file d'attente de l'unité pour une seule machine virtuelle. Cela permet de réduire la file d'attente de la grappe de stockage de toutes les machines virtuelles afin d'obtenir un partage et un régulateur égaux de la file d'attente de stockage. Le paramètre SIOC est implémenté uniquement si des ressources sont contraintes et que le temps d'attente d'entrée-sortie du stockage est supérieur au seuil défini.

Vous devez définir un seuil pour que la fonction SIOC puisse déterminer quand une unité de stockage est saturée ou contrainte. Le temps d'attente du seuil de surcharge est différent selon les types de stockage. Cette conception recommande et implémente un temps d'attente de seuil de 10 millisecondes.

Vous pouvez également limiter des disques virtuels individuels de machines virtuelles individuelles ou leur accorder des partages différents grâce à la fonction SIOC. La limitation des disques et l'octroi de différents partages vous permettent de faire correspondre et d'aligner l'environnement à la charge de travail avec le nombre d'IOPS de volume de stockage de fichier acquis. Cette limite est définie par le nombre d'IOPS et il est possible de définir une pondération différente ou des partages. 

Les partages de disques virtuels ayant pour valeur **High** (2 000 partages) reçoivent deux fois plus d'entrées-sorties qu'un disque ayant pour valeur **Normal** (1 000 partages) et quatre fois plus qu'un disque ayant pour valeur **Low** (500 partages). La valeur **Normal** est définie par défaut pour toutes les machines virtuelles, par conséquent, vous devez ajuster les valeurs **Normal** pour les machines virtuelles qui l'exigent. 

## Stockage supplémentaire pour NFS v3

Lorsque vous avez besoin d'ajouter du stockage supplémentaire à l'environnement en raison d'un espace insuffisant ou d'un temps d'attente élevé, vous pouvez commander un autre partage NFS à partir de la console. Une fois le partage commandé, connectez l'exportation aux hôtes vSphere ESXi dans le cluster et placez-la dans le cluster de stockage. Le fait de placer le nouveau partage NFS dans le cluster de stockage ajoute efficacement et directement le stockage qui est associé à l'environnement sans vous imposer des migrations de niveau stockage.

## Paramètres de configuration avancée

Cette conception ajoute les paramètres de configuration avancée qui sont recommandés par {{site.data.keyword.cloud_notm}}. Par conséquent, les paramètres suivants sont définis sur chaque hôte vSphere ESXi qui est connecté au partage NFS {{site.data.keyword.cloud_notm}}.

Tableau 2. Paramètres de configuration avancée NFS

| Paramètre       | Valeur  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### Liens connexes

* [Présentation de la solution](../solution/solution_overview.html)
