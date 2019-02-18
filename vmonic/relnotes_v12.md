---

copyright:

  years:  2016, 2019

lastupdated: "2016-12-12"

---

# Release notes for V1.2

This release includes new features, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Component updates

The new version of VMware ESXi is vSphere 6.0 u2 p03, updated from ESXi 6.0 u2 in the previous release.

## IBMid and Bluemix accounts association

{{site.data.keyword.vmwaresolutions_full}} is provided as an infrastructure solution in the IBM Bluemix® catalog. You must associate the **IBMid** account with a Bluemix account to use your **IBMid** account to log in to the {{site.data.keyword.vmwaresolutions_short}} console.

For more information, see the following topics:
* [Getting started](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started-with-ibm-cloud-for-vmware-solutions)
* [Troubleshooting for accessing Bluemix](/docs/account?topic=account-accessing){:new_window}

## Zerto disaster recovery

You can order both VMware Cloud Foundation instances and VMware vCenter Server instances with Zerto disaster recovery included when you order your instance. You can also add Zerto disaster recovery to your existing Cloud Foundation instances and vCenter Server instances in the instance details page.

For more information, see the following topics:
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances)
* [Viewing Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-viewing-cloud-foundation-instances)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)
* [Viewing vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-viewing-vcenter-server-instances)
* [Zerto disaster recovery](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto-on-ibm-cloud-overview)

## Pricing information

You can now see and review the estimated cost of your ordered instance before you decide to place an order. After you select your components when you order your instance, the total cost and the detailed pricing of all components are displayed on the **Summary** page.

For more information, see the following topics:
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)

## Enhancements to the instance order process

The instance order process is greatly improved through the following enhancements:
* For both Cloud Foundation instances and vCenter Server instances, new validation checks are in place to ensure that the SoftLayer® user account that you are using has the required user permissions, that VLAN spanning is enabled, and that the correct API key is provided. If any requirements are not met, you get instructions right on the user interface to fix the problems.
*  For vCenter Server instances, the order in which you select the instance components is optimized so that only the data centers that have the available hardware and ESXi servers that you need are displayed. This change minimizes the possibility of errors later on.

For more information, see the following topics:
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-ordering-cloud-foundation-instances)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances)

## Additional email notifications

You now receive a notification by email when new ESXi servers are added to your instances and when existing ESXi servers are removed. In addition, you get notified by email when an instance is deleted. The notification settings are enabled by default. Based on your preferences, you can set what notifications you want to receive on the **Settings** page.

For more information, see [User account and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-accounts-and-settings).
