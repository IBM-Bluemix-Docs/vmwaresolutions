---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Mission Critical VMware on IBM Cloud overview

Mission Critical VMware on {{site.data.keyword.cloud}} delivers a multi-zone cloud architecture to help enterprises prevent downtime for cloud applications and to automate failovers within a cloud region.

With this cloud architecture, customers can achieve a higher availability and failover success rate than most VMware clients can achieve with on-premises environments or competing cloud platforms.

This architecture supports existing mission-critical, legacy workloads, including non-cloud native applications, at a targeted aggregate availability of 99.99%. IBM Cloud multi-zone regions are designed to keep mission-critical workloads online if a site outage occurs. Workloads in a failed site are automatically restarted in near real time, while workloads in adjoining sites remain online and available.

The architecture covers various enterprise services, including networks, storage, resiliency, and other tools built for monitoring and troubleshooting cloud-based applications. In addition, this architecture can be integrated with the IBM Services Platform with Watson, built on the {{site.data.keyword.cloud_notm}}, to allow for a broader consumption of services. Using the platform’s cognitive capabilities, clients can mine data more effectively for new business insights to help maintain continuous operations.

## Technical specifications for Mission Critical VMware on IBM Cloud

The Mission Critical VMware on {{site.data.keyword.cloud_notm}} architecture is an end to end reference architecture that provides automated failover for customer workloads. It uses an {{site.data.keyword.cloud_notm}} multi-zone region with an IBM-managed service that covers the following components:

* Compute architecture (VMware vSphere)
* Network architecture (currently NSX-V)
* Storage architecture (VMware vSAN)
* Integration with IBM Services Platform with Watson to enable the consumption of services
* Tools for monitoring, troubleshooting, performance, and capacity management:
  * vRealize Suite pattern (Operations, Log Insight and Network Insight)
  * Active Directory pattern
  * Integration with Netcool/Bluecare for auto-ticketing, alerting, and event enrichment
  * Resiliency patterns (backup and recovery)

Mission Critical VMware on {{site.data.keyword.cloud_notm}} is available in the following regions:
* America: NA South - all IBM Cloud Data Centers in Dallas and NA East: all IBM Cloud Data Centers in Washington, DC
* Europe: all IBM Cloud Data Centers in Frankfurt and London
* Asia-Pacific: all IBM Cloud Data Centers in Sydney and Tokyo

### Base infrastructure architecture specifications

The base infrastructure has the following specifications:
* Each site has its own dedicated edge and management cluster
* The resource cluster is a vSphere + vSAN stretched cluster
* The witness site contains a witness ESXi host
* Single vCenter and NSX Manager architecture
* vCenter Server Appliance with embedded Platform Services Controller (PSC) that uses vCenter High Availability (HA) over an L3 network architecture
* NSX Manager recovery is using a Hot/Standby methodology that syncs up backup files

### Tooling and technology architecture specifications

The tooling and technology architecture has the following specifications:
* vRealize Operations, vRealize Log Insight, and vRealize Network Insight to provide operations and management capabilities specific to the VMware products being used, for example NSX, vSAN, and vSphere
* IBM Software Defined Environment Automation Tool Health Check (SAT HC) for validating deployments against best practices and security policies
* Optional Disaster Recovery (DR) to an out of Region {{site.data.keyword.cloud_notm}} site
* Fortigate Security Appliance or similar to secure any internet access and to facilitate active-active network integration with the on-premises network

### vSphere + vSAN stretched cluster architecture specifications

The vSphere + vSAN stretched cluster architecture has the following specifications:
* The cluster provides storage and compute capabilities that span two sites to provide enhanced availability.
* Write requests from virtual machines (VMs) are synchronously written to both sites incurring site to site network latency.
* Read requests from VMs are fulfilled locally to the physical location of where the VM is located, thus avoiding extra latency.
* The witness site and witness host act as the split brain/quorum.
* vSAN Native Encryption (for at rest encryption) can be used in combination with this architecture.

### Network architecture specifications

The network architecture has the following specifications:
* Edge/DLR/VXLANs in combination with BGP metric-based routing to facilitate an active-active site design with automated failover.
* Each site has the concept of their own set of Edges/DLRs and VXLANs.
* Under normal circumstances, any VMs connected to DLR-A, for example VM-A will be in {{site.data.keyword.cloud_notm}} availability zone #1 and traffic will both ingress and egress locally.
* During a vMotion activity for VM-A, traffic will still ingress and egress via {{site.data.keyword.cloud_notm}} availability zone #1.
* During a site or edge failure, traffic will route out of the remaining available site.

### Related links

* [Requesting Mission Critical VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-mission-critical-vmware-on-ibm-cloud)
