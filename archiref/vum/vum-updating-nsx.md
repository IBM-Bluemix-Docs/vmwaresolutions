---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Updating NSX

The following information is an example of the update process for NSX. Refer to the VMware guide for the update process for the NSX version that you are upgrading to.

If you need to upgrade both NSX and vSphere, VMware recommends completing the NSX upgrade first, and then completing the vSphere upgrade as NSX VIBs are specific to the version of ESXi that is installed on the host. However, it is recommended to use VUM, as documented in this document if done manually use the following workflow, one host at a time:

1. **Upgrade ESXi** - After the ESXi upgrade completes, the host exits maintenance mode, however, you cannot move VMs connected to logical switches to the host until the next step is complete.
2. **Upgrade NSX VIBs** - After the VIBs are upgraded and the host is removed from maintenance mode, you can move VMs connected to logical switches to the host.

NSX is updated by updating NSX Manager by using a download from _my.vmware.com_. Therefore, you need an account to the download the update. If you are consuming {{site.data.keyword.cloud}} subscription licensing with your VMware vCenter Server on {{site.data.keyword.cloud_notm}} instance, you will not be able to download the updates with your **my.vmware.com** account. Therefore, you need to [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support).

Before you begin the upgrade, check the NSX notes for upgrade issues and workarounds. Using the release notes, verify that vCenter meets the new system requirements for NSX.

If you installed any additional software from VMware business partners, consult the business partner documentation for compatibility and upgrade details. If you deployed vCenter Server primary and secondary instances and have a cross-vCenter NSX environment, refer to the release notes foe the correct upgrade process.

In a cross-vCenter NSX environment, the Primary NSX Manager appliance is updated first, followed by all the secondary NSX Manager appliances.
**Downgrades are not supported**, so take a backup of NSX Manager before you proceed with an upgrade, all NSX Edge configurations, logical routers, and edge services gateways are backed up as part of the NSX Manager backup.

After NSX Manager is upgraded successfully, NSX cannot be downgraded. It is advised that any maintenance activities are carried out in an agreed maintenance window, therefore, follow your enterprise guidance. It is recommended that all NSX components are upgraded in a single outage window to minimize downtime and reduce functionality issues. The NSX upgrade process can take some time, so it is important to understand the NSX deployment upgrade order:
* NSX Manager
* NSX Controller Cluster
* NSX Host Clusters
* Edge Services Gateways can be upgraded at any time after the NSX Manager upgrade
* Guest Introspection, if used follow the instructions in the release notes

The workflow is as follows:
1. Log in to your jump-server and then open a browser.
2. Using your _my.vmware.com_ credentials, navigate to the download section and search for _NSX for vSphere_.
3. Select the version that you require.
4. On the download page, select **Upgrade Bundle, Download Now**.
5. Download to a suitable folder.
6. **Upgrade NSX Manager**:
  - Log in to the NSX Manager Virtual Appliance, by using the IP address and credentials that are documented in the IC4VS Console, and click the Upgrade button on the home page.
  - Log in to the NSX Manager.
  - Under **Appliance Management**, click **Backups & Restore**.
  - Click Backup and enter an appropriate file name. VMware recommends that you reinstall the NSX Manager appliance before you restore NSX Manager data. While a restore operation on an existing NSX Manager appliance might work, it isn't officially supported. The best practice is to take note of the IP settings for the NSX Manager appliance so that they can be used to specify IP information and backup location information for the newly deployed NSX Manager appliance.
  - On the upper-right, click the **Upload Bundle** and upload the file that you downloaded from _my.vmware.com_.
  - Read the upgrade information and select if you want to enable SSH and participate in the VMware Customer Experience Improvement Program.
  - Click **Upgrade**.
  - When the upload completes, you are redirected to the NSX Manager login page. Login back in and verify that the current software version displays is correct.
7. **Upgrade the NSX Controller Cluster**:
  - Open the vSphere Web Client and log in to the VCSA.
  - Navigate to **Home** > **Networking & Security** > **Installation**, select the **Management tab**, and click **Upgrade Available** in the Controller Cluster Status column.
  - The controllers in your environment are upgraded and rebooted one at a time. After you initiate the upgrade, the system downloads the upgrade file, upgrades each controller, restarts each controller, and updates the upgrade status of each controller.
8. **Upgrade NSX Host Clusters**:
  - After upgrading NSX Manager and NSX Controllers, the host clusters are updated the NSX VIBs on the vSphere ESXi hosts.
  - In the vSphere Web Client, navigate to **Home** > **Networking & Security** > **Installation**, select the **Host Preparation tab**. For each cluster that you want to upgrade, click **Upgrade available**. The Installation Status displays Installing.
  - The cluster Installation Status displays _Not Ready_. Click **Not Ready** to display more information and click **Resolve all** to attempt to complete the VIB installation. The host is put in maintenance mode and rebooted if required, to complete the upgrade. The Installation Status column displays Installing. After the upgrade is complete the Installation Status column displays a green check mark and the upgraded NSX version.
9. **Edge Services Gateways**:
  - During the upgrade process, a new Edge virtual appliance is deployed alongside the existing one. When the new Edge is ready, the old Edge's vNICs are disconnected and the new Edge's vNICs are connected. The new Edge then sends gratuitous ARP (GARP) packets to update the ARP cache of connected switches. When HA is deployed, the upgrade process is performed twice. This process can temporarily affect packet forwarding.
  - In the vSphere Web Client, select **Networking & Security** > **NSX Edges**. For each NSX Edge instance, select **Upgrade Version** from the **Actions** menu.
  - After the NSX Edge is upgraded successfully, the Status is Deployed, and the Version column displays the new NSX version. If an Edge fails to upgrade and does not roll back to the old version, click the **Redeploy NSX Edge** icon and then retry the upgrade.

### Related links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
