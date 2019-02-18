---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuration and settings for attached storage

This design supports the attachment of shared storage via NFS v3 only. NFS v4 and v4.1 aren't supported.

The attached storage for this design is limited to the {{site.data.keyword.cloud_notm}} storage available in the same {{site.data.keyword.CloudDataCent_notm}} as the vCenter Server solution. Additionally, all virtual disks that are stored to the datastore are thin-provisioned by default.
{:note}

The architecture specifies that NFS v3 datastores are attached by using the DNS name from {{site.data.keyword.cloud_notm}} storage to connect to the share. The NFS share is attached to all hosts in the vCenter Server cluster and placed into a datastore cluster with storage DRS enabled.

## vSphere Storage Distributed Resource Scheduler (Storage DRS)

Use Storage DRS to manage the aggregated resources of a datastore cluster. When Storage DRS is enabled, it provides recommendations for virtual machine (VM) disk placement and migration to balance space and I/O resources across the datastores in the datastore cluster.

The following features are available when storage DRS is turned on:
* Space load balancing among datastores within a datastore cluster
* I/O load balancing among datastores within a datastore cluster
* Initial place for virtual disks based on space and I/O workload.

In this design, Storage DRS is enabled with the automation level set to **Fully Automated**. As a result, files are migrated automatically to optimize resource usage on the data cluster. Since the cluster is fully automated, all other Storage DRS options are set to **Use cluster settings**.

## Storage DRS runtime settings for NFS v3

The aggressiveness of Storage DRS is determined by specifying thresholds for space that is used and I/O latency. Storage DRS collects resource usage information for the datastores in a datastore cluster. vCenter Server uses this information to generate recommendations for placement of virtual disks on datastores.

When low aggressiveness level is set for a datastore cluster, Storage DRS recommends Storage vMotion migrations only when necessary. For example, if I/O load, space utilization, or their imbalance is high, Storage DRS recommends a migration. If high aggressiveness level is set for a datastore cluster, Storage DRS recommends migrations whenever the datastore cluster can benefit from space or I/O load balancing.

The following threshold categories are available in the datastore cluster.

* Space Utilization: Storage DRS generates recommendations or performs migrations when the percentage of space utilization on the datastore is greater than the threshold you set in the vSphere Web Client.
* I/O Latency: Storage DRS generates recommendations or performs migrations when the 90th percentile I/O latency measured over a day for the datastore is greater than the threshold.

In this design, the Storage DRS Runtime Settings are enabled and thresholds are kept to their respective default values. Change these values based on the workload I/O requirements and latency sensitivity.

The following table shows the settings in the VMware vSphere Web Client.

Table 1. Storage DRS runtime settings

| Setting       | Value  |
|:--------------- |:------ |
| Enable I/O metric for SDRS recommendations | Selected |
| Utilized space | Selected, set to 80% |
| I/O latency threshold | 15 ms |

For more information about configuring these settings in the vSphere Web Client, see [Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

## Storage I/O Control for NFS v3

When SIOC (Storage I/O Control) is enabled in the environment, it changes the device queue length for the single VM. The change to the device queue length reduces the storage array queue for all VMs to an equal share and throttle of the storage queue. SIOC engages only if resources are constrained and the storage I/O latency is higher than a defined threshold.

In order for SIOC to determine when a storage device is congested or constrained, it requires a defined threshold. The congestion threshold latency is different for different storage types. This design recommends and implements a threshold latency of 10 milliseconds.

You can limit individual virtual disks for individual VMs or grant them different shares with SIOC. Limiting of disks and granting different shares allows you to match and align the environment to the workload with the acquired file storage volume IOPS number. The limit is set by IOPS and it is possible to set a different weight or shares.

Virtual disks shares set to **High** (2,000 shares) receive twice as much I/O as a disk set to **Normal** (1,000 shares) and four times as much as one set to **Low** (500 shares). **Normal** is the default value for all the VMs, so you need to adjust the **Normal** settings for the VMs that require it.

## Additional storage for NFS v3

When the need arises to add more storage to the environment due to insufficient space or high latency, you can order another NFS share from the console. After the share is ordered, attach the export to the vSphere ESXi hosts in the cluster and place it into the storage cluster. Placing the new NFS share in the storage cluster effectively and seamlessly scales out the storage that is associated with the environment without burdening you with storage-level migrations.

## Advanced configuration parameters

This design adds advanced configuration parameters that are recommended by {{site.data.keyword.cloud_notm}}. As a result, the following parameters are set on each vSphere ESXi host that is attached to the {{site.data.keyword.cloud_notm}} NFS share.

Table 2. NFS advanced configuration parameters

| Parameter       | Value  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MaxQueueDepth | 64 |

### Related links

* [Solution overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-overview-of-ibm-cloud-for-vmware-solutions)
