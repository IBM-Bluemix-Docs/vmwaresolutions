---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud overview

The Zerto on {{site.data.keyword.cloud}} service integrates replication and disaster recovery capabilities into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}.

This service is available only to instances that are deployed in V1.2 or later. The current Zerto version that is installed is 6.0 update 3.
{:note}

## Technical specifications for Zerto on IBM Cloud

The following components are ordered and included in the Zerto on {{site.data.keyword.cloud_notm}} service.

Zerto Virtual Replication Appliance (VRA) components are deployed only into the default cluster.
{:note}

### VSIs

* One Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz cores
* 4 GB RAM
* Windows Server 2016 Standard Edition (64-bit)

### Storage

100 GB (SAN) disk

### Networking

* One primary private IP address
* 1 Gbps private network uplink

### Licenses and fees

Zerto Replication V6.0 update 3 license

### Related links

* [About {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-about-ibm-cloud-for-vmware-solutions)
* [Ordering Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-zerto-on-ibm-cloud)
* [Managing Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-zerto-on-ibm-cloud)
* [Requesting managed services for Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-managed-services-for-zerto-on-ibm-cloud)
* [zerto.com website](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
