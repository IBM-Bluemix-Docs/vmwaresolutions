---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# Release notes for V1.3

This release includes new features, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and more tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Shared File-level Storage for vCenter Server instances

You can now add shared NAS (Network Attached Storage) to vCenter Server instances. The addition of this feature enables you to run production workloads on vCenter Server and to prevent loss of data if node failures occur. NFS (Network File System) File Storage is provided as an option in the ordering process for vCenter Server instances. For more information, see [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html).

## Zerto disaster recovery removal

Whether you ordered Zerto disaster recovery as part of your instance or added it to an existing instance, you can now remove this service when you no longer need it. After you request to remove the service from the console, you are guided by IBM Support to complete the removal process.

For more information, see the following topics:

* [Disaster recovery removal](../services/removingzertodr.html)
* [Viewing Cloud Foundation instances](../sddc/sd_viewinginstances.html)
* [Viewing vCenter Server instances](../vcenter/vc_viewinginstances.html)

## VMware NSX Edge for Cloud Foundation instances

NSX Edge is now included as part of the new Cloud Foundation instances that you are ordering. NSX Edge provides network edge security and gateway services to isolate a virtualized network.

During instance deployment, a Management NSX Edge Services Gateway (ESG) is deployed by IBM. This ESG is used by the IBM management virtual machines to communicate with specific external IBM management components that are related to automation. This ESG is deployed to include two interfaces: one interface is connected to the {{site.data.keyword.cloud_notm}} private VLAN, and the other one is connected to the {{site.data.keyword.cloud_notm}} public VLAN.

To ensure security, firewall rules are in place to allow only outbound HTTPS communications that are initiated by the management virtual
machines. This ESG is deployed in a Large configuration, and only IBM Support can modify the configuration.

For more information, see the following topics:

* [Technical specifications for Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [Does the management services NSX Edge pose a security risk?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Instance order process

The instance order process is improved for both Cloud Foundation instances and vCenter Server instances:

* The summary page displays all applicable terms and conditions for all components and services that are ordered, for easy access to review and agree with these terms before you place the order.
* You can save and print the order summary for your instance before you place the order. With this new function, you can review the instance settings and cost, modify the components that are ordered if needed, obtain approval, and then come back to your order.

For more information, see the following topics:

* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

## Instance management

New features and improvements are made to the instance management process:

* For both Cloud Foundation instances and vCenter Server instances, you can see and review the estimated cost of your ESXi servers before you decide to add them to your instance. After you specify how many servers you want to add, the estimated cost per server, per month, is displayed on the console. For more information, see [Expanding and contracting capacity for Cloud Foundation instances](../sddc/sd_addingremovingservers.html) and [Expanding and contracting capacity for vCenter Server instances](../vcenter/vc_addingremovingservers.html).
* For both Cloud Foundation instances and vCenter Server instances, the total number of instances is displayed at the top of the summary page. You can also order an instance with one click from the instance summary pages. Also, on the summary page you can view detailed order status during provisioning. When you hover over the status that is displayed, you can see more details about the current step or the error, if any.
* For Cloud Foundation instances, the instance details page displays the deployment history of the instance, with information about the deployment status step by step. For more information, see [Viewing Cloud Foundation instances](../sddc/sd_viewinginstances.html).
* For Cloud Foundation instances, the usability of the updates and patches process is improved by providing more details about the update on the **Update and Patch** page, such as: the downtime that is required for a patch, the time that the update was scheduled for, and visual indication when a required patch needs to be applied before the current one. For more information, see [Applying updates and patches to Cloud Foundation instances](../sddc/sd_applyingupdates.html).

## Email notifications

You now receive a notification by email when a new order was placed for instance deployment and when a service was added, deployed, or removed from your instance. The notification settings are enabled by default. Based on your preferences, you can set what notifications you want to receive on the **Settings** page. For more information, see [User accounts and setting](useraccount.html).
