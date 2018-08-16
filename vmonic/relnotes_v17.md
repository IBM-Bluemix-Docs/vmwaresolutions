---

copyright:

  years:  2016, 2018

lastupdated: "2017-07-05"

---

# Release notes for V1.7

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and additional tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Updates for VMware Cloud Foundation instances

This update applies the following upgrades and improvements:
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* Stability improvements to the IBM CloudDriver component
* EVC mode (based on the Intel “Haswell” 2690-V3 processor) is enabled on pre-existing VMware deployments that are on V3 servers at the time of upgrade.

  **Note**: EVC mode is not enabled for any existing or new deployments on V4 servers.

* VMware Cloud Foundation deployments that were deployed prior to May 22 and are therefore using V3 servers will now order V4 servers when adding a new node to the instance. These servers have 256 GB of memory; if you require 512 GB of memory, after adding the servers, open a support ticket to request a server upgrade to 512 GB of memory. For more  information about contacting IBM Support, see [Contacting IBM Support](trbl_support.html).

For more information about components, see [Technical specifications for Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

### Update process requirements

Depending on the complexity of your Cloud Foundation instance deployment and whether you have a multi-site configuration, the update process might require a sequence of steps that you must complete as displayed on the **Update and Patch** tab on the console. For more information, see [Applying updates to Cloud Foundation instances](../sddc/sd_applyingupdates.html#applying-updates-to-cloud-foundation-instances).

## Updates for VMware vCenter Server instances

### Cluster support

Starting with the V1.7 release, you can use clusters to manage ESXi servers in vCenter Server instances for better resources management and high availability. The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default. You can view the cluster details or add up to a total of five clusters to an instance from the newly introduced **Infrastructure** tab on the instance details page. When you are expanding or contracting capacity for an instance, you can select which cluster to add ESXi servers to or to remove ESXi servers from. For more information, see [Adding and viewing clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html).

### Enhancements to the deployment of Zerto disaster recovery

The deployment of Zerto disaster recovery is now automated rather than handled through a support ticket. All Zerto components, such as a private portable subnet, a Windows VSI (Virtual Service Instance), and the Zerto license charges are listed on the estimated cost, so you can review before you place your order. For more information, see [Deployment process of Zerto disaster recovery](../services/addingzertodr.html).

### NSX license upgrade capabilities

You can upgrade your NSX license edition from the **Summary** tab of your vCenter Server instance. The license upgrade replaces all existing NSX SoftLayer licenses in your account with the new license. For more information, see [Viewing vCenter Server instances](../vcenter/vc_viewinginstances.html).

## Usability enhancements

Improvements are made throughout the user interface:
* The **Properties** tab on the Cloud Foundation instance details page is renamed to **Summary**. You can now view details of the instance, the access information of the instance-related components, and the instance deployment history on this tab.
* A new **Infrastructure** tab is introduced on the Cloud Foundation instance details page. You can view, add, or remove ESXi servers on this tab.
* The documentation for {{site.data.keyword.vmwaresolutions_short}} has a new format and is now completely integrated into the Bluemix catalog, together with the Bluemix set of documentation. You can access the documentation in one of the following ways:
  * From the {{site.data.keyword.vmwaresolutions_short}}, click **Docs** at the left of the banner.
  * From the Bluemix documentation catalog, scroll down to the **Compute & Services** section and click **{{site.data.keyword.vmwaresolutions_short}}**.
