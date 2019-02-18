---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-01"

---

# Release notes for V2.6

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to vulnerabilities related to Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

For more information, see [Addressing Spectre and Meltdown vulnerabilities](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-addressing-spectre-and-meltdown-vulnerabilities).

## High Performance with Intel Optane option

This release provides the option to add high-performance cache for vSAN storage when you are ordering a new instance or when you add a new vSAN cluster after initial deployment.

This option allows you to increase the number of storage capacity disks from eight to a maximum of ten.

The High Performance with Intel Optane option is available only for customized configurations with Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140 processors.

For more information, see the appropriate ordering topic for your instance or cluster type.

## Enabling a public or private network

You can now deploy vCenter Server and vCenter Server with Hybridity Bundle instances, as well as VMware vSphere clusters, with public and private network interface cards (NICs) enabled or private only NICs enabled. This option is also available when you add a new cluster to your vCenter Server and vCenter Server with Hybridity Bundle instance.

Some add-on services require public NICs and are not available if you select to enable a private only network.

For more information, see the _Network interface settings_ section in the following topics:

* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances#network-interface-settings)
* [Ordering vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-with-hybridity-bundle-instances#network-interface-settings)
* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters#network-interface-settings)

## Deleting ESXi servers

You can now delete any ESXi server from your vCenter Server, vCenter Server with Hybridity Bundle, or Cloud Foundation instance if you meet the minimum requirements for your instance.

For more information on ESXi server requirements, see the following topics:

* [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-instances)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-with-hybridity-bundle-instances)
* [Expanding and contracting capacity for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-expanding-and-contracting-capacity-for-cloud-foundation-instances)

## Updates for VMware vCenter Server instances

This release applies the following upgrades and improvements:

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## Updates for VMware vCenter Server with Hybridity Bundle

### Removing the Hybridity Bundle from a vCenter Server instance

You can now remove the Hybridity Bundle license from your vCenter Server instance. To do so, you are required to replace the VMware NSX and VMware vSAN rental license keys with Bring Your Own License (BYOL) keys and open a support ticket to cancel charges for the rental licenses.

For more information, see [Removing the Hybridity Bundle from a vCenter Server instance](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-removing-the-hybridity-bundle-from-a-vcenter-server-instance).

### vCenter Server with Hybridity Bundle availability

Business Partners can now order a vCenter Server with Hybridity Bundle instance. Business Partners cannot upgrade an existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance and cannot remove the Hybridity Bundle from a vCenter Server with Hybridity Bundle instance.

For more information, see the following topics:

* [vCenter Server with Hybridity Bundle overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-with-hybridity-bundle-overview)
* [Ordering vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-with-hybridity-bundle-instances)

## Updates for VMware Cloud Foundation instances

This release applies the following upgrades and improvements:

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## Updates for add-on services

### HyTrust KeyControl on IBM Cloud

The HyTrust KeyControl on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.5 and later releases. The service simplifies the management of encrypted workloads by automating and simplifying the lifecycle of encryption keys. The service can easily manage encryption keys at scale by using FIPS 140-2 compliant encryption. By using this service, you can manage the encryption keys for all your virtual machines and encrypted data stores, and scale it to support thousands of encrypted workloads in large deployments.

You can order instances with the service included when you order your instance, or add this service to your existing instances later.

For more information, see the following topics:
* [Components and considerations for HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hytrust-keycontrol-on-ibm-cloud-overview)
* [Managing HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-hytrust-keycontrol-on-ibm-cloud)

### HyTrust CloudControl on IBM Cloud

The current release installs HyTrust CloudControl 5.4 on all newly deployed instances. For more information about the new features in HyTrust CloudControl 5.4, see [HyTrust CloudControl v 5.4 Online Documentation Set](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html).

### HyTrust DataControl on IBM Cloud

The current release installs HyTrust DataControl 4.2 on all newly deployed instances. For more information about the new features in HyTrust DataControl 4.2, see [What's New in HyTrust DataControl 4.x](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm).

### Veeam on IBM Cloud support for vSphere ESXi V6.5 update 2c

Beginning in V2.6, new instances and new hosts are provisioned using the vSphere ESXi V6.5 Update 2c. If you are using Veeam Backup and Replication, Veeam recommends that you update your Veeam on {{site.data.keyword.cloud_notm}} instance to V9.5u3a or later to ensure the best compatibility with vSphere ESXi 6.5 Update 2c.

It is recommended that existing Cloud Foundation instances that have Veeam on {{site.data.keyword.cloud_notm}} installed also update to V9.5u3a or later.

For more information on Veeam on {{site.data.keyword.cloud_notm}}, see [Veeam on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam-on-ibm-cloud-overview).

### VMware HCX on IBM Cloud

The current release installs VMware HCX 3.5.1 on all newly deployed instances. For more information about the new features in HCX 3.5.1, see [VMware NSX Hybrid Connect Documentation](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/index.html).

### Zerto on IBM Cloud support for vSphere ESXi V6.5 update 2c

If you update existing hosts to vSphere ESXi V6.5 update 2, and have previously installed Zerto on {{site.data.keyword.cloud_notm}}, the  Zerto Virtual
Replication console might show the `Unsupported ESX Version` warning message under the Zerto Virtual Replication Appliances (VRAs) status.

For more information about how to resolve this warning message, see:

* [Zerto Virtual Replication Interoperability Matrix](http://s3.amazonaws.com/zertodownload_docs/6.0_Latest/Zerto%20Virtual%20Replication%20Operability%20Matrix.pdf)
* [Updating a ZVM to Support Zerto-Approved Host Releases Prior to a Full ZVR Update](https://www.zerto.com/myzerto/knowledge-base/updating-a-zvm-to-support-zerto-approved-host-releases-prior-to-a-full-zvr-update/)

## New and updated documentation

### Reference architecture documentation
The {{site.data.keyword.vmwaresolutions_short}} architecture document is updated to include important considerations to understand your responsibilities for managing and operating your VMware instance.

For more information, see [Post-deployment considerations for your VMware instance](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-post-deployment-considerations-for-your-vmware-instance).

## User interface updates and enhancements

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
