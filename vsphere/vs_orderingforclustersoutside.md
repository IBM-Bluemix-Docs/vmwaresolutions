---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Scaling clusters created outside of the console

You can use the VMware vSphere offering to scale existing vSphere clusters that are created outside of the {{site.data.keyword.vmwaresolutions_full}} console. To scale a vSphere cluster that is created outside of the console, re-create the cluster with the same settings with the console and then scale the cluster.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
*  You reviewed the requirements and considerations in [Requirements and planning for VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-requirements-and-planning-for-vmware-vsphere-on-ibm-cloud).

## Procedure to scale clusters created outside of the console

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** on the left navigation pane, and then click **VMware vSphere** in the **Virtual Data Centers** section.
2. On the **VMware vSphere on IBM Cloud** page, click **Create**.  
   Ensure that you are on the **Create New** tab and that **New cluster** is displayed in the **Cluster Configurations** list.
3. Create a cluster with the same settings as the existing cluster that is created outside of the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters).  
   For network interface, to scale a cluster that is created outside of the {{site.data.keyword.vmwaresolutions_short}} console, you must select the existing VLANs for the cluster.
   {:note}
4. In the **Order Summary** pane, verify the cluster configuration, and then click **Save Configuration**.   
5. On the **Getting Started** page, click the **VMware vSphere on IBM Cloud** card.
6. On the **VMware vSphere on IBM Cloud** page, click **Create**.
7. Click the **Scale Existing** tab. From the **Cluster Configurations** list, select the cluster that you recently created.
8. In the **{{site.data.keyword.baremetal_short}}** section, specify the number of {{site.data.keyword.baremetal_short}} that you want to add to the cluster.
9. If the cluster does not include the FortiGate 300 Series Security Appliance HA Pair on its public VLAN, you can order one by selecting **Include with purchase** under **FortiGate Physical Appliance 300 Series HA Pair**.
10. In the **Order Summary** pane, verify the instance configuration and the estimated cost, ensure that the account to be charged is correct, review and accept the terms, and then click **Provision**.

## Results

The deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

The vSphere clusters are not displayed on the **Deployed Instances** page, together with the vCenter Server and Cloud Foundation instances.
{:note}

### Related links

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters)
* [Ordering vSphere clusters based on existing configurations](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-vsphere-clusters-based-on-existing-configurations)
* [Scaling existing vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-existing-vsphere-clusters)
