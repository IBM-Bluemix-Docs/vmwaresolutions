---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware overview

This solution architecture describes the KMIP on VMware architecture for protecting your VMware on {{site.data.keyword.cloud_notm}} instances. Many storage encryption options are available to protect your VMware workload. KMIP for VMware works together with VMware native vSphere encryption and vSAN encryption to provide simplified storage encryption management together with the security and flexibility of {{site.data.keyword.cloud_notm}} Key Protect customer-managed keys.

This solution is considered to be an extra component and extension of both the vCenter Server and VMware Cloud Foundation solution offerings on {{site.data.keyword.cloud_notm}}. As a result, this document doesn't cover the existing configuration of these foundation solutions on {{site.data.keyword.cloud_notm}}. To understand more about the foundation solution architecture, refer to our [VMware on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-overview-of-ibm-cloud-for-vmware-solutions).

## Key benefits

While many storage encryption solutions are available for your VMware workload, KMIP for VMware offers the following benefits:

* Integration with VMware vSAN encryption and vSphere encryption, both of which are implemented in the hypervisor layer rather than the storage or virtual machine layer. This approach allows easy management and transparency to your storage solution and application.
* Fully managed key management server available in many IBM Cloud multi-zone regions (MZRs).
* Integrating your VMware cluster with IBM Cloud Key Protect provides you with fully customer-managed keys that you can revoke at any time.

## Related links

* [Solution design](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-for-vmware-design)
* [Implementation and management](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-for-vmware-implementation-and-management)
