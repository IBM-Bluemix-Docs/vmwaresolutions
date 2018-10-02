---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---
# Présentation de la conception

{{site.data.keyword.vmwaresolutions_full}} fournit l'automatisation du déploiement des composants de technologie VMware dans les {{site.data.keyword.CloudDataCents_notm}} situés dans le monde entier.

## Offres de la solution

Les offres de la solution incluent les produits VMware vSphere suivants dans un cluster automatiquement déployé et configuré :
* VMware Cloud Foundation : vSphere ESXi, Platform Services Controller (PSC), VMware vCenter Server Appliance, SDDC Manager, VMware NSX et VMware vSAN.
* VMware vCenter Server : vSphere ESXi, Platform Services Controller (PSC), vCenter Server Appliance, NSX et éventuellement vSAN.

Dans cette conception, une instance est déployée dans un pod d'un {{site.data.keyword.CloudDataCent_notm}} lors de la commande initiale. Après le déploiement initial, vous pouvez étendre votre environnement virtuel dans d'autres pods au sein du même centre de données ou dans d'autres centres de données.

La conception permet l'extension et la contraction automatisées de la capacité virtuelle dans une instance Cloud Foundation ou vCenter Server.

## Composants de VMware on IBM Cloud

Figure 1. Composants de VMware on {{site.data.keyword.cloud_notm}}
![Composants de VMware on {{site.data.keyword.cloud_notm}}](design_overview.svg "La solution est constituée d'une infrastructure physique, d'une infrastructure virtuelle, d'une gestion d'infrastructure et de services communs.")

### Liens connexes

* [Conception d'infrastructure physique](design_physicalinfrastructure.html)
* [Conception d'infrastructure virtuelle](design_virtualinfrastructure.html)
* [Conception des services communs](design_commonservice.html)
* [Conception de gestion d'infrastructure](design_infrastructuremgmt.html)
