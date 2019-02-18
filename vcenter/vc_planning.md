---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Requirements and planning for vCenter Server instances

Review the following requirements before you order your VMware vCenter Server instances. Plan your instance based on the {{site.data.keyword.CloudDataCent}} location, your workload capacity requirements, and add-on service requirements.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-requirements-for-the-ibm-cloud-infrastructure-account).

## IBM Cloud Data Center availability

The vCenter Server deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for vCenter Server deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vCenter Server instances

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server options |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdam | Europe | Skylake, Broadwell |
| CHE01 | Chennai | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| DAL09 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL10 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL12 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL13 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| FRA02 | Frankfurt | Europe | Skylake, SAP-certified, Broadwell |
| FRA04 | Frankfurt | Europe | Skylake, SAP-certified, Broadwell |
| HKG02 | Hong Kong | Asia-Pacific | Skylake, Broadwell |
| LON02 | London | Europe | Skylake, Broadwell |
| LON04 | London | Europe | Skylake, SAP-certified, Broadwell |
| LON06 | London | Europe | Skylake, SAP-certified, Broadwell |
| MEL01 | Melbourne | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| MEX01 | Queretaro | NA South | Skylake, SAP-certified, Broadwell |
| MIL01 | Milan | Europe | Skylake, SAP-certified, Broadwell |
| MON01 | Montreal | NA East | Skylake, SAP-certified, Broadwell |
| OSL01 | Oslo | Europe | Skylake, Broadwell |
| PAR01 | Paris | Europe | Skylake, Broadwell |
| SAO01 | Sao Paulo | South America | Skylake, SAP-certified, Broadwell |
| SEO01 | Seoul | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapore | Asia-Pacific | Skylake, Broadwell |
| SYD01 | Sydney | Asia-Pacific | Skylake, Broadwell |
| SYD04 | Sydney | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| TOK02 | Tokyo | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| TOR01 | Toronto | NA East | Skylake, SAP-certified, Broadwell |
| WDC04 | Washington, DC | NA East | Skylake, SAP-certified, Broadwell |
| WDC06 | Washington, DC | NA East | Skylake, SAP-certified, Broadwell |
| WDC07 | Washington, DC | NA East | Skylake, SAP-certified, Broadwell |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when ordering vCenter Server instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |

## Backup of management components

You are responsible for maintaining and ensuring the availability of all instance components. It is strongly recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-backing-up-components).

## Services for vCenter Server instances

You can order add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-instances).

## Capacity considerations

For more information about capacity considerations, see [Scaling capacity](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-scaling-capacity).

### Related links

* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-overview)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-instances)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-instances)
