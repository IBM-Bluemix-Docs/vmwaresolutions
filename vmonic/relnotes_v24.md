---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Release notes for V2.4

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and additional tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

For more information, see [Addressing Spectre and Meltdown vulnerabilities](../vmonic/trbl_fix_spectre.html).

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

**Note**: The reference architecture documents are available in English only.

## Skylake Xeon CPU support

Starting with the V2.4 release, the following new Bare Metal Server CPU models are available for deployment for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}}, and VMware Federal on {{site.data.keyword.cloud_notm}} instances and clusters:

* Dual Intel Skylake Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz
* Dual Intel Skylake Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz
* Dual Intel Skylake Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz

For more information, see the *Bare Metal Server settings* section in:

* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Ordering new vSphere clusters](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [Ordering VMware Federal instances](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## Updates for VMware vCenter Server instances

### Network File System performance enhancement

The performance level of 10 IOPS/GB, designed for the most demanding workload types, is no longer limited to specific {{site.data.keyword.CloudDataCent_notm}}, but is now available to all. For more information, see the *Storage* section in [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

## Updates for VMware Federal instances

### New IBM Cloud Data Center option

You can now deploy VMware Federal instances to the DAL08 - Dallas, TX {{site.data.keyword.CloudDataCent_notm}}. For more information, see the *IBM Cloud Data Center availability* section in [Requirements and planning for VMware Federal instances](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability).

## Updates for add-on services

### IBM Spectrum Protect Plus on IBM Cloud

The current release installs IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 on all newly deployed instances. For more information about the new features in IBM Spectrum Protect Plus V10.1.1 Patch 1, see [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

A new option is now available for you to choose between public network and private network for HCX interconnects when you order this service. For more information, see [Ordering VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_ordering.html).

## New and updated documentation

### Reference architecture documentation

The {{site.data.keyword.vmwaresolutions_short}} architecture document is now available in the *Reference* section of the user documentation. The reference architecture document is available in English only. For more information, see [Solution overview](../archiref/solution/solution_overview.html).

### Services documentation

The services information has been restructured and the navigation has been improved to easily locate relevant information when ordering services.

For more information, see the following topics:

* [Ordering F5 on {{site.data.keyword.cloud_notm}}](../services/f5_ordering.html)
* [Ordering FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_ordering.html)
* [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_ordering.html)
* [Ordering Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_ordering.html)
* [Ordering Hytrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_ordering.html)
* [Ordering IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/spp_ordering.html)
* [Ordering KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_ordering.html)
* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_ordering.html)
* [Ordering Zerto on {{site.data.keyword.cloud_notm}}](../services/zerto_ordering.html)

## User interface updates and enhancements

The user interface is updated and provides the following enhancements:

* The add cluster and add service panes now use a page format, with a better organized layout, which allows you to complete tasks more efficiently.
* The functionality of the **Deployed Instances** page is enhanced with search, pagination, and sorting features. These improvements allow you to locate your instances very quickly.
* The instance detail page now uses a left navigation menu, which allows you to access the instance information easily and quickly.
* Various error messages and tooltip enhancements have been made to assist you in selecting the appropriate setting on the user interface.
