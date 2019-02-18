---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud overview

The KMIP for VMware on {{site.data.keyword.cloud}} service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys. It also provides management capability to maintain the associations between the client credentials and the encryption keys.

The KMIP for VMware on {{site.data.keyword.cloud_notm}} service is available as a stand-alone service without being associated to a VMware instance. Each instance of the service can serve one or more Cloud Foundation instances, vCenter Server instances, or vSphere clusters.

## Technical specifications for KMIP for VMware on IBM Cloud

The following specifications are included with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service:

* A VMware-compatible Key Management Interoperability Protocol (KMIP)
* A managed service
* Available in multiple geographic regions worldwide
* Two KMIP service endpoints provided in each region for high availability

## Considerations when installing KMIP for VMware on IBM Cloud instances

Review the following considerations before you install a KMIP for VMware on {{site.data.keyword.cloud_notm}} instance:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} uses the IBM Key Protect for {{site.data.keyword.cloud_notm}} service to create, encrypt, and decrypt encryption keys. Therefore, before you install KMIP for VMware on {{site.data.keyword.cloud_notm}}, ensure that:
   * You ordered a usable Key Protect service in the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware on {{site.data.keyword.cloud_notm}} instance is to be hosted. For more information, see [Provisioning the service](/docs/services/key-protect?topic=key-protect-provision).
   * An {{site.data.keyword.cloud_notm}} service ID was created by following the steps in [Creating a service ID](/docs/iam?topic=iam-serviceids). This service ID is used to access the Key Protect service instance that you created.
   * You granted the following access levels for the service ID:
      * At the platform access level: Viewer authority to your IBM Key Protect instance
      * At the service access level: Manager authority to your IBM Key Protect instance
   * You have an API key for the created service ID. The key is required when you order the service.
   * You created at least one customer root key (CRK) from the Key Protect user interface by following the steps in [Creating root keys](/docs/services/keymgmt/keyprotect_create_root.html), or by using the REST API in [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect).

     **Important:** You cannot order the service without CRKs. It is highly recommended that you use the method to create a CRK using existing key material, and back up the key material that you are creating. By doing so, you ensure that you can recover your keys if a failure of the data center where IBM Key Protect is applied to store your CRKs.
* Ensure that your {{site.data.keyword.cloud_notm}} infrastructure account is enabled for Virtual Routing and Forwarding (VRF) and for connectivity to Service Endpoints. For more information, see:
   * [Overview of Virtual Routing and Forwarding (VRF) on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Enabling your account for using Service Endpoints by using IBM Cloud CLI](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* Because only private connection is supported, you do not need to configure any firewall or SNAT rules in vCenter Server for the network connectivity from the vCenter Server to the endpoint of the KMIP for VMware on {{site.data.keyword.cloud_notm}} instance.

For more information, see [KMIP for VMware on IBM Cloud solution architecture](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-for-vmware-overview).

## Considerations when deleting KMIP for VMware on IBM Cloud instances

All data protected by the KMIP for VMware on IBM Cloud service, including encrypted backups, cannot be decrypted after you remove the service.

### Related links

* [Ordering KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-kmip-for-vmware-on-ibm-cloud-instances)
* [Adding, viewing, and deleting certificates for KMIP for VMware on IBM Cloud instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-adding-viewing-and-deleting-certificates-for-kmip-for-vmware-on-ibm-cloud-instances)
* [Viewing KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-viewing-kmip-for-vmware-on-ibm-cloud-instances)
* [Deleting KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-deleting-kmip-for-vmware-on-ibm-cloud-instances)
* [Activity Tracker events](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-activity-tracker-events)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
