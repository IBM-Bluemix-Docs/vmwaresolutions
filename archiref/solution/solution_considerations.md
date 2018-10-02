---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Remarques relatives au post-déploiement pour votre instance VMware

Les offres {{site.data.keyword.vmwaresolutions_full}}, VMware vCenter Server et VMware Cloud Foundation ne sont pas des services gérés. La configuration, la sécurité, la gestion et la surveillance de tous les composants logiciels vous incombent. Avec les droits d'accès administrateur complets qui vous sont affectés, vous disposez d'un pouvoir et d'une latitude qui requièrent d'importantes compétences techniques, administratives et opérationnelles dans différents domaines. La gestion d'une instance VMware dans {{site.data.keyword.cloud_notm}} requiert la même planification et les mêmes compétences que la planification d'une instance locale. Les technologies définies par les logiciels, telles que VMware NSX et VMware vSAN, simplifient considérablement certains aspects de la gestion d'instances, mais peuvent tout de même nécessiter de nouvelles compétences et de nouveaux outils pour être correctement gérées et utilisées. Combiner la puissance, la vitesse et la fiabilité du déploiement VMware automatisé par {{site.data.keyword.cloud_notm}} avec la planification et les tests opérationnels appropriés garantit une navigation rapide et réussie vers un cloud hybride. 

Consultez les remarques ci-après pour bien comprendre quelles sont vos responsabilités en termes de gestion et d'exécution de l'instance avant et après son déploiement.  

**Remarque :** la liste suivante n'est pas exhaustive. Pour plus d'informations, voir [Services gérés par IBM](../../services/managing_imi.html).

## Accès à un compte IBM Cloud

Pour gérer l'accès à votre compte {{site.data.keyword.cloud_notm}}, autorisez d'autres membres de votre équipe à accéder à votre instance dans la console {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Invitation des utilisateurs à accéder à des services et des ressources](../../vmonic/iamuserinvite.html).

## Limitations

Familiarisez-vous avec les limitations de votre instance répertoriées ci-dessous :

- [Impacts de la modification des artefacts vCenter](../../vcenter/vcenter_chg_impact.html)
- [Remarques et limitations relatives à la mise en réseau](../../vcenter/vc_networkingonvcenterserver.html)
- [Foire aux questions](../../vmonic/faq.html)

## Conception et connectivité du réseau

Procédez comme suit pour gérer les accès à votre réseau {{site.data.keyword.cloud_notm}} et vos composants de gestion VMware et pour planifier votre topologie de réseau {{site.data.keyword.cloud_notm}} :

- Accédez aux noeuds finaux de gestion d'instances à l'aide du [réseau privé virtuel {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/vpn-access) ou de votre [connexion {{site.data.keyword.cloud_notm}} Direct Link](https://www.ibm.com/cloud/direct-link).
- Elaborez une stratégie pour la connectivité au réseau public à partir de votre instance. Vous pouvez utiliser au choix l'exemple de passerelle ESG (Edge Services Gateway) VMware NSX du client, des dispositifs de passerelle, tels que Vyatta et FortiGate, et des serveurs proxy déployés dans le réseau {{site.data.keyword.cloud_notm}} ou sur votre propre réseau accessible via DirectLink.
- Planifiez le déploiement de votre charge de travail sur des VLAN {{site.data.keyword.cloud_notm}} à l'aide des [adresses IP portables {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/subnets/getting-started.html) ou sur des [commutateurs logiques NSX (VXLAN) à l'aide de vos propres adresses IP](../nsx/nsx_overview.html). Sachez que l'utilisation de la mise en réseau définie par logiciel NSX vous offre la plus grande souplesse pour gérer et sécuriser votre réseau de charge de travail dans {{site.data.keyword.cloud_notm}}.
- Utilisez des passerelles NSX ESG, [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance) et l'appairage DirectLink pour planifier la connectivité à des charges de travail (Network Address Translation, Virtual Private Network, routage).
- Si vous implémentez Cross-vCenter NSX, assurez-vous que les plages d'ID de segment local ne se chevauchent pas avant de déployer des charges de travail locales. 

## Planification et renforcement de la sécurité

Il vous incombe de sécuriser, chiffrer et surveiller votre instance VMware et vos charges de travail afin de satisfaire aux normes d'entreprise, du secteur et réglementaires. Procédez comme suit pour assurer une sécurité appropriée :

- Modifiez tous les mots de passe affichés dans la console {{site.data.keyword.vmwaresolutions_short}} et utilisez votre propre système de gestion de mots de passe. Sachez qu'IBM conserve des ID utilisateur distincts qui sont requis pour l'automatisation et le support en continu. 
- Passez en revue les règles sur les mots de passe, liées notamment à la complexité et à la période d'expiration, sur tous les composants. 
- Passez en revue les paramètres de chiffrement sur tous les composants. 
- Planifiez et implémentez les solutions de pare-feu physiques ou virtuelles appropriées, par exemple, un pare-feu DFW (Distributed Firewall) NSX, des passerelles NSX ESG, [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html) et [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance).
- Planifiez et implémentez les solutions de sécurité et d'équilibrage de charge d'application appropriées, par exemple, [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html).
- Planifiez et implémentez les solutions SIEM (gestion des événements et des informations de sécurité) appropriées, par exemple, [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence).
- Planifiez et implémentez le scannage de vulnérabilité approprié. 
- Planifiez et implémentez la gestion des changements, les approbations, les audits et le contrôle d'accès appropriés pour votre instance en utilisant des solutions, telles que [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html).

## Personnalisation

Procédez comme suit pour personnaliser l'installation d'instance VMware de base en fonction de à vos exigences :

- Utilisez votre propre autorité de certification pour générer des certificats pour les composants, tels que vCenter, VMware Platform Services Controller (PSC) et NSX Manager.
- Configurez les services déployés. Par exemple :
  - Pour HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, configurez les paramètres d'intégration AD, de contrôle d'accès, de protocole SMTP (Simple Mail Transfer Protocol), ainsi que les règles de conformité. 
  - Pour Zerto on {{site.data.keyword.cloud_notm}}, planifiez l'adressage IP et le routage des communications Zerto Virtual Replication Appliance (VRA) dans la mesure où le balayage de conversion NAT n'est pas pris en charge. Envisagez d'avoir recours à la tunnellisation ou au redéploiement de vos dispositifs VRA pour l'adressage et le routage appropriés. 
  - Pour les services de sauvegarde, tels que Veeam on {{site.data.keyword.cloud_notm}} et IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}, configurez votre travail de sauvegarde, configurez éventuellement du stockage supplémentaire et configurez des alertes de surveillance. 
  - Pour les services de mise en réseau et de sécurité, tels que F5 on {{site.data.keyword.cloud_notm}} et FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, configurez des interfaces réseau, des certificats, la haute disponibilité ainsi que des règles en fonction de votre topologie de réseau et d'autres exigences. 

## Active Directory

Procédez comme suit pour assurer la configuration et la gestion appropriées de la connexion unique : 

- Configurez la planification des mises à jour et du réamorçage du serveur Active Directory (AD). 
- Si vous avez choisi de déployer des serveurs AD dans le cluster vSphere, indiquez les licences et l'activation Microsoft Windows pour les serveurs afin d'assurer la conformité et la disponibilité. 
- Etablissez une confiance mutuelle entre l'instance et votre serveur AD local. 
- Intégrez NSX VPN, le cas échéant, à SSO AD. 
- Intégrez des hôtes ESXi à SSO AD. 

## Planification de la maintenance 

Procédez comme suit pour assurer une planification appropriée de la maintenance logicielle :

- Configurez VMware Update Manager (VUM) via un proxy pour obtenir des mises à jour VMware. 
- Le cas échéant, configurez vSAN via un proxy pour gérer la base de données HCL (Hardware Compatibility List) de vSAN. 
- Planifiez la maintenance régulière des composants VMware qui ne sont pas pris en charge par VUM. Par exemple, VMware vCenter, PSC et NSX.
- Passez en revue la configuration EVC (Enhanced vMotion Compatibility) de vSphere. Il se peut que votre cluster ne soit pas configuré avec EVC activé si la version en cours de vSphere ne prend pas en charge EVC pour votre niveau matériel. 
- Planifiez la maintenance régulière des services complémentaires, tels que Veeam on {{site.data.keyword.cloud_notm}}, Zerto on {{site.data.keyword.cloud_notm}} et F5 on {{site.data.keyword.cloud_notm}}.

## Surveillance

Prenez soin de planifier et d'implémenter les solutions suivantes pour la surveillance de votre instance et ses composants : 

- Un serveur de journalisation qui inclut l'acheminement ou la collecte de journaux pour tous les composants d'instance, ainsi que la conservation appropriée des journaux. 
- Une infrastructure d'alerte, y compris la configuration du serveur SMTP et de la passerelle SMS (Short Message Service), si besoin. 
- La surveillance proactive d'hôtes, d'unités, de logiciels de gestion et de réseau. 
- La surveillance vSAN, le cas échéant. 
- La surveillance et la planification de capacité. Vous pouvez [ajouter et retirer des clusters](../../vcenter/vc_addingviewingclusters.html) et [ajouter et retirer des hôtes](../../vcenter/vc_addingremovingservers.html) dans votre instance à partir de la console {{site.data.keyword.vmwaresolutions_short}}. 
- La surveillance de votre infrastructure de sauvegarde et de vos tâches de sauvegarde. 

## Disponibilité et continuité des opérations

Votre instance VMware s'exécute sur des serveurs bare metal dans {{site.data.keyword.cloud_notm}}. Procédez comme indiqué ci-après pour être certain de planifier la haute disponibilité et la continuité des opérations de manière adéquate. 

- Passez en revue la configuration de la haute disponibilité vSphere et de vSphere Distributed Resource Scheduler (DRS) par rapport à vos exigences. 
- Passez en revue la configuration du contrôle des E-S de stockage et de réseau par rapport à vos exigences. 
- Configurez l'ordre de démarrage des machines virtuelles au regard de vos exigences. 
- Configurez des pools de ressources, en fonction de vos besoins, pour la gestion et la charge de travail. 
- Planifiez, implémentez et surveillez une solution de sauvegarde à la fois pour les [composants de gestion d'instances](solution_backingup.html) et pour la charge de travail. 
- Planifiez la haute disponibilité de la gestion d'instances, y compris l'éventualité de plusieurs instances, plusieurs clusters, la haute disponibilité de vCenter et la haute disponibilité de PSC. 
- Planifiez la continuité des opérations pour vos charges de travail à l'aide de solutions, telles que la [reprise après incident Zerto](../../services/addingzertodr.html), [Veeam Backup and Replication](../../services/veeam_considerations.html) et [IBM Spectrum Protect Plus](../../services/spp_considerations.html).

## Planification du stockage

En plus de la planification de la capacité, procédez comme indiqué ci-après pour vous assurer que la configuration de stockage répond à vos exigences en matière de performances et de disponibilité. 

- Les performances de stockage dépendent de différents facteurs, y compris la configuration RAID et la segmentation des données du disque, la configuration du réseau, la taille de bloc, les IOPS (opérations d'entrée/sortie par seconde) configurées pour le stockage en réseau NAS, la configuration matérielle de machine virtuelle et la méthode de connexion de stockage, les méthodes de mise en cluster et de réplication et l'utilisation de règles de stockage, telles que le chiffrement, le dédoublonnage et la compression. Prévoyez du temps pour tester et ajuster votre configuration en fonction de vos besoins en termes de performances de stockage. 
- Passez en revue vos règles de stockage
  - RAID-1 fournit des performances plus élevées et des fenêtres de risque d'échec séquentiel (par exemple, une durée de reconstitution plus courte) plus réduites que RAID-5. Cela dit, RAID-5 présente un temps système de stockage inférieur. 
  - RAID-6 assure la protection contre les échecs en double, mais requiert au moins six hôtes alors que RAID-5 n'en nécessite que quatre.
- Pour ajouter davantage de stockage à votre cluster vSAN, vous devez ajouter de nouveaux hôtes au cluster ou ajouter un stockage {{site.data.keyword.cloud_notm}} Endurance NFS à la place. Actuellement, il n'est pas permis d'ajouter des disques aux hôtes existants. 
- Si vous montez davantage de stockage {{site.data.keyword.cloud_notm}} Endurance NFS sur votre cluster, prenez soin de suivre les conseils relatifs à l'architecture et de configurer des routes hôte vers le stockage en utilisant les adresses de groupe de ports `SDDC-DPortGroup-NFS`. Vous devez autoriser ces adresses, au lieu des hôtes proprement dits, vers le stockage. Pour plus d'informations, voir [Gestion d'infrastructure de stockage connecté](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing). Voir aussi la recette developerWorks montrant comment [ajouter davantage de stockage Endurance à votre cluster VMware](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/) en utilisant IBM Spectrum Protect Plus comme exemple. 

### Liens connexes

* [Présentation de la solution](solution_overview.html)
* [Présentation de la conception](design_overview.html)
* [Mise à l'échelle de la capacité](solution_scaling.html)

