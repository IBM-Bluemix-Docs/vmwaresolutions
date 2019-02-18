---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering vSphere clusters based on existing configurations

You can order a VMware vSphere cluster based on a configuration template that you saved. Use this procedure to define a new cluster configuration based on an existing cluster configuration.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
*  You reviewed the requirements and considerations in [Requirements and planning for vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-requirements-and-planning-for-vmware-vsphere-on-ibm-cloud).
*  You created a configuration template to be reused.

## Procedure to order vSphere clusters based on existing configurations

1. From the {{site.data.keyword.cloud_notm}} catalog, click **VMware** on the left navigation pane, and then click **VMware vSphere** in the **Virtual Data Centers** section.
2. On the **VMware vSphere on IBM Cloud** page, click **Create**.  
3. Click the **Create New** tab and select a configuration template from the **Cluster Configurations** list.
4. Enter a new cluster name.
5. Review the cluster settings that are automatically completed and update the settings according to your needs. For more information about the settings, see [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters).
6. In the **Order Summary** pane, verify the instance configuration and the estimated cost.
   * To save the configuration as a template without placing an order, click **Save Configuration**.
   * To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Provision**.

   Only the {{site.data.keyword.baremetal_short}} are installed. You're responsible for installing and configuring various components after cluster deployment, such as VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

## Results

If you saved the cluster configuration as a template, you get a console notification that the configuration was saved. You can then find the template in the **Cluster Configurations** list.

If you placed an order, the deployment of the cluster starts automatically. You receive an email confirmation that the order is being processed. When the cluster is ready to use, you're also notified by email.

The vSphere clusters, unlike the vCenter Server and Cloud Foundation instances, are not displayed on the **Deployed Instances** page.
{:note}

### Related links

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters)
* [Scaling existing vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-existing-vsphere-clusters)
* [Scaling clusters created outside of the console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-scaling-clusters-created-outside-of-the-console)
