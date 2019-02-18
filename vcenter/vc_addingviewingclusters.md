---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting clusters for vCenter Server instances

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default.

You can add your own clusters to VMware vCenter Server instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, delete the added clusters from your instances.

The delete cluster feature is available only to instances that are deployed in (or upgraded to) V2.3 and later.
{:note}

## Adding clusters to vCenter Server instances

The number of clusters that can be added to an instance depends on the instance version:
* For instances that were deployed in (or upgraded to) V2.5 and later, the number of clusters, hosts, and VMs determines the maximum limit for the number of clusters you can add. You must remain within the VMware sizing guidelines and limits for your deployment.
* For instances that were deployed in (or upgraded to) V2.2 and later, you can add up to 10 clusters.
* For instances that were deployed in V2.1 or earlier, you can add up to five clusters.

For more information about maximum limits, see [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.

### System settings

When you add a cluster for a vCenter Server instance, you must specify the following settings.

#### Cluster name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum number of characters is 30.
* The cluster name must be unique within the vCenter Server instance.

#### Data center location

The {{site.data.keyword.CloudDataCent}} location of the cluster is set to the {{site.data.keyword.CloudDataCent_notm}} of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.CloudDataCents_notm}} is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/).

If you deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} or {{site.data.keyword.cloud_notm}} infrastructure pod, three extra VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

### Bare Metal Server settings

You can choose **Skylake**, **SAP-certified**, or **Broadwell**.

#### Skylake

For the **Skylake** setting, you have options for the **CPU Model** and **RAM**. Available options might differ depending on the version that your instance was initially deployed in.

Table 1. Options for Skylake {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

#### SAP-certified

When you select **SAP-certified**, you cannot alter the CPU or RAM settings.

Based on your requirements, select a Bare Metal Server configuration:
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 192 GB RAM
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 384 GB RAM
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 768 GB RAM
* Dual Intel Xeon E5-2690 v4 processor / 28 cores total, 2.6 GHz / 512 GB RAM
* Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.2 GHz / 1024 GB RAM
* Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.2 GHz / 2048 GB RAM
* Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.2 GHz / 4096 GB RAM

#### Broadwell

For the **Broadwell** setting, you have a number of options for the **CPU Model** and **RAM**. Available options might differ depending on the version that your instance was initially deployed in.

Table 2. Options for Broadwell {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Number of Bare Metal Servers

Clusters require at least two {{site.data.keyword.baremetal_short}}.

For vCenter Server instances that are deployed in V2.1 or later, you can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster. You can add 1 - 59 ESXi servers at a time.

For vCenter Server instances that were deployed in V2.0 or earlier, you can add up to 32 {{site.data.keyword.baremetal_short}} for a cluster. You can add 1 - 20 ESXi servers at a time for the **Skylake**, **SAP-certified**, and **Broadwell** Bare Metal Server configuration.

After deployment, you can create up to four more clusters. If you select the **Skylake** or **Broadwell** Bare Metal Server configuration with VMware vSAN storage, four servers are required for both the initial cluster and post-deployment clusters.

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
* **vSAN License**: Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

If your initial cluster was a vSAN cluster, any additional vSAN clusters use the same vSAN license and have the same configuration as the initial one. This is also true if any cluster in the instance has vSAN chosen to be deployed on it (initial or additional). The first time you're prompted for the vSAN license (BYOL or purchased) and the edition. The next time that you select vSAN for a new cluster, the license that is chosen initially is reused.

#### NFS storage

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

The number of file shares must be in the range of 1 to 32.
{:note}

* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of Shares**: When want to use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **ADD NFS**: Select to add individual file shares with different configuration settings.

Table 3. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 0.25 IOPS/GB | This option is designed for workloads that are not used often. Example applications include: vaulted data, hosting large databases with legacy data, or virtual disk images of virtual memory system as backup. |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine (VM) disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |

### Local Disks

The local disks option is available for the **SAP-certified** Quad Intel Xeon E7-8890 v4 processor Bare Metal configuration only. Specify the following options:
* **Disk Count**: Select the number of disks that you want to add.
* **Disk type**: Select an option for the disk type that you need.

### Licensing settings

Specify the licensing option for the VMware vSphere component in the cluster:
* For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
* For non-Business Partner users, you can use the IBM-provided VMware licenses for this component by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### Network interface settings

Network interface card (NIC) enablement settings are based on your selection of either **Public and Private Network** or **Private Network Only**. The following add-on services require public NICs and are not available if you select the private option:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Order summary

Based on your selected configuration for the cluster, the estimated cost is instantly generated and displayed in the **Order Summary** right pane.

## Procedure to add clusters to vCenter Server instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to add clusters to.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.
   {:note}
3. Click **Infrastructure** on the left navigation pane and click **Add** on the upper-right corner of the **CLUSTERS** table.
4. On the **Add Cluster** page, enter the cluster name.
5. If you want to host the cluster in a different {{site.data.keyword.CloudDataCent_notm}} than the one that the instance is hosted in, under **Bare Metal Server**, check the **Select a different location** check box and choose the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Complete the Bare Metal configuration.
   * If you selected **Skylake** or **Broadwell**, specify the **CPU Model**, the amount of **RAM**, and the **Number of {{site.data.keyword.baremetal_short}}**.
   * If you selected **SAP-certified**, specify the CPU model.
7. Complete the storage configuration.
  * If you select **vSAN Storage**, specify the disk types for the capacity and cache disks, the number of disks, and the vSAN License edition. If you want more storage, check the **High-Performance Intel Optane** box.
  * If you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Performance**, and **Size (GB)**.
  * If you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**. Then click the **+** icon next to the **Add Shared Storage** label and select the  **Performance** and **Size (GB)** for each  file share. You must select at least one file share.
  * If you select **Local Disks**, specify the disk count and disk type.
8. Complete the network interface settings.
8. Specify how the vSphere license key is provided:
  * For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
  * For users who aren't Business Partners, you can select one of the following options:
      * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the component.
      * If you want to use your own VMware license for the component, select **I will provide** and enter your license key.
9. Select the network setting of either **Public and Private Network** or **Private Network Only**.
10. On the **Order Summary** pane, verify the cluster configuration before you add the cluster.
   1. Review the settings for the cluster.
   2. Review the estimated cost of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
   4. Click **Provision**.

### Results after you add clusters to vCenter Server instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** page of the instance.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You can't change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{:important}

## Procedure to view clusters in vCenter Server instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click an instance to view the clusters in it.
3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, view the summary about the clusters:
  * **Name**: The name of the cluster.
  * **ESXi Servers**: The number of ESXi servers in the cluster.
  * **CPU**: The CPU specification of the ESXi servers in the cluster.
  * **Customized vSAN Disks**: The number of vSAN disks in the cluster, including the disk type and capacity.
  * **Memory**: The total memory size of the ESXi servers in the cluster.
  * **Data Center Location**: The {{site.data.keyword.CloudDataCent_notm}} where the cluster is hosted.
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
4. Click a cluster name to view the details of ESXi servers and storage:

  * ESXi servers details:
     * **Name**: The name of the ESXi server is in the format `<host_prefix><n>.<subdomain_label>.<root_domain>`, where:

       `host_prefix` is the host name prefix,

       `n` is the sequence of the server,

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
  * Storage details:
    * **Name**: The data store name.
    * **Size**: The capacity of the storage.
    * **IOPS/GB**: The performance level of the storage.
    * **NFS Protocol**: The NFS version of the storage.

## Deleting clusters from vCenter Server instances

You might want to delete a cluster from an instance when it's no longer needed.

### Before you delete

* Use this procedure to delete clusters from instances that are deployed in V2.3 or later.
* For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 if you want to delete the clusters that you added to the instance.
* You can delete a single cluster at a time. To delete more than one cluster, you must do it in sequence. Wait for the previous cluster to be deleted before you delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs from the cluster are also deleted and they can't be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster can't be deleted.

### Procedure to delete clusters from vCenter Server instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you can't delete clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon in the **Actions** column.
4. Confirm that you completed the migration of VMs to other clusters, if needed, and that you want to delete the cluster.

### Related links

* [Viewing vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vcenter-server-instances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-instances)
