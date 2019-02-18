---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and deleting Single-node Trial for Migration and App Modernization instances

Review the planning requirements before you order a Single-node Trial for Migration and App Modernization instance.

## Requirements and planning for ordering Single-node Trial for Migration and App Modernization instances

Ensure that you confirm the following requirements and complete the following tasks.

### Prerequisites for on-premises HCX instances

* Requires VMware vSphere and vCenter 5.5 or higher.
* The vSphere environment must have distributed switches for the VMs that will be migrated to the {{site.data.keyword.cloud_notm}}.
* The HCX Manager Virtual Appliance must be able to be deployed on a private network in the on-premises environment and must be allowed to access the public internet.

### IBM Cloud infrastructure account

* To use {{site.data.keyword.vmwaresolutions_short}} to order instances, you must have an {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account. The cost of the components that are ordered in your instances is billed to that {{site.data.keyword.cloud_notm}} account.
*  Configure the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Settings** from the left navigation pane.

### Instance name requirements

Review the instance name requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The instance name must start with an alphabetic character and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

## Procedure to order Single-node Trial for Migration and App Modernization instances

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** from the left navigation pane and then click **Single-node Trial for Migration and App Modernization** in the **Virtual Data Centers** section.
2. On the **Single-node Trial for Migration and App Modernization** page, click **Continue**.
3. Complete the steps to request an {{site.data.keyword.cloud_notm}} infrastructure account or provide your existing **User Name** and **API Key** and click **Retrieve**.

 This section is hidden if the API key exists.
 {:note}
4. Enter the instance name.
5. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.  

 By default, the DAL09 {{site.data.keyword.CloudDataCent_notm}} is preselected. Select a different {{site.data.keyword.CloudDataCent_notm}} location, if needed.
 {:note}
6. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   4. Click **Provision**.

### Results

The deployment of the instance starts automatically and the on-premises HCX on {{site.data.keyword.cloud_notm}} service activation key is ordered.

#### Deployment process for HCX on IBM Cloud

The deployment of HCX on {{site.data.keyword.cloud_notm}} is automated. The following steps are completed by the {{site.data.keyword.vmwaresolutions_short}} automation process:
1. Three subnets are ordered for HCX from the {{site.data.keyword.cloud_notm}} infrastructure:
   * Two private portable subnets for HCX management.
   * One public portable subnet for activation and maintenance with VMware. This subnet is also used for HCX interconnects.

   The IP addresses in the subnets that are ordered for HCX are intended to be managed by the VMware on {{site.data.keyword.cloud_notm}} automation. These IP addresses cannot be assigned to VMware resources, such as VMs and NSX Edges, that are created by you. If you need more IP addresses for your VMware artifacts, you must order your own subnets from {{site.data.keyword.cloud_notm}}.
   {:important}
3. Three resource pools and VM folders for HCX are created, which are needed for the HCX interconnects, local HCX components, and remote HCX components.
4. A pair of VMware NSX Edge Services Gateways (ESGs) for the HCX management traffic is deployed and configured:
   * Public and private uplink interfaces are configured by using the ordered subnets.
   * The ESGs are configured as a pair of extra large edge appliances with High Availability (HA) enabled.
   * The firewall rules and network address translation (NAT) rules are configured to allow inbound and outbound HTTPS traffic to and from the HCX Manager.
   * The load balancer rules and resource pools are configured. These rules and resource pools are used to forward HCX-related inbound traffic to the appropriate virtual appliances of HCX Manager and vCenter Server (with embedded Platform Services Controller).
   * An SSL certificate to encrypt the HCX-related inbound HTTPS traffic that is coming through the ESGs is applied.

   The HCX management edge is dedicated to the HCX management traffic between the on-premises HCX components and the cloud-side HCX components. Do not modify the HCX management edge or use it for HCX network extensions. Instead, create separate edges for network extensions. In addition, by using a firewall or disabling the HCX management edge communications to the private IBM management components or public internet might adversely impact the HCX functionality.
   {:important}

5. The HCX Manager on {{site.data.keyword.cloud_notm}} is deployed, activated, and configured:
   * The HCX Manager is registered with vCenter Server.
   * The HCX Manager, vCenter Server (with embedded Platform Services Controller), and NSX Manager are configured.
   * The HCX fleet is configured.
   * Local and remote HCX deployment containers are configured.
6. The host name and IP address of the HCX Manager is registered with the DNS server of VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Viewing instance details

You can check the status of the deployment by viewing the instance details. Click **Deployed Instances** from the left navigation pane and locate the **vCenter Server Instances** or **On-premises HCX Instances** table to view information about the instances that you ordered.

When the instance is successfully deployed, the components that are described in the *Technical specifications* sections of this topic are installed on your VMware virtual platform and the on-premises HCX on {{site.data.keyword.cloud_notm}} service activation key is listed in the **On-premises HCX Instances** table.

The status of the instance changes to **Ready to Use** and you receive a notification by email.

### What to do next

Install the on-premises HCX Enterprise Manager and configure the connection to your HCX on {{site.data.keyword.cloud_notm}} instance.

1. Locate the on-premises activation key on the **Deployed Instances** page.
  1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
  2. In the **vCenter Server Instances** table, review the **Type** column to locate the Single-node Trial for Migration and App Modernization instance and make note of the instance name.
  3. Scroll to the **On-premises HCX Instances** table and review the **Name** column to locate the instance that has the same name as the single-node instance that you ordered with the *-OnPrem* suffix.
  4. Make note of the key in the **Activation key** field.
2. Obtain the on-premises HCX Enterprise Manager Open Virtual Appliance (OVA) from the HCX on {{site.data.keyword.cloud_notm}} HCX Manager console.
  1. Connect to the HCX Cloud Console.
    1. In the **vCenter Server Instances** table, click the Single-node Trial for Migration and App Modernization instance to view the instance details.
    2. Under **Access Information**, locate and make note of the vCenter credentials.
    3. Click **Services** from the left navigation pane.
    4. On the **Services** page, click **HCX on IBM Cloud**.
    5. On the **HCX on IBM Cloud** details page, locate and make note of the **HCX Cloud IP**.
    6. Ensure that you are connected to the VPN to access your {{site.data.keyword.cloud_notm}} private network.
    7. Click **View HCX Cloud Console**.
  2. In the **HCX Cloud Console**, complete the following steps:
      1. Click the **Administration** tab.
      2. On the **System Updates** tab, click **REQUEST DOWNLOAD LINK**.
      3. Click **COPY LINK**, and then use this link to download the HCX Enterprise Client onto an on-premises environment with access to your on-premises vSphere environment.
3. In the VMware vSphere Web Client, deploy the HCX Enterprise Client as an HCX Manager virtual appliance (HCX Manager) into your on-premises environment. For more information, see [Installing the HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    You must deploy the on-premises HCX Manager on a private network and allow it to access the public network. You can use an NSX Edge, Vyatta, or similar gateways to allow internet access to the on-premises HCX Manager. If the gateways used for private network access and public network access are different, it is recommended that you use the default gateway to allow for public network access and the on-premises **HCX Manager Admin Console** to create a static route for private network access.  
    {:note}
4. Use the on-premises activation key noted in step 1 to activate your on-premises HCX Enterprise Manager VM.
  1. Log in to your on-premises HCX Enterprise Manager VM by using the credentials that are specified when deploying the OVA.
  2. Enter the activation key when prompted.

  For more information, see [HCX Activation and Initial Configuration](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. A self-signed SSL certificate was generated by the HCX on {{site.data.keyword.cloud_notm}} service. You must import the certificate into the on-premises HCX Manager by completing the following steps:
    1. In the on-premises **HCX Manager Admin Console**, click the **Administration** tab.
    2. From the left navigation pane, click **Trusted CA Certificate**, and then click **IMPORT** on the right.
    3. Click **URL** and then enter the URL of the certificate you want to apply. This is the **HCX Cloud IP** (``https://<cloud-side public IP>``) that you can find on the HCX on {{site.data.keyword.cloud_notm}} service details page in the {{site.data.keyword.vmwaresolutions_short}} console.
    4. Click **APPLY**.
6. Continue the initial configuration and build the interconnect. For more information, see [Installing and Configuring VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Extend networks in VMware HCX from on-premises to {{site.data.keyword.cloud_notm}}. For more information, see [Extending Networks with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migrate VMs between on-premises and {{site.data.keyword.cloud_notm}}. For more information, see [Migrating Virtual Machines with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

You must manage the {{site.data.keyword.vmwaresolutions_short}} infrastructure components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console and can make your environment unstable.
{:important}

## Procedure to delete Single-node Trial for Migration and App Modernization instances

When you delete a Single-node Trial for Migration and App Modernization instance, the following components are released sequentially:

1. All deployed services
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.
{:note}

Complete the following steps to delete a Single-node Trial for Migration and App Modernization instance:

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

### Related links

* [vCenter Server and IBM Cloud Private guide](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction)
* [Open a Ticket for IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=en_US)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#/vm-documentation)
* [Obtaining the HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
