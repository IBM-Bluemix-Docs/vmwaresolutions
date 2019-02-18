---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Managing user access with IAM

Access to {{site.data.keyword.vmwaresolutions_full}} service instances for the users in your account is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Every user that accesses the {{site.data.keyword.vmwaresolutions_short}} services in your account must be assigned an access policy with an IAM user role defined.

The access policy determines the actions that the user can perform within the context of the service or the instance that you select. The allowable actions are customized and defined by the {{site.data.keyword.cloud_notm}} service as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles.

Policies enable access to be granted at different levels. Some of the options include the following accesses:

* Access across all service instances in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance
* Access to all IAM-enabled services in your account

After you define the scope of the access policy, you assign a role.

Review the following information, which outlines the actions that each role allows within the {{site.data.keyword.vmwaresolutions_short}} service.

## Platform management roles and permissions

Platform management roles enable users to perform tasks on service resources at the platform level. For example, assign user access to the service, create or delete service IDs, create instances, and bind instances to applications.

The following table provides information about the actions that are mapped to platform management roles.

Table 1. Platform management roles and allowed actions

| Platform management role | Actions | Example actions |
|:----------------- |:----------------- |:----------------- |
| Viewer | Read-only actions | <ul><li>View the summary of instances</li><li>View the details of an instance</li></ul>|
| Editor | Update a specific instance |<ul><li>Add or remove ESXi servers</li><li>Add or remove clusters</li><li>Add or remove services</li><li>Upgrade an instance to a higher version</li></ul> |
| Operator | Read-only actions | <ul><li>List instances</li><li>View the details of an instance</li></ul> |
| Administrator | Full management access |<ul><li>Create new instances</li><li>Delete instances</li><li>Grant platform access to other users</li></ul>|

For {{site.data.keyword.vmwaresolutions_short}}, the following actions exist:

Table 2. Action descriptions and required roles

| Action | Operation on service | Role |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Create new instances | Administrator |
| vmware-solutions.instances.delete | Delete instances | Administrator |
| vmware-solutions.instances.view | <ul><li>List instances</li><li>View the detail of an instance</li></ul> | Viewer, Operator, Editor, and Administrator |
| vmware-solutions.instances.update | <ul><li>Add or remove ESXi servers</li><li>Add or remove clusters</li><li>Add or remove services</li><li>Upgrade an instance to a higher version</li></ul> | Editor and Administrator |
| vmware-solutions.account.update | Update account settings | Administrator |

## Managing access for users

You can add new users to the {{site.data.keyword.cloud_notm}} account so that these users can share the services and resources that are provisioned for the account. For more information, see [Inviting users to access services and resources](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inviting-users-to-access-services-and-resources).

You can also manage the access for existing users, including modifying existing access, assigning new access, and reviewing assigned access. To manage access for users, you must be the account owner or you must have the **Administrator** platform management role. For more information, see [Managing access to resources](/docs/iam?topic=iam-iammanidaccser).

## Migrating existing instances to IBM Cloud accounts

Because of the integration of {{site.data.keyword.vmwaresolutions_short}} with IAM, instances that are deployed in V2.5 and later releases in your {{site.data.keyword.cloud_notm}} account are automatically added to your account and are managed by IAM.

For your existing instances that were deployed in V2.4 and earlier releases, you can migrate them to specified {{site.data.keyword.cloud_notm}} accounts for IAM-enabled management. For more information, see the following topics:
* [Migrating pre-V2.5 vCenter Server instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-migrating-pre-v2-5-vcenter-server-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 vCenter Server with Hybridity Bundle instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-migrating-pre-v2-5-vcenter-server-with-hybridity-bundle-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 Cloud Foundation instances to IBM Cloud accounts](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-migrating-pre-v2-5-cloud-foundation-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 NetApp ONTAP Select instances to IBM Cloud accounts](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-migrating-pre-v2-5-netapp-ontap-select-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 VMware Federal instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-migrating-pre-v2-5-vmware-federal-instances-to-ibm-cloud-accounts)

### Related links

* [Managing identity and access](/docs/iam?topic=iam-getstarted)
* [Managing users and access](/docs/iam/iamusermanage.html)
* [What is IAM](/docs/iam?topic=iam-iamoverview)
