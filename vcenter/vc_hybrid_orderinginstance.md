---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering vCenter Server with Hybridity Bundle instances

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance. Your vCenter Server with Hybridity Bundle instance order includes the VMware Hybrid Cloud Extension (HCX) licensing and entitles you to the VMware HCX on {{site.data.keyword.cloud_notm}} service. You can also add services, such as [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto-on-ibm-cloud-overview) for disaster recovery.

## Requirements for ordering vCenter Server with Hybridity Bundle instances

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
*  You reviewed the information in [Requirements and planning for vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-requirements-and-planning-for-vcenter-server-with-hybridity-bundle-instances).
* You reviewed the instance and domain name format. The domain name and subdomain label are used to generate the user name and server names of the instance.

Table 1. Value format for instance and domain names

| Name        | Value Format      |
  |:------------- |:------------- |
  | Domain name | `<root_domain>` |  
  | vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
  | vCenter Server (with embedded PSC) FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |
  | Single Sign-On (SSO) site name | `<subdomain_label>` |
  | Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `<n>` is the sequence of the ESXi server. The maximum length is 50 characters. |

Don't modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## System settings

You must specify the following system settings when you order a vCenter Server with Hybridity Bundle instance.

### Instance name

The instance name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The instance name must start with an alphabetic character and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Primary or secondary

Select whether to order a new primary instance or a secondary instance for an existing primary instance.

## Licensing settings

The following VMware licenses are included with your vCenter Server with Hybridity Bundle instance order. You must specify the edition for the NSX and vSAN licenses.

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5u1
* NSX Service Providers 6.4 (Advanced or Enterprise edition)
* vSAN 6.6 (Advanced or Enterprise edition)

### Attention

* vCenter Server with Hybridity Bundle instances do not support Bring Your Own License.
* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want.

## Bare Metal Server settings

Bare Metal settings are based on your selection of {{site.data.keyword.CloudDataCent_notm}} and bare metal server configuration.

Four ESXi servers are required for both the initial and post-deployment clusters for vSAN configurations. All ESXi servers share the same configuration. In post-deployment, you can add four more clusters.

### Data center location

Select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.

### Skylake

When you select **Skylake**, you can choose the CPU and RAM combination for the Bare Metal Server according to your needs.

Table 2. Options for Skylake {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

### Broadwell

When you select **Broadwell**, you can choose the CPU and RAM combination for the Bare Metal Server according to your needs.

Table 3. Options for Broadwell {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Number of Bare Metal Servers

Four ESXi servers are selected by default and cannot be changed.

## Storage settings

VMware vSAN 6.6 is included with your vCenter Server with Hybridity Bundle instance order. Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of eight, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 10 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.

## Network interface settings

You must specify the following network interface settings when ordering a vCenter Server with Hybridity Bundle instance.

### Host name prefix

  The host name prefix must meet the following requirements:
  *  Only alphanumeric and dash (-) characters are allowed.
  *  The host name prefix must start and end with an alphanumeric character.
  *  The maximum length of the host name prefix is 10 characters.

### Subdomain label

The subdomain label must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The subdomain label must start with an alphabetic character and end with an alphanumeric character.
*  The maximum length of the subdomain label is 10 characters.
*  The subdomain label must be unique within your account.

### Domain name

The root domain name must meet the following requirements:
* The domain name must consist of two or more strings that are separated by period (.)
* The first string must start with an alphabetic character and end with an alphanumeric character.
* All strings, except for the last one, can contain only alphanumeric and dash (-) characters.
* The last string can contain only alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the FQDN (Fully Qualified Domain Name) for hosts and VMs (virtual machines) is 50 characters. Domain names must accommodate for this maximum length.
{:note}

### Public or private network

Network interface card (NIC) enablement settings are based on your selection of either **Public and Private Network** or **Private Network Only**. The following add-on services require public NICs and are not available if you select the private option:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Order New VLANs

Select **Order New VLANs** to order one new public VLAN and two new private VLANs.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each Bare Metal Server.

### Select Existing VLANs

Depending on the {{site.data.keyword.CloudDataCent_notm}} that you selected, existing public and private VLANs might be available.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each Bare Metal Server.

Select **Select Existing VLANs** to reuse existing public and private VLANs and choose from the available VLANs and subnets.


* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all of the VLANs you select are in the same pod because ESXi servers cannot be provisioned on mixed-pod VLANs.
{:important}

### DNS configuration

Select the Domain Name System (DNS) configuration for your instance:

* **Single Public Windows VSI for Active Directory/DNS**: A single Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and VMs are registered, is deployed and can be looked up.
* **Two highly available dedicated Windows Server VMs on the management cluster**: Two Microsoft Windows VMs are deployed, helping enhance security and robustness.

You must provide two Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows VMs. Use the Microsoft Windows Server 2012 R2 Standard edition license, or the Microsoft Windows Server 2012 R2 Datacenter edition license, or both.
{:important}

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license is capable of running two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information on ordering Windows licensing, see [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Services settings

When you order a vCenter Server with Hybridity Bundle instance, you can also order additional services. For more information about the services, see [Available services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Order summary

Based on your selected configuration for the instance and add-on services, the estimated cost is instantly generated and displayed in the **Order Summary** section on the right pane. Click **Pricing details** at the bottom of the right pane to generate a PDF document that provides the estimate details.

## Procedure to order vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** from the left navigation pane and then click **vCenter Server** in the **Virtual Data Centers** section.
2. On the **VMware vCenter Server on IBM Cloud** page, click the **vCenter Server with Hybridity Bundle** card and click **Create**.
3. On the **vCenter Server** page, enter the instance name.
4. Select the instance type:
   * Click **Primary Instance** to deploy a single instance in the environment or to deploy the first instance in a multi-site topology.
   * Click **Secondary Instance** to connect the instance with an existing (primary) instance in the environment for high availability and complete the following steps:
     1. Select the primary instance that you want the secondary instance to be connected with.
     2. For primary instances V2.8 or later, enter the vCenter Server administrator password for the primary instance.
     3. For primary instances V2.7 or earlier, enter the PSC administrator password for the primary instance.
5. Select the NSX license edition and the vSAN license edition.
6. Complete the Bare Metal Server settings.
  1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
  2. Select the **Skylake** or **Broadwell** CPU model and the amount of **RAM**.

  The **Number of Bare Metal Servers** is set to four by default and cannot be changed.
  {:note}
7. Complete the storage configuration. Specify the disk types for the capacity and cache disks, and the number of disks. If you want more storage, check the **High-Performance Intel Optane** box.
8. Complete the network interface configuration.
  1. Enter the host name prefix, subdomain label, and root domain name.
  2. Select the network setting of either **Public and Private Network** or **Private Network Only**.
  3. Select the VLAN configuration.
     *  If you want to order new public and private VLANs, click **Order New VLANs**.
     *  If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs**, and then select the public VLAN, the primary subnet, the private VLAN, the private primary subnet, and the secondary private VLAN.
  4. Select the DNS configuration.
9. Complete the configuration for the included HCX on {{site.data.keyword.cloud_notm}} service. For more information about how to provide settings for the service, see the _VMware HCX on IBM Cloud configuration_ section in [Ordering VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-vmware-hcx-on-ibm-cloud#vmware-hcx-on-ibm-cloud-configuration).
10. Select the add-on services to deploy into the instance by clicking the corresponding service card. If a service requires configuration, complete the service-specific settings and click **Add Service** on the card.  
For more information about how to provide settings for a service, see the corresponding service ordering topic.

8. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   4. Click **Provision**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [Technical specifications for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-with-hybridity-bundle-overview#technical-specifications-for-vcenter-server-with-hybridity-bundle-instances) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **cluster1** by default. If you ordered add-on services, the deployment of the services starts after your order is completed.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

## What to do next

View and manage the vCenter Server with Hybridity Bundle instance that you ordered.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account	 only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account	 when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the 	{{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

### Related links

* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing-up-for-required-accounts)
* [Viewing vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vcenter-server-with-hybridity-bundle-instances)
* [Multi-site configuration for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-multi-site-configuration-for-vcenter-server-with-hybridity-bundle-instances)
* [Adding and viewing clusters for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vcenter-server-with-hybridity-bundle-instances)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-with-hybridity-bundle-instances)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Deleting vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-deleting-vcenter-server-with-hybridity-bundle-instances)
