---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Operational considerations for vCenter Server networking

## Backup

### VMware vCenter Server on IBM Cloud backup

As part of {{site.data.keyword.vmwaresolutions_full}}, Veeam backup software is optionally deployed on an {{site.data.keyword.cloud_notm}} virtual server instance (VSI) by using {{site.data.keyword.cloud_notm}} Endurance storage outside the VMware cluster. The purpose of this software is to back up the management components in the solution. [Veeam on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam-on-ibm-cloud-overview) provides details about offering.

The backup of all NSX components is crucial to restore the system to its working state if a failure occurs. It is not sufficient to back up the NSX virtual appliances, the NSX backup function within the NSX manager must be employed for an effective backup. This operation requires that an FTP or SFTP server is specified for the repository of NSX backup data.

The NSX Manager backup contains all of the NSX configuration, including controllers, logical switching and routing entities, security, firewall rules, and everything else that you configure within the NSX Manager user interface or API. The vCenter database and related elements like the virtual switches need to be backed up separately. See [NSX file-based backup](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-backing-up-components#nsx-file-based-backup) for details. The NSX configuration should be backed up along with a [vCenter file-based  backup](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-backing-up-components#vcenter-file-based-backup).

### Backup and disaster recovery for IBM Cloud Private

Backups for an {{site.data.keyword.icpfull_notm}} deployment are crucial to restore the system to its working state if a failure occurs. For a traditional VM backup, there is a sticking point: every {{site.data.keyword.icpfull_notm}} master node runs an *etcd* service, and *etcd* documentation clearly states not to use traditional VM backup to restore it.

For {{site.data.keyword.cloud_notm}} Private at the platform level, you will need to back up the following components.
- **etcd** - etcd is used to store Kubernetes resources and Calico state information.
- **Docker Registry** - This private image registry is used to store container image files.
- **MongoDB** - This database is used by the metering service, Helm repository server, Helm API server, LDAP configuration, tenant (namespace) and team/user/usergroup role configurations.
- **MariaDB** - This database is used by OIDC.
-	**Elasticsearch** - stores the system and application logs.
-	**Prometheus** - stores data for monitoring.
-	**Persistent Storage** - used for management services that use {{site.data.keyword.cloud_notm}} Private or Kubernetes Persistent Volume and storage provider.

You can use the backup or restore technology that is provided by the storage provider. A similar process can be extended into your user’s application as well. For more information, see [How to back up and restore {{site.data.keyword.cloud_notm}} Private blog](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) or  [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/).

### Backup and disaster recovery for CAM

Backups of a CAM deployment are crucial to restore the system to its working state if a failure occurs. The CAM backup requires the customer to back up the following components:
-	**Mongo Database** – Main CAM database.
-	**Maria Database** - Used by CAM Blueprint Designer.
-	**NFS/Gluster File Systems** - CAM data resides in four persistent volumes.

### Backup and DR for IBM Cloud Kubernetes Service

Backup of the etcd database is provided to the customer as part of the managed service, any application data must be backed by the customer however.

## Scalability

### vCenter Server Scalability

After the deployment of the initial hosts, users can scale out the compute capacity from within the {{site.data.keyword.cloud_notm}} for VMware portal.

Scale out of the environment follows one of these paths:
-	Addition of new sites managed by separate vCenter Servers.
-	Addition of new clusters.
-	Addition of new hosts to an existing cluster.

#### Multi-site deployments

VMware on {{site.data.keyword.cloud_notm}} can use the {{site.data.keyword.cloud_notm}} worldwide data center presence and integrated network backbone to allow for various cross geography use cases to be deployed and functioning within a fraction of the time it would take to build such an infrastructure from scratch. Further information can be found at [Multi-site configuration for vCenter Server on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-multi-site-configuration-for-vcenter-server-on-ibm-cloud-instances).

#### Scale out with new cluster

Users can also scale out the compute capacity by creating a new cluster from within the console by ordering the hosts and the new hosts are automatically added to the new cluster. This option creates a separate cluster in the environment and gives users the ability to physically and logically segregate management workloads from application workloads, the ability to segregate workloads based on other characteristics (for example, Microsoft SQL database cluster) and the ability to deploy applications in highly available topologies. For more information, see [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances).

#### Scale out existing cluster

The user can scale out an existing cluster by ordering hosts from within the console and the new hosts are automatically added to the cluster. For more information, see [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-instances) for details. You might need to adjust the HA reservation policy for the cluster based on their reservation requirements.

### IBM Cloud Private and IBM Cloud Kubernetes Service scalability

Based on the available compute capacity at the on-premises or cloud locations, users can scale out the node architecture from the boot node initially deployed. To scale out of the environment:
-	Expand the {{site.data.keyword.icpfull_notm}} worker nodes.
-	Expand and use the {{site.data.keyword.containerlong_notm}} offering.

#### IBM Cloud Private expansion

{{site.data.keyword.icpfull_notm}} worker virtual machine nodes are scaled to expand the compute and application:
- Customer provisions a new virtual machine in the same VXLAN that {{site.data.keyword.icpfull_notm}} is deployed.
- Customers can scale worker nodes by provisioning new virtual machines, then logging in to the boot node and running a command to bring the new nodes into the cluster. See [Adding or removing cluster nodes](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html) for further details.
- Use CAM to automate the provisioning of the VM and running the commands to add it to the {{site.data.keyword.icpfull_notm}} Cluster.

#### IBM Cloud Kubernetes Service expansion

Users can provision an {{site.data.keyword.containerlong_notm}} environment by using the {{site.data.keyword.cloud_notm}} Portal to extend and use a container environment. For more information, see [Hybrid enhancements across {{site.data.keyword.cloud_notm}} Private and {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

Application deployments into {{site.data.keyword.containerlong_notm}} are possible by using the following methods:
-	{{site.data.keyword.containerlong_notm}} connection and services are developed in CAM and published to {{site.data.keyword.icpfull_notm}} catalog.
-	Multi Cloud Manager, a future enhancement to manage {{site.data.keyword.containerlong_notm}} instances.
-	Helm command line.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
