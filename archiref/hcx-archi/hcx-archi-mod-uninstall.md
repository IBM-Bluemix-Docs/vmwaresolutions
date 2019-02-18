---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modifying or uninstalling HCX

Existing installations can be upgraded, or some or all of a Hybrid Cloud Services deployment can be removed.

##  Unstretching a Layer 2 network

Unstretching a Layer 2 network is necessary before you remove the associated Layer 2 concentrator service virtual appliance, or before you uninstall Hybrid Cloud Services.

1. Check the stretched networks.
2. From the Hybrid Cloud Services plug-in page, view the Hybrid Services tab and check the Network Extension Service section. If active or scheduled jobs are in progress, wait until they are complete or stop them before you continue.
3. To remove the network, click the Delete (red X) icon on the right.
4. Click **OK** to confirm.

## Uninstalling HCX virtual appliances

A service appliance might be uninstalled in preparation for uninstalling Hybrid Cloud Services or due to a change in the installation architecture. Use the Hybrid Cloud Services to administer appliances, as outlined in the following procedure.

### Prerequisites for uninstalling HCX virtual appliances

* Cancel or reset the execution time for any migrations that might occur during the uninstallation task.
* Check the vSphere Web Client task console for any running migrations, and wait until they are complete.
* Ensure that there are no active Hybrid Cloud Services tasks of any type.

Never delete virtual appliances from the vSphere inventory. Always use the management portal to interact with service virtual appliances.
{:note}

### Procedure to uninstall HCX virtual appliances

1. In the vSphere Web Client interface, select the Hybrid Cloud Services plug-in from the left pane.
2. In the center pane, click the **Hybrid Services** tab.
3. Locate the Hybrid Cloud Gateway appliance and click the entry to display the details.
4. On the lower right, click the Delete icon to remove the appliance.
5. If a stretched network does not share an IP address with the Hybrid Cloud Gateway, you must remove it separately. Expand the Network Extensions Service details, and click the Delete icon to remove the Layer 2 Concentrator.

The Hybrid Cloud Gateway and any hybrid service virtual appliances that use the Hybrid Cloud Gateway are removed from both the vCenter and the VCF/VCS Hybrid Cloud Services Cloud.

## Uninstalling HCX Manager

The HCX Manager appliance should be uninstalled before you remove the HCX solution from the on-premises data center. Follow these steps to uninstall the Hybrid Cloud Services virtual machine.

1. Unstretch all Layer 2 networks.
2. Remove the hybrid service virtual appliances.
3. In the on-premises vCenter, power off the Hybrid Cloud Services virtual machine.
4. Delete the Hybrid Cloud Services virtual machine.

All virtual service appliances are removed. The following elements might remain behind:
* Logs
* Migrated VMs

### What to do next

The migrated VMs and logs can be manually backed up or deleted.

## Logging in to the HCX Management Portal

The Hybrid Cloud Services deployment can be administered from the Management Portal by using a browser-based user interface.

1. In a web browser, enter the IP address assigned to the Hybrid Cloud Services, and specify the port number 9443. For example, `https://HCXip:9443`.
2. The Hybrid Cloud Services user interface opens in a web browser window by using SSL. If necessary, accept the security certificate. The VMware Hybridity and Networking log in screen opens.
3. Enter the user name and password. By default, the user name is Admin. The password is the value that was supplied when the Hybrid Cloud Services virtual appliance was installed.

### Related links

* [Troubleshooting HCX on IBM Cloud](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-troubleshooting-hcx-on-ibm-cloud)
