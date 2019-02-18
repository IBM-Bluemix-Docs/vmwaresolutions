---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering VMware Federal instances

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware Federal instance. VMware Federal instances help you disconnect the open management connection and secure your deployed instance.

Currently, only vCenter Server instances support VMware Federal on {{site.data.keyword.cloud}}.
{:note}

## Requirements to order VMware Federal instances

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
* You reviewed the information in [Requirements and planning for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-requirements-and-planning-for-vmware-federal-instances).
* You reviewed the instance and domain name format. The domain name and subdomain label are used to generate the user name and server names of the instance.

Table 1. Value format for instance and domain names

| Name        | Value Format      |
  |:------------- |:------------- |
  | Domain name | `<root_domain>` |  
  | vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
  | vCenter Server FQDN | `vcenter.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |
  | Single Sign-On (SSO) site name | `<subdomain_label>` |
  | Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `<n>` is the sequence of the ESXi server. The maximum length is 50 characters. |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |

Don't modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## System settings

You must specify the following system settings when you order a VMware Federal instance.

### Instance name

The instance name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The instance name must start with an alphabetic character and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Primary or secondary

Order a new primary instance. Deploying a secondary instance for high availability is not supported currently.

## Licensing settings

IBM-provided licenses for the following VMware components:

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5u1
* NSX Service Providers 6.4 (Base, Advanced, or Enterprise edition)
* (For vSAN clusters) vSAN 6.6 (Advanced or Enterprise edition)

### Attention

* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge will be incurred at time of order, but the license charge will subsequently be credited to your account.

## Bare Metal Server settings

Bare Metal settings are based on your data center selection and bare metal server configuration.

### Data center location

Select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.

### Skylake

Specify the CPU model and RAM for the Bare Metal Server.

Table 2. Options for Skylake {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

### Broadwell

Specify the CPU model and RAM for the Bare Metal Server.

Table 3. Options for Broadwell {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB |

### Number of Bare Metal Servers

You can configure the number of ESXi servers in the range 2 - 20.

All ESXi servers share the same configuration. In post-deployment, you can add four more clusters. For vSAN storage settings, 4 ESXi servers are required for both the initial and post-deployment clusters. For more information about minimum of ESXi servers, see [Is a two-node vCenter Server instance highly available?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions#is-a-two-node-vcenter-server-instance-highly-available-)

## Storage settings

Storage settings are based on your selection of Bare Metal Server configuration and the storage type.

### vSAN storage

Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of eight, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 10 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.
* **vSAN License**: Select the vSAN 6.6 license edition (Advanced or Enterprise).

### NFS storage

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

The number of file shares must be in the range of 1 to 32.
{:note}

* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of Shares**: When using the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
* **ADD NFS**: Select to add individual file shares that use different configuration settings.

Table 3. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |

## Network interface settings

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

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{:note}

### DNS configuration

Select the Domain Name System (DNS) configuration for your instance:

* **Single Public Windows VSI for Active Directory/DNS**: A single Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and virtual machines are registered, is deployed and can be looked up.
* **Two highly available dedicated Windows Server VMs on the management cluster**: For V2.3 and future releases, two Microsoft Windows virtual machines are deployed, helping enhance security and robustness.

You must provide two Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows virtual machines. Use the Microsoft Windows Server 2012 R2 Standard edition license or the Microsoft Windows Server 2012 R2 Datacenter edition license or both.
{:important}

Currently, each license can be assigned to only one single physical server and covers up to two physical processors. By using one Standard edition license, you can run two virtualized Microsoft Windows virtual machines per 2-processor server. Therefore, two licenses are required since two Microsoft Windows virtual machines are deployed in two different hosts.

You have 30 days to activate the virtual machines.

For more information about ordering Windows licensing, see [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Order summary

Based on your selected configuration for the instance, the estimated cost is instantly generated and displayed in the **Order Summary** section on the right pane. Click **Pricing details** at the bottom of the right pane to generate a PDF document that provides the estimate details.

## Procedure to order VMware Federal instances

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** from the left navigation pane and then click **vCenter Server** in the **Virtual Data Centers** section.
2. On the **VMware vCenter Server on IBM Cloud** page, click the **vCenter Server** card and click **Create**.
3. On the **vCenter Server** page, enter the instance name.
4. Click **Primary Instance** to deploy a single instance in the environment.
5. Specify the VMware NSX license edition.
6. Complete the Bare Metal Server configuration:
   1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
   2. Select the **Skylake** or **Broadwell** CPU model and the amount of **RAM**.
7. Complete the storage configuration.
   * If you select **vSAN Storage**, specify the disk types for the capacity and cache disks, the number of disks, and the vSAN License edition. If you want more storage, check the **High-Performance Intel Optane** box.
   * If you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Size**, and **Performance**.
   * If you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add NFS** label and select the **Size** and **Performance** for each individual file share. You must select at least one file share.
8. Complete the network interface configuration.
   1. Enter the host name prefix, subdomain label, and root domain name.
   2. Select the DNS configuration.
9. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   3. Review the estimated cost of the instance by clicking the cost link under **Calculate Cost**. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. Click **Provision**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [Technical specifications for VMware Federal on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vmware-federal-on-ibm-cloud-overview#technical-specifications-for-vmware-federal-on-ibm-cloud-instances) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **cluster1** by default.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

## What to do next

View, manage, or secure the VMware Federal instance that you ordered.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components

   Exceptions to these activities include managing the shared storage file shares from the 	{{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

### Related links

* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing-up-for-required-accounts)
* [Viewing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vmware-federal-instances)
* [Expanding and contracting capacity for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vmware-federal-instances)
* [Adding, viewing, and deleting clusters for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vmware-federal-instances)
* [Securing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-securing-vmware-federal-instances)
* [Deleting VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-deleting-vmware-federal-instances)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
