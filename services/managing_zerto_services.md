---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Requesting managed services for Zerto on IBM Cloud

The Zerto on {{site.data.keyword.cloud}} service provides replication and disaster recovery capabilities. These capabilities can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}.

When you request managed services for Zerto on {{site.data.keyword.cloud_notm}}, a fully managed disaster recovery (DR) environment can be deployed by using both Zerto DR software and IBM Resiliency Services.

The following models for managed services for Zerto on {{site.data.keyword.cloud_notm}} are available.

## IBM Orchestrated Managed Services for Zerto

This model is suitable if you're using the Zerto on {{site.data.keyword.cloud_notm}} offering.

In this model, the {{site.data.keyword.cloud_notm}} Resiliency Orchestration service is provisioned for Zerto on {{site.data.keyword.cloud_notm}}. This model can continuously protect the virtual machines, operating systems, and data on the {{site.data.keyword.cloud_notm}}, with uninterrupted DR testing, RTO/RPO (Recovery Time Objective/Recovery Point Objective) visibility, fail-over and fail-back capability.

All functions are managed via the {{site.data.keyword.cloud_notm}} Resiliency Orchestration dashboard by IBM Resiliency Services Global Command Center.

For more information, see [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration).

## IBM Managed Services for Zerto (without Orchestration)

In this model, a fully managed DR solution is provisioned for Zerto on {{site.data.keyword.cloud_notm}}. This model is suitable if you want a managed service for Zerto Virtual Replication only, without the {{site.data.keyword.cloud_notm}} Resiliency Orchestration service on the {{site.data.keyword.cloud_notm}}.

For more information, see [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top).

## Procedure to request managed services for Zerto on IBM Cloud

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Getting Started** from the left navigation pane.
2. Scroll down the page and under **Order additional managed services**, click the **Managed Services for Zerto on IBM Cloud** card.
3. On the **Zerto on IBM Cloud** page, review the description and technical specifications for Zerto on {{site.data.keyword.cloud_notm}} as a managed service, and then click **Create**.
4. Specify the configuration settings according to your requirements or accept the default values.
5. Click either **vCenter Server** or **Cloud Foundation** to add the service to one of your instances.
6. To add the service while you order a new instance, click **Add to New Instance**, and then continue with ordering a new [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances), [vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-with-hybridity-bundle-instances), or [Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances) instance.
7. To add the service to an existing instance, click **Add to Existing Instance**, select the instance that you want from the list, and then confirm that you want to proceed with the order by clicking **Provision**.

### Related links

* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-viewing-and-removing-services-for-vcenter-server-instances)
* [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-viewing-and-removing-services-for-cloud-foundation-instances)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
