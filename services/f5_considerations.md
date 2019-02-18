---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 on IBM Cloud overview

The F5 on {{site.data.keyword.cloud}} service (F5 BIG-IP® Virtual Edition) provides intelligent L4-L7 load balancing and traffic management services at a local and global scale, robust network and web application firewall protection, and secure and federated application access.

You can install more than one instance of this service as needed.

This service is available only to instances that are deployed in V1.9 or later. The current BIG-IP VE version that is installed is v13.1.1.2.
{:note}

## Technical specifications for F5 on IBM Cloud

The following components are included with the F5 on {{site.data.keyword.cloud_notm}} service:

### Virtual machines
* Two virtual machines (VMs) with all options available.
* 2, 4, or 8 vCPUs per virtual machine depending on the licensing option.
* 4, 8, or 16 GB RAM per virtual machine depending on the licensing option.

### Networking
* Private Virtual Extensible LAN (VXLAN) for High Availability (HA) synchronization.
* Access to Traffic Management Shell (TMSH) and Management Console through private management network.

### Licenses and fees
License fees for each VM are applied to each billing cycle depending on the licensing option (Good, Better, or Best) and the selected bandwidth.

You cannot change the licensing level after service installation. To change the licensing level, you must remove the existing service and reinstall the service using a different licensing option.
{:important}

## Installation considerations for F5 on IBM Cloud

Before you install the F5 on {{site.data.keyword.cloud_notm}} service, review the following considerations.

Based on the license model and bandwidth that you select, two BIG-IP VE VMs (virtual machines) are deployed with the following configuration:

Table 1. CPU and RAM deployments for different bandwidth and license model selections

| Maximum Bandwidth | License Model: Good | License Model: Better | License Model: Best |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbps           | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 200 Mbps          | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 1 Gbps            | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 3 Gbps            | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |
| 5 Gbps            | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |
| 10 Gbps           | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |

### Additional considerations

* F5 BIG–IP limits the appliance throughput based on your chosen maximum bandwidth. Because network performance is affected by many factors, not all configurations and topologies may be able to achieve your chosen maximum bandwidth.
* The HA (High Availability) pair of BIG-IP VE VMs will be deployed only into the default cluster.

  In addition, 100% of CPU and RAM for the two BIG-IP VE VMs are also reserved because these VMs are in the data plane of the network communications and it is critical that resources are still available for them.

  To calculate the CPU and RAM reservation for a single BIG-IP VE VM, use the following formula:

  `CPU reservation = CPU speed of ESXi server * number of vCPUs` (from Table 1)

  `RAM reservation = RAM size` (from Table 1)

### Planning considerations
You must meet the following requirements to avoid failures with F5 on {{site.data.keyword.cloud_notm}}:
* At least two active ESXi servers are available for the two BIG-IP VE VMs to be deployed with the anti-affinity rule of keeping the VMs on separate servers.
* The two active ESXi servers have enough resources available so that one BIG-IP VE VM can be hosted on each ESXi server with 100% CPU and RAM reservation.
* VMware vSphere HA has enough resources to host two BIG-IP VMs with 100% CPU and RAM.

Due to these requirements, you must plan for the space that is needed for F5 on {{site.data.keyword.cloud_notm}}. If needed, before you order F5 on {{site.data.keyword.cloud_notm}}, add 1-2 ESXi servers to your instance, or reduce vSphere HA CPU reservation for failover, or both.

## F5 on IBM Cloud order example

You order a VMware vCenter Server **Small** instance with 2 ESXI servers with the following configuration: sixteen cores at 2.10 GHz each with 128 GB RAM. For F5 on {{site.data.keyword.cloud_notm}}, you select the **Best** license model and a value of 5 Gbps for **Maximum Bandwidth**.

In this case, a single BIG-IP VM requires, on each server:
* 2.1 GHz * 8 vCPU = 16.8 GHz of CPU, and
* 16 GB RAM

In total, that is 33.6 GHz CPU and 32 GB RAM for two BIG-IP VMs.

Each ESXi server has a capacity of 16 cores * 2.1 GHz = 33.6 GHz, so we meet the first two requirements if both servers are active and there is at least 16.8 GHz of CPU and 16 GB RAM available on each server.

However, by default, vSphere HA reserves 50 percent of CPU and RAM for failover on vCenter Server instances that were initially deployed with 2 ESXi servers. For this example, the following is available:

`50% of 2 * 16 cores * 2.1 GHz = 33.6 GHz available`

Since there will be other workloads present on the ESXi servers, for example, VMware vCenter Server, VMware NSX Controller, VMware NSX Edge, using these resources we cannot satisfy the third requirement, because we need 33.6 GHz of CPU and 32 GB RAM for the two BIG-IP VMs.

In this case, the F5 on {{site.data.keyword.cloud_notm}} installation might fail, unless at least one ESXi server is added to the environment and vShpere HA failover reservations are updated appropriately to ensure that there are enough resources for two BIG-IP VE VMs. If additional resources are needed to run the F5 on {{site.data.keyword.cloud_notm}} service, you can add more ESXi servers before installing F5 on {{site.data.keyword.cloud_notm}}.

## Considerations when removing F5 on IBM Cloud

Before you remove the F5 on {{site.data.keyword.cloud_notm}} service, ensure that the existing BIG-IP VE configuration is removed correctly. Specifically, network traffic must be routed around BIG-IP VE instead of through BIG-IP VE. Otherwise, the existing data traffic from your environment might be impacted.

### Related links

* [Ordering F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-f5-on-ibm-cloud)
* [Managing F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-f5-on-ibm-cloud)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [F5 website](https://f5.com/){:new_window}
