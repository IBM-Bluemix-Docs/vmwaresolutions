---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance on IBM Cloud overview

The FortiGate Virtual Appliance on {{site.data.keyword.cloud}} service deploys a pair of FortiGate Virtual Appliances to your environment, which can help you reduce risk by implementing critical security controls within your virtual infrastructure.

You can install multiple instances of this service as needed. You can manage this service by using the FortiOS Web Client or the command line interface through SSH.

This service is available only to instances that are deployed in V2.0 or later releases. The current service version that is installed is 6.0.3.
{:note}

## Technical specifications for FortiGate Virtual Appliance on IBM Cloud

The following components are ordered and included in the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service:

### Virtual machines

* All options include a highly available (HA) pair of virtual machines
* 2, 4, or 8 vCPUs per virtual machine depending on the deployment size and subscription type
* 4, 6, or 12 GB RAM per virtual machine depending on the deployment size and subscription type

### High availability

Two virtual machines are deployed and ready for HA or Virtual Router Redundancy Protocol (VRRP) configuration.

### Networking

Access to the FortiGate® console is provided through a private management network.

### License and fees

License fees for each virtual machine are applied to each billing cycle depending on the selected deployment size and monthly subscription license model.

You cannot change the licensing level after service installation. To change the licensing level, you must remove the existing service and reinstall the service using a different licensing option.
{:important}

## Considerations when installing FortiGate Virtual Appliance on IBM Cloud

Review the following considerations before you install the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service:
* The FortiGate virtual machines (VMs) are deployed only into the default cluster.
* 100% of CPU and RAM for the two FortiGate VMs are also reserved because these VMs are in the data plane of the network communications and it is critical that resources are still available for them.

  To calculate the CPU and RAM reservation for a single FortiGate VM, use the following formula:
   * `CPU reservation = CPU speed of ESXi server * number of vCPUs`
   * `RAM reservation = RAM size`
* When you deploy an HA-pair of FortiGate Virtual Appliances to you instance, SNAT and firewall rules are defined on the Management NSX Edge Services Gateway (ESG) along with static routes on the FortiGate Virtual Appliances to allow outbound HTTPS communications from your instance to the public network for license activation and for acquiring latest security policies and content.
* You cannot change the license level after service installation. To change the license level, you must remove the existing service and then reinstall the service by selecting a different license option.
* You must meet the following requirements to avoid failures with FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:
   * At least two active ESXi servers are available for the two FortiGate VMs to be deployed with the anti-affinity rule of keeping the VMs on separate servers.
   * The two active ESXi servers have enough resources available so that one FortiGate VM can be hosted on each ESXi server with 100% CPU and RAM reservation.
   * VMware vSphere HA has enough resources to host two FortiGate VMs with 100% CPU and RAM.

  Due to these requirements, you must plan for the space needed for FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} carefully. If needed, before ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, add 1 - 2 ESXi servers to your instance, or reduce the vSphere HA CPU reservation for failover, or both.

## FortiGate Virtual Appliance on IBM Cloud order example

You order a VMware vCenter Server **Small** instance with 2 ESXi servers with the following configuration: 16 cores at 2.10 GHz each with 128 GB RAM. For FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, you select the **Large** (8 vCPUs / 12 GB RAM) for deployment size and any subscription license model.

In this case, a single FortiGate VM requires, on each server:
* 2.1 GHz * 8 vCPU = 16.8 GHz of CPU, and
* 12 GB RAM

In total, that is 33.6 GHz CPU and 24 GB RAM for two FortiGate VMs.

Each ESXi server has a capacity of 16 cores * 2.1 GHz = 33.6 GHz, so we meet the first two requirements if both servers are active and there is at least 16.8 GHz of CPU and 12 GB RAM available on each server.

By default however, vSphere HA reserves 50% of CPU and RAM for failover on vCenter Server instances that were initially deployed with 2 ESXi servers, so we only have:

`50% of 2 * 16 cores * 2.1 GHz = 33.6 GHz available`

Since other workloads exist on the ESXi servers, for example, VMware vCenter Server, VMware NSX Controller, or VMware NSX Edge, by using these resources, the third requirement is not met. This is because we need 33.6 GHz of CPU and 24 GB RAM for the two FortiGate VMs.

In this case, the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installation might fail, unless at least one ESXi server is added to the environment and vShpere HA failover reservations are updated appropriately to ensure that there are enough resources for two FortiGate VMs.

If additional resources are needed to run the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service, you can add more ESXi servers before installing the service.

## Considerations when removing FortiGate Virtual Appliance on IBM Cloud

Before you remove the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service, ensure that the configuration of the existing FortiGate Virtual Appliances is removed correctly. Specifically, network traffic must be routed around FortiGate Virtual Appliances instead of through FortiGate Virtual Appliances. Otherwise, the existing data traffic within your environment might be impacted.

### Related links

* [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-fortigate-virtual-appliance-on-ibm-cloud)
* [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-fortigate-virtual-appliance-on-ibm-cloud)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [Fortinet website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
