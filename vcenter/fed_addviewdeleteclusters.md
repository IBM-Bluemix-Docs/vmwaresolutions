---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting clusters for VMware Federal instances

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default.

You can add clusters to your VMware Federal instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, you can delete the added clusters from your instances.

**Availability:** The adding and deleting clusters feature is available only to instances that were deployed in (or upgraded to) V2.3 and later releases.

## Adding clusters to VMware Federal instances

The number of clusters that can be added to an instance depend on the instance version:
* For instances that were deployed in (or upgraded to) V2.5 and later, the number of clusters, hosts, and VMs determines the maximum limit for the number of clusters you can add. You must remain within the VMware sizing guidelines and limits for your deployment.
* For instances that were deployed in (or upgraded to) V2.2 and later, you can add up to 10 clusters.

For more information about maximum limits, see [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.

### System settings

When you add a cluster for a VMware Federal instance, you must specify the following settings.

#### Cluster name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the VMware Federal instance.

#### Data center location

The data center of the cluster is set to the data center of the VMware Federal instance by default.

### Bare Metal Server settings

#### Skylake

Specify the CPU model and RAM for the Bare Metal Server. Available options might differ depending on the version that your instance was initially deployed in.

Table 1. Options for Skylake {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

#### Broadwell

Specify the CPU model and RAM for the Bare Metal Server. Available options might differ depending on the version that your instance was initially deployed in.

Table 2. Options for Broadwell {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |

#### Number of Bare Metal Servers

A minimum of 2 {{site.data.keyword.baremetal_short}} is required for a cluster.

For VMware Federal instances that are deployed in V2.3 or later, you can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster, and you can add 1 - 59 ESXi servers at a time.

After deployment, you can create up to four more clusters. For vSAN storage settings, four servers are required for both the initial cluster and post-deployment clusters.

### Storage settings

Storage settings are based on your selection of Bare Metal Server configuration and the storage type.

#### vSAN storage

Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of eight, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 10 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.
* **vSAN License**: Select the VMware vSAN 6.6 license edition (Advanced or Enterprise).

If your initial cluster was added as a vSAN cluster, any additional vSAN clusters use the same vSAN license and the same configuration as the initial vSAN cluster. This is also true if any cluster in the instance has vSAN chosen to be deployed on it (initial or additional). The first time that you add a cluster, you are prompted for the vSAN license and the edition. The next time that you select vSAN for a new cluster, whatever you chose initially is reused.

#### NFS storage

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

The number of file shares must be in the range of 1 to 32.
{:note}

* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of Shares**: When using the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
* **ADD NFS**: Select to add individual file shares with different configuration settings.

Table 3. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share.|

### Licensing settings

{{site.data.keyword.IBM}}-provided licenses for the following VMware components:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Base, Advanced, or Enterprise edition)
  * (For vSAN clusters) vSAN 6.6 (Advanced or Enterprise edition)

### Order summary

Based on your selected configuration for the cluster, the estimated cost is instantly generated and displayed in the **Order Summary** right pane.

## Procedure to add clusters to VMware Federal instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instance** table, click the instance that you want to add clusters to.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.
   {:note}
3. Click **Infrastructure** on the left navigation pane and click **Add** at the upper-right corner of the **CLUSTERS** table.
4. On the **Add Cluster** page, enter the cluster name.
5. Select the **CPU Model**, the amount of **RAM**, and the **Number of Bare Metal Servers** for the Bare Metal configuration.
6. Complete the storage configuration.
  * If you select **vSAN Storage**, specify the disk types for the capacity and cache disks, and the number of disks. If you want more storage, check the **High-Performance Intel Optane** box.
  * If you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Size**, and **Performance**.
  * If you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add NFS** label and select the **Size** and **Performance** for each individual file share. You must select at least one file share.
7. Select the license edition for VMware vSAN for the license configuration.
8. On the **Order Summary** pane, verify the cluster configuration before you add the cluster.
   1. Review the settings for the cluster.
   2. Review the estimated cost of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper-right corner of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
   4. Click **Provision**.

## Results after adding clusters to VMware Federal instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the instance summary page.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{:important}

## Procedure to view clusters in VMware Federal instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click an instance to view the clusters in it.
3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, view the summary about the clusters:
   * **Name**: The name of the cluster.
   * **ESXi Server**: The number of ESXi servers in the cluster.
   * **CPU**: The CPU specification of the ESXi servers in the cluster.
   * **Customized vSAN Disks**: The number of vSAN disks in the cluster, including the disk type and capacity.
   * **Memory**: The total memory size of the ESXi servers in the cluster.
   * **Data Center Location**: The data center where the cluster is hosted.
   * **Pod**: The pod where the cluster is deployed.
   * **Status**: The status of the cluster. The status can have one of the following values:
     <dl class="dl">
         <dt class="dt dlterm">Initializing</dt>
         <dd class="dd">The cluster is being created and configured.</dd>
         <dt class="dt dlterm">Modifying</dt>
         <dd class="dd">The cluster is being modified.</dd>
         <dt class="dt dlterm">Ready to Use</dt>
         <dd class="dd">The cluster is ready to use.</dd>
         <dt class="dt dlterm">Deleting</dt>
         <dd class="dd">The cluster is being deleted.</dd>
         <dt class="dt dlterm">Deleted</dt>
         <dd class="dd">The cluster is deleted.</dd>
     </dl>
   * **Actions**: Click the **Delete** icon to delete the cluster.
4. Click a cluster name to view the ESXi server, storage, and license details.

### ESXi servers

   * **Name**: The name of the ESXi server is in the format `<host_prefix><n>.<subdomain_label>.<root_domain>`, where:

      `host_prefix` is the host name prefix,
      `n` is the sequence of the ESXi server,
      `subdomain_label` is the subdomain label, and
      `root_domain` is the root domain name.

   * **Version**: The version of the ESXi server.
   * **Credentials**: The user name and password to access the ESXi server.
   * **Private IP**: The private IP address of the ESXi server.
   * **Status**: The status of the ESXi server, which can be one of the following values:
        <dl class="dl">
        <dt class="dt dlterm">Added</dt>
        <dd class="dd">The ESXi server is added and is ready for use. </dd>
        <dt class="dt dlterm">Adding</dt>
        <dd class="dd">The ESXi server is being added. </dd>
        <dt class="dt dlterm">Deleting</dt>
        <dd class="dd">The ESXi server is being deleted.</dd>
        </dl>

### Storage

   * **Name**: The data store name.
   * **Size**: The capacity of the storage.
   * **IOPS/GB**: The performance level of the storage.
   * **NFS/Portal**: The NFS version of the storage.
   * **Status**: The status of the storage, which can be one of the following values:
        <dl class="dl">
        <dt class="dt dlterm">Added</dt>
        <dd class="dd">The ESXi server is added and is ready for use. </dd>
        <dt class="dt dlterm">Adding</dt>
        <dd class="dd">The ESXi server is being added. </dd>
        <dt class="dt dlterm">Deleting</dt>
        <dd class="dd">The ESXi server is being deleted.</dd>
        </dl>

### Licenses

   * **License**: The license type.
   * **Order Type**: The license was IBM-provided or user-provided.
   * **License Edition**: The version and edition of the license.
   * **License Key**: The license key.
   * **Total Capacity (CPU)**: The total amount of CPU capacity for the license.
   * **Free Capacity (CPU)**: The amount of free CPU capacity for the license.

## Deleting clusters from VMware Federal instances

You might want to delete a cluster from an instance when it is no longer needed.

Use this procedure to remove clusters from instances that are deployed in (or upgraded to) V2.3 and later releases.
{:note}

### Before you delete

* Use this procedure to delete clusters from instances that are deployed in V2.3 or later releases.
* For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.
* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you attempt to delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster are also deleted and they cannot be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster cannot be deleted.

## Procedure to delete clusters from VMware Federal instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot delete clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon in the **Actions** column.

### Related links

* [Viewing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vmware-federal-instances)
* [Expanding and contracting capacity for VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vmware-federal-instances)
