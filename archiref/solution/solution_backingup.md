---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Sauvegarde des composants

La configuration, la gestion et la surveillance de tous les composants logiciels, notamment la sauvegarde et la disponibilité de votre infrastructure de gestion et de vos charges de travail, vous incombent.

Dans le cadre de la solution, vous pouvez éventuellement déployer les services complémentaires {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}}. Veeam et IBM Spectrum Protect Plus peuvent vous aider à répondre aux exigences de sauvegarde relatives à vos composants de gestion.

Ces services complémentaires sont déployés en même temps que le stockage {{site.data.keyword.cloud_notm}} Endurance. Ils vous aident à sauvegarder vos charges de travail et les composants de gestion. Les rubriques de [présentation de l'architecture IBM Spectrum Protect Plus](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} et de [présentation de l'architecture Veeam](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window} fournissent des commentaires utiles en matière de planification et de dimensionnement de déploiement. Vous pouvez également demander des [services gérés](https://console.bluemix.net/infrastructure/vmware-solutions/console/gettingstarted/veeam/vcs/managed) pour votre déploiement Veeam.

Différents composants de solution requièrent différentes stratégies de sauvegarde. Certains composants sont protégés à l'aide d'une sauvegarde par image et d'autres composants sont protégés à l'aide d'une sauvegarde de niveau fichier pour leur configuration et leurs données.

## Serveur de fichiers pour une sauvegarde de niveau fichier

Certains composants, tels que VMware vCenter Server, Platform Services Controller (PSC) et VMware NSX, nécessitent que leur configuration soit sauvegardée dans un serveur de fichiers.

Pour héberger ces sauvegardes, déployez un serveur de fichiers Linux dans votre cluster en procédant comme suit :

1. Commandez un sous-réseau portable privé depuis l'infrastructure {{site.data.keyword.cloud_notm}} et implantez-le sur le même réseau local virtuel que vos composants système. Il s'agit du réseau local virtuel privé sur lequel résident les adresses IP de gestion de vos hôtes.
2. Téléchargez une image de système d’exploitation sur votre magasin de données de gestion VMware, par exemple, [Ubuntu Server 18.04 LTS](http://mirrors.service.softlayer.com/ubuntu-releases/ubuntu-server/bionic/daily-live/current/){:new_window}, depuis le miroir privé d'{{site.data.keyword.cloud_notm}}.
3. Déployez cette machine virtuelle dans votre cluster sur le groupe de ports de gestion à l'aide d'une adresse IP portable privée commandée précédemment. Vérifiez que la machine virtuelle est configurée pour pointer vers vos serveurs AD/DNS et ajoutez éventuellement la machine virtuelle au serveur DNS de votre sous-domaine.
4. Créez un ID utilisateur de sauvegarde autre que root sur ce serveur et assurez-vous que tous les services nécessaires sont configurés et démarrés pour les transferts de fichiers. Par exemple FTP ou SSH.
5. Assurez-vous que cette machine virtuelle est incluse dans votre tâche de sauvegarde de gestion Veeam ou IBM Spectrum Protect Plus. 

## Sauvegarde de niveau fichier vCenter

VMware vCenter Server et PSC fournissent une[interface utilisateur de gestion de dispositif et une API permettant d'exporter la base de données et la configuration dans un serveur de fichiers](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window} à l'aide de divers protocoles. Vous trouverez dans VMware un exemple montrant comment configurer cette opération [pour qu'elle s'exécute régulièrement en tant que travail cron](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window} directement sur le dispositif vCenter Server Appliance et le contrôleur PSC.

Vous devez sauvegarder le dispositif vCenter Server Appliance et le contrôleur PSC séparément à l'aide de cette technique. Familiarisez-vous avec cette technique et planifiez les aspects et les limitations documentés par VMware. En outre, planifiez une rotation et une expiration régulières des sauvegardes de fichiers sur votre serveur de fichiers. Notez que VMware exige que l'emplacement de sauvegarde soit un dossier vide, par conséquent, vous devez planifier votre rotation ou automatisation de sauvegarde de manière à laisser l'emplacement vacant pour chaque tâche de sauvegarde successive.

## Sauvegarde de niveau fichier NSX

Il est essentiel de sauvegarder correctement tous les composants NSX afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. La conception exige que vous configuriez la sauvegarde NSX via la fonction de sauvegarde de NSX Manager. Pour cela, vous pouvez [configurer NSX Manager de sorte qu'il effectue régulièrement des sauvegardes](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window} sur votre serveur de fichiers. Assurez-vous que votre serveur de fichiers ou ses données sont correctement sauvegardés et assurez la rotation des anciennes sauvegardes NSX.

## Sauvegarde par image des machines virtuelles de gestion

Après avoir déployé votre instance et le service de sauvegarde IBM Spectrum Protect Plus ou Veeam, configurez une tâche de sauvegarde pour vos machines virtuelles de gestion. Prévoyez de sauvegarder les machines virtuelles suivantes avec au moins 7 jours de sauvegardes quotidiennes :

* VMware SDDC Manager, si présent
* Serveurs Active Directory, si présents
* Serveur de sauvegarde de fichier

Prévoyez d'allouer un nombre suffisant de licences Veeam ou IBM Spectrum Protect Plus pour la sauvegarde de ces machines virtuelles et prévoyez au moins 2 To de stockage de sauvegarde pour les machines virtuelles.

## Services complémentaires

Si vous déployez des composants de solution complémentaires dans votre instance, vous devez également planifier la sauvegarde de ces composants dans le cadre de votre stratégie de sauvegarde de gestion :

* Réplication virtuelle Zerto : le système ZVM (Zerto Virtual Manager) est déployé en tant qu'instance de serveur virtuel {{site.data.keyword.cloud_notm}} et sa sauvegarde n'est pas prise en charge par Veeam ou IBM Spectrum Protect Plus. Si votre stratégie de reprise après incident nécessite de restaurer le système ZVM sans effectuer un basculement de site, vous devez utiliser votre solution de sauvegarde Windows préférée pour sauvegarder et restaurer le système ZVM.
* F5 BIG-IP : F5 recommande la [sauvegarde de niveau fichier de la configuration BIG-IP](https://support.f5.com/csp/article/K13132){:new_window}, que vous pouvez diriger vers votre serveur de fichiers.
* FortiGate Security Appliance ou machine virtuelle : Fortinet recommande la [sauvegarde de niveau fichier de la configuration FortiGate](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}, que vous pouvez diriger vers votre serveur de fichiers.
* HyTrust Cloud Control et Data Control : HyTrust prend en charge la sauvegarde par image et la sauvegarde de niveau fichier des dispositifs de serveur HyTrust. Pour plus d'informations, voir les guides d'administration HyTrust.
* VMware HCX : l'interface de gestion de dispositif HCX vous permet de créer et télécharger une sauvegarde de niveau fichier de la configuration HCX Manager qui est semblable à celle du dispositif vCenter Server Appliance.

## Autres remarques

Si vous choisissez de déployer votre serveur AD/DNS en tant qu'instance de serveur virtuel {{site.data.keyword.cloud_notm}}, vous ne pouvez pas le sauvegarder à l'aide de Veeam ou IBM Spectrum Protect Plus. Dans ce cas, utilisez votre solution de sauvegarde Windows préférée pour les opérations de sauvegarde et de restauration ou envisagez de déployer votre instance à l'aide de machines virtuelles AD/DNS dans votre cluster VMware, lesquelles peuvent être sauvegardées par Veeam ou IBM Spectrum Protect Plus.

A partir de VMware vCenter 6.5u2, VMware prend en charge la sauvegarde de la base de données vCenter Postgres à l'aide de sauvegardes par image, au moyen de scripts de suspension et de reprise intégrés pour la base de données durant la fenêtre de sauvegarde afin de garantir l'intégrité de la base de données. Si vous mettez à niveau votre instance VMware vers vCenter 6.5u2, vous pouvez choisir d'utiliser Veeam ou IBM Spectrum Protect Plus pour sauvegarder votre serveur vCenter Server et votre contrôleur PSC au lieu d'utiliser des sauvegardes de niveau fichier. Dans ce cas, vous devez utiliser la fonction de mise au repos de Veeam ou d'IBM Spectrum Protect Plus pour assurer l'intégrité des bases de données.

## Restauration depuis une sauvegarde

Vous devez tenir compte de plusieurs remarques spécifiques lorsque vous restaurez vos sauvegardes de gestion :

* Pour vCenter et le contrôleur PSC, VMware fournit un programme d'installation qui peut déployer un nouveau dispositif virtuel et restaurer la configuration à partir d'une sauvegarde.
* Lorsque vous restaurez un dispositif à partir d'une sauvegarde, le programme d'installation détecte le type de dispositif (vCenter Server ou contrôleur PSC) en fonction des informations de sauvegarde que vous indiquez.
* Etant donné que vous effectuez un déploiement directement sur l'un de vos hôtes, il se peut que vous ne puissiez pas effectuer ce déploiement sur un commutateur ou un groupe de ports distribué. Vous devrez peut-être créer un ensemble commutateur/groupe de ports standard temporaire en vue du déploiement des dispositifs restaurés, puis faire migrer temporairement l'une de vos cartes d'interface réseau de machine virtuelle (VMNIC) vers ce commutateur pour fournir la connectivité réseau nécessaire à vos machines virtuelles. Après le déploiement, vous pouvez faire migrer les machines virtuelles vers le groupe de ports distribué et renvoyer la carte d'interface réseau de machine virtuelle (VMNIC) au commutateur virtuel distribué (dvSwitch).
* Pour NSX, vous devrez peut-être redéployer votre gestionnaire NSX et vos contrôleurs NSX avant de restaurer la configuration à partir d'une sauvegarde.
* Prenez soin de vous familiariser avec les remarques et les limitations propres à VMware pour les opérations de sauvegarde et de restauration vCenter.

## Récapitulatif

Grâce à une planification appropriée, vous avez l'assurance que votre instance VMware puisse supporter la perte de ses composants de gestion et être restaurée avec succès. Pour votre infrastructure de gestion et pour vos charges de travail, et de façon régulière, prenez soin de vérifier que vos tâches de sauvegarde aboutissent, de contrôler la disponibilité de vos données de sauvegarde et de tester votre plan de sauvegarde et de restauration.

### Liens connexes

* [Présentation de la solution](solution_overview.html)
* [Présentation de la conception](design_overview.html)
* [Mise à l'échelle de la capacité](solution_scaling.html)
