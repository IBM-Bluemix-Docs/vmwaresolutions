---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud overview

VMware vSphere on {{site.data.keyword.cloud}} is a streamlined and optimized ordering platform for VMware. With this platform, you can build your own IBM-hosted VMware environment by customizing and ordering the VMware-compatible hardware based on your selected VMware components.

The {{site.data.keyword.vmwaresolutions_short}} console filters the hardware automatically, based on the VMware components that you select. For example, when you create a new all-flash VMware vSAN cluster, only the hardware that is validated against the [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) is presented. Also, a minimum of four ESXi servers is required.

VMware vSphere on {{site.data.keyword.cloud_notm}} does not automate the installation, configuration, and bring-up of the optional VMware components. The platform allows maximum of flexibility to design and build your hosted VMware environment while incorporating VMware-compatible hardware.

Use this offering to create a new cluster of ESXi servers or scale out an existing cluster of ESXi servers in an {{site.data.keyword.CloudDataCent_notm}}. Depending on the VMware components that you select, you can start with just one ESXi server and then scale the cluster later as needed.

## Technical specifications for VMware vSphere on IBM Cloud clusters

Review the components of VMware vSphere on {{site.data.keyword.cloud_notm}}.

The availability and pricing of standardized hardware configurations might vary based on the {{site.data.keyword.CloudDataCent_notm}} that is selected for deployment.
{:note}

### VMware components

Select licenses (IBM-provided or BYOL) for the following VMware components:
* VMware vSphere Enterprise Plus 6.0u2, 6.5u1, or 6.5u2
* The following VMware components are optional:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced, or Enterprise)
   * VMware vSAN (Advanced or Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

Select one or more {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} with your selected CPU model and RAM size:
* 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)
* SAP-certified (Intel Xeon 6140/E5-2690/E7-8890 series)
* 2-CPU Intel Broadwell generation (Intel Xeon E5-2600/E7-4800 series)

The options available depend on whether you selected the VMware vSAN component.

Additionally, the following disk and networking specifications:
* 10 Gbps dual public and private network uplinks
* One RAID disk controller

### Networking

* One VLAN (Virtual LAN) public VLAN and two private VLANs
* (Optional) An HA-pair of FortiGate Security Appliance devices

### Storage

User-customized storage for vSAN configuration when the VMware vSAN component is selected:
* Storage disk options of 960 GB SSD SED, 1.9 TB SSD SED, or 3.8 TB SSD SED
* Disk quantity options of 2, 4, 6, or 8

  Additionally, two cache disks of 960 GB are also ordered per host.

  3.8 TB SSD (Solid State Disk) drives are supported when they are made generally available in a data center.
  {:note}
* High-Performance Intel Optane option, which provides two extra capacity disk bays for a total of 10 capacity disks. This option depends on the CPU model.

## Technical specifications for vSphere cluster expansion nodes

Each vSphere cluster expansion node deploys and incurs charges for the following components in your {{site.data.keyword.slportal}} account.

### Hardware for expansion nodes

One {{site.data.keyword.cloud_notm}} Bare Metal Server with the hardware configuration presented in [Technical specifications for VMware vSphere on {{site.data.keyword.cloud_notm}} clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-on-ibm-cloud-overview#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### Networking for expansion nodes

One {{site.data.keyword.cloud_notm}} Bare Metal Server with the networking configuration presented in [Technical specifications for VMware vSphere on {{site.data.keyword.cloud_notm}} clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-on-ibm-cloud-overview#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

### VMware components for expansion nodes

* One {{site.data.keyword.cloud_notm}} Bare Metal Server with VMware vSphere Enterprise Plus 6.0u2 or 6.5u1  
* Optional VMware components presented in [Technical specifications for VMware vSphere on {{site.data.keyword.cloud_notm}} clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-on-ibm-cloud-overview#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters).

You must manage the ESXi servers, optional VMware components, and additional hardware that are ordered and delivered to your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.slportal}}. After creating a new cluster in the {{site.data.keyword.vmwaresolutions_short}} console, you can return to the console and use the saved information to scale the new cluster. For more information, see [Scaling existing vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-existing-vsphere-clusters).
{:important}

### Related links

* [VMware vSphere Software Bill of Materials](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-bill-of-materials)
* [Planning vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-requirements-and-planning-for-vmware-vsphere-on-ibm-cloud)
* [Ordering vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters)
* [Scaling existing vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-existing-vsphere-clusters)
