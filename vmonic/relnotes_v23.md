---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Release notes for V2.3

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and additional tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715 and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

For more information, see [Addressing Spectre and Meltdown vulnerabilities](../vmonic/trbl_fix_spectre.html).

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

This release introduces the VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle offering. The vCenter Server with Hybridity Bundle is a hosted private cloud that helps quickly and easily extend your on-premises infrastructure into the cloud. The VMware environment is based on IBM-provided VMware Software Defined Data Center licenses and includes the VMware HCX on {{site.data.keyword.cloud_notm}} service that easily and securely connects a vSphere 5.0+ environment on-premises with {{site.data.keyword.cloud_notm}} sites for seamless infrastructure hybridity and true application mobility.

The HCX on {{site.data.keyword.cloud_notm}} service is available only through the vCenter Server with Hybridity Bundle instance. You can upgrade your existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance after first applying the base vCenter Server V2.3 software update. For more information, see [Applying updates to vCenter Server instances](../vcenter/vc_applyingupdates.html).

For more information about the vCenter Server with Hybridity Bundle, see the following topics:

* [vCenter Server with Hybridity Bundle overview](../vcenter/vc_hybrid_overview.html)
* [Requirements and planning for vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_planning.html)
* [Ordering vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_orderinginstance.html)

## Delete cluster support for vCenter Server and Cloud Foundation instances

You can now delete clusters from an instance without having to delete the entire instance. For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.

For more information, see the following topics:

* [Adding, viewing, and deleting clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Adding, viewing, and deleting clusters for Cloud Foundation instances](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## Updates for VMware vCenter Server instances

This release applies the following upgrades and improvements:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 with patch level ESXi650-201803001 applied)
*	VMware vCenter Server 6.5 Update 1g

### Enhancements for vCenter Server instances and clusters

Starting with the V2.3 release, the following new CPU models are available for deployment when you choose the **Customized** Bare Metal setting:
* Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz
* Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz

For more information, see the following topics:

* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)
* [Adding, viewing, and deleting clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html)

## Updates for VMware Cloud Foundation instances

This release applies the following upgrades and improvements:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 with patch level ESXi650-201803001 applied)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Updates for VMware Federal instances

### DNS configuration for VMware Federal instances

You now have the option to select the deployment of a single Microsoft Windows Server Virtual Server Instance (VSI) for Microsoft Active Directory (AD) or two high availability Microsoft Windows virtual machines in the management cluster. For V2.2, the single Microsoft Windows VSI for Microsoft AD was automatically deployed by default. The new option to select two Microsoft Windows virtual machines provides more privacy and the option to backup and restore the virtual machines using the Veeam service.

**Note:** You must provide two Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows virtual machines. Use the Microsoft Windows Server 2012 R2 Standard edition license and/or the Microsoft Windows Server 2012 R2 Datacenter edition license. You have 30 days to activate the virtual machines.

For more information, see the *Network interface settings* section in [Ordering VMware Federal instances](../vcenter/vc_fed_orderinginstance.html#network-interface-settings)​.

### Add and delete cluster support for VMware Federal Instances

You can now use clusters to manage ESXi servers in VMware Federal instances that are deployed in V2.3 and later releases for better resource management and high availability. The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default. You can view the cluster details on the instance overview page or add up to a total of 10 clusters to an instance. When you are expanding or contracting capacity for an instance, you can select which cluster to add ESXi servers to or to remove ESXi servers from.

You also have the option to delete one or more clusters from the instance without deleting the entire instance.

For more information, see [Adding, viewing, and deleting clusters for VMware Federal instances](../vcenter/fed_addviewdeleteclusters.html).

## Updates for add-on services

### HyTrust CloudControl on IBM Cloud

The HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later releases. The service enforces and controls compliance against security standards, and provides role-based access control (RBAC). When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.cloud_notm}} data center.

You can order instances with the service included when you order your instance, or add this service to your existing instances later.

For more information, see the following topics:
* [Components and considerations for HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)
* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

The HyTrust DataControl on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later releases. The service offers strong encryption with integrated key management to secure workloads throughout their lifecycles. The service can provide encryption at both the operating system level and data level, which means that any directory, folder, or file within a workload can be encrypted and decrypted.

You can order instances with the service included when you order your instance, or add this service to your existing instances later.

For more information, see the following topics:
* [Components and considerations for HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)
* [Managing HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

The current release installs IBM Spectrum Protect&trade; Plus V10.1.1, as the default backup service, on all newly deployed instances. For more information about the new features in IBM Spectrum Protect Plus V10.1.1, see [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## New and updated documentation

A new developerWorks recipe is available with step-by-step instructions on how to add storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment. For more information, see [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## User interface updates and enhancements

The user interface is updated and provides the following enhancements:
* **Consistency**: The user interface now provides a consistent look and feel with other services on {{site.data.keyword.cloud_notm}}.
* **Ease of access**: You can now access the VMware offerings directly from the {{site.data.keyword.cloud_notm}} **Catalog**.
* **Streamlined and simplified ordering experience**: You can now complete ordering a VMware instance and deploying its add-on services in a single interface. In addition, estimated cost is calculated and shown instantly in the same interface so that you can adjust your configuration based on your cost plan.
* The option to Bring Your Own License (BYOL) when ordering instances or adding clusters is not available to Business Partner users.
* Various error messages and tooltip enhancements have been made to assist you in selecting the appropriate setting on the user interface.
