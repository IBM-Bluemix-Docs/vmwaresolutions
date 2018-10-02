---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---

# Mise à l'échelle de la capacité

Après le déploiement initial, vous pouvez ajouter de la capacité de calcul à partir de la console {{site.data.keyword.vmwaresolutions_full}}. La conception prend en charge les parcours d'évolutivité horizontale suivants :
* Ajout de nouveaux sites gérés par des serveurs vCenter distincts
* Ajout de nouveaux clusters
* Ajout de nouveaux hôtes à un cluster existant

## Ajout d'autres sites

{{site.data.keyword.vmwaresolutions_short}} peut exploiter la présence de centres de données {{site.data.keyword.cloud_notm}} partout dans le monde et d'un réseau principal intégré pour déploiement de divers scénarios d'utilisation multi-régions opérationnels en une fraction du temps que prendrait la construction d'une telle infrastructure de toutes pièces.

Dans cette conception, la définition d'un déploiement multisite comprend les éléments suivants ;
* Un déploiement VMware initial ou principal contenant un nouveau nom de domaine racine DNS/AD, sous-domaine, domaine SSO et site SSO à fournir.
* Les sites secondaires uniques ou multiples mis à disposition du domaine SSO des sites principaux requièrent la configuration suivante :
   * Nouveau nom de site SSO
   * Nouveau site/sous-domaine DNS lié à la racine du domaine principal
   * Configuration de la réplication DNS et AD entre les machines virtuelles AD du site principal et du site secondaire
   * Contrôleur PSC déployé et configuré pour la synchronisation avec le contrôleur PSC du site principal
   * Configuration vCenter en mode lien étendu (Enhanced Linked) sur le serveur vCenter du site principal

De plus, le gestionnaire NSX sur les sites secondaires peut être configuré en tant que gestionnaires NSX secondaires pour le gestionnaire NSX sur le site principal.

## Ajout de nouveaux clusters

Vous pouvez également ajouter de la capacité de calcul en créant un nouveau cluster à partir de la console {{site.data.keyword.vmwaresolutions_short}} et en commandant de nouveaux hôtes qui sont ajoutés automatiquement au nouveau cluster.

Cette méthode vous permet de réaliser les opérations suivantes :
* Création d'un cluster distinct supplémentaire dans l'environnement
* Séparation des charges de travail de gestion à partir de charges de travail d'application, de façon physique et logique
* Séparation des charges de travail en fonction d'autres caractéristiques, par exemple, un cluster de base de données Microsoft SQL
* Déploiement d'applications dans des topologies à haute disponibilité

**Remarque** : lorsque le cluster initial est converti en un cluster de gestion uniquement, la migration des charges de travail existantes implique des étapes que l'utilisateur doit réaliser manuellement. Il peut s'agir de réassocier les magasins de données au nouveau cluster ou d'effectuer une migration de stockage. Les adresses IP des charges de travail devront peut-être être modifiées si le nouveau cluster réside dans un autre pod {{site.data.keyword.cloud_notm}} ou si un autre ID VLAN lui est affecté.

## Ajout d'hôtes ESXi dans des clusters existants

Vous pouvez ajouter un cluster existant en commandant des hôtes à partir de la console {{site.data.keyword.vmwaresolutions_short}}.  Les nouveaux hôtes sont ajoutés automatiquement au cluster. Notez que vous devrez peut-être ajuster la règle de réservation haute disponibilité pour le cluster en fonction de vos exigences de réservation.

### Liens connexes

* [Présentation de la solution](solution_overview.html)
* [Présentation de la conception](design_overview.html)
* [Sauvegarde des composants](solution_backingup.html)
