---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Applying updates to vCenter Server with Hybridity Bundle instances

The process of applying patches and updates to vCenter Server with Hybridity Bundle instances is automated for the management components only. The VMware updates must be applied manually.

## Before you begin

Beginning with V2.5, IBM CloudDriver updates are no longer listed because automatic updates are enabled. Actions such as adding a host, adding a cluster, and ordering a service automatically updates the instance to the latest version. For more information about automatic updates, see the *IBM CloudDriver resiliency* section in [Release notes for V2.5](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-release-notes-for-v2-5).
{:note}

Before you attempt to apply an update, expand the update entry by clicking the down arrow and verify the following information:
* The version of the update. You must apply the updates in chronological sequence that is from the earliest one to the most recent one. Ensure that you applied all the previous updates before you apply the most recent one. For example, you must apply the V2.3 update before attempting to apply the V2.4 update.
* Whether downtime is required.
* The total estimated time to complete the update.
* The impact of the update on the VMware virtual environment.
* The update details.

The following table shows how different levels of impact affect the system.

Table 1. Update levels and impact

| Update level  | Impact        |  
|:------------- |:------------- |
| Low    | This update does not affect any systems. You do not have to apply it during scheduled downtime. |  
| Medium | This update might affect some systems. It is recommended that you apply it during scheduled downtime. |  
| Major  | This update affects some or all systems. You must apply it during scheduled downtime. |  

## Procedure to apply updates to vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.vmwaresolutions_full}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to update.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then, click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.
   If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver Virtual Server Instance (VSI), as a result of a firewall rule or other networking issue. Resolve the problem before continuing with the next step, otherwise the update might fail.
4. Click **Update and Patch** on the left navigation pane.

   The **Update and Patch** page contains only the packages for updating the IBM management components, not the VMware updates. {{site.data.keyword.vmwaresolutions_short}} applies VMware updates for the following operations:
   * When a new vCenter Server instance is deployed.
   * When new ESXi servers are added, the new ESXi servers are provisioned with VMware updates, but the existing ESXi servers are not updated.
   * When new clusters are added, the new clusters are provisioned with VMware updates, but the existing clusters are not updated.
   {:note}

5. For license upgrades, click **Upgrade**. Select the edition you want to upgrade to from the list and click **Upgrade**. License edition downgrades are not available.

   The license upgrade replaces all existing NSX licenses on the instance. Additional charges might be incurred from an overlap of old and new licenses if you upgrade in the middle of a billing cycle. To avoid additional charges, it is recommended to upgrade the license at the end of the billing cycle.
   {:note}

6. For software updates, click the down arrow to expand the update that you want to apply and then complete one of the following steps:
   *  To start the update immediately, click the overflow menu icon in the **Actions** column of the update entry, and then click **Update Now**.
   *  To schedule a future update, click the overflow menu icon in the **Actions** column of the update entry, and then click **Schedule Update**. Select the date, time, and time zone when you want the update to be started. Click **OK**.
7. If you are applying updates to vCenter Server instances in multi-site deployment configuration, a section titled **Steps Required to Update** is displayed. This section lists the update operations required for all instances in the multi-site deployment. You must complete the steps in sequence by clicking **Apply Update** for each step. You must wait for the previous step to complete before you start the next step.   

## Results

2. After you apply an update, a record appears in the software update status list, where you can view the detailed progress and status of the update. When the update is completed successfully, a record appears in the installed software updates list.

  To retrieve the most recent status for an update job, click the refresh icon in the upper right of the page.
  {:tip}

3. For details about the update statuses, see the following list:
<dl class="dl">
<dt class="dt dlterm">Available</dt>
<dd class="dd">The update is available to be applied. You cannot select an available update until all its previous updates are applied.
</dd>
<dt class="dt dlterm">In progress</dt>
<dd class="dd">The update job is initiated but not finished yet. You cannot apply any other updates until the current update job is
completed.</dd>
<dt class="dt dlterm">Installed</dt>
<dd class="dd">The update job is completed. The corresponding component of the VMware platform is updated.</dd>
<dt class="dt dlterm">Failed</dt>
<dd class="dd">The update job fails. The console reports an error for the update failure. Review the error and fix the reported issue
before you reapply the update.</dd>
<dt class="dt dlterm">Scheduled</dt>
<dd class="dd">The update job is scheduled for a later time. The update job starts automatically at the time that you scheduled.</dd>
<dt class="dt dlterm">Unknown</dt>
<dd class="dd">The status of the update job cannot be obtained. Contact IBM Support for assistance.</dd>
</dl>

4. If the update process fails at a specific step, [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support) for assistance. You will be advised how to resolve the problem and guided to attempt the upgrade again from the step that failed.

### Related links

* [vCenter Server with Hybridity Bundle overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-with-hybridity-bundle-overview)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQs](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
