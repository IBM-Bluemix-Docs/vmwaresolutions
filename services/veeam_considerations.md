---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud overview

The Veeam on {{site.data.keyword.cloud}} service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service provides recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.

This service is available only to instances that are deployed in V1.8 or later. The current Veeam version that is installed is 9.5u3.
{:note}

## Technical specifications for Veeam on IBM Cloud

The following components are ordered and included in the Veeam on {{site.data.keyword.cloud_notm}} service:

### VSIs

* Single VSI with Veeam Backup and Replication 9.5 OS Add-on
* Windows Server 2016 Standard Edition (64-bit)
* 4 x 2.0 GHz Cores
* 8 GB RAM
* 1 Gbps private network uplink
* 100 GB disk (SAN)

### Storage for backups

* Endurance iSCSI storage (2000, 4000, 8000, or 12000 GB)
* Storage performance (0.25, 2, or 4 IOPS/GB)

### Networking

One primary private IP address.

### Licenses and fees

Veeam Backup and Replication 9.5 Enterprise Plus (10, 25, 50, 100, or 200 VM license).

### Management

Management backups that are configured by default with up to 5 VMs and 2000 GB of storage.

## Considerations when you install Veeam on IBM Cloud

The storage repository and the Veeam server are in the original pod and data center. Therefore, the performance of the backup operations for remote clusters might deteriorate.

## Considerations when you remove Veeam on IBM Cloud

Removal of the Veeam on {{site.data.keyword.cloud_notm}} service stops all backups and deletes all the previous backups. The backups of the management VMs stop and the deletion of previous backups is irreversible. If the management VMs are corrupted, they can't be restored.

### Related links

* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-veeam-on-ibm-cloud)
* [Managing Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-veeam-on-ibm-cloud)
* [Requesting managed services for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-managed-services-for-veeam-on-ibm-cloud)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [Veeam website](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
