---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-01"

---

# Adding, viewing, and deleting clusters for vCenter Server instances

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default.

You can add your own clusters to VMware vCenter Server instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, you can delete the added clusters from your instances.

**Availability**: The delete cluster feature is available only to instances that are deployed in (or upgraded to) V2.3 and later releases.

## Adding clusters to vCenter Server instances

The number of clusters that can be added to an instance depend on the instance version:
* For instances that were deployed in (or upgraded to) V2.2 and later releases, you can add up to 10 clusters.
* For instances that were deployed in V2.2 or earlier releases, you can add up to 5 clusters.

### System settings
When you add a cluster for a vCenter Server instance, you must specify the following settings.

#### Cluster name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server instance.

#### Data center location

The {{site.data.keyword.CloudDataCent}} location of the cluster is set to the {{site.data.keyword.CloudDataCent_notm}} of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.CloudDataCents_notm}} is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

If you deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} or {{site.data.keyword.cloud_notm}} infrastructure pod, three additional VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

### Bare Metal settings

You can choose either **Customized** or **Preconfigured**.

#### Customized

For the **Customized** setting, you have a number of options for the **CPU Model** and **RAM**.

Table 1. Options for customized {{site.data.keyword.baremetal_short}}

| CPU options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

#### Preconfigured

For the **Preconfigured** setting, you can choose a **Bare Metal Server Configuration** depending on your requirements:
* Small (Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz / 128 GB RAM / 2 disks)
* Medium (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz / 256 GB RAM / 2 disks)
* Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz / 512 GB RAM / 2 disks)

#### Number of Bare Metal Servers

A minimum of two {{site.data.keyword.baremetal_short}} is required for a cluster.

For vCenter Server instances that are deployed in V2.1 or later releases, you can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster, and you can add 1 - 59 ESXi servers at a time.

For vCenter Server instances that were deployed in V2.0 or earlier releases, you can add up to 32 {{site.data.keyword.baremetal_short}} for a cluster. The number of the {{site.data.keyword.baremetal_short}} that you can add at a time is as follows:
* For the **Small**, **Medium**, and **Large** Bare Metal Server configurations, you can add 1 - 10 ESXi servers at a time.
* For the **Customized** Bare Metal Server configuration, you can add 1 - 20 ESXi servers at a time.

After deployment, you can create up to four more clusters. If you select the **Customized** Bare Metal Server configuration with VMware vSAN storage, 4 servers are required for both the initial cluster and post-deployment clusters.

### Storage settings

For your storage, you can use either **vSAN** or **NFS**.

#### vSAN

vSAN is available only for the customized Bare Metal configuration. You can customize the VMware vSAN storage by specifying the number of vSAN capacity disks (2, 4, 6, or 8), the disk type and size that meet your storage needs, and the vSAN licensing option.

If your initial cluster was a vSAN cluster, any additional vSAN clusters use the same vSAN license and have the same configuration as the initial one. This is also true if any cluster in the instance has vSAN chosen to be deployed on it (initial or additional). The first time you are prompted for the vSAN license (BYOL or purchased) and the edition. The next time you select vSAN for an additional cluster, the license chosen initially is reused.

#### NFS

For NFS, you can add file-level shared storage for your instance. Specify the following storage options:

* **File Shares**: Specify the number of file shares for the NFS shared storage that you want to add. The number of file shares must be in the range of 1 to 32.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements. The performance levels available to you depend on the {{site.data.keyword.CloudDataCent_notm}} that you select.
* **Configure shares individually**: Optionally select to complete individual file share configuration.
* **Add NFS**: Optionally select if you are configuring your file shares individually and need to add additional file shares.

Table 2. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share, and it is supported only for the following {{site.data.keyword.CloudDataCents_notm}}: AMS03, DAL09, DAL10, DAL12, DAL13, FRA02, HKG01, LON02, LON04, LON06, MEL01, MEX01, MON01, OSL01, PAR01, SJC03, SJC04, SYD01, TOK02, TOR01, WDC04, WDC06, and WDC07. |

### License settings

You can specify the licensing option for the VMware vSphere component in the cluster:
* For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
* For non-Business Partner users, you can use the IBM-provided VMware licenses for this component by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

## Procedure to add clusters to vCenter Server instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to add clusters to.

   **Note**: Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.

3. Click the **Infrastructure** tab and click **Add** on the upper-right corner of the **CLUSTERS** table.
4. Enter the cluster name.
5. Optionally, select **Select a different location** and select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Complete the Bare Metal configuration.
   * If you selected **Customized**, specify the **CPU Model**, the amount of **RAM**, and the **Number of {{site.data.keyword.baremetal_short}}**.
   * If you selected **Preconfigured**, specify the **Bare Metal Server Configuration**, and the **Number of {{site.data.keyword.baremetal_short}}**. If you are planning to use vSAN as your storage solution, note that a minimum of 4 {{site.data.keyword.baremetal_short}} are needed.
7. Complete the storage configuration.
   * If you selected **vSAN**, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks**.
   * If you selected **NFS**, specify the **File Shares**, **Size**, and **Performance**. Optionally select **Configure shares individually** to complete individual file configuration. Use the **Add NFS** option to add additional file shares, if necessary.
8. Specify how the vSphere license key is provided:
  * For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
  * For non-Business Partner users, you can select one of the following options:
      * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the component.
      * If you want to use your own VMware license for the component, select **I will provide** and enter your license key for it.
9. Click **Calculate Cost** and review the estimated cost of the cluster. To save or print your order summary, click the **Print** or **Download** icon on the upper-right corner of the PDF window.
10. Click **Add** to add your cluster.

### Results after adding clusters to vCenter Server instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** tab on the instance details page.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Viewing clusters in vCenter Server instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click an instance to view the clusters in it.
3. Click the **Infrastructure** tab. In the **CLUSTERS** table, view the summary about the clusters:
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
4. Click the cluster name to view the list of ESXi servers and their information:

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
  * The storage details:
    * **Name**: The data store name.
    * **Size**: The capacity of the storage.
    * **IOPS/GB**: The performance level of the storage.
    * **NFS Protocol**: The NFS version of the storage.

## Deleting clusters from vCenter Server instances

You might want to delete a cluster from an instance when it is no longer needed.

### Before you delete

* Use this procedure to delete clusters from instances that are deployed in V2.3 or later releases.
* For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.
* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you attempt to delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before deleting the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster will also be deleted and they cannot be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster cannot be deleted.

## Procedure to delete clusters from vCenter Server instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to delete clusters from.

   **Note**: Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot delete clusters from the instance.

3. Click the **Infrastructure** tab. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon.
4. Confirm that you completed the migration of virtual machines to other clusters, if needed, and that you want to delete the cluster.

## Related links

* [Viewing vCenter Server instances](vc_viewinginstances.html)
* [Expanding and contracting capacity for vCenter Server instances](vc_addingremovingservers.html)
