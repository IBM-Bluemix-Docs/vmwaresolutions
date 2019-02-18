---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing user accounts and settings

{{site.data.keyword.vmwaresolutions_full}} communicates with the {{site.data.keyword.cloud_notm}} infrastructure through {{site.data.keyword.slapi_short}} calls. To access the {{site.data.keyword.slapi_short}} securely, you must link the credentials of your {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account to your {{site.data.keyword.cloud_notm}} account.

The {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account was previously known as the IBM SoftLayer account.
{:note}

You can also specify whether you want to receive email and console notifications for various events.

## Before you begin

* You can link only one {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account to one {{site.data.keyword.cloud_notm}} user account.
* The {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account that you're using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} infrastructure account requirements](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-requirements-for-the-ibm-cloud-infrastructure-account).
* If the API key for your {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account changes, you must update the key on the **Settings** page in the {{site.data.keyword.vmwaresolutions_short}} console.

   **Important:** It is your responsibility to ensure that the API key that is saved on the **Settings** page is correct and up-to-date. Otherwise, operations that require API key validation might fail.

## Procedure to manage user accounts and settings

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Settings** from the left navigation pane.
2. In the **Notifications** area, specify your notification settings.
   * If you want to be notified by email when events occur, click **Enable email notifications**.
   * If you want to be notified in the console when events occur, click **Enable console notifications**.
3. In the **IBM Cloud Infrastructure Credentials** area, enter the user name and API key of your {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account:
   * If your {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account and your {{site.data.keyword.cloud_notm}} account are linked, click **Retrieve** to enter the credentials automatically.
   * If your {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account and your {{site.data.keyword.cloud_notm}} account aren't linked, you must link them. Log in to the [{{site.data.keyword.cloud_notm}} infrastructure customer portal](https://control.softlayer.com/) and follow the instructions on the console to get the credentials, then enter them.
   * If you don't have an {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account, [sign up for one](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing-up-for-required-accounts) and follow the instructions on the console to get the credentials, then enter them.
4. Click **Save Credentials**.

## Results

After the {{site.data.keyword.cloud_notm}} account and the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account are linked, the console automatically retrieves the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account credentials to communicate with your VMware environment on {{site.data.keyword.cloud_notm}}.

The stored {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account credentials are used in future operations that require interaction with the {{site.data.keyword.cloud_notm}} infrastructure.

If email or console notifications are enabled for certain instance events, you're notified by email or console messages when these events occur.

### Related links

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)
* [Notifications](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-system-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api){:new_window}
