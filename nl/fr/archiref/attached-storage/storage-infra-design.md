---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# Conception d'infrastructure de stockage connecté

{{site.data.keyword.vmwaresolutions_full}} fournit la technologie VMware qui est déployée de façon automatisée dans {{site.data.keyword.CloudDataCents_notm}} partout dans le monde. Dans le portefeuille de solutions {{site.data.keyword.cloud_notm}}, l'offre VMware vCenter Server on {{site.data.keyword.cloud_notm}} de base comprend 10 clusters contenant chacun jusqu'à 59 hôtes vSphere, un contrôleur PSC (Platform Services Controller) et un dispositif vCenter Server Appliance pouvant gérer jusqu'à 400 hôtes et 4 000 machines virtuelles. 

L'architecture qui est présentée ici complète la solution vCenter Server en ajoutant du stockage connecté sous la forme d'une unité de stockage partagé pour l'environnement. L'unité de stockage connecté se situé dans le même {{site.data.keyword.CloudDataCent_notm}} que le déploiement de vCenter Server et comprend un partage NFS (Network File System) ou plusieurs exportations NFS à partir d'{{site.data.keyword.cloud_notm}}.

Le graphique suivant décrit l'architecture globale du stockage connecté sur un déploiement vCenter Server :

Figure 1. Architecture de haut niveau de stockage connecté sur {{site.data.keyword.cloud_notm}}

![Architecture de stockage connecté](../solution/physical_nfs.svg "Architecture de haut niveau de stockage connecté sur IBM Cloud")

## Conception d'infrastructure physique

L'infrastructure physique est constituée de trois composants principaux, notamment le calcul physique, le stockage physique et le réseau physique. Cela inclut le réseau de services {{site.data.keyword.cloud_notm}}, ainsi que le stockage physique utilisé par l'infrastructure.

## Conception de réseau physique

La mise en réseau physique est gérée par {{site.data.keyword.cloud_notm}}. Cette section décrit le réseau physique qui est fourni par {{site.data.keyword.cloud_notm}} lorsqu'il est associé au stockage connecté.

### Présentation du réseau IBM Cloud

Le réseau physique d'{{site.data.keyword.cloud_notm}} est séparé en trois réseaux distincts, un réseau public, un réseau privé et un réseau de gestion. Pour plus d'informations sur le réseau public, le réseau privé et le réseau de gestion, voir [Présentation de la solution](../solution/solution_overview.html).

Pour plus d'informations sur le réseau {{site.data.keyword.cloud_notm}}, voir [The {{site.data.keyword.cloud_notm}} network](https://www.ibm.com/cloud-computing/bluemix/our-network){:new_window}.

Consultez les informations suivantes pour obtenir une description du réseau des services faisant partie du réseau privé.

### Réseau de services privé

{{site.data.keyword.cloud_notm}} contient un réseau de services privé qui fournit des services communs, tels que le stockage par blocs, le stockage de fichiers, le stockage d'objets, les programmes de résolution DNS et les serveurs NTP. Ce réseau privé est distinct du réseau privé du client et il permet aux environnements de se connecter de manière transparente aux services situés dans {{site.data.keyword.cloud_notm}}. Le réseau privé est composé de plusieurs niveaux de sorte que les serveurs et une toute autre infrastructure sont connectés à des commutateurs BCS (Back-end Customer Switch) agrégés. Ces commutateurs agrégés sont connectés à une paire de routeurs distincts, à savoir des routeurs BCR (Back-end Customer Router), pour la mise en réseau L3. Le réseau privé prend également en charge l'utilisation de trames jumbo (MTU 9000) pour des connexions hôte physiques.

### Réseaux locaux virtuels

Pour plus d'informations sur les réseaux virtuels locaux, voir la section _Conception de réseau physique_ dans [Conception d'infrastructure physique](../solution/design_physicalinfrastructure.html).

## Conception de stockage physique

Cette section présente la configuration de l'unité de stockage connecté présente dans {{site.data.keyword.cloud_notm}}. L'unité de stockage connecté complète la solution vCenter Server existante. Par conséquent, les disques connectés localement qui sont internes aux hôtes physiques ne sont pas présentés.

## Performances du stockage connecté

Le stockage Performance et le stockage Endurance sont des solutions de stockage {{site.data.keyword.cloud_notm}} conçues pour prendre en charge des applications à entrées-sorties élevées qui nécessitent des niveaux prévisibles de performances. Ces performances prévisibles sont obtenues au moyen de l'allocation d'IOPS de niveau protocole à des volumes individuels.

Entre 100 et 48 000 IOPS peuvent être mises à disposition avec des tailles de stockage allant de 20 Go à 12 To. Les volumes de stockage Performance et les volumes de stockage Endurance sont disponibles pour le stockage par blocs et pour le stockage de fichiers.

Dans cette conception, la solution vCenter Server offre le stockage Endurance pour le stockage connecté. Par conséquent, vous pouvez sélectionner et connecter (via l'automatisation) des exportations Endurance NFS dont la taille est comprise entre 20 Go et 12 To. {{site.data.keyword.cloud_notm}} permet à 64 hôtes vSphere ESXi au maximum de se connecter à une exportation Endurance NFS.

Endurance est disponible dans trois niveaux de performance d'IOPS pour prendre en charge les divers besoins des applications. Notez qu'après la mise à disposition d'un partage NFS, celui-ci peut être redimensionné ou reconfiguré pour permettre davantage ou moins d'IOPS. 

Pour connaître les options d'IOPS détaillées, voir la section _Paramètres de stockage_ dans la rubrique [Commande d'instances vCenter Server](../../vcenter/vc_orderinginstance.html).

Outre les niveaux de stockage, le stockage {{site.data.keyword.cloud_notm}} Endurance prend en charge un vaste choix de besoins applicatifs, y compris les instantanés et la réplication, ainsi que le chiffrement des données au repos dans les emplacements {{site.data.keyword.CloudDataCent_notm}}.

### Liens connexes

* [Présentation de la solution](../solution/solution_overview.html)
