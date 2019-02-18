---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting clusters for vCenter Server with Hybridity Bundle instances

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default.

You can add clusters to your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance to expand the compute and storage capacity. Within a cluster, manage the ESXi servers for better resource allocation and high availability. When no longer needed, delete the added clusters from your instance.

## Adding clusters to vCenter Server with Hybridity Bundle instances

The number of clusters that can be added to an instance depends on the instance version:
* For instances that were deployed in (or upgraded to) V2.5 and later, the number of clusters, hosts, and VMs determines the maximum limit for the number of clusters you can add. You must remain within the VMware sizing guidelines and limits for your deployment.
* For instances that were deployed in (or upgraded to) V2.3 and later, you can add up to 10 clusters.

For more information about maximum limits, see [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.

### System settings

When you add a cluster for a vCenter Server with Hybridity Bundle instance, you must specify the following settings.

#### Cluster name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server with Hybridity Bundle instance.

#### Data center location

The {{site.data.keyword.CloudDataCent_notm}} location of the cluster is set to the {{site.data.keyword.CloudDataCent_notm}} of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.CloudDataCents_notm}} is less than 150 ms. To check the network latency, use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

If you deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} or {{site.data.keyword.cloud_notm}} infrastructure pod, three more VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

### Bare Metal Server settings

Specify the CPU model and RAM for the Bare Metal Server. Available options might differ depending on the version that your instance was initially deployed in.

#### Skylake

When you select **Skylake**, you can choose the CPU and RAM combination according to your needs.

Table 1. Options for Skylake Bare Metal Servers

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

#### Broadwell

When you select **Broadwell**, you can choose the CPU and RAM combination according to your needs.

Table 2. Options for Broadwell Bare Metal Servers

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Number of Bare Metal Servers

At least two {{site.data.keyword.baremetal_short}} is required for a cluster.

You can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster, and you can add 1 - 59 ESXi servers at a time.

After deployment, you can create up to four more clusters. For VMware vSAN storage, four servers are required for both the initial cluster and post-deployment clusters.

### vSAN storage settings

VMware vSAN 6.6 is included with your vCenter Server with Hybridity Bundle instance order. Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of eight, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 10 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.
* **vSAN License**: Select the VMware vSAN 6.6 license edition (Advanced or Enterprise).

### Licensing settings

IBM-provided licenses for the following VMware components:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Advanced or Enterprise edition)

### Network interface settings

Network interface card (NIC) settings are based on your selection of either **Public and Private Network** or **Private Network Only**. The following add-on services require public NICs and aren't available with the private option:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Order summary

Based on your selected configuration for the cluster, the estimated cost is instantly generated and displayed in the **Order Summary** right pane.

## Procedure to add clusters to vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to view the clusters in it.

   Ensure that the instance status is **Ready to Use**. Otherwise, you can't add clusters to the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane and click **Add** at the upper-right corner of the **CLUSTERS** table.
4. On the **Add Cluster** page, enter the cluster name.
5. You can host the cluster in a different {{site.data.keyword.CloudDataCent_notm}} than the one that the instance is hosted in. To do so, under **Bare Metal Server**, check the **Select a different location** check box and choose the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Select the **CPU Model**, the amount of **RAM**, and the **Number of Bare Metal Servers** for the Bare Metal configuration.
7.  Select **vSAN Storage** and specify the disk types for the capacity and cache disks and the number of disks. If you want more storage, check the **High-Performance Intel Optane** box.
8. Select the license edition for VMware vSAN for the license configuration.
9. Select the network setting of either **Public and Private Network** or **Private Network Only**.
10. On the **Order Summary** pane, verify the cluster configuration before you add the cluster.
   1. Review the settings for the cluster.
   2. Review the estimated cost of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
   4. Click **Provision**.

### Results after you add clusters to vCenter Server with Hybridity Bundle instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history on the **Summary** page of the instance.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You can't change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{:important}

## Procedure to view clusters in vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to view the clusters in it.
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

## Deleting clusters from vCenter Server with Hybridity Bundle instances

You might want to delete a cluster from an instance when it's no longer needed.

### Before you delete

* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster are also deleted and they can't be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster can't be deleted.

## Procedure to delete clusters from vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to delete clusters from.

   **Note:** Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot remove clusters from the instance.

3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon in the **Actions** column.

### Related links

* [Viewing vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vcenter-server-with-hybridity-bundle-instances)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-with-hybridity-bundle-instances)
