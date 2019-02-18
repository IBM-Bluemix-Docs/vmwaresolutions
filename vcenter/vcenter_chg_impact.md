---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Considerations about changing vCenter Server artifacts

Changing users, resources, or subnets that are reserved for {{site.data.keyword.vmwaresolutions_full}} can impact management operations.

Do not edit the global permissions of the **ic4v-vCenter** group in the **Users and Groups** page on the VMware vSphere Web Client. Such changes include: changing the user name, deleting the user, or changing its password.
Use the **root** host user ID. The **ic4vroot** host user ID has been created for IBM use only.
{:important}

## automation ID
{: faq}

The **automation** ID is a user account that is used by the automated operations provided in the {{site.data.keyword.vmwaresolutions_short}} console.

Users and passwords for the automated operations in the console must not be changed because the console operations that depend on those credentials might fail.

## Service-specific user accounts

Each service creates an internal user account in vCenter Server. This account is necessary so that management operations that are associated to a service can connect to vCenter Server to perform the operations on the service.

To prevent outages and connection problems, if you change the user ID, password, or password expiration settings for this user account, ensure that you also update the information in the associated service.
{:important}

The user ID for this account is in the format `<service_name>-<truncated service_uuid>@test.local` or `<service_name>-<truncated service_uuid>@example-domain.local`. For example, the user ID that the Veeam on {{site.data.keyword.cloud_notm}} service uses to connect to vCenter Server to perform scheduled backups is `Veeam-<Veeam_uuid>@test.local`.

The `<service_name>` together with the `<service_uuid>` truncates to 20 characters.
{:note}

## VMware resources for vCenter Server instances (V1.9 and later)

For instances deployed in V1.9 and later, if the vCenter Server instance is in a **Ready to Use** state, you can modify the VMware virtual datacenter, cluster, switches, port groups, and customer datastore names from the VMware vSphere Web Client.

However, you must not change the name of the management datastore from its default value, which is  **vsanDatastore** for vSAN instances and **management-share** for Network File System (NFS) instances. In addition, you must not change the name of the network uplinks that are created during provisioning.

## VMware resources for vCenter Server instances (V1.8 and earlier)

The following table lists the operations that might be impacted if the SSO administrator changes VMware vCenter Server resources outside of the {{site.data.keyword.vmwaresolutions_short}} console. If a solution to recover is available, it is provided as well.

This table is applicable to instances deployed at V1.8 and earlier, in addition to instances deployed at V1.8 and earlier and then upgraded to V1.9 or later.

Table 1. Operations that are impacted by changing VMware resources

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Change the VMware virtual datacenter name. | Adding a VMware virtual datacenter might fail because the new ESXi server cannot join the changed virtual datacenter. | Important | Change the VMware virtual datacenter name back to the original name. |
| Change any port group names.    | Adding an ESXi server might fail. | Important | Change the port group name back to the original name. |
| Change the cluster name. | Adding an ESXi server might fail. | Important | Change the cluster name back to the original name.
| Change the public or private Distributed Virtual Switch (DVS) name. | Adding an ESXi server might fail. | Important | Change the public or private Distributed Virtual Switch (DVS) name to the original name.
| Change the vSAN datastore name in the instance that uses vSAN. | Adding an ESXi server might fail.<br><br>Upgrading the instance might fail. | Important | Change the vSAN datastore name back to the original name, **vsanDatastore**.
| Change the management NFS datastore name in the instance that uses NFS. | Adding an ESXi server might fail.<br><br>Upgrading the instance might fail. | Important | Change the NFS management datastore name back to the original name, **management-share**, and remount the NFS datastore as read-only on the ESXi server.

The following table lists the operations that might be impacted if SSH or shell access is disabled for various resources.

Table 2. Operations that are impacted by SSH and shell access (local)

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Disable SSH or shell access for vCenter Server or PSC.    | Pairing a primary and secondary instance might fail.    | Important    | N/A    |
| Disable SSH or shell access for ESXi.    | Adding and removing hosts, services, and network storage to the instance might fail.    | Important    | N/A    |

If you choose to disable SSH or shell access, you should re-enable it temporarily before performing the indicated operations.

## Management subnets for vCenter Server instances

The following information discusses the subnets that are ordered by {{site.data.keyword.vmwaresolutions_short}} and it provides options for you to order extra subnets for your own use.

**CAUTION:** Do not use these components for other purposes, or the stability of your environment is severely compromised.

With each {{site.data.keyword.cloud_notm}} Bare Metal Server order, the following ranges of IP addresses are ordered by default:
*  A primary public range of 32 IP addresses
*  A primary private range of 64 IP addresses

In addition, the following management subnets are also reserved for {{site.data.keyword.vmwaresolutions_short}}:
*  Two portable private subnets of 64 IP addresses on the first VLAN: one for management and the other one for VTEPS
*  Two portable private subnets of 64 IP addresses on the second VLAN: one for VMotion and one for vSAN
*  A public portable subnet of 16 IP addresses on the public VLAN

If you need more subnets to use, you can obtain IP addresses to use in one of the following ways:
*  **Option 1 (recommended)**: Use VMware NSX virtual network overlays. A sample VXLAN template is provided upon order. This VXLAN can be used as a starting point for building software-defined networking (SDN). For more information, see [Configuring your network to use the customer-managed NSX Edge](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).
*  **Option 2**: Order your own portable public or private subnets to obtain IP addresses. To distinguish the subnets that you order from the management subnets, you can add notes to all the subnets that you are ordering.
