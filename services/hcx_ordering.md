---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering VMware HCX on IBM Cloud

You can order the VMware HCX on {{site.data.keyword.cloud}} service while ordering a new VMware vCenter Server with Hybridity Bundle instance with the service included or by adding the service to your existing instance.

## Ordering VMware HCX on IBM Cloud for a new instance

To order a new VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle instance with VMware HCX on {{site.data.keyword.cloud_notm}}, select **VMware HCX on IBM Cloud** in the **Services** section when you order the instance from the {{site.data.keyword.vmwaresolutions_short}} console.


## Ordering VMware HCX on IBM Cloud for an existing instance

To add the VMware HCX on {{site.data.keyword.cloud_notm}} service into an existing VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle instance, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.

## VMware HCX on IBM Cloud configuration

To install HCX on {{site.data.keyword.cloud_notm}}, complete the following settings:
1. Specify the **HCX interconnect type** by selecting one of the following options:
  * **Public network:** HCX creates an encrypted connection between sites over the public network. License registration and metering are performed over the public network.
  * **Private interconnect:** HCX creates an encrypted connection between sites over the private network. License registration and metering are performed over the public network.
  * **Private network:** HCX creates an encrypted connection between sites over the private network. License registration and metering are performed over private network through HTTP proxy.
3. If you select **Private network**, complete the following fields:
  * **Proxy Address:** The IPv4 address of the proxy server.
  * **Proxy Port:** The proxy server port. The port number is typically 8080 or 3128.
  * **Username:** The user name if proxy authentication is required.
  * **Password:** The password if proxy authentication is required.
  * **Reenter Password:** Reenter the password for proxy authentication validation.
2. Specify the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
  * **Certificate Contents:** Enter the contents of the CA certificate.
  * **Private Key:** Enter the private key of the CA certificate.
  * (Optional) **Password:** Enter the password for the private key if it is encrypted.
  * (Optional) **Reenter Password:** Enter the password for the private key again.
  * (Optional) **Hostname:** The host name to be mapped to the common name (CN) of the CA certificate. HCX on {{site.data.keyword.cloud_notm}} requires that the format of the CA certificate must be accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Deployment process for HCX on IBM Cloud

The deployment of HCX on {{site.data.keyword.cloud_notm}} is automated. Whether you order a vCenter Server with Hybridity Bundle instance with the service included or you deploy the service later into your instance, the following steps are completed by the {{site.data.keyword.vmwaresolutions_short}} automation process:
1. Three subnets are ordered for HCX from the {{site.data.keyword.cloud_notm}} infrastructure:
   * One private portable subnet for HCX management.
   * One private portable subnet for HCX interconnects. This subnet is used when the **Private network** option is selected for **HCX interconnect type**.
   * One public portable subnet for activation and maintenance with VMware. If the **Public network** option is selected for **HCX interconnect type**, this subnet is also used for HCX interconnects.

   The IP addresses in the subnets that are ordered for HCX are intended to be managed by the VMware on {{site.data.keyword.cloud_notm}} automation. These IP addresses cannot be assigned to VMware resources, such as VMs and NSX Edges, that are created by you. If you need additional IP addresses for your VMware artifacts, you must order your own subnets from {{site.data.keyword.cloud_notm}}.
   {:important}
2. If **Private network** was selected for **HCX interconnect type**, a port group that is named **SDDC-DPortGroup-HCX-Private** is created on the private Distributed Virtual Switch (DVS).
3. An HCX activation key is ordered from VMware.
4. Three resource pools and VM folders for HCX are created, which are needed for the HCX interconnects, local HCX components, and remote HCX components.
5. A pair of VMware NSX Edge Services Gateways (ESGs) for the HCX management traffic is deployed and configured:
   * Public and private uplink interfaces are configured by using the ordered subnets.
   * The ESGs are configured as a pair of extra large edge appliances with High Availability (HA) enabled.
   * The firewall rules and network address translation (NAT) rules are configured to allow inbound and outbound HTTPS traffic to and from the HCX Manager.
   * The load balancer rules and resource pools are configured. These rules and resource pools are used to forward HCX-related inbound traffic to the appropriate virtual appliances of HCX Manager and vCenter Server (with embedded Platform Services Controller).
   * An SSL certificate to encrypt the HCX-related inbound HTTPS traffic that is coming through the ESGs is applied.

   The HCX management edge is dedicated to the HCX management traffic between the on-premises HCX components and the cloud-side HCX components. Do not modify the HCX management edge or use it for HCX network extensions. Instead, create separate edges for network extensions. In addition, using a firewall or disabling the HCX management edge communications to the private IBM management components or public internet might adversely impact the HCX functionality.
   {:important}

6. The HCX Manager on {{site.data.keyword.cloud_notm}} is deployed, activated, and configured:
   * The HCX Manager is registered with vCenter Server.
   * The HCX Manager, vCenter Server (with embedded Platform Services Controller), and NSX Manager are configured.
   * The HCX fleet is configured.
   * Local and remote HCX deployment containers are configured.
7. The host name and IP address of the HCX Manager is registered with the DNS server of VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

### Related links

* [HCX on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-specifications-and-considerations)
* [Managing HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-vmware-hcx-on-ibm-cloud)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Glossary of HCX terms](/docs/services/vmwaresolutions/services?topic=vmware-solutions-glossary-of-hcx-terms)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://cloud.vmware.com/vmware-hcx/resources)
