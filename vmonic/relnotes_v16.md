---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# Release notes for V1.6

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and additional tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Updates for VMware Cloud Foundation instances

The following components are new or updated:

*  SDDC Manager 2.2.1
*  IBM management components V1.6
*  New hardware specifications: **Small** or **Standard**, depending on your requirements.
*  New data centers available for deployment: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seoul**, **SNG01 - Singapore**, and **SYD04 - Sydney**.

For the complete list of components, see [VMware Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html).

## Updates for VMware vCenter Server instances

### Hardware enhancements for vCenter Server instances

Starting with the V1.6 release, several enhancements are available for your vCenter Server instances.

*  Full implementation of the V2.0 specification for the vCenter Server offering. For more information, see the [VMware vCenter Server on {{site.data.keyword.cloud_notm}} solution architecture](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0).
*  New hardware specifications: **Small**, **Medium**, or **Large**, depending on your requirements.
*  New data centers available for deployment: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seoul**, **SNG01 - Singapore**, and **SYD04 - Sydney**.
*  At least two ESXi servers in your instance order, with VMware vSphere DRS (Distributed Resource Scheduler) and VMware HA (High Availability) enabled by default.
*  Up to seven NFS file shares can be added when you order instances. The management components (vCenter, PSC, NSX Manager and Controllers, CloudDriver) are now running on an NFS file share for high availability.
*  Automatic deployment and configuration of customer-managed VMware NSX Edge Services Gateway.

Because of these changes, you cannot use as is (or upgrade) your existing vCenter Server instances in the current release. vCenter Server instances from pre-V1.6 releases are still visible on the {{site.data.keyword.vmwaresolutions_short}} console in view-only mode. These instances are marked on the user interface as **Deprecated** with a warning symbol icon.

The following actions are available on the pre-V1.6 vCenter Server instances:

*  View the information on the instance details page. The information that is displayed in the instance properties reflects the data as of the V1.6 release date and it is no longer refreshed.
*  Open the VMware vSphere Web Client and use the instance in vCenter.
*  Delete instance.

All other actions on pre-V1.6 instances are no longer available.

### Networking enhancements for vCenter Server instances

*  A public subnet with 16 IP addresses on the public VLAN is ordered on your behalf to allow your VMs (virtual machines) to access the Internet.
*  A private subnet with 64 IP addresses on the private VLAN is ordered on your behalf to allow your VMs to access the SoftLayer® internal network.
*  NSX controllers are deployed with anti-affinity rules and run on separate ESXi servers in a 3-node deployment configuration.
*  New VMware NSX Edge Services Gateway for customer usage.

   An additional NSX Edge Services Gateway (ESG) is now deployed as part of the new vCenter Server instances that you are ordering.

   This ESG is provided to be used with your own VMs for communications between the private and public subnets that are ordered on your
   behalf and it includes two interfaces: one interface is connected to the virtualized VXLANs associated with your VMs and the
   other one is connected to the public VLAN. In addition, the following settings are configured:
   *  Firewall rule to allow all outgoing traffic from the private subnet range of IP addresses.
   *  SNAT (Source Network Address Translation) rule (disabled by default) to translate all IP addresses from the private subnet to a
   single IP address on the public subnet.
   * VMware HA (High Availability) is configured to use a new port group that is shared between the management ESG and the customer-managed
   ESG.

   This ESG is deployed for all instance hardware types, and customers can modify the configuration. For more information, see the
   following topics:
   *  [Configuring your network to use the customer-managed NSX Edge Services Gateway with your VMs](../vcenter/vc_esg_config.html)
   *  [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Usability enhancements

Improvements are made throughout the user interface:

*  The main navigation on the console is greatly improved through the introduction of the left navigation pane with access to all areas of the user interface. You can quickly order a new instance, view your deployed instances, review system notifications, change settings, and access the online documentation.
*  The new **Getting Started** page accessible from the left navigation pane provides you enough details directly on the console to help you make an informed decision about the components of the instance you are ordering. On the **Getting Started** page, you are also guided step-by-step through the process of ordering an instance, starting with meeting all prerequisites for ordering an instance, such as required user accounts, and ending with placing an order.
*  The summary details for both Cloud Foundation instances and vCenter Server instances are consolidated onto a single page, which is accessible from the **Deployed Instances** menu on the left navigation pane. From that page, you can select the appropriate tab to filter either Cloud Foundation instances or vCenter Server instances.
* If you have Zerto disaster recovery installed on your instance, you can access the Zerto console from the service details page directly with a single click. For more information, see [Ordering, viewing, and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html) and [Ordering, viewing, and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html).
