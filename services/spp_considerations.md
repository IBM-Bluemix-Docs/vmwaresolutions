---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Spectrum Protect Plus on IBM Cloud overview

The {{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement the service as a stand-alone solution or you can integrate it with your IBM Spectrum Protect environment to offload copies for long-term storage and data governance.

This service is available only to instances that are running vSphere 6.5 and that are deployed in or upgraded to  V2.2 or later. The current {{site.data.keyword.IBM}} Spectrum Protect Plus version that is installed is V10.1.2.
{:note}

## Technical specifications for IBM Spectrum Protect Plus on IBM Cloud

The following components are ordered and included in the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service:

### vCenter resources

* Server VM running IBM Spectrum Protect Plus server
   * Linux 3.10.0-693.11.1.el7.x86_64 operating system
   * 4 x 2.0 GHz cores
   * 32 GB RAM
   * 370 GB disk
* Secondary VM running IBM Spectrum Protect Plus vSnap server and VADP proxy
   * Linux 3.10.0-693.11.1.el7.x86_64 operating system
   * CPU and RAM configured based on the selected storage size and the [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) sizing guidance
   * 150 GB disk

### Storage for backups

Customizable storage for backups with the following options:
* Number of file storage: 1 - 10
* Each endurance file storage: 500, 1000, 2000, 4000, 8000, or 12000 GB
* Storage performance: 0.25, 2, or 4 IOPS/GB

See the [IBM Spectrum Protect Plus blueprint and sizing tool](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) for planning and sizing.

### Storage for management

One 1000 GB, 2 IOPS/GB endurance file storage that hosts the IBM Spectrum Protect Plus virtual machine and running on the same subnet as the backup storage.

### Networking

Two portable private IP addresses.

### Licenses and fees

* IBM Spectrum Protect Plus (10 to a maximum of 1000 VM licenses in increments of 10)
* IBM Spectrum Protect Plus license offered through the {{site.data.keyword.vmwaresolutions_short}} console (number of VMs in packages of 10) or as BYOL

## Considerations when you install IBM Spectrum Protect Plus on IBM Cloud

Review the following considerations before you install the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service.

* Ensure that the CPU and memory in the default cluster of your instance is sufficient for the IBM Spectrum Protect Plus virtual machine.
* Ensure that the NFS mounts available on the ESXi servers are sufficient based on the version of the ESXi servers.

  Cloud Foundation instances and vCenter Server instances that are deployed in (or upgraded) to V2.2 or later releases have an `NFS.MaxVolumes` parameter setting in VMware. This parameter defines the maximum number of NFS mounts on an ESXi server and can be set to a maximum of 256 that is specific to the version of the ESXi server. For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

  The IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service can use up to 11 of the NFS volumes on each ESXi server in the default cluster of your instance. In addition, the service creates transient NFS mounts for backup and restore purposes. Therefore, you must set the number of NFS mounts to a minimum of 64 to ensure that the service can be installed and function successfully.

## Considerations when you remove IBM Spectrum Protect Plus on IBM Cloud

Review the following considerations before you remove the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service:
* Ensure that all the backup job configurations are removed along with active backup or restore operations.
* When you remove the service, the storage for the backup repository is removed from the IBM Spectrum Protect Plus VM and the storage order is canceled, which deletes the backup repository data permanently.
* When you remove the service, the backup storage that is ordered for the service is removed too. All the backups become inaccessible during service removal.

### Related links

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Managing IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-ibm-spectrum-protect-plus-on-ibm-cloud)
* [Ordering IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-ibm-spectrum-protect-plus-on-ibm-cloud)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
