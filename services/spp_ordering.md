---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Ordering IBM Spectrum Protect Plus on IBM Cloud

You can order the {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service while ordering a new instance with the service included or by adding the service to your existing instance.

## Ordering IBM Spectrum Protect Plus on IBM Cloud for a new instance

You can order a new instance with IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **IBM Spectrum Protect Plus on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **IBM Spectrum Protect Plus on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering IBM Spectrum Protect Plus on IBM Cloud for an existing instance

You can add the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **IBM Spectrum Protect Plus on IBM Cloud**, specify the service settings and select **Add to Existing Instance**.

## IBM Spectrum Protect Plus on IBM Cloud service configuration

When you order the service, provide the following settings.

### Number of Storage Volumes

The number of volumes that meet your storage needs.

### Storage Size per Volume

The storage capacity per volume.

### Storage Performance

The IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
* If you want to order licenses for IBM Spectrum Protect Plus, specify the **Number of VMs to License** on the **Order Licenses** tab.
* If you want to Bring Your Own License (BYOL), click the **IBM Spectrum Protect Plus licenses** tab, and then click **Add License Files** to upload the IBM Spectrum Protect Plus license files that you own.

## Deployment process for IBM Spectrum Protect Plus on IBM Cloud

The deployment of IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} is automated. Whether you order an instance with this service included or you deploy the service later into your instance, the following steps are completed by the {{site.data.keyword.vmwaresolutions_short}} automation process:

1. Based on the settings you specify, endurance NFS storage is ordered from the {{site.data.keyword.cloud_notm}} infrastructure for the IBM Spectrum Protect Plus backup repository.
2. Based on the settings you specify, a number of licenses for IBM Spectrum Protect Plus are ordered from the  {{site.data.keyword.cloud_notm}} infrastructure. The licenses are ordered in increments of 10 virtual machine (VM) license packs, based on the number of VMs that you specified to license when ordering the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service. If you want to bring an existing IBM Spectrum Protect Plus license, no license order is placed from the {{site.data.keyword.cloud_notm}} infrastructure.
3. The NFS storage ordered for this service is mounted to all the ESXi servers in the default cluster of the instance, including adding correct static routes on each ESXi server to the storage private subnet.
4. NFS datastores are created in vCenter Server for all NFS storage volumes that are mounted to the ESXi servers.
5. The IBM Spectrum Protect Plus VMs are deployed, activated, and configured in the default cluster of the instance.
6. The NFS storage that was ordered for this service is attached to the IBM Spectrum Protect Plus VM and the backup repository is configured.
7. The host name and IP address of the IBM Spectrum Protect Plus VM are registered with the DNS server of the instance.

### Related links

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ibm-spectrum-protect-plus-on-ibm-cloud-overview)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Managing IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-ibm-spectrum-protect-plus-on-ibm-cloud)
* [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-viewing-and-removing-services-for-cloud-foundation-instances)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-instances)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-with-hybridity-bundle-instances)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
