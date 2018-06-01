---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-01"

---

# Adding, viewing, and deleting clusters for Cloud Foundation instances

The ESXi servers that you configured when you ordered an instance are grouped under a default cluster. The default cluster name is:
* For instances that were deployed in V2.1 or later releases: **MGMT-Cluster-`<subdomain_label>`**
* For instances that were deployed in V2.0 or earlier releases: **SDDC-Cluster**

You can add your own clusters to VMware Cloud Foundation instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, you can delete the added clusters from your instances.

**Availability**:
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

The data centers available to you depend on the Bare Metal Server configuration selected for deployment. If you select the **Customized** configuration, you can also deploy the cluster to a different {{site.data.keyword.cloud}} infrastructure pod, if the selected data center contains additional pods. This is useful when the default {{site.data.keyword.cloud_notm}} infrastructure pod where the initial instance is deployed has reached its maximum capacity.

**Note:** The standardized **Small** and **Large** Bare Metal Server configurations use a default pod that cannot be changed.

If you deploy the cluster to a different data center or pod, three additional VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

### Bare Metal settings

You can choose **Customized** or **Preconfigured**.

#### Customized

For the **Customized** setting, you have a number of option for the **CPU Model** and **RAM**.

Table 1. Options for customized {{site.data.keyword.baremetal_short}}

| CPU options   | RAM options   |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

#### Preconfigured

For the **Preconfigured** setting, you can choose a **Bare Metal Server Configuration** depending on your requirements:
* Small (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz / 128 GB RAM / 12 disks)
* Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz / 512 GB RAM / 12 disks)

### vSAN storage settings

For the **Preconfigured** Bare Metal Server configurations, you cannot change the vSAN storage settings:
* For the **Small** configuration, two disk drives of 1.9 TB SSD SED are ordered.
* For the **Large** configuration, four disk drives of 3.8 TB SSD SED are ordered.

For the **Customized** Bare Metal Server configuration, you can customize the vSAN storage by specifying the number of vSAN capacity disks, the disk type and size that meet your storage needs.

### Licenses settings

You can specify the licensing options for the VMware components in the cluster, including VMware vSphere and VMware vSAN:
* For Business Partner users, the vSphere license (Enterprise Plus edition) and the vSAN license are included and purchased on your behalf. However, you must specify the edition for the vSAN license.
* For non-Business Partner users, you can use the IBM-provided VMware licenses for the components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) for the components by selecting **I will provide** and entering your own license keys.

## Procedure to add clusters to Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation instances** table, click the instance that you want to add clusters to.

   **Note:** Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.

3. Click the **Infrastructure** tab and click **Add** at the upper-right corner of the **CLUSTERS** table.
4. Enter the cluster name.
5. (Optional) Select **Select a different location** and select the {{site.data.keyword.CloudDataCent_notm}} to host the cluster.
6. Complete the Bare Metal configuration:
   * If you selected **Customized**, select the **CPU Model** and the **RAM** size.
   * If you selected **Preconfigured**, select the **Bare Metal Server Configuration**.
7. Complete the storage configuration:
   * If you selected **Customized** for the Bare Metal configuration, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks**.
   * If you selected **Preconfigured** for the Bare Metal configuration, note that the storage settings for the **Small** and **Large** Bare Metal Server configurations cannot be changed.
8. Specify how your license keys are provided:
   * For Business Partner users, the vSphere license (Enterprise Plus edition) and the vSAN license are included and purchased on your behalf. However, you must specify the edition for the vSAN license.
   * For non-Business Partner users, you can select one of the following options:
       * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the components. For VMware vSAN, also select the license edition.
       * If you want to use your own VMware license for a component, select **I will provide** and enter the license key for the component.
9. Click **Calculate Cost**, and then review the estimated cost of the cluster by clicking the price link. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
10. Click **Add** to add the cluster.

### Results after adding clusters to Cloud Foundation instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** tab on the instance details page.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Viewing clusters in Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation instances** table, click an instance to view the clusters in it.
3. Click the **Infrastructure** tab. View the summary about the clusters::
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
   * **Actions**: Click the Delete icon to delete the cluster.
4. Click a cluster name to view its details, which include the list of ESXi servers and their information, as well as the details of licenses:

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
   * The details of the vSAN license and the vSphere license. The vSphere license details is available only when you selected to use your own VMware license (BYOL) for it during cluster ordering:
       * **License type**: The vSAN license or the vSphere license.
       * **Order type**: The license is provided by the user (BYOL) or is purchased on the user's behalf.
       * **License edition**: The edition of the license.
       * **License key**: The license key.
       * **Total capacity (CPU)**: The total capacity or the number of CPU provided by the license.
       * **Free capacity (CPU)**: The capacity that is currently available in the license.

## Deleting clusters from Cloud Foundation instances

You might want to delete a cluster from an instance when it is no longer needed.

### Before you delete

* Use this procedure to delete clusters from instances that are deployed in V2.3 or later releases.
* For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.
* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you attempt to delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before deleting the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster will also be deleted and they cannot be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster cannot be deleted.

## Procedure to delete clusters from Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation instances** table, click the instance that you want to delete clusters from.

   **Note**: Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot delete clusters from the instance.

3. Click the **Infrastructure** tab. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon.
4. Confirm that you completed the migration of VMs to other clusters, if appropriate, and that you want to delete the cluster.

## Related links

* [Viewing Cloud Foundation instances](sd_viewinginstances.html)
* [Expanding and contracting capacity for Cloud Foundation instances](sd_addingremovingservers.html)
