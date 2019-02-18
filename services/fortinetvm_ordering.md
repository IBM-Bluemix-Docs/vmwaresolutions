---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering FortiGate Virtual Appliance on IBM Cloud

You can order the FortiGate Virtual Appliance on {{site.data.keyword.cloud}} service when you order a new instance with the service included or by adding the service to your existing instance.

## Ordering FortiGate Virtual Appliance on IBM Cloud for a new instance

You can order a new instance with FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **FortiGate Virtual Appliance on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **FortiGate Virtual Appliance on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering FortiGate Virtual Appliance on IBM Cloud for an existing instance

You can add the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **FortiGate Virtual Appliance on IBM Cloud**, specify the service settings, and select **Add to Existing Instance**.

## FortiGate Virtual Appliance on IBM Cloud service configuration

When you order the service, provide the following settings.

### FortiGuard Network Connection

Select **Public network** or **Private network** for FortiGuard. If the target cluster is configured with private-only network interfaces, only the **Private network** option is available. This selection determines how FortiGuard will contact the Fortinet license server to activate the license and to download security patches, and it doesn't impact the workload data plane.

If you select **Private network**, specify the following settings:
* **Proxy IP Address**: The IPv4 address of the proxy server.
* **Proxy Port Number**: The port number of the proxy server, usually 8080 or 3128.
* **Proxy User Name**: If you require proxy authentication, enter the user name of the proxy server.
* **Proxy Password**: If you require proxy authentication, enter the password of the proxy server.

### Name

Enter the service name.

### Deployment size

{{site.data.keyword.cloud_notm}} provides the following deployment size options:
* Small (2 vCPUs / 4 GB RAM)
* Medium (4 vCPUs / 6 GB RAM)
* Large (8 vCPU / 12 GB RAM)

### License model

The license model for FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} offers the following options:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">This bundle includes Stateful Packet Inspection, VLAN Protection and Advanced Logging, Ingress and Egress Firewall Rules, SSL/IPSec VPN Termination, and 24 x 7 support.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">This bundle includes all standard firewall services in addition to the Advanced Malware Protection (AMP) service. It includes Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service, and Content Disarm & Reconstruct. It also includes the Web Filtering, IPS, Antispam, Application Control, and FortiCare services.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">This bundle includes all standard firewall and UTM services in addition to the following services:<ul><li>Cloud Access Security Broker (CASB) - This service provides visibility, compliance, data security, and threat protection for cloud-based services.</li><li>Industrial Security - This service provides signatures for common ICS/SCADA protocols.</li><li>Security Rating - This service provides audit capabilities to identify critical vulnerabilities and configuration weaknesses and implement best practice recommendations.</li></ul></dd>
</dl>

In 3Q 2018, Fortinet added three new services (CASB, Industrial Security, and Security Rating) to their Enterprise bundle. These services are available on FortiGate 6.0 only.
{:note}

You can't change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service by selecting a different license option.
{:important}

### Related links

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortigate-virtual-appliance-on-ibm-cloud-overview)
* [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-fortigate-virtual-appliance-on-ibm-cloud)
* [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-viewing-and-removing-services-for-cloud-foundation-instances)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-instances)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [Fortinet website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
