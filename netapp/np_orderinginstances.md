---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering NetApp ONTAP Select instances

To deploy a VMware virtualized platform with a dedicated and highly available software-define storage appliance, order a NetApp ONTAP Select instance.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
*  You reviewed the requirements and considerations in [Requirements and planning for NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-requirements-and-planning-for-netapp-ontap-select-instances).

Do not modify any values that are set during instance order or deployment. Doing so make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## System settings

When you order a NetApp ONTAP Select instance, you must specify the following basic settings.

### Instance name

The instance name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The instance name must start with an alphabetic character and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

## Network interface settings

You must specify the following network interface settings when you order a NetApp ONTAP Select instance.

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
* All strings, except for the last one, can include only alphanumeric and dash (-) characters.
* The last string can include only alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the FQDN (Fully Qualified Domain Name) for hosts and VMs (virtual machines) is 50 characters. Domain names must accommodate for this maximum length.
{:note}

## Licensing settings

You must upload four NetApp licensing files, one for each of the four {{site.data.keyword.baremetal_short}}. Contact your NetApp sales team to obtain the appropriate licensing for your high performance or high capacity deployment.

## Bare Metal Server settings

### Data center location

You must select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.

### Bare Metal Server configuration

Select a Bare Metal Server configuration based on your requirements:
* **High Performance (Medium)** – Premium license / Dual Intel Xeon E5-2650 v4 (24 cores total, 2.2 GHz) / 128-GB RAM / 22 1.9 TB SSD drives capacity per node / Effective capacity of a 4-node cluster – 59 TB
* **High Performance (Large)** – Premium license / Dual Intel Xeon E5-2650 v4 (24 cores total, 2.2 GHz) / 128 GB RAM / 22S 3.8 TB SSD drives capacity per node / Effective capacity of a 4-node cluster – 118 TB
* **High Capacity** – Standard license / Dual Intel Xeon E5-2650 v4 (24 cores total, 2.2 GHz) / 64 GB RAM / Thirty Four 4 TB SATA drives capacity per node / Effective capacity of a 4-node cluster – 190 TB

3.8 TB SSD (Solid-State Disk) drives are supported when they are made generally available in an {{site.data.keyword.CloudDataCent_notm}}.
{:note}

### Number of Bare Metal Servers

The number of ESXi servers of a NetApp ONTAP Select instance is 4 by default. You cannot change it. All the ESXi servers share configuration.

## Procedure to order NetApp ONTAP Select instances

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** on the left navigation pane, and then click **NetApp ONTAP Select** in the **Virtual Data Centers** section.
2. On the **NetApp ONTAP Select** page, click **Create**.
3. On the **NetApp ONTAP** page, enter the instance name.
4. Complete the network interface settings by entering the **Hostname Prefix**, **Subdomain Label**, and **Domain Name**.
5. Complete the licensing settings by clicking **Add License Files** to upload four NetApp license files that are required by the four {{site.data.keyword.baremetal_short}}.
6. Complete the Bare Metal Server settings:
   1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
   2. Select the Bare Metal Server configuration.
7. On the **Order Summary** pane, verify the instance configuration before you place the order.
    1. Review the settings for the instance.
    2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon from the PDF window.
    3. Ensure that the account to be charged is correct and then select the **I understand that the account listed below will be charged** check box.
    4. Click the link or links of the terms that apply to your order. Ensure that you agree with these terms and then select the **I have read and agreed to the Third-Party Service Agreements listed below** check box.
    5. Click **Provision**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [Technical specifications for NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-netapp-ontap-select-overview#technical-specifications-for-netapp-ontap-select-instances) are installed on your VMware virtual platform.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

## What to do next

View and manage the NetApp ONTAP Select instance that you ordered.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal}}, or any other means outside of the console. If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Powering off components

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

### Related links

* [Viewing NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-viewing-netapp-ontap-select-instances)
* [Deleting NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-deleting-netapp-ontap-select-instances)
* [NetApp ONTAP Documentation Center](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
