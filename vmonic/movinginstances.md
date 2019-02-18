---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrading your instances from pre-V1.4 releases

## Problem

The instance network topology in V1.4 and later releases is different from releases earlier than V1.4. Because of this change, the instances that were deployed in pre-V1.4 releases cannot be used in their state in the current release.

## Resolution

In V1.4 and later releases, several network topology enhancements are available for your instances:
* (Applies to all instances): Optimized networking configuration. Because the {{site.data.keyword.cloud}} account that you are using must be either a VRF (Virtual Routing and Forwarding) account or must have VLAN spanning enabled if it is a classic (non-VRF) account, a second portable IP address is not needed. Only the primary {{site.data.keyword.cloud_notm}} infrastructure portable IP address is required for deployment.
* (Applies to Cloud Foundation instances only): Multi-site deployment capability with Microsoft Windows AD SSO (Active Directory Single Sign-On) and Domain Name System (DNS) server.

If you have not migrated or deleted your instances from pre-V1.4 releases, they might still be visible on the {{site.data.keyword.vmwaresolutions_short}} console in view-only mode. These instances are marked on the user interface as **Deprecated** with a warning symbol icon.

The information that is displayed in the instance properties reflects the data as of the V1.4 release date and it is no longer refreshed.
{:note}

The following actions are available on the pre-V1.4 instances:
*  View the information on the instance details page.
*  View instance backup information.
*  Open the vSphere Web Client and use the instance in vCenter.
*  Request instance restore by opening an {{site.data.keyword.cloud_notm}} Support ticket.
*  Delete instance.

All other actions on pre-V1.4 instances are no longer available.

If you have pre-V1.4 instances and you plan to continue to use them, you can upgrade them by creating new instances and then moving your existing configurations to these new instances.

To move your pre-V1.4 instances to new instances, complete the following steps in the vSphere Web Client:
1. From your pre-V1.4 instance, export all VMs (virtual machines).
2. Create an instance in the current release.
3. Import all exported VMs from **Step 1**.
4. Use your new instance.

For more information about exporting and importing VMs, see your VMware vSphere documentation.

If you need assistance with {{site.data.keyword.vmwaresolutions_short}}, [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support) through one of the support channels.
