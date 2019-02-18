---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Registering HCX Manager with vCenter

Register the Hybrid Cloud Services plug-in in the VMware vSphere Web Client and start the Hybrid Cloud Services management service.

## Before you begin

The Hybrid Cloud Services virtual appliance must be powered on before it can be registered.

## Procedure to register HCX Manager with vCenter

1. Log in to Hybrid Cloud Services service virtual appliance.
2. Click the **Manage Settings** tile.
  1. In the left pane, under **Configure Systems**, select vCenter.
  2. Click **Add vCenter** on the upper right.
  3. Enter the IP address of the vCenter Server in the form `https:vCenter-host-name` or `https:vCenter-IP-address`. For example, `https:My-vCenter` or `https:10.108.26.211`.
  4. Enter the vCenter Server user name and password. The account that is used must have the vCenter Administrator role.
  5. Click **OK**. Do not restart when the _You need to restart the app_ message is displayed.
3. Configure the lookup service.
  1. Click the **Manage** tab.
  2. Click the **Edit** button on the far right of the **Lookup Service URL** text box.
  3. Enter the lookup service endpoint in the following form:
    * For vCenter Server 5.5u3 `https://ssoip:/7444/lookupservice/sdk`
    * For vCenter Server 6.0u2 `https://ssoip/lookupservice/sdk`
  4. Click **OK**. Do not restart when a message to restart the web engine is displayed.
4. Click the **Summary** tab and find the **Hybridity Management Components** section. Stop and start both the application engine and the web engine.
5. To finalize the registration, log out of the vSphere Web Client. Log back in to verify that the screen update has occurred.

## Results

Notice the existing **Hybrid Cloud** icon and the **Hybrid Cloud Services** menu item on the left. The Hybrid Cloud Services registration updates these labels. In the inventory, the icon label becomes **Hybrid Cloud Services**.

### Related links

* [Installing and configuring hybrid services](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-installing-and-configuring-hybrid-services)
