---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Infrastructure management design

Infrastructure management refers to the components that are managing the VMware infrastructure. This design uses a single external Platform Services Controller (PSC) instance and a single vCenter Server instance:
* The vCenter Server is the centralized platform for managing vSphere environments and is one of the fundamental components in this solution.
* The PSC is used in this solution to provide a set of infrastructure services, which include VMware vCenter Single Sign On, license service, lookup service, and VMware certificate authority.

The PSC instances and vCenter Server instances are separate virtual machines (VMs).

## PSC design

This design deploys a single external PSC as a virtual appliance on a portable subnet on the private VLAN that is associated with the management VMs. Its default gateway is set to the back-end customer router (BCR). The virtual appliance is configured with the specifications in the following table.

These values are set at the time of deployment and cannot be changed.
{:note}

Table 1. Platform Services Controller specifications

| Attribute                    | Specification                  |
|------------------------------|--------------------------------|
| Platform Services Controller | Virtual appliance              |
| Number of vCPUs              | 2                              |
| Memory                       | 4 GB                           |
| Disk                         | 114 GB on local VMFS datastore |
| Disk type                    | Thin provisioned               |

The PSC located in the primary instance is assigned the default SSO domain of `vsphere.local`.

## vCenter Server design

The vCenter Server is also deployed as a virtual appliance. Additionally, the vCenter Server is installed on a portable subnet on the private VLAN that is associated with management VMs. Its default gateway is set to the IP address assigned on the BCR for that particular subnet. The virtual appliance is configured with the specifications in the following table.

Table 2. vCenter Server Appliance specifications

| Attribute                    | Specification                       |
|------------------------------|-------------------------------------|
| vCenter Server               | Virtual appliance                   |
| Appliance installation size  | Medium (up to 400 hosts, 4,000 VMs) |
| Platform Services Controller | External                            |
| Number of vCPUs              | 8                                   |
| Memory                       | 24 GB                               |
| Disk                         | 400 GB on local datastore           |
| Disk type                    | Thin provisioned                    |

### vCenter Server database

The vCenter Server configuration uses a local, embedded PostgreSQL database that is included with the appliance. The embedded database is used to remove any dependencies on external databases and licensing.

### vCenter Server cluster specification

With this design, you can cluster the vSphere ESXi hosts that are provisioned through the solution. However, before clusters can be created a data center object is created that signifies the location of the vSphere ESXi hosts as well as the pod within the data center. A cluster is created after the data center object is created. The cluster is deployed with VMware vSphere High Availability (HA) and VMware vSphere Distributed Resource Scheduler (DRS) enabled.

### vSphere Distributed Resource Scheduler

This design uses vSphere Distributed Resource Scheduling (DRS) in the initial cluster to place VMs and uses DRS in additional clusters to dynamically migrate VMs to achieve balanced clusters. The automation level is set to fully automated so that initial placement and migration recommendations are run automatically by vSphere. Additionally, the migration threshold is set to moderate so that vCenter applies priority 1, 2, 3 recommendations to achieve at least a decent improvement in the load balance of the cluster.

Power management via the **Distributed Power Management** feature is not used in this design.
{:note}

### vSphere High Availability

This design uses vSphere High Availability (HA) in the initial cluster and extra clusters to detect compute failures and recover VMs that run within a cluster. The vSphere HA feature in this design is configured with both the **Host Monitoring** and **Admission Control** options enabled in the cluster. Additionally, the initial cluster reserves one node’s resources as spare capacity for the admission control policy.

You are responsible to adjust the admission control policy when the cluster is later expanded or contracted.
{:note}

By default, the **VM restart priority** option is set to medium and the **Host isolation response** option is disabled. Additionally, **VM monitoring** is disabled and the **Datastore Heartbeating** feature is configured to include any of the cluster data stores. This approach uses the NAS data stores if they are present.

## Automation

The cornerstone to these solutions is automation. Automation brings the following benefits:
* Reduces the complexity of deployment.
* Drastically reduces the deployment time.
* Ensures that the VMware instance is deployed in a consistent manner.

{{site.data.keyword.IBM}} CloudBuilder, IBM CloudDriver, and SDDC Manager VMs work together to start a new VMware instance and perform lifecycle management functions.

### IBM CloudBuilder and IBM CloudDriver

The IBM CloudBuilder and IBM CloudDriver virtual server instance (VSI) are IBM-developed components that you cannot access.
* The IBM CloudBuilder is a temporary {{site.data.keyword.cloud_notm}} virtual server instance (VSI) that bootstraps the deployment, configuration, and validation of the solution components within the provisioned bare metal ESXi hosts.
* The IBM CloudDriver VSI is deployed for instance creation and then periodically, as needed, with the latest {{site.data.keyword.cloud_notm}} for VMware code for operations such as deploying more nodes, clusters, or services. The IBM CloudDriver communicates with the {{site.data.keyword.vmwaresolutions_short}} console through a VMware NSX Edge Services Gateway, which is deployed exclusively for instance management purpose, and acts as an agent to maintain the instance. The IBM CloudDriver is responsible for ongoing actions such as the addition of new bare metal hosts to the cluster and the deployment of add-on services into the instance. For Cloud Foundation instances, the IBM CloudDriver communicates with the VMware SDDC Manager VM to perform functions such as host addition and patching.

It is possible for the user to delete or damage the VMs described in the following sections. When a VM is removed, shut down, or it becomes inoperable, the following Cloud Foundation or vCenter Server operations on the {{site.data.keyword.vmwaresolutions_short}} console are interrupted:
* Viewing the instance or host status
* Adding or removing clusters
* Adding or removing ESXi hosts
* Adding or removing services
* Patching

### SDDC Manager

For Cloud Foundation instances, the SDDC Manager VM is a component that is developed and maintained by VMware. It remains as part of the instance during its entire lifecycle. It is responsible for the following lifecycle functions of instances:
* Management of VMware components: vCenter Server, Platform Services Controller (PSC), vSAN, and NSX, including IP address allocation and host name resolution.
* Expansion and retraction of ESXi hosts within the cluster, which includes any affected services, such as NSX VTEP, vSAN, and resource pools.

For vCenter Server instances, these activities are performed by the IBM CloudDriver as there is no SDDC Manager.

### Automation flow

The following procedure describes the order of events when a VMware instance is ordered via the {{site.data.keyword.vmwaresolutions_short}} console:
1.  Ordering VLANs and subnets for networking from {{site.data.keyword.cloud_notm}}.
2.  Ordering {{site.data.keyword.baremetal_short}} with vSphere Hypervisor installed.
3.  If applicable, ordering Microsoft Windows Virtual Server Instance (VSI) to serve as Active Directory domain controller.
4.  Validation of the networking and deployed hardware.
5.  If applicable, initial configuration of single node vSAN.
6.  If applicable, deployment and configuration of two Microsoft Windows virtual machines to serve as Active Directory domain controllers.
7.  Deployment and configuration of vCenter, PSC, and NSX.
8.  Clustering of remaining ESXi nodes, expansion of vSAN if applicable, and configuration of NSX components (VTEP).
9.  Deploying VMware Cloud Foundation SDDC Manager VM, if applicable, and the IBM CloudDriver VSI.
10.  Validating the installation and configuration of the environment.
11. Removal of the CloudBuilder VSI.
12. Deployment of optional services, such as backup server and storage.

### Related links

* [Physical infrastructure design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-physical-infrastructure-design)
* [Virtual infrastructure design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-virtual-infrastructure-design)
* [Common services design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-common-services-design)
