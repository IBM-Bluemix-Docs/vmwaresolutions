---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Ordering KMIP for VMware on IBM Cloud instances

You can order a KMIP for VMware on {{site.data.keyword.cloud}} instance without associating it to any VMware instance for flexible management of the service and instances.

## Before you begin

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
* You reviewed all the considerations in [Considerations when installing KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip-for-vmware-on-ibm-cloud-overview).

## Procedure to order KMIP for VMware on IBM Cloud instances

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Getting started** from the left navigation pane.
2. In the **Order additional services** area, click **KMIP for VMware on IBM Cloud**.
3. On the **KMIP for VMware on IBM Cloud** page, configure the service settings as required.
4. Click **Provision**.

## KMIP for VMware on IBM Cloud service configuration

When you order this service, provide the following settings:

### Instance Name

Specify a name for your KMIP for VMware {{site.data.keyword.cloud_notm}} instance.

### Service Region

Select the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware {{site.data.keyword.cloud_notm}} instance is to be hosted.

{{site.data.keyword.cloud_notm}} maintains a highly available KMIP for VMware on {{site.data.keyword.cloud_notm}} service endpoint in each region where the service is available.

Table 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} service endpoint regions

| Region         | Endpoints               |
|:---------------|:-----------------------|
| Germany        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokyo          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| US South       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### API Key for Service ID

Enter the API key for the {{site.data.keyword.cloud_notm}} Service ID that is used to access the IBM Key Protect Service instance.

### Key Protect Instance

Click **Retrieve** to get the list of available IBM Key Protect Service instances and select the one to use for key management.

### Customer Root Key

Click **Retrieve** to get the customer root key that is stored in your selected IBM Key Protect instance.

## Results

The ordering of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the order by viewing the instance details.

When the instance is ready to use, the status of the instance is changed to **Installed** and you receive a notification by email.

## What to do next

Add client certificates for the KMIP for VMware on {{site.data.keyword.cloud_notm}} instance that you ordered. For more information, see [Adding, viewing, and deleting certificates for KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-adding-viewing-and-deleting-certificates-for-kmip-for-vmware-on-ibm-cloud-instances).

## Related links

* [Viewing KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-viewing-kmip-for-vmware-on-ibm-cloud-instances)
* [Deleting KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-deleting-kmip-for-vmware-on-ibm-cloud-instances)
* [Activity Tracker events](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-activity-tracker-events)
