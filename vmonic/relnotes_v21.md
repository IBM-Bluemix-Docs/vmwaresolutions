---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# Release notes for V2.1

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and additional tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715 and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

For more information, see [Addressing Spectre and Meltdown vulnerabilities](../vmonic/trbl_fix_spectre.html).

## VMware HCX on IBM Cloud

The HCX on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.1 or later releases. This service can seamlessly extend the networks of your on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows bi-directional migration of virtual machines (VMs) between your on-premises data centers and {{site.data.keyword.cloud_notm}} without any change. By establishing a layer 2 bridge, HCX leverages WAN optimization, deduplication, compression, and encryption to more quickly and securely migrate data over a Direct Link or VPN tunnel. The bulk migration of VMs is backwards compatible with VMware vSphere 5.1 or greater. If you use vSphere 6.0 or greater on-premises, you can vMotion live (powered-on) VMs from on-premises to an {{site.data.keyword.CloudDataCent_notm}}. You are not required to have VMware NSX installed in your data center when using HCX.

You can order Cloud Foundation or vCenter Server instances with the HCX on {{site.data.keyword.cloud_notm}} service included when you order your instance, or add this service to your existing instances later from the **Services** tab on the instance details page.

You can also order an on-premises HCX instance for licensing and activation of your on-premises HCX installation.

For more information, see the following topics:
* [Considerations for HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)
* [Managing HCX on {{site.data.keyword.cloud_notm}}](../services/managinghcx.html)
* [Considerations for on-premises HCX instances](../services/standalone_considerations.html)
* [Ordering on-premises HCX instances](../services/standalone_orderingserviceinstances.html)

## More flexible Bring Your Own License model for VMware Cloud Foundation and vCenter Server

Bring Your Own License (BYOL) or purchase IBM-provided subscription licensing when creating a new cluster is now available to V2.1 and later VMware Cloud Foundation instances and VMware vCenter Server instances allowing you to leverage your existing component key or to rent the license from IBM. Prior to V2.1, you could not purchase IBM-provided licensing for a specific VMware component if you BYOL. At this time, only VMware vSphere and VMware vSAN are available for licensing per cluster.

Additionally, when adding nodes to a cluster that is licensed with your key, the console prompts you to provide a new license key if the number of nodes exceeds the key capacity.

For more information, see the following topics:

* [Adding and viewing clusters for Cloud Foundation instances](../sddc/sd_addingviewingclusters.html)
* [Adding and viewing clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html)
* [FAQ about BYOL](../vmonic/faq_byol.html)

## Zerto on IBM Cloud service component updates

For Zerto on {{site.data.keyword.cloud_notm}} service deployed in V2.1 and later Cloud Foundation instances and vCenter Server instances, Zerto Virtual Replication 5.5u2 is provisioned. Zerto virtual replication appliances (VRAs) are now deployed to the management datastore (either vSAN or Endurance) rather than to the local datastore for performance reasons. If you have existing VRAs, you should consider migrating their storage to the management datastore for better performance.

For more information, see [Zerto on {{site.data.keyword.cloud_notm}} overview](../services/addingzertodr.html).

## Updates for VMware vCenter Server instances

### Network MTU configuration settings

For V2.1 or later releases, new vCenter Server instances are ordered with the setting Public Distributed Virtual Switch (DVS) as MTU 1500 (default). For more information, see _Network MTU configuration settings_ in [vCenter Server Bill of Materials](../vcenter/vc_bom.html).

### Automatic application of VMware ESXi patches and updates to hosts

In V2.0 and earlier VMware vCenter Server instances, patches were not automatically applied to ESXi hosts that were added to a cluster.

In V2.1 and later instances, the automation applies patches to new ESXi hosts so that the patch level matches the patch level at the time that the initial instance was provisioned. You are responsible for manually applying any future patches and updates.
When VMware patches and updates become available in future releases, the automation will scan the ESXi hosts of your existing instances and email you a reminder to apply the latest patches and updates manually.

For more information, see [Applying updates to vCenter Server instances](../vcenter/vc_applyingupdates.html).

### Price estimates for VMware NSX license upgrades

You can now see a price estimate before submitting an order to upgrade to the VMware NSX Advanced or Enterprise edition. The pricing is based on the number of ESXi hosts in the vCenter Server instance. This purchase only changes the NSX license key and upgrades your VMware NSX Base edition to the Advanced or Enterprise edition. The purchase does not upgrade the NSX software version.

For more information, see [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html).

### Maximum servers per cluster increases from 32

For the default cluster in an instance, you can deploy or expand up to 51 servers. For all subsequent clusters in an instance, you can deploy or expand up to 59 servers. For more information, see [Adding and viewing clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html).

**Note:** This capability is available only to instances that are deployed in V2.1 and later. Instances that are upgraded to V2.1 from pre-V2.1 releases do not have this functionality.

### User customized IBM Cloud Bare Metal Server configuration options

User customized Bare Metal Servers configuration now offers the Dual Intel Xeon Gold 6140 with 36 cores total, 2.3 GHz.

For more information, see the following topics:
* [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

### Individual NFS file share configurations

You now have the option to configure NFS file shares on an individual basis. Select the file size and performance level for each individual file share or select the same file size and performance level for all of the file shares that you order.

For more information, see the following topics:
* [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)
* [Adding and viewing clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html)

## User interface updates and enhancements

Improvements are made throughout the user interface:

* The **Order Instance** option has been removed from the left navigation pane. Click **Getting Started** to complete the steps to order an instance.
* The **Subdomain Prefix** field from the **Basics** page when ordering an instance is renamed to **Subdomain Label**.
* In addition to viewing your cost estimate on the **Summary** page when ordering a primary or secondary vCenter Server or Cloud Foundation instance, you can now calculate a cost estimate on any panel as you provide the details for your instance order.
* Breadcrumb navigation is added to the **Deployed Instances** page as an alternative method of navigation, thus reducing the number of steps required to reach parent pages on these pages.
* Various error messages and tooltip enhancements have been made to assist you in selecting the appropriate setting on the user interface.

## New and updated documentation

A new developerWorks recipe is available with step-by-step instructions on how to attach dedicated storage to existing {{site.data.keyword.vmwaresolutions_full}} deployments using NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}. For more information, see [Steps to attach dedicated storage to VMware Solutions on IBM  Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/).
