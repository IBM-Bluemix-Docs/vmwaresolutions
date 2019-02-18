---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Architecture overview

The {{site.data.keyword.vmwaresolutions_full}} offerings provide automation to deploy VMware technology components in {{site.data.keyword.CloudDataCents_notm}} across the globe.
The architecture consists of a single cloud region and supports the ability to extend into more cloud regions that are located in another geography or into another {{site.data.keyword.cloud_notm}} pod within the same data center.

You can manually deploy the {{site.data.keyword.cloud_notm}} Private and Cloud Automation Manager (CAM) products into your on-premises virtualization platform, enabling cloud management from on-premises locations. Alternatively, {{site.data.keyword.icpfull_notm}} and CAM are offered as service extensions to an existing or new VMware vCenter Server on {{site.data.keyword.cloud_notm}} deployment, through automation, enabling cloud management from {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} Private is an application platform for developing and managing on-premises, containerized applications. {{site.data.keyword.cloud_notm}} Private is an integrated environment for managing containers that includes the container orchestrator Kubernetes, a private image repository, a management console, and monitoring frameworks.

IBM Multi-Cluster Manager (MCM) provides user visibility, application-centric management (policy, deployments, health, operations), and policy-based compliance across clouds and clusters. With MCM, you have control of your Kubernetes clusters. MCM helps you ensure that your clusters are secure, they operate efficiently, and they deliver a service management platform that runs on {{site.data.keyword.cloud_notm}} Private, which empowers developers and administrators to meet business demands.

Use Cloud Automation Manager Service Composer to display hybrid cloud services in the {{site.data.keyword.cloud_notm}} Private catalog.

## IBM Cloud side cloud management platform

The following diagram is an example of an {{site.data.keyword.icpfull_notm}} and CAM deployment with the {{site.data.keyword.cloud_notm}} infrastructure, with connections to the on-premises vCenter and {{site.data.keyword.containerlong_notm}} deployed on {{site.data.keyword.cloud_notm}}. Users can deploy virtual machines (VMs) on-premises and VMs into a vCenter Server instance, and containers to the {{site.data.keyword.icpfull_notm}} and {{site.data.keyword.containerlong_notm}} cluster.

Figure 1. Cloud management from cloud side

![On cloud - cloud management](vcsicp-oncloud-cloudmgt.svg)

In the diagram, CAM logically creates cloud connections to the vCenters, cloud providers, {{site.data.keyword.icpfull_notm}}, and {{site.data.keyword.containerlong_notm}} environments. {{site.data.keyword.icpfull_notm}} Clusters must be deployed to each data center cloud environment, with MCM providing the mechanism to connect the {{site.data.keyword.icpfull_notm}} clusters into a single management view.

You can deploy {{site.data.keyword.icpfull_notm}} with NSX-V or NSX-T components. {{site.data.keyword.icpfull_notm}} with NSX-V, enables the {{site.data.keyword.icpfull_notm}} VMs to run on the VXLAN network and use Kubernetes Calico internal networking.

{{site.data.keyword.icpfull_notm}} with NSX-T, allowing users to control and configure networking, subnet, policies from central UI (NSX-T Manager). See [vCenter Server networking guide](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcenter-server-networking-introduction) for the differences between NSX-V and NSX-T.

## On-premise cloud management platform

The following diagram in an example of an {{site.data.keyword.icpfull_notm}} and CAM deployment in the on-premises infrastructure, with connections to the vCenter and {{site.data.keyword.containerlong_notm}} deployed on {{site.data.keyword.cloud_notm}}. Users can deploy VMs and containers on-premises, VMs into vCenter Server instances, and containers to the {{site.data.keyword.containerlong_notm}} cluster.

Figure 2. Cloud management from on-premises side
![On-premises cloud management](vcsicp-onprem-cloudmgt.svg)

The strongSwan VPN is used to established connectivity with the deployed {{site.data.keyword.containerlong_notm}} containers. The strongSwan VPM might be replaced with Direct link connectivity.

In the diagram, CAM logically creates cloud connections to the vCenters, cloud providers, {{site.data.keyword.icpfull_notm}}, and {{site.data.keyword.containerlong_notm}} environments. {{site.data.keyword.icpfull_notm}} clusters must be deployed to each data center cloud environment, with MCM providing the mechanism to connect the {{site.data.keyword.icpfull_notm}} clusters into a single management view.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
