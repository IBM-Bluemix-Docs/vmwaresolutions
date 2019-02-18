---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Use cases

## Workload migration to IBM Cloud

Acme Skateboards wants to seamlessly extend their on-premises VMware SDDC into a VMware vCenter Server on {{site.data.keyword.cloud}} instance. They need to keep their business up and running and keep their downtime to a minimum. Reconfiguring their applications to run in the cloud isn't an optimal solution.

The VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle enables the creation of seamless connections between {{site.data.keyword.cloud_notm}} and an on-premises VMware virtualized datacenter.

The vCenter Server with Hybridity Bundle offering from {{site.data.keyword.cloud_notm}} enables secure connections between the peer on-premises source site and the {{site.data.keyword.cloud_notm}} target site.

Figure 1. VMware Hybridity services
![VMware Hybrid Cloud Extension Services](vcsiks-hcx.svg)

The vCenter Server with Hybridity Bundle creates a loosely coupled interconnectivity between on-premises and {{site.data.keyword.cloud_notm}} and enables capabilities such as:
- **Simple interconnectivity** – logical network connections are established easily over any physical connection that includes public internet, private VPN, or {{site.data.keyword.cloud_notm}} Direct Link.
- **Layer 2 extension** – on-premises networks that include on-premises subnets and IP addressing are extended into the cloud.
- **Encryption** – network traffic is securely encrypted between the peer sites.
- **Network optimization** – selects the best connection and efficiently floods the connection so that network traffic is moved as fast as possible.
- **Data deduplication** – as much as 50% reduction in network traffic can be achieved.
- **Intelligent routing** – when a workload is moved, proximity routing can change the network path, or gateway, so that network traffic uses the target site gateway and doesn't “hairpin” back to the originating site.
- **Zero downtime migration** – a running virtual machine can be moved to (or back from) the cloud by using vMotion.
- **Scheduled migration** – any number of virtual machines can be replicated to the destination site and then activated on that site at a designated time to replace the systems running on the originating site.
- **Migration of security policies** – if NSX is used on-premises any security policies, firewalls, and so on, are moved along with the workload.

Using this solution Acme Skateboards successfully migrated their on-premises VMware workloads to the {{site.data.keyword.cloud_notm}} meeting their requirements of little to no downtime and no application reconfiguration.

## Hybrid architecture deployment

Acme Skateboards wants to deploy a hybrid architecture on {{site.data.keyword.cloud_notm}} consisting of vCenter Server and {{site.data.keyword.icpfull_notm}}, for their journey to application modernization. Their requirements are to run their databases on virtual machines, the applications and web services in containers, and use a common set of tools for network and security management.

Figure 2. Acme Skateboards hybrid application
![Acme Skateboards hybrid application diagram](vcsiks-acme-app-arch.svg)

{{site.data.keyword.vmwaresolutions_short}} provides automation to deploy VMware technology components in {{site.data.keyword.CloudDataCents_notm}} across the globe. The architecture consists of a single cloud region and supports the ability to extend into more cloud regions that are located in another geography or into another {{site.data.keyword.cloud_notm}} pod within the same data center.

The {{site.data.keyword.icpfull_notm}} and Cloud Automation Manager (CAM) products are manually deployed into your on-premises virtualization platform, enabling cloud management from the on-premises location. Alternatively, {{site.data.keyword.icpfull_notm}} and CAM are offered as a service extension to an existing or new vCenter Server deployment, via automation, enabling cloud management from {{site.data.keyword.cloud_notm}}.

The following diagram represents {{site.data.keyword.icpfull_notm}} running on top of a vCenter Server instance. NSX-V is configured with a dedicated switch/VXLAN, a DLR, and an ESG specifically for the {{site.data.keyword.icpfull_notm}} overlay network, routing is set up through the ESG for access to the underlaying network.

Using the {{site.data.keyword.cloud_notm}} automation, Acme Skateboards can provision a hybrid solution that encompasses VMware on {{site.data.keyword.cloud_notm}} to run their database VMs and {{site.data.keyword.icpfull_notm}} on VMware on {{site.data.keyword.cloud_notm}} to run their apps and front-end web services in containers. NSX gives them a common set of management tools for network and security in the overlay network.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
