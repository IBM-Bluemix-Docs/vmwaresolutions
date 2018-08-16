---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# Release notes for V1.4

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and additional tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Component updates for Cloud Foundation instances

The following components are new or updated:

* VC/PSC (vCenter/Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* A new Windows VSI (Virtual Server Instance) is ordered for Microsoft Active Directory (AD) and DNS (Domain Name System) services, which are required for multi-site configuration support in this release. This VSI has the following specifications: Windows 2012 R2 (8 GB RAM / 2 CPU cores / 100 GB disk / Dual 1 Gbps private uplinks).

For more information, see [Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html).

## Component updates for vCenter Server instances

The following components are new or updated:

### VMware NSX for vSphere 6.2.4

VMware NSX for vSphere 6.2.4 is now installed by default on all vCenter Server instances (previously on Cloud Foundation instances only).

As part of the NSX installation, the NSX Manager is installed and licensed on all new instances that are deployed. In addition, an NSX Edge is created for instance management, but you can create your own NSX Edge components if required. For more information about the NSX Edge, see the _VMware NSX Edge_ section on this page.

**Note**: The NSX Controller is not installed on vCenter Server instances (the way it is installed on Cloud Foundation instances). If you are using VXLAN or distributed logical routers for your vCenter Server instances, then you must install the NSX Controller yourself.

For more information about the enhancements that are introduced in VMware NSX for vSphere 6.2.4, its requirements, and known issues, see [NSX for vSphere 6.2.4 release notes](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### VMware NSX Edge

NSX Edge is now included as part of the new vCenter Server instances that you are ordering. NSX Edge provides network edge security and gateway services to isolate a virtualized network.

During instance deployment, a Management VMware NSX Edge Services Gateway (ESG) is deployed by IBM. This ESG is used by the IBM management virtual machines to communicate with specific external IBM management components that are related to automation. This ESG is deployed to include two interfaces: one interface is connected to the {{site.data.keyword.cloud_notm}} private VLAN, and the other one is connected to the {{site.data.keyword.cloud_notm}} public VLAN.

To ensure security, firewall rules are in place to allow only outbound HTTPS communications that are initiated by the management virtual machines. This ESG is deployed in a Large configuration, and only IBM Support can modify the configuration. For more information, see the following topics:

* [vCenter Server technical specifications](../vcenter/vc_vcenterserveroverview.html)
* [Does the management services NSX Edge pose a security risk?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### NSX license

A VMware NSX Base for Service Providers Edition license per node is ordered.

### New subnet address block

A subnet block of 16 public portable addresses per node is ordered.

## Service charge model updates

The service charge model is simplified:

* For Cloud Foundation instances, the _VMware Cloud Foundation instance service_, _VMware Cloud Foundation storage service_, and
   _VMware Solutions Hypervisor_ fees are discontinued.
* For vCenter Server instances, the _VMware vCenter Server instance_ and _VMware Solutions Hypervisor_ fees are discontinued.
* For both instance types, a new _Support and Services_ fee is introduced, which is a monthly fee that is applied to each node.

## Updates to instance networking topology

This release includes the following topology enhancements for your instances:

* For both Cloud Foundation instances and vCenter Server instances: Optimized networking configuration, that is, only the primary public and private IP addresses that are assigned by SoftLayer® are attached to ESXi servers. Portable private addresses are no longer deployed for management traffic.
* For Cloud Foundation instances only: Windows AD SSO (Active Directory Single Sign-On) and Domain Name System (DNS) server

**Note**: Because of these changes, you cannot use your existing pre-V1.4 instances in the current release. To reuse the configuration of your existing instances, you must upgrade them to the current version. For more information, see [Upgrading instances from pre-V1.4](movinginstances.html).

## Multi-site configuration support for Cloud Foundation instances

You can now deploy either a single Cloud Foundation instance, just like in previous releases or, in addition, deploy secondary instances that are attached to a primary instance. The multi-site configuration model uses a hub and spoke topology with a primary site and a maximum of 7 secondary sites.

For more information, see [Multi-site configuration for Cloud Foundation instances](../sddc/sd_multisite.html).

## Enhancements to the deployment of Zerto disaster recovery

* For Cloud Foundation instances, the deployment of Zerto disaster recovery is automated rather than handled through a support ticket. All Zerto components, such as a private portable subnet, a Windows VSI (Virtual Service Instance), and the Zerto license charges are listed on the estimated cost, so you can review before you place your order.
* For vCenter Server instances, the deployment of Zerto disaster recovery is done through a support ticket, as in the previous release. However, NSX Edge and the public portable subnet are no longer needed, since they are now included in the base deployment. The charges for a private portable subnet, a Windows VSI (Virtual Service Instance), and the Zerto license still apply.

For more information, see [Zerto disaster recovery](../services/addingzertodr.html).

## Instance order process

The instance order process is greatly simplified:

* For both Cloud Foundation instances and vCenter Server instances, the SoftLayer Credentials page is no longer displayed during the order process. The SoftLayer credentials that are defined on the Settings page are used by default and you are prompted to update them only if they do not meet the requirements.
* In addition, for vCenter Server instances, only the **Large** option for the **Hardware** type and the **10 Gbps Dual** setting for the **Uplink Port Speed** are now available, which reduces the number of settings to specify when ordering.

For more information, see the following topics:

* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

## Instance management

New features and improvements are made to the instance management process:

* For Cloud Foundation instances, you can view the user name and passwords for various instance components on the instance details page. For more information, see [Viewing Cloud Foundation instances](../sddc/sd_viewinginstances.html).
* For vCenter Server instances, you can now install software updates and patches for IBM components directly from the console. For more information, see [Applying updates and patches to vCenter Server instances](../vcenter/vc_applyingupdates.html).

## Console notifications

You can now configure console notifications on the **Settings** page. By default, the setting is enabled, which means that you receive a notification in the console for all events. You can also disable notifications for the console on the **Settings** page.

For more information, see the following topics:

* [User accounts and settings](useraccount.html)
* [Notifications](notifications.html)
