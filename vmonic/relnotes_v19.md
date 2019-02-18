---

copyright:

  years:  2016, 2019

lastupdated: "2017-10-13"

---

# Release notes for V1.9

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud

This release introduces the VMware vSphere on {{site.data.keyword.cloud_notm}} offering. This offering allows you to build your own IBM-hosted VMware virtual environment by customizing and ordering the VMware-compatible compute, storage, and network resources based on selected VMware components. While vSphere on {{site.data.keyword.cloud_notm}} does not automate the installation, configuration, and opening of the optional VMware components, you have maximum flexibility to design and architect an environment that best fits your business needs. Start by creating a new vSphere cluster of ESXi servers or by scaling out an existing vSphere cluster in an {{site.data.keyword.CloudDataCent_notm}}.

For more information, see the following topics:
* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters)
* [Scaling existing vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-existing-vsphere-clusters)

## NetApp ONTAP Select on IBM Cloud

This release introduces the NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} offering, a virtual appliance for software-defined storage, which implements NetApp ONTAP Select as a service on IBM Cloud’s dedicated {{site.data.keyword.baremetal_short}}. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} is offered in both high-performance (all SSD) and high-capacity (all SATA) configurations.
This offering hosts your storage on dedicated infrastructure and provides NetApp capabilities, such as deduplication, compression, and encryption of data at rest. Provision storage resources with agility and flexibility while you protect data by using advanced data management functions. For example, use the fast and efficient NetApp Snapshot® copies, FlexClone® copies, and SnapMirror® replication.

For more information, see the following topics:
* [NetApp ONTAP Select overview](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-netapp-ontap-select-overview)
* [Ordering NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-ordering-netapp-ontap-select-instances)

## F5 on IBM Cloud service

The F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} service is now available to both VMware Cloud Foundation and VMware vCenter Server instances. This service provides intelligent L4-L7 load balancing and traffic management services at a local and global scale, robust network and web application firewall protection, secure, and federated application access.
Order instances with the F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} service included when you order your instance or add this service to your existing instances later from the **Services** tab on the instance property details page of the {{site.data.keyword.vmwaresolutions_short}} console. Depending on your requirements, you can select one of the three licensing options for BIG-IP VEs.

For more information, see the following topics:
* [Considerations for F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5-on-ibm-cloud-overview)
* [Managing F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-f5-on-ibm-cloud)

## Managed services from IBM-Integrated Managed Infrastructure

Managed services from IBM-Integrated Managed Infrastructure (IMI) are now available to VMware Cloud Foundation instances. IMI can simplify VMware virtual infrastructure management with modular services and can serve as a single, trusted provider to reduce complexity of monitoring and managing virtual IT infrastructures. Offload certain day to day operations to IMI, such as monitoring, so that you can focus on higher value initiatives.

You can request a consultation and estimate at any time from the **Getting Started** page.
For more information, see [Requesting managed services from IMI](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-managed-services-from-imi#requesting-managed-services-from-imi).

## Instance name restrictions for vCenter Server and NetApp ONTAP Select instances

Instance names entered on the {{site.data.keyword.vmwaresolutions_short}} when you order your instances cannot have special characters (such as the dash character) in them. Only alphanumeric characters are allowed. This restriction does not apply to Cloud Foundation instances.

For more information, see the following topics:
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)
* [Ordering NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-ordering-netapp-ontap-select-instances)

## Updates for VMware Cloud Foundation instances

### Customize your instance CPU and memory

A user-customized server option is available alongside the pre-built and tested Small and Standard options. In order to better match the CPU-to-RAM ratio of your workloads to the VMware-compatible hardware, you can now independently select the total number of cores on a dual-CPU server and the amount of RAM. Local storage is not customizable.

For more information, see [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances).

## Updates for VMware vCenter Server instances

### Cross data center cluster support

In order to enhance the scale out of your hosted VMware environment, you can now create a new cluster in a different {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) pod, or a different {{site.data.keyword.CloudDataCent_notm}} than the initial cluster deployed in the instance.

For more information, see [Adding and viewing clusters for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vcenter-server-instances).

### Changing components

This release eliminates the impact to operations within the {{site.data.keyword.vmwaresolutions_short}} console when the Single Sign-On administrator changes certain vCenter Server resources from a native VMware tool. For example, you can now modify the VMware virtual data center, cluster, switches, port groups, and data store names from the VMware vSphere Web Client to customize deployments to company or personal naming conventions and without any downstream impact to the operations from within the {{site.data.keyword.vmwaresolutions_short}} console.

For more information, see [Impacts of changing components for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-considerations-about-changing-vcenter-server-artifacts).

### Additional RAM sizes

When you order vCenter Server instances or add clusters for vCenter Server instances, you now have more RAM sizes to choose from to help match the CPU-to-RAM ratio of the workload to the hardware. The following options are available in the **User customized** configuration option when you order a server from the {{site.data.keyword.vmwaresolutions_short}} console: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1.5 TB.

For more information, see [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances).

### Network File System version update

Network File System (NFS) Version 4.1 is no longer available as a storage setting from the user interface. All vCenter Server instances are deployed with NFS V3. Although NFS V3 is an older protocol version, it enables enhanced features on VMware environments with support for VMware Storage Distributed Resource Scheduler (SDRS) and Storage I/O Control (SIOC).

For more information, see [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances).

### Single site Domain Name Server domain name

You can now provide the Domain Name Server (DNS) domain name for a vCenter Server instance during an order. A Microsoft Windows Server Virtual Server Instance (VSI), that functions as the DNS for the instance where the hosts and virtual machines are registered, is deployed and can be looked up. Microsoft Active Directory (AD) is also set up on the Microsoft Windows VSI and the DNS domain name is the AD domain forest root. This Microsoft Windows VSI is only available in V1.9 and later.

For more information, see the following topics:
* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-overview)
* [Viewing vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vcenter-server-instances)

## Requirements for Windows Server automatic installation of updates

The Microsoft Active Directory (AD) / Domain Name Server (DNS) is automatically set up to download updates only. It does not automatically install and restart these updates. You must install the updates manually and restart at a scheduled time that avoids any interruptions of the ongoing Active Directory server configuration and other backup jobs. To apply Windows updates, install the updates manually.

## New and updated documentation

* Learn how to safeguard your private multi-site Cloud Foundation instances while extending your VMware applications to use public {{site.data.keyword.cloud_notm}} services. For more information, see [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* More documentation is provided for configuring firewalls that permit all protocol communication from the IBM CloudDriver and the SDDC Manager virtual machines. For more information, see [Components and considerations for Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortigate-security-appliance-on-ibm-cloud-overview).
