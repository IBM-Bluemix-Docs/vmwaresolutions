---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# A propos du stockage pour vCenter Server

Le stockage connecté est une extension de l'offre VMware vCenter Server on {{site.data.keyword.cloud}}. L'architecture de la solution de stockage connecté pour l'offre VMware vCenter Server on {{site.data.keyword.cloud_notm}} détaille les composants de la solution et la configuration de haut niveau de chaque composant de la conception.

Pour plus d'informations sur la conception vCenter Server, voir [Présentation de la solution](../solution/solution_overview.html).

## Principaux avantages du stockage connecté pour vCenter Server

Si le stockage connecté n'est pas un élément prérequis pour les environnements VMware, son utilisation en tant qu'unité de stockage partagé offre de nombreux avantages aux utilisateurs pour des opérations informatiques. L'utilisation d'unités de stockage partagé peut vous aider à obtenir la haute disponibilité, la fonction DRS, à utiliser efficacement la capacité de stockage et à effectuer des opérations de gestion simplifiée en activant les fonctions vSphere décrites dans le tableau ci-après.

Tableau 1. Description des fonctions du stockage connecté pour vCenter Server

| Fonction | Description |
|:------- |:----------- |
| vSphere Distributed Resource Scheduler and Resource Pools | Cette fonction permet une gestion flexible des abstractions des ressources via l'équilibrage de charge et le placement de machine virtuelle. Les pools de ressources peuvent être regroupés en hiérarchies et utilisés pour partitionner de manière hiérarchique les ressources d'UC et de mémoire disponibles. |
| vSphere High Availability | Cette fonction fournit la haute disponibilité pour les machines virtuelles (en les regroupant dans des pools) et pour les hôtes qui résident dans un cluster. Les hôtes présents dans le cluster sont surveillés. Si un incident se produit, les machines virtuelles présentes sur un hôte défaillant sont redémarrées sur d'autres hôtes. |
| vSphere Datastore Clusters | Cette fonction fournit un ensemble de magasins de données avec des ressources partagées et une interface de gestion partagée. |
| vSphere Fault Tolerance | Cette fonction fournit une disponibilité continue pour des machines virtuelles, en éliminant les temps d'arrêt et les interruptions, même en cas d'arrêt anormal de l'hôte. |

### Liens connexes

* [Présentation de la solution](../solution/solution_overview.html)
