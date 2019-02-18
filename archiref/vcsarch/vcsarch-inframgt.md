---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Infrastructure management

Infrastructure management refers to the vSphere components that are
managing the VMware infrastructure. The vCenter server component is the
centralized platform for managing vSphere environments and is one of the
fundamental components in this solution. In addition to the vCenter
server, the Platform Services Controller (PSC) is used in this
solution to private a set of infrastructure services that include VMware
vCenter Single Sign On, license service, lookup service, and VMware
certificate authority. This design uses a Platform Services Controller
function that is integrated into an instance of vCenter server. The
Platform Services Controller and vCenter server are housed within the
same virtual machine (VM).

Figure 1. Infrastructure management
![Infrastructure management](VCSv4RAdiagrams-RA-InfraMgmt.svg)

## Platform Services Controller design

The platform services controller within any vCenter Server instance is
assigned the default SSO domain of vsphere.local.

## vCenter Server design

The vCenter Server is installed on a portable subnet on the private VLAN
associated with management VMs. Its default gateway is set
to the IP address assigned on the BCR for that particular subnet. The
virtual appliance is configured with the specification that is listed in Table
1.

Table 1. vCenter Server Appliance specifications

 Attribute | Specification
--|---|--
**vCenter Server** | Virtual appliance
**Appliance installation size** | Large (up to 1000 hosts, 10,000 VMs)
**Platform Services Controller** | integrated
**Number of vCPUs** | 16
**Memory** | 32 GB
**Disk** | 990 GB on local datastore (Large disk deployment)
**Disk type** | Thin provisioned


#### vCenter Server database

This vCenter Server configuration uses a local, embedded PostgreSQL
database that is included with the appliance. The embedded database is
used to remove any dependencies on external databases and licensing.
vCenter Server cluster specification This design uses clusters that
comprise vSphere ESXi hosts provisioned as part of the solution. However, before clusters can be created, a data center object is created that
signifies the location of the vSphere ESXi hosts and the pod
within the data center. After the data center object is created, the
cluster is created. The cluster is deployed with VMware vSphere High
Availability (HA) and VMware vSphere Distributed Resource Scheduler
(DRS) enabled.

##### vSphere distributed resource scheduler

This design uses vSphere Distributed Resource Scheduling (DRS) in
the initial cluster and within the additional compute clusters to
initially place and dynamically migrate VMs to achieve
balanced clusters. The automation level is set to fully automated so initial placement and migration recommendations are run
automatically by vSphere.

Power management through the Distributed
power management feature is not used in this design. Additionally, the
migration threshold is set to moderate so that vCenter applies
priority 1, 2, and 3 recommendations to achieve at least a decent
improvement in the cluster’s load balance.
{:note}

#### vSphere High Availability

This design uses vSphere HA in the initial cluster and within the
additional compute clusters to detect compute failures and recover
VMs running within a cluster. The vSphere HA feature in
this design is configured with both host monitoring and admission
control that is enabled within the cluster. Additionally, the initial cluster
reserve's one node’s resources as spare capacity for the admission
control policy.

You must adjust
the admission control policy if the cluster is expanded or
contracted later. By default, the VM restart priority is set to medium and the
host isolation response is set to “leave powered on.” VM
monitoring is disabled and the datastore heart beating feature is
configured to include any of the cluster data stores. This approach
uses the NAS data stores if they are present.
{:note}

#### Enhanced vMotion Compatibility

To simplify vMotion compatibility across cluster nodes with potentially
differing CPU capabilities, Enhanced vMotion Compatibility (EVC) mode is enabled at a “Skylake” level to
ensure vMotion compatibility across cluster nodes when newer processors
arrive within {{site.data.keyword.cloud}} inventory and allows for cluster expansion in the
future if Skylake processor servers aren't in inventory.

## IBM CloudDriver

Cornerstone to these solutions is automation. Automation
reduces the complexity of deployment, drastically reduces deployment
time, and ensures the VMware instance is deployed in a consistent manner.
Cloud Builder is an ephemeral {{site.data.keyword.cloud_notm}} VM virtual server instance (VSI) which
works to bring up a new VMware instance and perform lifecycle management
functions. It is deployed when overall vCenter Server instance
management is required and is destroyed when the process is complete.
Cloud Driver can be configured to communicate back to the {{site.data.keyword.vmwaresolutions_short}} (IC4V) management infrastructure over public or optionally,
over a private network connection through {{site.data.keyword.cloud_notm}} object storage as the
message queue. Cloud Driver is an IBM developed component, is not user accessible, and has the following attributes and function:

- Deployment and configuration of the vCenter Server instance within the
user account.
- Add and remove hosts from the vCenter Server clusters.
- Add and remove clusters from vCenter Server instances.
- Add and remove add on services or function to vCenter Server
instances.

## Automation flow

The following describes the order of events when you use the {{site.data.keyword.vmwaresolutions_short}} console to order a VMware instance:
1. Ordering VLANs and subnets for networking from {{site.data.keyword.cloud_notm}}.
2. Ordering {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} with vSphere Hypervisor
installed.
3. Ordering of Microsoft Windows VSI to serve
as the Active Directory domain controller.
4. Deployment of the Cloud Driver VSI.
5. Validation of the networking and deployed hardware.
6. If applicable, the initial configuration of the single node vSAN.
7. Deployment and configuration of vCenter, PSC, and NSX.
8. Clustering of remaining ESXi nodes, expansion of vSAN if applicable,
and configuration of NSX components (VTEP).
9. Validating the installation and configuration of the environment.
10. Deployment of optional services, such as backup server and storage.
11. Removal of the Cloud Driver VSI.

## IDs and passwords

IC4V management infrastructure stores all vCenter Server contained IDs
and passwords encrypted within the {{site.data.keyword.cloud_notm}} management plane. Any
change to these passwords by the user can disrupt the automation
capabilities within vCenter Server.

You can provide changed passwords in the IC4V solutions portal so that the automation can process
functions uninterrupted. The solutions portal optionally allows for
verification of the entered passwords.

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity
Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
