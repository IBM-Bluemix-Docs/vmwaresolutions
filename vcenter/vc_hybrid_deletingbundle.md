---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Removing the Hybridity Bundle from a vCenter Server instance

To remove the Hybridity Bundle license from your vCenter Server instance, you must replace the VMware NSX and VMware vSAN rental license keys with Bring Your Own License (BYOL) keys in the VMware vSphere Web Client. Additionally, you must open a support ticket to cancel charges for the rental licenses.

Downgrading your license might cause your vCenter Server instance to fail. You can choose to downgrade a license at your own risk, but first consider the functions that are not available when you downgrade. For more information, see [Comparison chart for VMware component editions](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-comparison-chart-for-vmware-component-editions).
{:important}

## Important considerations before you remove the Hybridity Bundle from a multi-site environment

Review the following considerations before you remove the Hybridity Bundle from a multi-site environment:

* You must apply BYOL licenses to all multi-site deployments before you remove rental licenses.
* You must combine VMware NSX licenses and have enough capacity to use across all multi-site deployments.
* You must create a single support ticket to remove the Hybridity Bundle from all multi-site deployments.

While removing the Hybridity Bundle from a multi-site environment, BYOL licenses are applied. It is your responsibility to ensure that the license editions are consistent across all sites in the multi-site configuration.
{:note}

## Before you remove the Hybridity Bundle

Verify the following requirements before you remove the Hybridity Bundle:

* You have a V2.4 or later vCenter Server instance with the Hybridity Bundle enabled.
* You do not have the VMware HCX on {{site.data.keyword.cloud_notm}} service installed on your vCenter Server instance.
* You have access to the VMware vSphere Web Client as Administrator.
* If not already applied, you have BYOL keys available to apply for VMware NSX and each VMware vSAN cluster.
* Optionally and if not already applied, you have BYOL keys available to apply for the VMware vCenter Server and VMware vSphere Enterprise Plus licenses.

## Procedure to remove the Hybridity Bundle

1. Log in as **Administrator** to the VMware vSphere Web Client where you want to remove the Hybridity Bundle.
2. Click **Home > Administration > Licensing > Licenses**.
3. Click the **Assets** tab.
4. Complete the following steps to install a VMware NSX BYOL:
   1. Click the **Solutions** tab.
   2. Select NSX for vSphere and click **All Actions > Assign license**.
   3. Click the **Add** icon and type the license key. Click **Next**.
   4. Type the name for the license and click **Next**. Click **Finish** to add the license.
   5. Select the new license key.
   6. Write down the full license keys for both the license that is applied and the license that is replaced.

   You must have the license details available to use later in this procedure.
   {:important}
   7. Click **OK** to assign the license.
5. Complete the following steps to install a VMware vSAN BYOL:
   1. Click the **Clusters** tab.
   2. Complete the following steps for each vSAN cluster that is associated with your vCenter Server instance:
    1. Select a vSAN cluster and click **All Actions > Assign license**.
    2. Click the **Add** icon and type the license key. Click **Next**.
    3. Type the name for the license and click **Next**. Click **Finish** to add the license.
    4. Select the new license key.
    5. Write down the cluster name and full license keys of both the license that is applied and the license that is replaced.

    You must have the license details available to use later in this procedure.
    {:important}
    6. Click **OK** to assign the license.
6. Optionally complete the following steps to install a VMware vCenter Server BYOL:
   1. Click the **vCenter Server systems** tab.
   2. Select vCenter Server and click **All Actions > Assign license**.
   3. Click the **Add** icon and type the license key. Click **Next**.
   4. Type the name for the license and click **Next**. Click **Finish** to add the license.
   5. Select the new license key.
   6. Write down the full license keys of both the license that is applied and the license that is replaced.

   You must have the license details available to use later in this procedure.
   {:important}

   7. Click **OK** to assign the license.
7. Optionally complete the following steps to install a VMware vSphere Enterprise Plus BYOL:
  1. Click the **Hosts** tab.
  2. Complete the following steps for each cluster that is associated with your vCenter Server instance or complete for all clusters at the same time if the same license is being applied to all clusters associated to your vCenter server:
    1. Select all hosts that are associated to the cluster and click **All Actions > Assign license**.
    2. Click the **Add** icon and type the license key. Click **Next**.
    3. Type the name for the license and click **Next**. Click **Finish** to add the license.
    4. Select the new license key.
    5. Write down the cluster name and full license keys of both the license that is applied and the license that is replaced.

    You must have the license details available to use later in this procedure. If license keys are not same across all clusters, ensure to write down the cluster name associated to each license key.
    {:important}

    6. Click **OK** to assign the license.
8. Remove the rental licenses.
   1. Click the **Licenses** tab.
   2. Select the licenses that you replaced in steps 4 - 7.
   3. Click the **Remove Licenses** icon.
9. Open a support ticket and provide the following information to cancel charges for the rental licenses:
  * The name of your vCenter Server instance or instances.
  * The ID associated with your vCenter Server instance or instances.
  * A list of the BYOL license keys that you installed in this procedure. Where applicable, provide the instance and cluster name with license keys for vSphere and the vSAN clusters.
  * A list of the rental license keys that you removed in this procedure. Where applicable, provide the instance and cluster name with license keys for vSphere and vSAN clusters.

  The IBM Support and Operations teams access the vCenter management layer of your {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account to verify that the rental licenses have been removed before canceling the Hybridity Bundle rental license charges.
  {:note}

### Related links

* [Ordering vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-with-hybridity-bundle-instances)
* [Viewing vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vcenter-server-with-hybridity-bundle-instances)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
