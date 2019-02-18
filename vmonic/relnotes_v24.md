---

copyright:

  years:  2016, 2019

lastupdated: "2018-06-22"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Release notes for V2.4

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

For more information, see [Addressing Spectre and Meltdown vulnerabilities](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-addressing-spectre-and-meltdown-vulnerabilities).

## National Language support

Starting with the V2.4 release, National Language Support (NLS) is available for {{site.data.keyword.vmwaresolutions_short}}.
All features on the console, including the user documentation, are available in multiple languages.

The following languages are supported, in addition to English:
* German
* Spanish
* French
* Italian
* Japanese
* Korean
* Brazilian Portuguese
* Simplified Chinese
* Traditional Chinese

## Skylake Xeon CPU support

Starting with the V2.4 release, the following new Bare Metal Server CPU models are available for deployment for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}}, and VMware Federal on {{site.data.keyword.cloud_notm}} instances and clusters:

* Dual Intel Skylake Xeon Silver 4110 processor / 16 cores total, 2.1 GHz
* Dual Intel Skylake Xeon Gold 5120 processor / 28 cores total, 2.2 GHz
* Dual Intel Skylake Xeon Gold 6140 processor / 36 cores total, 2.3 GHz

For more information, see the *Bare Metal Server settings* section in:

* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances#bare-metal-server-settings)
* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters#bare-metal-server-settings)
* [Ordering VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vmware-federal-instances#bare-metal-server-settings)

## Updates for VMware vCenter Server instances

### Network File System performance enhancement

The performance level of 10 IOPS/GB, designed for the most demanding workload types, is no longer limited to specific {{site.data.keyword.CloudDataCent_notm}}, but is now available to all. For more information, see the *Storage* section in [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-overview#technical-specifications-for-vcenter-server-instances).

## Updates for VMware Federal instances

### New IBM Cloud Data Center option

You can now deploy VMware Federal instances to the DAL08 - Dallas, TX {{site.data.keyword.CloudDataCent_notm}}. For more information, see the *IBM Cloud Data Center availability* section in [Requirements and planning for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-requirements-and-planning-for-vmware-federal-instances#ibm-cloud-data-center-availability).

## Updates for add-on services

### IBM Spectrum Protect Plus on IBM Cloud

The current release installs IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 on all newly deployed instances. For more information about the new features in IBM Spectrum Protect Plus V10.1.1 Patch 1, see [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

A new option is now available for you to choose between public network and private network for HCX interconnects when you order this service. For more information, see [Ordering VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-vmware-hcx-on-ibm-cloud).

## New and updated documentation

### Reference architecture documentation

The {{site.data.keyword.vmwaresolutions_short}} architecture document is now available in the *Reference* section of the user documentation. For more information, see [Solution overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-overview-of-ibm-cloud-for-vmware-solutions).

### Services documentation

The services information is restructured and the navigation is improved to easily locate relevant information when you order services.

For more information, see the following topics:

* [Ordering F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-f5-on-ibm-cloud)
* [Ordering FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-fortigate-security-appliance-on-ibm-cloud)
* [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-fortigate-virtual-appliance-on-ibm-cloud)
* [Ordering Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-hytrust-cloudcontrol-on-ibm-cloud)
* [Ordering Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-hytrust-datacontrol-on-ibm-cloud)
* [Ordering IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-ibm-spectrum-protect-plus-on-ibm-cloud)
* [Ordering KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_ordering.html)
* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-veeam-on-ibm-cloud)
* [Ordering Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-zerto-on-ibm-cloud)

## User interface updates and enhancements

The user interface is updated and provides the following enhancements:

* The add cluster and add service panes now use a page format, with a better organized layout, which allows you to complete tasks more efficiently.
* The functionality of the **Deployed Instances** page is enhanced with search, pagination, and sorting features. These improvements allow you to locate your instances quickly.
* The instance detail page now uses a left navigation menu, which allows you to access the instance information easily and quickly.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
