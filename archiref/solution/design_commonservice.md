---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Conception des services communs

Les services communs fournissent les services qui sont utilisés par d'autres services de la plateforme de gestion du cloud. Les services communs de la solution comprennent des services d'identité et d'accès, des services de nom de domaine, des services NTP, des services SMTP et des services d'autorité de certification.

## Services d'identité et d'accès

Dans cette conception, Microsoft Active Directory (AD) est utilisé pour la gestion des identités. La conception déploie une ou deux machines virtuelles Windows Active Directory dans le cadre de l'automatisation du déploiement Cloud Foundation et vCenter Server. vCenter sera configuré pour utiliser l'authentification AD.

### Microsoft Active Directory

Par défaut, une seule interface de serveur virtuel est déployée sur l'infrastructure {{site.data.keyword.cloud}}. La conception permet également de déployer deux serveurs Microsoft Active Directory haute disponibilité en tant que machines virtuelles Windows Server dédiées dans le cluster de gestion.

**Remarque** : vous êtes tenu de fournir l'octroi de licence et l'activation Microsoft si vous choisissez cette option.

Active Directory sert à authentifier les accès uniquement pour gérer l'instance VMware et non pour héberger les utilisateurs finaux des charges de travail dans les instances déployées. Le nom de domaine racine de forêt du serveur Active Directory est identique au nom de domaine DNS que vous spécifiez. Ce nom de domaine est indiqué uniquement pour l'instance Cloud Foundation et vCenter Server si plusieurs instances sont liées. Dans le cas d'instances liées, chaque instance contient un serveur Active Directory qui se trouve dans l'anneau de réplique racine de forêt. Les fichiers de la zone DNS sont également répliqués sur les serveurs Active Directory.

### Domaine SSO vSphere

Le domaine SSO (Single Sign On) vSphere est utilisé comme mécanisme d'authentification initial pour une seule instance ou pour plusieurs instances liées. Le domaine SSO est également utilisé pour connecter une instance VMware à plusieurs instances liées au serveur Microsoft Active Directory. La configuration SSO suivante est appliquée :  
* Le domaine SSO `vsphere.local` est déjà utilisé
* Pour les instances VMware liées à une instance existante, le contrôleur PSC est joint au domaine SSO de l'instance existante
* Le nom de site SSO est identique au nom de l'instance

## Services de nom de domaine (DNS)

Dans cette conception, DNS concerne uniquement les composants d'infrastructure et de gestion de cloud.

### VMware vCenter Server

Le déploiement vCenter Server utilise les serveurs Active Directory déployés comme serveurs DNS pour l'instance. Tous les composants déployés (vCenter, PSC, NSX et hôtes ESXi) sont configurés pour pointer vers le serveur Active Directory en tant que serveur DNS par défaut. Vous pouvez personnaliser la configuration de zone DNS si votre configuration n'interfère pas avec la configuration des composants déployés.

Cette conception intègre les services DNS sur les serveurs Active Directory via la configuration suivante :
* Vous pouvez spécifier la structure de domaine. Le nom de domaine peut comporter un nombre quelconque de niveaux (jusqu'au nombre maximum pouvant être géré par les composants vCenter Server). Le niveau le plus bas est le sous-domaine de l'instance.
   * Le nom de domaine DNS que vous spécifiez sera utilisé comme nom de domaine racine de forêt Active Directory. Par exemple, si le nom de domaine DNS est `cloud.ibm.com`, le nom de domaine racine de forêt Active Directory est `cloud.ibm.com`. Ce nom de domaine DNS et ce nom de domaine Active Directory sont identiques dans toutes les instances vCenter Server liées.
   * Vous pouvez également indiquer un nom de sous-domaine pour l'instance. Le nom de sous-domaine doit être unique dans toutes les instances vCenter Server liées.
* Les serveurs DNS Active Directory sont configurés comme faisant autorité pour le domaine et l'espace de sous-domaine DNS.
* Les serveurs DNS Active Directory sont configurés pour pointer vers les serveurs DNS {{site.data.keyword.cloud_notm}} pour toutes les autres zones.
* N'importe quelle instance qui doit être intégrée à une instance cible existante doit utiliser le même nom de domaine que l'instance principale.

### VMware Cloud Foundation

Le déploiement Cloud Foundation utilise l'automatisation VMware Cloud Foundation, laquelle utilise son propre serveur DNS qui réside dans le composant de machine virtuelle SDDC Manager. Par leur conception, les composants Cloud Foundation qui sont gérés par SDDC Manager, y compris vCenter, PSC, NSX et les hôtes ESXi, sont configurés pour utiliser l'adresse IP de machine virtuelle SDDC Manager comme serveur DNS par défaut.

Etant donné que SDDC Manager génère et conserve les noms d'hôte pour les composants qu'il gère, il n'est pas recommandé de fausser avec son fichier de zone DNS directement pour l'ajout et le retrait d'hôtes.

Cette conception intègre les services DNS sur les serveurs Active Directory avec la machine virtuelle SDDC Manager dans la configuration suivante :
* Vous pouvez spécifier la structure de domaine. Le nom de domaine peut comporter un nombre quelconque de niveaux (jusqu'au nombre maximum pouvant être géré par les composants Cloud Foundation).
* Le niveau le plus bas est le sous-domaine pour lequel SDDC Manager fait autorité.
* Le nom de domaine DNS que vous spécifiez sera utilisé comme nom de domaine racine de forêt Active Directory. Par exemple, si le nom de domaine DNS est `cloud.ibm.com`, la racine de forêt de domaine Active Directory est `cloud.ibm.com`. Ce domaine DNS et ce domaine Active Directory sont identiques dans toutes les instances Cloud Foundation liées.
* Vous pouvez également indiquer un nom de sous-domaine pour l'instance. Le nom de sous-domaine doit être unique dans toutes les instances Cloud Foundation liées.  
* La configuration DNS de SDDC Manager est modifiée fin de pointer vers les serveurs Active Directory pour toutes les zones, à l'exception de la zone dont elle est responsable.
* Les serveurs DNS Active Directory sont configurés comme faisant autorité pour l'espace de domaine DNS au-dessus du sous-domaine d'instance SDDC Manager et Cloud Foundation.
* Les serveurs DNS Active Directory sont configurés pour pointer vers l'adresse IP SDDC Manager pour la délégation de sous-domaine de la zone pour laquelle SDDC Manager fait autorité.
* Les serveurs DNS Active Directory sont configurés pour pointer vers les serveurs DNS {{site.data.keyword.cloud_notm}} pour toutes les autres zones.
* Toutes les instances secondaires devant être intégrées à la première instance ou à l'instance cible doivent utiliser la même structure de nom DNS au-dessus du sous-domaine SDDC Manager.

## Services NTP

Cette conception utilise les serveurs NTP de l'infrastructure {{site.data.keyword.cloud_notm}}. Tous les composants déployés sont configurés pour utiliser ces serveurs NTP. Le fait que tous les composants de la conception utilisent le même serveur NTP est essentiel pour que les certificats et l'authentification Active Directory puissent fonctionner correctement.

Figure 1. Services NTP

![Services NTP](commonservice_ntp.svg "Dans cette conception, tous les composants d'une instance utilisent le même serveur NTP de l'infrastructure {{site.data.keyword.cloud_notm}} via le service NTP.")

## Services d'autorité de certification

Par défaut, VMware vSphere utilise les certificats TLS qui sont signés par l'autorité de certification VMware (VMCA), qui se trouve sur le dispositif VMware Platform Services Controller.Ces certificats ne sont pas sécurisés par les terminaux ou les navigateurs de l'utilisateur final. La meilleure pratique en matière de sécurité consiste à remplacer les certificats d'utilisateur par des certificats qui sont signés par un tiers ou une autorité de certification d'entreprise. Les certificats pour la communication entre machines peuvent être conservés en tant que certificats signés par l'autorité de certification VMware (VMCA), toutefois, il est recommandé de suivre les meilleures pratiques pour votre organisation, ce qui implique généralement d'utiliser une autorité de certification d'entreprise identifiée.

Vous pouvez utiliser les serveurs Windows AD dans cette conception pour créer des certificats qui sont signés par l'instance locale. Cependant, vous pouvez également choisir de configurer des services d'autorité de certification si nécessaire.

### Liens connexes

* [Conception d'infrastructure physique](design_physicalinfrastructure.html)
* [Conception d'infrastructure virtuelle](design_virtualinfrastructure.html)
* [Conception de gestion d'infrastructure](design_infrastructuremgmt.html)
