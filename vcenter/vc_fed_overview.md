---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Federal on IBM Cloud overview

With VMware Federal on {{site.data.keyword.cloud}}, you can order a base vCenter Server instance in addition to providing US Federal Government agencies with the option to secure the deployed vCenter Server instances. When you secure a deployed instance, the sensitive information that is stored about the instance is removed. Also, the open connection for instance access is removed, which means that management functions, such as adding and removing hosts and clusters are no longer available. After you select the secure option, the only available function is instance delete.

For more information about vCenter Server on {{site.data.keyword.cloud_notm}} and the vCenter Server architecture, see [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-overview).

VMware Federal on {{site.data.keyword.cloud_notm}} offers only a subset of the vCenter Server offerings. Multi-site configuration, Bring Your Own License, and the option to order add-on services are not supported.
{:note}

## Technical specifications for VMware Federal on IBM Cloud instances

The following components are included:

### Bare Metal Server

You can order two or more {{site.data.keyword.baremetal_short}} with one of the following configurations:

* 2-CPU Intel Broadwell generation (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)

For NFS storage configuration, the recommended number of {{site.data.keyword.baremetal_short}} is set to the default of three.

If you select vSAN storage, the configuration requires four {{site.data.keyword.baremetal_short}}.
{:note}

### Networking

The following networking components are ordered:
*  Three VLANs (Virtual LANs): one public VLAN and two private VLANs
*  One VXLAN (Virtual eXtensible LAN) with DLR (Distributed Logical Router) for potential east-west communication between local workloads that are connected to layer 2 (L2) networks. The VXLAN is deployed as a sample routing topology, which you can modify, build on it, or remove it. You can also add security zones by attaching more VXLANs to new logical interfaces on the DLR.
*  Two VMware NSX Edge Services Gateways:
  * A secure management services VMware NSX Edge Services Gateway (ESG) for outbound HTTPS management traffic, which is deployed by IBM as part of the management networking typology. This ESG is used by the IBM management virtual machines to communicate with specific external IBM management components that are related to automation. For more information, see [Configuring your network to use the customer-managed ESG](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    This ESG is not accessible to you and you cannot use it. If you modify it, you might not be able to manage the vCenter Server instance from the {{site.data.keyword.vmwaresolutions_short}} console. In addition, using a firewall or disabling the ESG communications to the external IBM management components will cause {{site.data.keyword.vmwaresolutions_short}} to become unusable.
    {:important}
  * A secure customer-managed VMware NSX Edge Services Gateway for outbound and inbound HTTPS workload traffic, which is deployed by IBM as a template that can be modified by you to provide VPN access or public access. For more information, see [Does the customer-managed NSX Edge pose a security risk](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions#does-the-customer-managed-nsx-edge-pose-a-security-risk-).

  The VMware NSX Edge Services Gateway (ESG) for outbound HTTPS management traffic is removed as part of the action to secure your deployed VMware Federal instance. For more information, see [Securing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-securing-vmware-federal-instances).
  {:note}

### Virtual Server Instances

The following VSIs (Virtual Server Instances) are ordered:
* A VSI for IBM CloudBuilder, which is shut down after the instance deployment is completed.
* (For instances V2.3 and later) You can choose to deploy a single Microsoft Windows Server VSI for Microsoft Active Directory (AD) or two high availability Microsoft Windows VMs in the management cluster to help enhance security and reliability.
* (For V2.2 instances) A Microsoft Windows Server VSI for Microsoft Active Directory (AD) is deployed and can be looked up. This VSI functions as the DNS for the instance where the hosts and virtual machines are registered.

### Storage

During initial deployment, you can choose between vSAN and NFS storage options.

#### vSAN storage

The vSAN option offers customized configurations, with various options for disk type and quantity:
* Disk quantity: 2, 4, 6, or 8.
* Storage disk: 960 GB SSD SED, 1.9 TB SSD SED, or 3.8 TB SSD SED.

  In addition, two cache disks of 960 GB are ordered per host.
* High-Performance Intel Optane option, which provides two extra capacity disk bays for a total of 10 capacity disks. This option depends on the CPU model.

#### NFS storage

The NFS option offers customized shared file-level storage for workloads with various options for size and performance:
* Size: 1, 2, 4, 8, or 12 TB.
* Performance: 2, 4, or 10 IOPS/GB.
* Individually configure file shares.

If you choose the NFS option, one 2 TB, 4 IOPS/GB file share for management components is ordered.

### IBM-provided licenses and fees

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.4
* (For vSAN clusters) VMware vSAN Advanced or Enterprise 6.6

## Technical specifications for VMware Federal on IBM Cloud expansion nodes

Each vCenter Server expansion node will deploy and incur charges for the following components in your {{site.data.keyword.cloud_notm}} account.

### Hardware for expansion nodes

One Bare Metal Server with the configuration presented in [Technical specifications for VMware Federal on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vmware-federal-on-ibm-cloud-overview#technical-specifications-for-vmware-federal-on-ibm-cloud-instances).

### Licenses and fees for expansion nodes

* One VMware vSphere Enterprise Plus 6.5u1
* One VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.4
* (For vSAN clusters) VMware vSAN Advanced or Enterprise 6.6

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal}}, or any other means outside of the console. If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes aren't synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components, which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance, from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

### Related links

* [Requirements and planning for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-requirements-and-planning-for-vmware-federal-instances)
* [Ordering VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vmware-federal-instances)
* [Adding, viewing, and deleting clusters for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vmware-federal-instances)
* [Expanding and contracting capacity for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vmware-federal-instances)
* [Securing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-securing-vmware-federal-instances)
* [{{site.data.keyword.cloud_notm}} file and block storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
