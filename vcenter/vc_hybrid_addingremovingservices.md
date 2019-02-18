---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances

You can order services for your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instance.

## Available services for vCenter Server with Hybridity Bundle instances

The following services are available to vCenter Server with Hybridity Bundle instances, together with the installed service versions.

Table 1. Available services for vCenter Server with Hybridity Bundle instances

| Service name | Current service version | Instance version |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5-on-ibm-cloud-overview)                                 | BIG-IP VE v13.1.1.2 | V1.9 and later |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortigate-security-appliance-on-ibm-cloud-overview)       | 300 series | V1.8 and later |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortigate-virtual-appliance-on-ibm-cloud-overview) | 6.0.3 | V2.0 and later |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hytrust-cloudcontrol-on-ibm-cloud-overview)              | 5.4.0 | V2.3 and later |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hytrust-datacontrol-on-ibm-cloud-overview)              | 4.2.1 | V2.3 and later |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hytrust-keycontrol-on-ibm-cloud-overview)              | 4.2 | V2.5 and later |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ibm-cloud-private-hosted-overview) | 3.1 | V2.7 and later |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ibm-spectrum-protect-plus-on-ibm-cloud-overview)  | 10.1.2 | V2.2 and later |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip-for-vmware-on-ibm-cloud-overview)                  | 2.0  | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam-on-ibm-cloud-overview)                           | 9.5u3 | V1.8 and later |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-specifications-and-considerations)                        | 3.5.1 | V2.3 and later |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto-on-ibm-cloud-overview)                                  | 6.0 update 3 | V1.2 and later |

## Procedure to add services to vCenter Server with Hybridity Bundle instances

To apply a service to your vCenter Server with Hybridity Bundle instance, click the links in the table to review the considerations for the service. Then, check the components that are deployed and follow the instructions in the ordering topics to place your order.

### Service installation results

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** tab of the instance details with the **Installed** status.

## Procedure to view services for vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles using the credentials provided on the service details and you can manage the service from here.

## Procedure to remove services for vCenter Server with Hybridity Bundle instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to remove services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to remove and click the **Delete** icon.
5. In the **Delete Service** window, review the considerations or warnings if there are any. Select **I Understand** and click **Delete**.

### Service removal results

After your request for service removal is accepted, the service status is changed to **Removing**.

When the removal of the service is completed successfully, you are notified by email, and the service is removed from the **Services** page of the instance.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed services.
{:note}

### Related links

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
