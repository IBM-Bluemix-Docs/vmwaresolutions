---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# General FAQ about IBM Cloud for VMware Solutions

Find answers to frequently asked questions about {{site.data.keyword.vmwaresolutions_full}}.

## What user accounts do I need for IBM Cloud for VMware Solutions?

* **IBMid account**. This account is required to access the {{site.data.keyword.vmwaresolutions_short}} console. The console is a stand-alone user interface that is separate from the {{site.data.keyword.slportal}}. For more information, see [Getting started](../index.html).
* **{{site.data.keyword.cloud_notm}} account**. This account is required for provisioning. You can sign up for an {{site.data.keyword.cloud_notm}} account by using an existing **IBMid** or by creating a new **IBMid**. 
* **{{site.data.keyword.cloud_notm}} infrastructure account**. This account, which was previously known as **IBM SoftLayer** account, is used to log in to the {{site.data.keyword.cloud_notm}} infrastructure customer portal that provides some additional function to manage infrastructure products and services. You can get an {{site.data.keyword.cloud_notm}} infrastructure account by upgrading your **{{site.data.keyword.cloud_notm}} account** to a Pay-As-You-Go type of account, or by linking your existing {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account with your {{site.data.keyword.cloud_notm}} account. The {{site.data.keyword.cloud_notm}} infrastructure account that you are using must meet certain requirements. For more information, see [Signing up for required accounts](signing_softlayer_account.html) and [{{site.data.keyword.cloud_notm}} infrastructure account requirements](slaccountrequirement.html).

## How do I associate my IBM Cloud infrastructure credentials with the IBM Cloud for VMware Solutions console?

When you order your instance for the first time, follow the instructions on the **Settings** page in the console to locate and copy the {{site.data.keyword.cloud_notm}} infrastructure user name and API key from the {{site.data.keyword.slportal}}. The {{site.data.keyword.cloud_notm}} infrastructure credentials are stored in the {{site.data.keyword.vmwaresolutions_short}} console after the first order. Future orders automatically use the stored credentials.

## How are my VMware virtual platform consumptions billed?

All costs for the physical and virtual infrastructure and the licenses that result from the instance are charged to your {{site.data.keyword.cloud_notm}} account. When you order an instance, you must have an {{site.data.keyword.cloud_notm}} account and provide the {{site.data.keyword.slapi_short}} key that is associated with the account.

## What are the differences among a vCenter Server instance, Cloud Foundation instance, and VMware vSphere cluster?

All instance types provide deployment choices for VMware virtual environments. However, the difference is the extent of customizability and automation.

* When you order a VMware vCenter Server instance, you deploy a VMware virtual environment with customized compute, storage, and network resources. For more information about the deployed components, see [Technical specifications for vCenter Server instances](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).
* When you order a VMware Cloud Foundation instance, you deploy a unified software-defined data center (SDDC) platform. For more information about the deployed components, see [Technical specifications for Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).
* When you order a VMware vSphere cluster, you obtain the maximum of flexibility to design and build your hosted VMware environment while incorporating VMware-compatible hardware. However, {{site.data.keyword.cloud_notm}} does not automate the installation, configuration, and bring-up of the optional VMware components for the VMware vSphere cluster.
* The functions that are supported for vCenter Server instances, Cloud Foundation instances, and vSphere clusters are different. For more information, see [Offering comparison chart](inst_comp_chart.html).

## What is included in a vCenter Server instance?

For more information, see [Technical specifications for vCenter Server instances](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

## What is included in a Cloud Foundation instance?

For more information, see [Technical specifications for Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## What is included in a vSphere cluster?
For more information, see [Components of VMware vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_vsphereclusteroverview.html).

## Is a two-node vCenter Server instance highly available?

It is recommended to deploy production workloads into environments that have at least three nodes.

The VMware vSphere DRS (Distributed Resource Scheduler) and VMware HA (High Availability) are enabled by default. However, best practices from VMware suggest that you place each of the three NSX Controllers on an individual node.

In the two-node minimum deployment, one node has one NSX Controller, and the other node has two NSX Controllers. If the node with two NSX Controllers goes down, NSX Controller operations are placed in read-only mode, and new VMs (virtual machines) or vMotion VMs might experience networking issues.

When a third node is added to a two-node cluster, vCenter Server automatically rebalances the three NSX Controllers across the three nodes and creates a highly available environment.

## Can I set up VMware vCenter 6.5 HA configuration?

No, it is not recommended. Failures in the {{site.data.keyword.vmwaresolutions_short}} functions might occur.

## Can clusters be renamed?

For vCenter Server instances, the first cluster that is created during deployment has a default name of **cluster1**. You can rename the default cluster in the VMware vSphere Client. When you add a cluster to a vCenter Server instance, you can specify the name that you want on the {{site.data.keyword.vmwaresolutions_short}} console.

**Note**: For Cloud Foundation instances, the default cluster name cannot be changed.

##How are patches managed?

IBM provides ongoing updates to the IBM code by deploying the IBM CloudDriver virtual server instance (VSI) on demand. IBM does not provide ongoing updates to add-on services such as Zerto on {{site.data.keyword.cloud_notm}} or Veeam on {{site.data.keyword.cloud_notm}}. Obtaining and installing these updates is your responsibility.

VMware updates are applied in a different manner based on the type of VMware instance you have deployed:

* For VMware Cloud Foundation instances, the updates to vSphere ESXi, NSX, vCenter, Platform Services Controller, and SDDC Manager components are provided through the {{site.data.keyword.vmwaresolutions_short}} console.
* For VMware vCenter Server instances:
  * For instances deployed at, or upgraded to, V2.1 or higher, newly deployed ESXi servers and clusters will be patched with recent, but not necessarily the latest, ESXi updates from VMware.
  * You are responsible for all other updates to VMware components, including ensuring that newly deployed ESXi servers and clusters have all the most recent updates you require.
  * For instances that were deployed at V2.0 or higher, VMware Update Manager (VUM) is integrated into your vCenter server. You can configure VUM to download ESXi updates from VMware.

For more information, see the following resources:
* [VMware Support](https://www.vmware.com/support.html)
* [Applying updates to vCenter Server instances](../vcenter/vc_applyingupdates.html)
* [Applying updates to Cloud Foundation instances](../sddc/sd_applyingupdates.html)

## Does the management services NSX Edge pose a security risk?

Although the VMware NSX Edge for management services is on a public subnet, security measures are in place to ensure that it does not pose a security risk. These measures are:
*  The NSX Edge firewall is configured to allow only outgoing HTTPS (TCP port 443) traffic that is initiated by the management virtual machines.
*  SNAT (source network address translation) is used so that private IP addresses are not visible outside the private network.
*  Remote access for the management services NSX Edge appliance is disabled.
*  Passwords for accessing the management services NSX Edge from the private network are randomized and encrypted.

## Does the customer-managed NSX Edge pose a security risk?

Although the customer-managed NSX Edge is connected to the public VLAN, security measures are in place to ensure that it does not pose a security risk. The following security measures are in place:
*  A firewall rule is in place to allow only outgoing traffic from the private subnet range of IP addresses.
*  A SNAT (Source Network Address Translation) rule (disabled by default) is in place to translate all IP addresses from the private subnet to a single IP address on the public subnet.
*  Remote access for the customer-managed NSX Edge appliance is disabled.
*  Passwords for accessing the customer-managed NSX Edge from the private network are randomized and encrypted.

## How do I choose the data centers for my instances?

The instance deployments have strict physical infrastructure requirements, which vary among {{site.data.keyword.CloudDataCents_notm}}. When you place your instance order, the available data centers are listed within regions and you can select the one that you want from the list.

For more information, see the _IBM Cloud Data Center availability_ sections in:
* [Requirements and planning for vCenter Server instances](../vcenter/vc_planning.html)
* [Requirements and planning for vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_planning.html)
* [Requirements and planning for Cloud Foundation instances](../sddc/sd_planning.html)
* [Requirements and planning for VMware vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [Requirements and planning for NetApp ONTAP Select instances](../netapp/np_planning.html)
* [Requirements and planning for VMware Federal instances](../vcenter/vc_fed_planning.html)

## How long does it take for my instance to be deployed?

You can check the status of the instance deployment by viewing the deployment history on the instance details page from the {{site.data.keyword.vmwaresolutions_short}} console.

## Does VMware vSphere on IBM Cloud use automation to install, configure, and bring up the VMware stack?

No. VMware vSphere on {{site.data.keyword.cloud_notm}} does not use the advanced automation that is found in the Cloud Foundation and vCenter Server platforms. Based on what you order, the platform delivers optional VMware licenses, ESXi servers, and, optionally, an HA-pair of FortiGate physical firewalls. If a new cluster is created, three new VLANs are also provisioned: a public VLAN and two private VLANs.

VMware ESXi is automatically installed on each bare metal server, but you are responsible for installing any additional VMware components like vCenter Server or NSX. While vSphere on {{site.data.keyword.cloud_notm}} ensures that VMware-compatible hardware is ordered based on the VMware components selected, no automation exists to configure and bring up the VMware environment. You are responsible for designing and architecting the IBM-hosted environment.

## How can I view a list of all notifications?

To view the complete notification history, click **Notifications** from the left navigation pane.

## What if I have a problem with IBM Cloud for VMware Solutions?

If you need assistance with {{site.data.keyword.vmwaresolutions_short}}, contact IBM Support through one of the support channels. For more information, see [Contacting IBM Support](trbl_support.html).

### Related links

* [Notifications](notifications.html)
* [Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server instances](../vcenter/vc_vcenterserveroverview.html)
* [Accessing the console](loginmethod.html)
* [User accounts and settings](useraccount.html)
