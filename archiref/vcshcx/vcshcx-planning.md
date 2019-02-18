---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Pre-deployment planning

Much of the time that is spent in deploying HCX is in the pre-deployment stage.
While it is typical for information systems migration projects to take
many months to years, HCX allows for migrations and network
connectivity to the cloud to begin immediately after deployment. Since
the deployment of HCX for an enterprise-level customer typically
involves security, network, storage, and vSphere infrastructure teams, it
makes sense to involve these teams in the POC if possible. Effective
project management and early inclusion of stake holders, is critical to
ensure the speed of deployment and operation of HCX is realized.

## Avoiding analysis paralysis
Many of the hurdles and time that is taken in migration of a virtual machine (VM) or group of VMs
are there because of the need to modify parts of the application
environment, the design of those changes and the scheduling of the
downtime that is needed to make those changes. After these changes are made, the
migration becomes difficult to back out of, further adding to analysis
paralysis. Trying to capture all aspects of the migration, coordinating across teams, and changing key stake holders over in the
time it takes to finalize the plan can delay or force the project forward.

HCX allows for cross vSphere instance migration of a VM or group of VMs
that represent a partial or complete composite application, without any
modifications to the application. Because of this, backing out of a
migration means moving the VMs back or restretching the
networks. This negates the need for a large part of migration planning
and allows for some parallelism in the planning process. After
selecting the applications to move and creating a high-level network
design, the applications can begin migration with
minimal configuration on the cloud instance while the final network
connectivity and design is worked out.

## Stretched networks
The network stretch components of the HCX fleet are very stable. At
one particular customer with greater than 20 VLANs that are stretched into the
{{site.data.keyword.cloud}} across 1 Gbps WAN shared with other traffic and HCX migration
tunnels, there are no application issues attributed to the network.
The network links are up for greater than 6 months in this way.
More stretched networks were added and removed without issue.
Picking an {{site.data.keyword.CloudDataCent_notm}} in close proximity (< 6ms latency for this
particular customer) also plays into network stability of stretched
networking. Leaving the stretched networks up long term, should not be a
negative factor in your design given you have enough bandwidth and low
enough latency for your applications.


## Migration lifecycle
The following sections describe the phases within a typical HCX
migration lifecycle, denoting where work streams can be done in
parallel.

## vSphere inventory

- Use an application such as [RVTOOLS](https://www.robware.net/rvtools/)
to dump the inventory of the source vCenter(s) into spreadsheet form.
- Coarse-grained assessment of VMs within an application to be migrated.
Coarse grained implies understanding the VMs that participate in an
application, without delving into the details.
- If you plan to migrate many VMs and network bandwidth is limited
between the source and cloud sites, further group VMs by VLAN or VXLAN
if NSX is employed at the source. This allows for a cascading HCX
migration plan where groups of VMs by VLAN are migrated and the L2
networks they reside upon are stretched only until the point the VLANs
are evacuated. This means that the initial group of related L2 stretched
networks can only be unstretched when the cloud side network design
is finalized and deployed. Unstretching implies swinging the
particular VXLAN traffic to now route through the cloud instance
NSX infrastructure.


## 	Baseline network configuration

Create a hardened perimeter network within the cloud side vSphere
instance. This usually consists of an NSX DLR or Edge appliance. If you use HCX Proximity Routing, there is no need
to create any firewall rules or uplink topology as it can
be completed later or concurrently without effecting the stretched L2
traffic.

## 	Network extension

Extending the network merely means to take the existing VLAN or VXLAN
from the source vSphere environment, represented by a virtual
distributed switch port group (vDS), and extending it to an NSX VXLAN on
the cloud side of HCX.

## Pre-flight tests
Pre-flight tests involve performing an HCX migration with both the
vMotion and bulk migration function in order to establish a baseline
transfer rate.

## Migration of non-production apps
At this point, migration of VMs begins with the planned waves of
less critical VMs. Develoment, test, and so on, use internet connectivity for
migration and stretched L2 traffic.


## 	Cloud network design and implementation begins
While migrations continue, cloud side network designs are finalized
and implemented within the cloud side vSphere instance.


## More network connectivity considerations
While migrations continue, private WAN network connectivity is
ordered as it typically takes a few weeks to months to be established
with the cloud provider. After private network connectivity is
completed, HCX can be configured to use both, the dedicated private
network link and the internet for migration and stretched L2 traffic.

## Physical servers
When the goal is data center migration into the cloud, any physical
servers that interact with the VMs being migrated can be assessed for
migration into the {{site.data.keyword.cloud_notm}} as either a VM (P2V), bare metal or remain
at the source. If the physical server is to remain at the source, and
HCX will only be used during migration until a dedicated network is
established, it is important to understand if it resides on any network
that is stretched into the cloud with HCX. In this scenario, HCX is
allowing not only the VMs, but the entire subnet to migrated into the
cloud. To remove HCX at the end of the migration, the subnet cannot
exist in the source and destination if connection between physical
devices and the migrated VMs is to be maintained. This implies that any
physical devices left behind at the source site that exist on stretched
L2 networks, must be migrated to another network subnet that would be
capable of being routed to the cloud side. The exception to this is if
some other stretched L2 technology is employed, such as NSX L2 VPN, to
replace HCX stretched L2 endpoints.


## Migrate production  and complex applications
VMs with shared multi-writer VMDKs such as Oracle RAC or MS Exchange /
SQL clusters or VMs with raw device mappings are examples of VMs that
need extra consideration before migration.

## Network Swing
Network Swing occurs after the evacuation of the VMs on source side
networks is complete and the network design / implementation is
completed on the cloud side. Configuring HCX to un-stretch the networks
related to the completed VMs within migration waves, allows the migrated
VMs to route network traffic using the cloud side NSX
infrastructure.

## Client platforms supported
For network extension, only port groups with a vSphere virtual
distributed switch (vDS) are supported. This also implies that stand-alone ESXi hosts are not supported as you can only have a vDS when ESXi
hosts are managed by vCenter.
- vSphere 5.1 (command line only for vCenter 5.1 through API)
- vSphere 5.5 (web client UI supported on vCenter 5.5u3 and above)
- vSphere 6.0
- vSphere 6.5 (vDS must be at a 6.0 level)

## Cloud platforms supported
HCX Cloud side is provisioned by {{site.data.keyword.cloud_notm}} automation.

## Connectivity options

### Standard HCX connectivity
As deployed by the {{site.data.keyword.vmwaresolutions_short}} automation, HCX cloud side
installation is configured to connect to across the public internet by
default.

### Optional connectivity
Connection across the {{site.data.keyword.cloud_notm}} private network is selectable at the
time of ordering.

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
