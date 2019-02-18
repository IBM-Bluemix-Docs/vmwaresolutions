---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Requirements and planning for vCenter Server with Hybridity Bundle instances

Review the following requirements before you order your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance. Plan your instance based on the {{site.data.keyword.CloudDataCent_notm}} location, your workload capacity requirements, and additional service requirements.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-requirements-for-the-ibm-cloud-infrastructure-account).

## IBM Cloud Data Center availability

The vCenter Server with Hybridity Bundle deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for vCenter Server with Hybridity Bundle deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vCenter Server with Hybridity Bundle instances

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region |
|:-----|:----------------|
| AMS03 | Amsterdam | Europe |
| CHE01 | Chennai | Asia-Pacific |
| DAL09 | Dallas | NA South |
| DAL10 | Dallas | NA South |
| DAL12 | Dallas | NA South |
| DAL13 | Dallas | NA South |
| FRA02 | Frankfurt | Europe |
| FRA04 | Frankfurt | Europe |
| HKG02 | Hong Kong | Asia-Pacific |
| LON02 | London | Europe |
| LON04 | London | Europe |
| LON06 | London | Europe |
| MEL01 | Melbourne | Asia-Pacific |
| MEX01 | Queretaro | NA South |
| MIL01 | Milan | Europe |
| MON01 | Montreal | NA East |
| OSL01 | Oslo | Europe |
| PAR01 | Paris | Europe |
| SAO01 | Sao Paulo | South America |
| SEO01 | Seoul | Asia-Pacific |
| SJC03 | San Jose | NA West |
| SJC04 | San Jose | NA West |
| SNG01 | Singapore | Asia-Pacific |
| SYD01 | Sydney | Asia-Pacific |
| SYD04 | Sydney | Asia-Pacific |
| TOK02 | Tokyo | Asia-Pacific |
| TOR01 | Toronto | NA East |
| WDC04 | Washington, DC | NA East |
| WDC06 | Washington, DC | NA East |
| WDC07 | Washington, DC | NA East |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when ordering vCenter Server with Hybridity Bundle instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |

## Backup of management components

You are responsible for maintaining and ensuring the availability of all instance components. It is strongly recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-backing-up-components).

## Services for vCenter Server with Hybridity Bundle instances

The vCenter Server with Hybridity Bundle instance includes the VMware Hybrid Cloud Extension (HCX) licensing that entitles you to the VMware HCX on {{site.data.keyword.cloud_notm}} service. This service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you deploy this service, complete the following settings:
* Specify the **HCX interconnect type** by selecting one of the following options:
  * **Public network**: HCX creates an encrypted connection between sites over the public network.
  * **Private network**: HCX creates an encrypted connection between sites over the private network.
* Specify the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
  * **Certificate Contents**: Enter the contents of the CA certificate.
  * **Private Key**: Enter the private key of the CA certificate.
  * (Optional) **Password**: Enter the password for the private key if it is encrypted.
  * (Optional) **Reenter Password**: Enter the password for the private key again.
  * (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX on {{site.data.keyword.cloud_notm}} requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

You can order other add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances).

## Capacity considerations

For more information about capacity considerations, see [Scaling capacity](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-scaling-capacity).

### Related links

* [vCenter Server with Hybridity Bundle overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-with-hybridity-bundle-overview)
* [Ordering vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-with-hybridity-bundle-instances)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-with-hybridity-bundle-instances)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances)
