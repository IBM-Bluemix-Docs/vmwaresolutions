---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-30"

---

# vCenter Server overview

VMware vCenter Server on {{site.data.keyword.cloud}} is a hosted private cloud that delivers the VMware vSphere stack as a service. The VMware environment is built on top of a minimum of two (recommended three) {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, offers shared network-attached storage and dedicated software-defined storage options, and it includes the automatic deployment and configuration of an easy-to-manage logical edge firewall that is powered by VMware NSX.

The entire environment can be provisioned in a matter of hours, and the bare metal infrastructure can rapidly and elastically scale the compute capacity up and down as needed.

Post-deployment, you can increase shared storage by ordering additional NFS (Network File System) file shares from the  {{site.data.keyword.slportal}} and manually attach them across all ESXi servers in a cluster. If you require dedicated storage, [NetApp ONTAP Select on IBM Cloud](../netapp/np_netappoverview.html) is offered in both high-performance (all SSD) and high-capacity (all SATA) configurations.

VMware vSAN is also available as a dedicated storage option. To increase the vSAN-based storage capacity of a vSAN cluster, you can add more ESXi servers post-deployment.

If you purchased IBM-provided VMware licensing, you can upgrade the VMware NSX Base edition to Advanced or to Enterprise edition, and you can purchase additional VMware components, such as VMware vRealize Operations.

You can add IBM Managed Services if you want to offload the day-to-day operations and maintenance of the virtualization, guest OS or application layers. The IBM Cloud Professional Services team is also available to help you accelerate your journey to the cloud with migration, implementation, planning, and onboarding services.

## vCenter Server architecture

The following graphic depicts the high-level architecture and components of a three-node vCenter Server deployment.

Figure 1. vCenter Server high-level architecture for a three-node cluster

![vCenter Server architecture](vc_architecture.svg)

### Physical infrastructure

This layer provides the physical infrastructure (compute, storage, and network resources) to be used by the virtual infrastructure.

### Virtualization infrastructure (Compute and Network)

This layer virtualizes the physical infrastructure through different VMware products:
* VMware vSphere virtualizes the physical compute resources.
* VMware NSX is the network virtualization platform that provides logical networking components and virtual networks.

### Virtualization management

This layer consists of vCenter Server Appliance (vCSA), NSX Manager, two NSX ESGs, three NSX Controllers, Platform Services Controller (PSC) virtual appliance, and the IBM CloudDriver virtual machine.

The base offering is deployed with a vCenter Server appliance that is sized to support an environment with up to 400 hosts and up to 4000 VMs. The same vSphere API-compatible tools and scripts can be used to manage the IBM-hosted VMware environment.

In total, the base offering requires 38 vCPU and 67 GB vRAM that are reserved for the virtualization management layer. The remaining host capacity for your VMs depends on several factors, such as oversubscription rate, VM sizing, and workload performance requirements.

<!-- For details about the architecture, read the _Reference documentation_ on the [Virtualization reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## vCenter Server instance components

The following components are included in your vCenter Server instance.

**Note**: The availability and pricing of standardized hardware configurations might vary based on the {{site.data.keyword.CloudDataCent_notm}} that is selected for deployment.

### Hardware

You can order three or more {{site.data.keyword.baremetal_short}} with one of the following configurations:
*  **Customized**: You can select the CPU, RAM, and storage options.
*  **Preconfigured**: **Small** (Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz / 128 GB RAM / 2 disks), **Medium** (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz / 256 GB RAM / 2 disks), or **Large** (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz / 512 GB RAM / 2 disks).

**Notes** for the **Customized** configuration:
* Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz is also available for the **Customized** configurations.
* If you select vSAN storage, the configuration requires four {{site.data.keyword.baremetal_short}}.

### Networking

The following networking components are ordered:
*  Three VLANs (Virtual LANs): one public VLAN and two private VLANs
*  One VXLAN (Virtual eXtensible LAN) with DLR (Distributed Logical Router) for potential east-west communication between local workloads that are connected to layer 2 (L2) networks. The VXLAN is deployed as a sample routing topology, which you can modify, build on it, or remove it. You can also add security zones by attaching additional VXLANs to new logical interfaces on the DLR.
*  Two VMware NSX Edge Services Gateways:
  * A secure management services VMware NSX Edge Services Gateway (ESG) for outbound HTTPS management traffic, which is deployed by IBM as part of the management networking typology. This ESG is used by the IBM management virtual machines to communicate with specific external IBM management components that are related to automation. For more information, see [Configuring your network to use the customer-managed ESG](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Important**: This ESG is not accessible to you and you cannot use it. If you modify it, you might not be able to manage the vCenter Server instance from the {{site.data.keyword.vmwaresolutions_short}} console. In addition, note that using a firewall or disabling the ESG communications to the external IBM management components will cause {{site.data.keyword.vmwaresolutions_short}} to become unusable.
  * A secure customer-managed VMware NSX Edge Services Gateway for outbound and inbound HTTPS workload traffic, which is deployed by IBM as a template that can be modified by you to provide VPN access or public access. For more information, see [Does the customer-managed NSX Edge pose a security risk?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

### Virtual Server Instances

The following VSIs (Virtual Server Instances) are ordered:
* A VSI for IBM CloudBuilder, which is shut down after the instance deployment is completed.
* (For instances V1.9 and later) A Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and virtual machines are registered, is deployed and can be looked up.
* (For instances V1.8 and earlier) A VSI for the snapshot-based backup of the management components, which keeps running after the instance deployment is completed.

### Storage

During initial deployment, you can choose between vSAN and NFS storage options.

The vSAN option offers customized CPU model and RAM configurations, with various options for disk type and quantity:
* Disk quantity: 2, 4, 6, or 8
* Storage disk: 960 GB SSD SED, 1.9 TB SSD SED, or 3.8 TB SSD SED.

  In addition, 2 cache disks of 960 GB are also ordered per host.

  **Note:** 3.8 TB SSD (Solid State Disk) drives will be supported when they are made generally available in a data center.

The NFS option offers customized shared file-level storage for workloads with various options for size and performance:
* Size: 1, 2, 4, 8, or 12 TB
* Performance: 2, 4, or 10 IOPS/GB. The 10 IOPS/GB option is available for certain data centers only.
* Individual configuration of file shares.

If you choose the NFS option, the following file shares are ordered:
* One 2 TB, 4 IOPS/GB file share for management components.
* One 2 TB shared block-level storage for backups, which can be scaled up to 12 TB. You can choose whether you want storage for backups by selecting a backup service.

### Licenses (IBM-provided or BYOL) and fees

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.3
* (For vSAN clusters) VMware vSAN Advanced or Enterprise 6.6
* Support and Services fees

## vCenter Server expansion node components

Each vCenter Server expansion node will deploy and incur charges for the following components in your {{site.data.keyword.cloud_notm}} account.

### Hardware for expansion nodes

One Bare Metal Server with the configuration presented in [vCenter Server instance  components](../vcenter/vc_vcenterserveroverview.html#vcenter-server-instance-components).

### Licenses and fees for expansion nodes

* One VMware vSphere Enterprise Plus 6.5u1
* One VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.3
* One Support and Services fee
* (For vSAN clusters) VMware vSAN Advanced or Enterprise 6.6

**Important**: You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal_full}} or any other means outside of the console. If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.

**CAUTION**: Managing any {{site.data.keyword.vmwaresolutions_short}} components, which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance, from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

## Related links

* [vCenter Server Software Bill of Materials](vc_bom.html)
* [Planning vCenter Server instances](vc_planning.html)
* [Ordering vCenter Server instances](vc_orderinginstance.html)
* [{{site.data.keyword.cloud_notm}} file and block storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
