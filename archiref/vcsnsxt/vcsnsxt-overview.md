---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Overall architecture overview

The following information provides more details about the network architecture that is used in this reference architecture. It consists of the following sections:
* **VMware vCenter Server on {{site.data.keyword.cloud}} overview** – Describes the highlights of the vCenter Server platform.
* **Network overview** – Provides information on the network components that are used in this reference architecture:
  - **{{site.data.keyword.cloud_notm}} networking** – {{site.data.keyword.cloud_notm}} provides the physical network and is fully managed by {{site.data.keyword.cloud_notm}}. Review the key characteristics of {{site.data.keyword.cloud_notm}} networking to understand network flows between on and off premise and between workloads that are hosted in different services.
  - **NSX-V** – vCenter Server networking builds upon the {{site.data.keyword.cloud_notm}} network with an overlay that is provided by VMware NSX-V. This overlay segments traffic from the {{site.data.keyword.cloud_notm}} underlay network that allows greater control and configurability that includes Bring Your Own IP (BYOIP).
  - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} uses Calico as its Container Network Interface plug-in.
  - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} uses Calico as its Container Network Interface plug-in.

* **Integration** – Describes the architecture of the networking components to allow the required network traffic flows and addressing:
  - IP address allocation
  - Network traffic flows

## vCenter Server overview

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle is a hosted private cloud that helps you to quickly and easily extend your on-premises infrastructure into the cloud for secure and seamless infrastructure hybridity and true application mobility.

The vCenter Server Hybridity Bundle is deployed on a minimum of four {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, offers dedicated storage via a virtual storage area network (VSAN), and includes the automatic deployment and configuration of an easy-to-manage software-defined networking infrastructure (NSX-V). The vCenter Server Hybridity Bundle is a reference architecture that is deployed via automation, which ensures consistency, performance, and compliance. In many cases, you can provision the entire environment in less than a day and the bare metal infrastructure can rapidly and elastically scale the compute and storage capacity up and down as needed.

Many options are available to enhance and extend the vCenter Server Hybridity Bundle. {{site.data.keyword.cloud_notm}} service offerings not only include add on storage options and various public and private WAN connectivity options, but also cover areas from platform security, Network security, traffic load balancing to back up and disaster recovery.

Platform security services include HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, which provides automated security and compliance support, enabling better visibility and control over your cloud environment and administrators. HyTrust DataControl on {{site.data.keyword.cloud_notm}} delivers data protection with powerful encryption and scalable key management to secure your workloads throughout their lifecycles. {{site.data.keyword.cloud_notm}} Secure Virtualization simplifies compliance and protects your data with encryption, geo-fencing policies and role-based access controls, while KMIP for VMware on {{site.data.keyword.cloud_notm}} an encryption key lifecycle management offering manages the encryption keys used by {{site.data.keyword.cloud_notm}} services or customer built-in applications.

Network security options are the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} that provisions a highly available pair of FortiGate Security Appliance devices to analyze network traffic and protect your virtual infrastructure and the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, which deploys a high availability pair of FortiGate VMs on {{site.data.keyword.cloud_notm}} to reduce risk by implementing critical security controls within your virtual infrastructure. More Network security offerings are in development.

The F5 on {{site.data.keyword.cloud_notm}} network load balancer service offering optimizes performance and ensures the availability and security of your most critical applications with the F5 BIG-IP suite.

Back up and disaster recovery offerings from IBM, Veeam, and Zerto deliver peace of mind and operational continuity if disaster occurs. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} is a data protection and availability solution for virtual environments. Veeam on {{site.data.keyword.cloud_notm}} enables availability for the Always-On Enterprise™ with integrated backup, recovery, and replication on {{site.data.keyword.cloud_notm}}. Zerto on {{site.data.keyword.cloud_notm}} provides on-premises and {{site.data.keyword.cloud_notm}} customers with a secure, flexible, and scalable Disaster Recovery solution.

vCenter Server Hybridity Bundle isn't a managed service, though you can add IBM-Managed Services to offload the day-to-day operations and maintenance of the virtualization, guest OS or application layers. The {{site.data.keyword.cloud_notm}} Professional Services team is also available to help you accelerate your journey to the cloud with migration, implementation, planning, and onboarding services.

The platform integration options of the vCenter Server Hybridity Bundle are not limited to options available from VMware such as vRealize Suite or vSphere with Operations Management, but span multiple {{site.data.keyword.cloud_notm}} service offerings such as [vCenter Server and {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcenter-server-and-ibm-cloud-kubernetes-service-introduction) and [vCenter Server and {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction), which use open source Terraform to manage and deliver infrastructure as code.

The extensive portfolio of services and multi-offering integration options available for the vCenter Server Hybridity Bundle deliver a truly hybrid platform that makes Hybridity as a Service possible.

### Related Links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
