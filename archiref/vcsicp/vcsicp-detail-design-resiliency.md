---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Backup, disaster recovery, and scalability

## Backup and DR

### VMware vCenter Server on IBM Cloud backup

As part of {{site.data.keyword.vmwaresolutions_full}}, Veeam backup software is optionally deployed on an {{site.data.keyword.cloud_notm}} virtual server instance (VSI) that uses {{site.data.keyword.cloud_notm}} Endurance Storage outside the VMware cluster. The purpose of this software is to back up the management components in this solution.

### NSX backup

Proper backup of all NSX components is crucial to restore the system to its working state if failure occurs. It's not sufficient to back up the NSX virtual machines (VMs). Instead, the NSX backup function within the NSX Manager must be employed for a proper backup. An FTP or SFTP server must be specified for the repository of NSX backup data.
The NSX Manager backup contains all of the NSX configuration, including controllers, logical switching and routing entities, security, firewall rules, and anything else you configure within the NSX Manager user interface or API. The vCenter database and related elements, such as, the virtual switches must be backed up separately. The NSX configuration must be backed up along with a vCenter backup.

### Backup and DR for IBM Cloud Private

Backups for an {{site.data.keyword.icpfull_notm}} deployment are crucial to restore the system to its working state if failure occurs. In addition to a traditional VM backup, every {{site.data.keyword.icpfull_notm}} master node runs etcd. The etcd documentation clearly states not to use traditional VM backup to restore it.

For {{site.data.keyword.icpfull_notm}} at the platform level, you need to back up these components:
- **Etcd** is used to store Kubernetes resources and Calico state information.
- **Docker Registry** private image registry that is used to store container image files in an image repository.
- **MongoDB** database that is used by the metering service, Helm repository server, Helm API server, LDAP configuration, Tenant (namespace), and team/user/usergroup role configurations.
- **MariaDB** database that is used by OIDC.
- **Elasticsearch** stores the system and application logs.
- **Prometheus** stores data for monitoring.
- **Persistent storage** used for management services that use {{site.data.keyword.icpfull_notm}} or Kubernetes Persistent Volume and storage provider. You can use the backup or restore technology that is provided by the storage provider. A similar process can be extended into your user’s application as well.

### Backup and DR for CAM

Backup for a CAM deployment is crucial to restore the system to its working state if failure occurs. The CAM backup requires the customer to back up the following components:
- **Mongo database** is the main CAM database.
- **Maria database** is the database that is used by CAM Blueprint Designer.
- **NFS/GlusterFS** is where CAM data resides in four persistent volumes.

### Backup and DR for IBM Cloud Kubernetes Service

Backups of the etcd database are provided to the customer as part of the managed service, any application data must be backed by yourself.

## Scalability

### VCS scalability

After the deployment of the initial hosts, the user can scale out the compute capacity from within the {{site.data.keyword.cloud_notm}} for VMware portal.

This scale out of the environment follows one of three paths:
- Addition of new sites managed by separate vCenter Servers.
- Addition of new clusters.
- Addition of new hosts to an existing cluster.

#### Multi site deployments

VMware on {{site.data.keyword.cloud_notm}} can use IBM Cloud’s world–wide data center presence and integrated network backbone to allow for various cross–geography use cases to be deployed and functioning within a fraction of the time it would take to build such an infrastructure from scratch.

#### Scale out with new cluster

The user can scale out the compute capacity by creating a new cluster from within the console, ordering the hosts, and the new hosts are automatically added to the new cluster. This option creates a separate cluster in the environment and gives users the ability to physically and logically segregate management workloads from application workloads, the ability to segregate workloads based on other characteristics (for example, Microsoft SQL database cluster), and the ability to deploy applications in highly available topologies.

#### Scale out existing cluster

The user can scale out an existing cluster by ordering hosts from within the console and the new hosts are automatically added to the cluster. Users might need to adjust the HA reservation policy for the cluster based on their reservation requirements.

### IBM Cloud Private scalability

Based on the available compute capacity at the on-premises or cloud locations, the user can scale out the node architecture from the boot node initially deployed.

The scale out of the environment follows:
- Expand the {{site.data.keyword.icpfull_notm}} worker nodes.
- Expand and use the {{site.data.keyword.containerlong_notm}} offering.

#### IBM Cloud Private expansion

The {{site.data.keyword.icpfull_notm}} worker's VM nodes are scaled to expand the compute or application:
- Customer provisions a new VM, in the same VXLAN that {{site.data.keyword.icpfull_notm}} is deployed.
- Customers can scale worker nodes, by provisioning new VM, then logging in to the boot node and running a command to bring the new nodes into the cluster.
- Use CAM to automate the provisioning of the VM and running the commands to add to the {{site.data.keyword.icpfull_notm}} Cluster.

###  IBM Cloud Kubernetes Service expansion

Users can provision an {{site.data.keyword.containerlong_notm}} environment via the {{site.data.keyword.cloud_notm}} Portal to extend or use a container environment.

Use the folloiwng for application deployments into {{site.data.keyword.containerlong_notm}}:
- {{site.data.keyword.containerlong_notm}} connection or services are developed in CAM and published to {{site.data.keyword.icpfull_notm}} catalog.
- Multi-Cloud Manager future enhancement to manage {{site.data.keyword.containerlong_notm}} instances
- Helm command line interface.
- Use Multizone clusters to increase high availability.

### Related links

* [Adding or removing cluster nodes](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Adding worker nodes by resizing an existing worker pool](/docs/containers?topic=containers-clusters)
* [How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [{{site.data.keyword.icpfull_notm}} backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
