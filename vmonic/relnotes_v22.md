---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-19"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Release notes for V2.2

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715 and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

For more information, see [Addressing Spectre and Meltdown vulnerabilities](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-addressing-spectre-and-meltdown-vulnerabilities).

## IBM CloudDriver virtual machine upgrade

During the V2.2 upgrade process, the IBM CloudDriver virtual machine is redeployed with CentOS Linux release 7.4.1708. In addition, all new provisioned instances include CentOS Linux release 7.4.1708 on the IBM CloudDriver.

**Important:**

* If you are using a backup solution that references the IBM CloudDriver virtual machine, after you upgrade to V2.2, ensure that the backup solution is referencing the new IBM CloudDriver virtual machine.
* Before you upgrade to V2.2, ensure that you replace the Legacy Veeam VSI with the Veeam on {{site.data.keyword.cloud_notm}} service. Legacy Veeam is no longer supported in V2.2 and future releases, therefore the management component backups that are associated with Legacy Veeam are not available for a restore.

For more information about using the Veeam on {{site.data.keyword.cloud_notm}} service, see the following topics:
* [Components and considerations for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam-on-ibm-cloud-overview)
* [Managing Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-veeam-on-ibm-cloud)

## Support for VMware Federal on IBM Cloud

VMware Federal on {{site.data.keyword.cloud_notm}} provides the option to order a base vCenter Server instance in the WDC03 Federal on {{site.data.keyword.CloudDataCent_notm}}. In addition to supporting a subset of vCenter Server instance offerings, VMware Federal on {{site.data.keyword.cloud_notm}} provides US Federal Government agencies with the option to secure deployed VMware vCenter Server instances. Selecting the option to secure the deployed instances removes sensitive information that is stored about the instance and removes the open management connection for ongoing access to the instance for management functions, such as adding and removing hosts and clusters. After you select the secure option, all management functions are unavailable except for a full instance delete.

For important considerations before you secure a VMware Federal instance, see [Securing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-securing-vmware-federal-instances).

(Updated on 2 April 2018) You can now expand or contract the capacity of your VMware Federal instance by adding or removing ESXi servers. This option is available only to VMware Federal instances that have not been secured.

For more information, see the following topics:

* [VMware Federal on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vmware-federal-on-ibm-cloud-overview)
* [Adding, viewing, and deleting clusters for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vmware-federal-instances)
* [Expanding and contracting capacity for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vmware-federal-instances)

## Advanced configuration settings on ESXi servers

For V2.2 or later releases, new instances are ordered with a new set of advanced configuration settings for ESXi servers.
For instances that are upgraded from a previous release to V2.2 or later releases, some settings require rebooting the ESXi servers. Therefore, only a subset of configuration settings is applied automatically.

It is recommended that you change the remaining configuration settings to the new values for consistency across all instances and to allow adequate support for storage expansion. IBM plans to test only with these new settings for all {{site.data.keyword.cloud_notm}} for VMware Solutions future releases.

For more information, see _Advanced configuration settings for ESXi servers_ in:
* [vCenter Server Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-bill-of-materials#advanced-configuration-settings-for-esxi-servers)
* [Cloud Foundation Bill of Materials](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cloud-foundation-bill-of-materials#advanced-configuration-settings-for-esxi-servers)

## Support for up to 51 ESXi servers for an initial cluster and up to 59 ESXi servers for additional clusters

For V2.2 and later releases, you can now increase the number of ESXi servers to a maximum of 51 for an initial cluster and up to 59 for additional clusters.

For instances deployed in V2.1 or earlier releases, you must enable necessary vSAN support to increase the cluster size beyond 32. For more information about steps to increase the number of ESXi servers, see _How many ESXi servers can I add to a cluster?_ in [FAQ about ESXi servers](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq-about-esxi-servers#how-many-esxi-servers-can-i-add-to-a-cluster-).
{:important}

## More network configuration options for vCenter Server and Cloud Foundation instances

For vCenter Server and Cloud Foundation instance orders, you can now reuse existing public and private VLANs for your network configuration. When existing VLANs are not available, you can order one new public and two new private VLANs.

For important considerations before you select existing VLANs, see the *Network interface settings* sections in:
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances)

## Updates for VMware vCenter Server instances

### NSX component and port group configuration setting updates

The current release applies the VMware NSX for vSphere 6.3.5 component update. For more information about components, see [vCenter Server Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-bill-of-materials).

For VMware vCenter Server instances that are deployed in V2.2 or later releases, the NSX and port group configuration settings have changed. For more information, see the *NSX and port group configuration settings* section in [vCenter Server Software Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-bill-of-materials#nsx-and-port-group-configuration-settings).

### New option for DNS configuration

You can now select the deployment of a single Microsoft Windows Server Virtual Server Instance (VSI) for Microsoft Active Directory (AD) or two high availability Microsoft Windows virtual machines in the management cluster. For releases before V2.2, the single Microsoft Windows VSI for Microsoft AD was automatically deployed by default. The new option to select two Microsoft Windows virtual machines provides more privacy and the option to backup and restore the virtual machines that use the Veeam service.

You must provide 2 Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows virtual machines. Use the Microsoft Windows Server 2012 R2 Standard edition license and/or the Microsoft Windows Server 2012 R2 Datacenter edition license. You have 30 days to activate the virtual machines.
{:note}

For more information, see the *System settings* section in [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances#system-settings)​.

### Increased number of clusters per instance

You can now add up to 10 clusters to VMware vCenter Server instances that are deployed in or upgraded to V2.2. and later releases. For more information, see [Adding and viewing clusters for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vcenter-server-instances)​.

## Updates for VMware vSphere clusters

### Component license bundles available to Business Partner customers

Business Partner users can now select from four component license bundles when ordering a new vSphere cluster. Choose from Standard with Management, Advanced, Advanced with Networking, or Advanced with Networking and Management. You can also include additional VMware components to your order. However, the option to Bring Your Own License is not available.

For more information, see the *Licensing settings* section in [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters).

## Updates for NetApp ONTAP Select instances

The current release applies the update of NetApp ONTAP Select 9.3.

### Increased number of SATA drives for high capacity IBM Cloud Bare Metal Servers

Thirty Four SATA drives are now available for NetApp ONTAP Select high capacity {{site.data.keyword.baremetal_short}}. For more information, see [Technical specifications for NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-netapp-ontap-select-overview#technical-specifications-for-netapp-ontap-select-instances).

## Updates for add-on services

### Increased bandwidth option for F5 on IBM Cloud

You can now select a maximum bandwidth of 10 Gbps when you install the F5 on {{site.data.keyword.cloud_notm}} service for Cloud Foundation and vCenter Server instances. For more information, see [Considerations for F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5-on-ibm-cloud-overview).

### KMIP for VMware on IBM Cloud

You can now order a Cloud Foundation or vCenter Server instance with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service included or add the service to an existing Cloud Foundation or vCenter Server instance after initial deployment.

This service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and delete the encryption keys. In addition, this service provides management capability to maintain the associations between the client credentials and those encryption keys.

For more information, see [Considerations for KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_considerations.html).

### IBM Spectrum Protect Plus on IBM Cloud

The IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service is now available to instances that are deployed in (or upgraded to) V2.2 or later releases.

This service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement it as a stand-alone solution or you can integrate it with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance.

The IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service provides data protection for the workload VMs only.

For more information, see [Managing IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-ibm-spectrum-protect-plus-on-ibm-cloud).

### Managed Services

Managed services for Veeam on {{site.data.keyword.cloud_notm}} and for Zerto on {{site.data.keyword.cloud_notm}} are now available to VMware vCenter Server and VMware Cloud Foundation instances. Request these managed services if you do not want to manage the complexity of your own solution and environment.

The Veeam on {{site.data.keyword.cloud_notm}} service seamlessly integrates with your VMware hypervisors to help your enterprise achieve high availability (HA). A fully managed backup environment can be deployed using both Veeam backup software and IBM Resiliency Backup as a Service.

The Zerto on {{site.data.keyword.cloud_notm}} service provides replication and disaster recovery capabilities, which can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}. A fully managed disaster recovery (DR) environment can be deployed using both Zerto DR software and IBM Resiliency Services.

You can request managed services for your instances from the **Getting Started** page, either by placing a new instance order, or by adding the service to an existing instance.

For more information, see the following topics:
* [Requesting services for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-managed-services-for-veeam-on-ibm-cloud)
* [Requesting services for Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-managed-services-for-zerto-on-ibm-cloud)

## New and updated documentation

* A comparison table with the supported functions for Cloud Foundation and vCenter Server instances, as well as VMware vSphere clusters, is now available in the documentation. You can see, at a glance, the differences between the functions that each type of instance provides. For more information, see [Offering comparison chart](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-offering-comparison-chart).

* The VLANs and software Bill of Materials (BOM) is now provided in the documentation for Cloud Foundation, vCenter Server, and VMware vSphere clusters.

  For more information, see the following topics:

  * [vCenter Server Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-bill-of-materials)
  * [Cloud Foundation Bill of Materials](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cloud-foundation-bill-of-materials)
  * [VMware vSphere Bill of Materials](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-bill-of-materials)

## User interface updates and enhancements

Improvements are made throughout the user interface:

* When you order an instance, all hardware options are now filtered by location and the unavailable options are displayed in the disabled state.
* The **{{site.data.keyword.baremetal_short}}** configuration is now automatically populated when you order a vSphere cluster based on existing configurations. You can update the configuration according to your requirements.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
