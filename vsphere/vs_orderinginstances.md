---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering new vSphere clusters

To deploy a highly customizable VMware virtualized platform, order a VMware vSphere cluster on {{site.data.keyword.cloud}}. Use this procedure to define a new vSphere cluster.

This procedure guides you through the selection of VMware components, {{site.data.keyword.cloud_notm}} Bare Metal Server settings, storage settings, and networking choices, to create a new cluster. After you place the order, the cluster configuration is captured so that you can come back and continue to scale out the cluster as needed. After the order is completed, you can manually configure the VMware cluster based on your requirements.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
*  You reviewed the requirements and considerations in [Requirements and planning for vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-requirements-and-planning-for-vmware-vsphere-on-ibm-cloud).

## System settings

You must specify the following system settings when you order a new vSphere cluster.

### Cluster name

The cluster name must be unique within your account.

## Licensing settings

Select the VMware components to be ordered with your cluster and specify the licensing option for the components.

### Component bundles for IBM Business Partner users

If you're an IBM Business Partner user, you can select a component license bundle when you order a new vSphere cluster. The following bundles are available:

Table 1. IBM Business Partner component bundles for vSphere clusters

| Bundle | Components                   |
|:------------------------- |:----------------------- |
| Standard with Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

You can also include the following VMware components in your order:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

For IBM Business Partner users, the Bring Your Own License (BYOL) option is not available.
{:note}

### Individual components for non-Business Partner users

If you're a non-Business Partner, you can select the following components for your vSphere cluster:
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

The VMware vSAN component is not available when you order VMware vSphere Enterprise Plus 6.0. If you plan to use your own license for VMware vSphere Enterprise Plus 6.0, an {{site.data.keyword.cloud_notm}} infrastructure ticket is opened on your behalf. The ticket requests that the vSphere licenses of the ordered {{site.data.keyword.baremetal_short}} are replaced with your provided licenses.
{:note}

### Licensing options

You have the following options for licensing the selected VMware components:
* **Include license with purchase**: In this case, a new license for the VMware component is purchased on your behalf. A combined VMware license is generated to match the cluster size of the order.
* **I will provide the license**: In this case, you use your own license for the VMware component.

If you choose to purchase any license, except for vSphere Enterprise Plus and vCenter Server, and you order multiple ESXi servers, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to combine license keys. You are responsible to follow up with the ticket to ensure that you use only the license keys that the DevOps team generates.

Using individual license keys together with the combined license keys does not meet the payment requirements for the licenses you will need.
{:important}

## Bare Metal Server settings

### Data center location

Select the {{site.data.keyword.CloudDataCent_notm}} where the cluster is to be hosted.

**Notes:**
* If you select a vSAN component, the location list is filtered by SSD availability.
* The FRA05 data center does not support Broadwell bare metal server.
* The LON05 data center does not support SAP-certified or Broadwell bare metal server.

### Skylake

When you select **Skylake**, you can choose the CPU and RAM combination for the Bare Metal Server according to your needs. Options available depend on whether you selected the VMware vSAN component.

Table 2. Options for Skylake {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

### SAP-certified

The **SAP-certified** tab is not available if you selected VMware vSAN previously. When you select **SAP-certified**, you cannot alter the CPU or RAM settings.

Based on your requirements, select a Bare Metal Server configuration:
  * Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 192 GB RAM
  * Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 384 GB RAM
  * Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 768 GB RAM
  * Dual Intel Xeon E5-2690 v4 processor / 28 cores total, 2.6 GHz / 512 GB RAM
  * Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.2 GHz / 1024 GB RAM
  * Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.2 GHz / 2048 GB RAM
  * Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.2 GHz / 4096 GB RAM

### Broadwell

When you select **Broadwell**, you can choose the CPU and RAM combination for the Bare Metal Server according to your needs. Options available depend on whether you selected the VMware vSAN component.

Table 3. Options for Broadwell {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Number of Bare Metal Servers

The number of ESXi servers that you want add to the vSphere cluster. All the ESXi servers have the same configuration.
* If you selected the VMware NSX component, a minimum of three servers is required.
* If you selected the VMware vSAN component, a minimum of four servers is required.

## Storage settings

For orders without vSAN, ESXi servers are ordered with a 12-disk chassis, with two disks for the ESXi operating system (OS).

For orders with vSAN, ESXi servers are ordered with a 12-disk chassis and four disks ordered: two for the ESXi OS and two reserved for caching. These settings are configured by default and cannot be changed. You can order more capacity disks by selecting **Disk Type and Size for vSAN Capacity Disks** and **Number of vSAN Capacity Disks**.

If you select the VMware vSAN component for the cluster, specify the following settings.
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of eight, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 10 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.

## Network interface settings

You must specify the following network interface settings when you order a new vSphere cluster.

### Host name prefix

The host name is used for all bare metal server orders. It is recommended to use the host name for all management virtual machines, such as vCenter Server and NSX.

The host name prefix must meet the following requirements:
* The name must start and end with an alphanumeric character.
* Only alphanumeric and dash (-) characters are allowed.
* The maximum length is 10 characters.

### Subdomain label

The subdomain label must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The subdomain label must start and end with an alphanumeric character.
*  The maximum length of the subdomain label is 10 characters.
*  The subdomain label must be unique within your account.

### Domain name

The domain name is used for all {{site.data.keyword.baremetal_short}} and must meet the following requirements:
* The name must consist of two or more strings that are separated by period (.)
* Only alphanumeric and dash (-) characters are allowed.
* Each string must start with an alphabetic character and end with an alphanumeric character, and the last string can contain only alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.
* The length of other strings must be in the range 1 - 63 characters.
* The maximum length of the domain name is 189 characters.

### Public or private network

Network interface card (NIC) enablement settings are based on your selection of either **Public and Private Network** or **Private Network Only**. The following add-on services require public NICs and are not available if you select the private option:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLANs

Network settings are based on your selection of either **Order New VLANs** or **Select Existing VLANs**.

One public VLAN and two private VLANs are required for your cluster order. The two private VLANs are trunked into each Bare Metal Server.

#### Order New VLANs
Select to order one new public VLAN and two new private VLANs.

#### Select Existing VLANs  
Depending on the {{site.data.keyword.CloudDataCent_notm}} that you selected, existing public and private VLANs might be available.

  When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
  * **Public VLAN** is for public network access.
  * **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}.
  * **Secondary private VLAN** is for VMware features such as vSAN.
  * **Primary Subnet** is assigned to physical hosts for public network access.
  * **Primary Private Subnet** is assigned to physical hosts for management traffic.

**Important:**
* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.

#### FortiGate Physical Appliance 300 Series HA Pair

You can also select whether to include the FortiGate Physical Appliance 300 Series HA Pair to secure your cloud environment. For more information, see [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortigate-security-appliance-on-ibm-cloud-overview).

## Order summary

Based on your configurations, the estimated cost is instantly generated and displayed in the **Order Summary** pane on the right. Click **Pricing details** to generate a PDF document that provides the estimate details.

## Procedure to order vSphere clusters

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** on the left navigation pane, and then click **VMware vSphere** in the **Virtual Data Centers** section.
2. On the **VMware vSphere on IBM Cloud** page, click **Create**.  
   Ensure that you are on the **Create New** tab and that **New cluster** is displayed in the **Cluster Configurations** list.
3. Enter the cluster name.
4. Select the VMware components:
  * If you're an IBM Business Partner, select a license bundle and any additional available VMware components.
  * If you are a non-Business Partner, select the component, edition if any, and specify the licensing option.
  When you choose to Bring Your Own License (BYOL) for VMware vSphere Enterprise Plus, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to request the default vSphere licenses on your ordered {{site.data.keyword.baremetal_short}} to be replaced with your provided licenses.   

    **Important:** You are responsible to track the ticket so that you replace the vSphere license on the newly ordered ESXi servers. This way the {{site.data.keyword.cloud_notm}} infrastructure grants the cancellation of the initially provided {{site.data.keyword.cloud_notm}} infrastructure vSphere license charge. To replace your ESXi vSphere license, see [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.
5. Complete the Bare Metal Server settings:
   1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the cluster.
   2. Select the Bare Metal Server configuration.
      * When you select **Skylake** or **Broadwell**, specify the CPU model and the RAM size.
      * When you select **SAP-certified**, choose the CPU model.
   3. Specify the number of Bare Metal Servers.
6. If you selected the **VMware vSAN** component, complete the vSAN storage configuration. Specify the disk types for the capacity and cache disks, and the number of disks. If you want more storage, check the **High-Performance Intel Optane** box.
7. Complete the network interface settings:
   1. Enter the host name prefix, subdomain label, and domain name.
   2. Select the network setting of either **Public and Private Network** or **Private Network Only**.
   3. Select the network interface that you want to use.
    * If you want to order new public and private VLANs, click **Order New VLANs**.
    * If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs** and specify the VLANs and optionally the subnets.
    4. Specify whether to apply the FortiGate Physical Appliance 300 Series HA Pair to secure your cloud environment.  
8. In the **Order Summary** pane, verify the cluster configuration and the estimated cost.
   * To save the configuration as a template without placing an order, click **Save Configuration**.
   * To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Provision**.

   Only the {{site.data.keyword.baremetal_short}} are installed. You are responsible for installing and configuring various components after cluster deployment, such as VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

### Results

If you saved the cluster configuration as a template, you get a console notification that the configuration is saved successfully, and then you can find the template in the **Cluster Configurations** list.

If you placed an order, the deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

The vSphere clusters, unlike the vCenter Server and Cloud Foundation instances, are not displayed on the **Deployed Instances** page.
{:note}

### Related links

* [Ordering vSphere clusters based on existing configurations](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-vsphere-clusters-based-on-existing-configurations)
* [Scaling existing clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-existing-vsphere-clusters)
* [Scaling clusters created outside of the console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-clusters-created-outside-of-the-console)
