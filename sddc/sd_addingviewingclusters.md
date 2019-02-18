---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting clusters for Cloud Foundation instances

The ESXi servers that you configured when you ordered an instance are grouped under a default cluster. The default cluster name is:
* For instances that were deployed in V2.1 or later releases: **MGMT-Cluster-`<subdomain_label>`**
* For instances that were deployed in V2.0 or earlier releases: **SDDC-Cluster**

You can add your own clusters to VMware Cloud Foundation instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, you can delete the added clusters from your instances.

## Availability

* The add cluster feature is available only to instances that were deployed in (or upgraded to) V2.0 and later releases.
* The delete cluster feature is available only to instances that are deployed in (or upgraded to) V2.3 and later releases.  

## Adding clusters to Cloud Foundation instances

You can add up to five clusters to a Cloud Foundation instance.

### System settings

When you add a cluster to a Cloud Foundation instance, you must specify the following settings.

#### Cluster name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the Cloud Foundation instance.

#### Data center location

The {{site.data.keyword.CloudDataCent}} location of the cluster is set to the {{site.data.keyword.CloudDataCent_notm}} of the Cloud Foundation instance by default. You can deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.CloudDataCents_notm}} is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

The data centers available to you depend on the Bare Metal Server configuration that is selected for deployment. If you select the **Skylake** or **Broadwell** configuration, you can also deploy the cluster to a different {{site.data.keyword.cloud_notm}} infrastructure pod, if the selected data center contains more pods. This configuration is useful when the default {{site.data.keyword.cloud_notm}} infrastructure pod where the initial instance is deployed has reached its maximum capacity.

If you deploy the cluster to a different data center or pod, three more VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

### Bare Metal Server settings

You can choose **Skylake** or **Broadwell**.

#### Skylake

For the **Skylake** setting, you have a number of options for the **CPU Model** and **RAM**. Available options might differ depending on the version that your instance was initially deployed in.

Table 1. Options for Skylake {{site.data.keyword.baremetal_short}}

| CPU model options   | RAM options   |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

#### Broadwell

For the **Broadwell** setting, you have a number of options for the **CPU Model** and **RAM**. Available options might differ depending on the version that your instance was initially deployed in.

Table 2. Options for Broadwell {{site.data.keyword.baremetal_short}}

| CPU model options   | RAM options   |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### vSAN storage settings

For the **Skylake** and **Broadwell** Bare Metal Server configuration, you can customize the vSAN storage by specifying the following settings:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of eight, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 10 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.

### Licensing settings

You can specify the licensing options for the VMware components in the cluster, including VMware vSphere and VMware vSAN:
* For IBM Business Partner users, the vSphere license (Enterprise Plus edition) and the vSAN license are included and purchased on your behalf. However, you must specify the edition for the vSAN license.
* For users who aren't IBM Business Partners, you can use the IBM-provided VMware licenses for the components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) for the components by selecting **I will provide** and entering your own license keys.

## Procedure to add clusters to Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation instances** table, click the instance that you want to add clusters to.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane and click **Add** at the upper right of the **CLUSTERS** table.
4. On the **Add Cluster** page, enter the cluster name.
5. If you want to host the cluster in a different {{site.data.keyword.CloudDataCent_notm}} than the one that the instance is hosted in, under **Bare Metal Server**, check the **Select a different location** check box and choose the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Complete the Bare Metal configuration by specifying the **CPU Model** and the **RAM** size.
7. Complete the storage configuration:
   1. Specify the disk types for the vSAN capacity and cache disks, and the number of disks.
   2. If you want more storage, select the **High-Performance with Intel Optane** check box.
8. Specify how your license keys are provided:
   * For IBM Business Partner users, the vSphere license (Enterprise Plus edition) and the vSAN license are included and purchased on your behalf. However, you must specify the edition for the vSAN license.
   * For users who aren't IBM Business Partners, you can select one of the following options:
       * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the components. For VMware vSAN, also select the license edition.
       * If you want to use your own VMware license for a component, select **I will provide** and enter the license key for the component.
9. On the **Order Summary** pane, verify the cluster configuration before you add the cluster.
   1. Review the settings for the cluster.
   2. Review the estimated cost of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
   4. Click **Provision**.

### Results after you add clusters to Cloud Foundation instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history on the instance summary page.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You can't change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{:important}

## Procedure to view clusters in Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation instances** table, click an instance to view the clusters in it.
3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, view the summary about the clusters:
   * **Name**: The name of the cluster.
   * **ESXi servers**: The number of ESXi servers in the cluster.
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
4. Click a cluster name to view the list of ESXi servers and their information:

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
   * The details of the vSAN license and the vSphere license. The vSphere license details are available only when you selected to use your own VMware license (BYOL) for it when you order the cluster.
       * **License type**: The vSAN license or the vSphere license.
       * **Order type**: The license is provided by the user (BYOL) or is purchased on the user's behalf.
       * **License edition**: The edition of the license.
       * **License key**: The license key.
       * **Total capacity (CPU)**: The total capacity or the number of CPU provided by the license.
       * **Free capacity (CPU)**: The capacity that is available in the license.

## Deleting clusters from Cloud Foundation instances

You might want to delete a cluster from an instance when it is no longer needed.

### Before you delete

* Use this procedure to delete clusters from instances that are deployed in V2.3 or later releases.
* For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.
* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you attempt to delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster are also deleted and they can't be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster can't be deleted.

## Procedure to delete clusters from Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation instances** table, click the instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you can't delete clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon.
4. Confirm that you completed the migration of VMs to other clusters, if appropriate, and that you want to delete the cluster.

### Related links

* [Viewing Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-viewing-cloud-foundation-instances)
* [Expanding and contracting capacity for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-expanding-and-contracting-capacity-for-cloud-foundation-instances)
