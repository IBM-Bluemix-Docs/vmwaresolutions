---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing Zerto on IBM Cloud

After the Zerto on {{site.data.keyword.cloud}} service is deployed into your instance, you can configure or update Zerto Virtual Replication, and deploy more Virtual Replication Appliances to newly added ESXi servers.

## Using your own certificate for Zerto

As a best practice, use your own SSL certificate for Zerto Virtual Manager (ZVM). After you deployed Zerto on {{site.data.keyword.cloud_notm}}, replace the SSL certificate for ZVM with your own certificate. For more information, see [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Managing the configuration of Zerto replications

To manage the configuration of Zerto replications, log in to the Zerto Virtual Replication console by using the vCenter credentials with administrator permissions. For example, re-pairing Zerto instances or configuring virtual protection groups to replicate virtual machines.

When you're replicating between different {{site.data.keyword.cloud_notm}} Zerto instances, you can configure replication directly between the Zerto instances. If you're replicating between the {{site.data.keyword.cloud_notm}} Zerto instance and your own data center, you must install Zerto yourself in your own data center. This instance can license itself automatically when you pair it with the {{site.data.keyword.cloud_notm}} Zerto instance.

Zerto replication doesn't support Network Address Translation (NAT) traversal. Establishing connectivity between the {{site.data.keyword.cloud_notm}} Zerto instance and your own data center might require customization of routes on the Zerto Virtual Manager (ZVM) appliances or Zerto Virtual Replication Appliances (VRAs) on either side. Establishing connectivity might also require secure tunneling between the sites. When you're configuring or reconfiguring routes on ZVM appliances, you must ensure that all ZVM appliances can connect successfully to `zerto.com` for usage reporting. You can verify this connection by opening a browser session to `https://www.zerto.com` from the ZVM appliance.

The Management VMware NSX Edge Services Gateway (ESG) of Cloud Foundation instances and vCenter Server instances on {{site.data.keyword.cloud_notm}} is preconfigured to allow outbound HTTPS (TCP port 443) communications that originate from ZVM.
{:note}

## Updating Zerto Virtual Replication

To update Zerto Virtual Replication, log in to the Zerto Virtual Replication console.

## Deploying VRAs to newly added ESXi servers

When you add or remove ESXi servers for the primary cluster of your instance, VRAs are automatically deployed or removed. VRAs aren't automatically deployed to ESXi servers in the secondary clusters of your instance. You can deploy VRAs yourself from the Zerto Virtual Replication console.

### Related links

* [Zerto on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto-on-ibm-cloud-overview)
* [Requesting managed services for Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-requesting-managed-services-for-zerto-on-ibm-cloud)
* [zerto.com website](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Zerto disaster recovery](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explanation of Zerto Virtual Replication Alerts](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
