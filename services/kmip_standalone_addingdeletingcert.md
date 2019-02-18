---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting certificates for KMIP for VMware on IBM Cloud instances

After your KMIP for VMware on {{site.data.keyword.cloud}} instance is ready, you must add certificates to it. When you no longer need a certificate, delete it from your instance.

## Procedure to add certificates to KMIP for VMware on IBM Cloud instances

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. Scroll down to the **KMIP for VMware on IBM Cloud Instances** table, click the instance that you want to add certificates for.
3. Click **Add**.
4. In the **Add Client SSL Certificate** window, enter the certificate name and content.

   The certificate name cannot be reused within your selected instance. The certificate content must be valid and contain the BEGIN CERTIFICATE and END CERTIFICATE tags, and the certificate cannot be reused in the selected region where the instance is deployed.
   {:note}
5. Click **Add**.

## Procedure to view certificates for KMIP for VMware on IBM Cloud instances

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. Scroll down to the **KMIP for VMware on IBM Cloud Instances** table, click the instance to view the certificates for.
3. View the list of added certificates under the **Client SSL Certificates** section.
4. To view the content of a particular certificate, click **Download**.

## Procedure to delete certificates from KMIP for VMware on IBM Cloud instances

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. Scroll down to the **KMIP for VMware on IBM Cloud Instances** table, click the instance that you want to delete certificates from.
3. In the **Client SSL Certificates** table, locate the certificate that you want to delete and click the **Delete** icon.

   The client immediately loses access to all keys for the purpose of encrypting and decrypting data or backup data. For the client to gain access again, you must add the client SSL certificate again.
   {:note}

### Related links

* [Viewing KMIP for VMware on IBM Cloud instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-viewing-kmip-for-vmware-on-ibm-cloud-instances)
* [Ordering KMIP for VMware on IBM Cloud instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-kmip-for-vmware-on-ibm-cloud-instances)
* [Deleting KMIP for VMware on IBM Cloud instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-deleting-kmip-for-vmware-on-ibm-cloud-instances)
* [Activity Tracker events](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-activity-tracker-events)
