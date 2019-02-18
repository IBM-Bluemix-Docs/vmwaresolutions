---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Considerations for on-premises VMware HCX on IBM Cloud instances

Review the following considerations before you install or delete the HCX on {{site.data.keyword.cloud}} instances that you ordered for on-premises use.

A vCenter Server instance with HCX on {{site.data.keyword.cloud_notm}} is limited to three simultaneous connections from on-premises sites.
{:note}

## Considerations when installing on-premises HCX on IBM Cloud instances

The HCX on {{site.data.keyword.cloud_notm}} components must be installed both on {{site.data.keyword.cloud_notm}} and in your on-premises vSphere environment. It is recommended that you install the HCX on {{site.data.keyword.cloud_notm}} service into your vCenter Server with Hybridity Bundle instance on {{site.data.keyword.cloud_notm}} before you install the on-premises HCX on {{site.data.keyword.cloud_notm}} instance. For more information, see [Considerations for HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-specifications-and-considerations).

### Requirements on IP addresses

For full HCX functionality, you need at least five private IP addresses and you must allow them to access the Internet.

### Deployment process for on-premises HCX on IBM Cloud instances

You must complete the following tasks for a successful installation of the on-premises HCX on {{site.data.keyword.cloud_notm}} instance:
1. In the {{site.data.keyword.vmwaresolutions_short}} console, order the on-premises HCX on {{site.data.keyword.cloud_notm}} instance. For more information, see [Ordering on-premises VMware HCX on IBM Cloud instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-on-premises-vmware-hcx-on-ibm-cloud-instances).
2. In the **HCX Cloud Console**, complete the following steps:
    1. Click the **Administration** tab.
    2. On the **System Updates** tab, click **REQUEST DOWNLOAD LINK**.
    3. Click **COPY LINK**, and then use this link to download the HCX Enterprise Client onto an on-premises environment with access to your on-premises vSphere environment.
3. In the VMware vSphere Web Client, deploy the HCX Enterprise Client as an HCX Manager virtual appliance (HCX Manager) into your on-premises environment.

   You must deploy the on-premises HCX Manager on a private network and allow it to access the public network. You can use an NSX Edge, Vyatta, or similar gateways to allow Internet access to the on-premises HCX Manager. If the gateways used for private network access and public network access are different, it is recommended that you use the default gateway to allow for public network access and the on-premises **HCX Manager Admin Console** to create a static route for private network access.
   {:note}
4. After the HCX Manager deployment is completed, use the **HCX Manager Admin Console** to activate the on-premises HCX Manager. To obtain an activation key for the on-premises HCX Manager, order an on-premises HCX on {{site.data.keyword.cloud_notm}} instance in the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Ordering on-premises HCX instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-on-premises-vmware-hcx-on-ibm-cloud-instances).
5. If you used a self-signed SSL certificate when ordering the HCX on {{site.data.keyword.cloud_notm}} service, you must import the certificate into the on-premises HCX Manager by completing the following steps:
    1. In the on-premises **HCX Manager Admin Console**, click the **Administration** tab.
    2. From the left navigation pane, click **Trusted CA Certificate**, and then click **IMPORT** on the right.
    3. Click **URL** and then enter the URL of the certificate you want to apply, that is the **HCX Cloud IP** (``https://<cloud-side public IP>``), which you can find on the HCX on {{site.data.keyword.cloud_notm}} service details page in the {{site.data.keyword.vmwaresolutions_short}} console.
    4. Click **APPLY**.

You now completed the basic setup of the on-premises HCX Manager. You can proceed to pair the on-premises HCX on {{site.data.keyword.cloud_notm}} site with the cloud-side HCX site.

For more information, see [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Considerations when deleting on-premises HCX on IBM Cloud instances

Review the following considerations before you delete an HCX on {{site.data.keyword.cloud_notm}} instance that was ordered for on-premises use:
1. In the VMware vSphere Web Client, go to the HCX user interface, and then check the following items:
    1. Ensure that no HCX migration or disaster recovery operation is running.
    2. Ensure that all the extended networks are removed.
    3. Ensure that all the interconnect components with paired cloud sites are removed.

   You must complete all the considerations before you proceed to the next step. Otherwise, the license for the on-premises HCX on {{site.data.keyword.cloud_notm}} instance is canceled, because of which migrations cannot be performed and errors might occur to the HCX components.  
   {:important}
2. In the {{site.data.keyword.vmwaresolutions_short}} console, delete the on-premises HCX on {{site.data.keyword.cloud_notm}} instance that was ordered to obtain the activation key for the on-premises HCX Manager. Ensure that the deleted instance is no longer available in the console before you proceed to the next step.

   For more information, see [Deleting on-premises HCX on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-deleting-on-premises-vmware-hcx-on-ibm-cloud-instances).
3. In the VMware vSphere Web Client, delete the on-premises HCX Manager.

### Related links

* [Viewing on-premises HCX on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-viewing-on-premises-vmware-hcx-on-ibm-cloud-instances)
* [Glossary of HCX terms](/docs/services/vmwaresolutions/services?topic=vmware-solutions-glossary-of-hcx-terms)
* [VMware Hybrid Cloud Extension documentation](https://cloud.vmware.com/vmware-hcx/resources)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
