---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing FortiGate Security Appliance on IBM Cloud

After the FortiGate Security Appliance on {{site.data.keyword.cloud}} service is installed successfully, you can manage and configure firewall rules for the FSA from the FortiGate console.

You must ensure that the FSA firewall rules are defined to allow outbound HTTPS (TCP port 443) communications that are initiated by management components such as the Zerto Virtual Manager to communicate with the external management database on the {{site.data.keyword.cloud_notm}} infrastructure over the internet. The outbound HTTPS (TCP port 443) communications originate from the public IP address of the management services VMware NSX Edge Services Gateway (ESG) in your instance.
{:important}

## Accessing the FortiGate 300 series console

To manage the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service, you must access the FortiGate® 300 series console in one of the following ways:
* Log in to the FortiOS Web Client by using the credentials that you can find on the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service details page.
* Access the console via SSH connection by using the credentials that you can find on the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service details page.

For more information, see the following topics:
* [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-viewing-and-removing-services-for-cloud-foundation-instances)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-instances)

### Related links

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortigate-security-appliance-on-ibm-cloud-overview)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [fortinet.com website](https://www.fortinet.com/)
* [Fortinet technical documentation](http://docs.fortinet.com/fortigate/admin-guides)
