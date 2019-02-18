---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Installing and configuring HCX on the source

The on-premises installation entails deploying the HCX management appliance and registering it with the vCenter and one or more VCF/VCS HCX enabled cloud endpoints.

## Installing the HCX Manager Appliance

Install the HCX Manager appliance in the on-premises vCenter.

1. Log in to **My VMware** and download the Hybrid Cloud Services OVA file from the product download page.
2. Open a browser and log in to the vSphere Web Client. This task cannot be performed from the vSphere Client. View the **Home** tab.
3. In the **Inventories Trees** list, click **Host and Clusters**.
4. Expand the hierarchy to show the data centers.
5. Right-click the target data center and select **Deploy OVF Template** from the menu. It might take a few seconds for the **Deploy OVF template** menu item to appear.
6. Choose **Deploy OVF template**.
  1. Select **Local file** and click **Browse** to find the OVA file downloaded to the computer. Click **Next**.
  2. On the **Review details** page, check the **Accept extra configuration options** box and click **Next**.
  3. On the **Accept EULAs** page, scroll down to review the VMware user license agreement. Click **Accept** and **Next**.
  4. On the **Select name and folder** page, edit the name if necessary and select the location for the Hybrid Cloud Services. Click **Next**.
  5. On the **Select a resource** page, select the installation location.
  6. On the **Select storage** page, select the storage for the Hybrid Cloud Services and click **Next**. From the **Select virtual disk format** list, you can select either **thin provisioning** or **thick provisioning**.
  7. On the **Setup networks** page, map the Hybrid Cloud Services adapter to a host network chosen from the **Destination** list.
7. On the **Customized template** page, enter the values specific to the environment:
  * For the passwords, the default user name for both the command-line interface (CLI) and the web user interface is **admin**. The **admin** user and password to log in to the web user interface is required as is also a **root** user account that has a password that can be set.
  * Enter and reenter the CLI **admin** user password.
  * Enter and reenter the **root** user password. In the future, if help is needed from VMware Global Support Services (GSS), this password might have to be shared so they can troubleshoot the system.
  * For the network properties, enter the host name for the HCX Manager VM. Enter the network IPv4 address, the IPv4 prefix (the CIDR), and the default gateway. The following table shows sample values:

Table 1. Sample values for network properties

| Field                    | Value           |
|--------------------------|-----------------|
| Hostname                 | HCM_1           |
| Network 1 IPv4 Address   | 192.168.200.101 |
| Network 1 IPv4 Prefix    | 24              |
| Default IPv4 Gateway     | 192.168.200.1   |
| Network 1 IPv6 Address   |                 |
| Network 1 IPv6 Prefix    |                 |

8. Review the vService bindings page. Click **Next** to continue.
9. On the **Ready to complete** page, follow these steps:
  * Check the **Power on after deployment** box.
  * Review the Hybrid Cloud Services settings, and click **Finish**. It might take several minutes for the Hybrid Cloud Services appliance to power on.
  * To check the status, go to the vSphere Web Client home page, and on the **Home** tab, go to **Inventories** and click **Hosts and Clusters**. Expand the data center hierarchy, and click the Hybrid Cloud Services service virtual machine to display a summary in the center pane.
  * View the **Summary** tab, the console reads **Powered On** and the **Play** button is green.
10. The HCX Manager is powered on and ready to be registered with the vCenter.

### Related links

* [Preparing the installation environment](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-preparing-the-installation-environment)
