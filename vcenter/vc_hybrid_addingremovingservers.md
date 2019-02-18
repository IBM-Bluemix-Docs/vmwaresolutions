---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances

You can expand or contract the capacity of your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance according to your business needs, by adding or removing ESXi servers.

Because your initial cluster has vSAN as its storage, adding one or more ESXi servers after deployment can increase the cluster storage capacity.

## Adding ESXi servers to vCenter Server with Hybridity Bundle instances

### Before you add ESXi servers

* Do not add ESXi servers from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* vSAN storage requires at least 4 ESXi servers.

## Procedure to add ESXi servers

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **CLUSTERS** table, click the cluster to which you want to add ESXi servers.
5. In the **ESXi Servers** table, click **Add**.
6. In the **Add Server** window, select the number of servers that you want to add, click the price link to review the estimated cost, and then click **Add**.

### Results after you add ESXi servers

1. You might experience a slight delay on the console while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You're notified by email that your request to add ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. If you don't see the new ESXi servers added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Removing ESXi servers from vCenter Server with Hybridity Bundle instances

### Before you remove ESXi servers

* Do not remove ESXi servers from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* vSAN storage requires at least 4 ESXi servers.
* Before you remove ESXi servers with the F5 on {{site.data.keyword.cloud_notm}} or FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service installed, you must migrate the F5 BIG-IP and FortiGate VMs to a different ESXi server than the one that is hosting the VMs.
* Before you remove ESXi servers with the IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service installed, ensure that there are no active (failed or in progress) backup or restore operations because these active operations might prevent the ESXi servers to be removed.
* When you remove ESXi servers, the servers are placed in maintenance mode, and after that, all the virtual machines (VMs) running on the servers are migrated before they are removed from vCenter Server. For maximum of control over the relocation of VMs, it is recommended that you place the ESXi servers to be removed in maintenance mode and migrate the VMs running on them manually using the VMware vSphere Web Client. After that, remove the ESXi servers using the {{site.data.keyword.vmwaresolutions_short}} console.

## Procedure to remove ESXi servers

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **CLUSTERS** table, click the cluster from which you want to remove ESXi servers.
5. In the **ESXi Servers** table, select the servers that you want to remove and click **Remove**.

### Results after removing ESXi servers

1. You might experience a slight delay on the console while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before making additional changes to the instance.
2. You are notified by email that your request to remove ESXi servers is being processed. On the console, the status of the cluster associated with the ESXi servers is changed to **Modifying**.
3. The ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed ESXi servers.
   {:note}

### Related links

* [vCenter Server Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-bill-of-materials)
* [Requirements and planning for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-requirements-and-planning-for-vcenter-server-with-hybridity-bundle-instances)
* [Adding, viewing, and deleting clusters for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vcenter-server-with-hybridity-bundle-instances)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
