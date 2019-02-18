---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Inviting users to access services and resources

{{site.data.keyword.vmwaresolutions_full}} is integrated with {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) for collaboration among multiple users. After you sign up for an {{site.data.keyword.cloud_notm}} account and log in to the {{site.data.keyword.vmwaresolutions_short}} console, you can add users to the {{site.data.keyword.cloud_notm}} account. These added users can share the services and resources that are provisioned for the account.

## Before you begin

* Ensure that you are the account owner or that your platform management role for the **VMware Solutions** service is **Administrator**.
* Ensure that you reviewed the user roles and permissions in [Managing user access with Identity and Access Management](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam).

## Procedure to invite users to access services and resources

1. At the left side of the banner, click **Manage > Security > Identity and access**.
2. On the **Users** page, click **Invite users**.
3. On the **Invite users** page, in the **Users** section, enter the email addresses of the users that you want to invite in the **Email address** field.
4. In the **Access** section, expand **Services**, and then complete the following tasks:
   1. Select **Resource** from the **Assign access to** list.
   2. Select **VMware Solutions** from the **Services** list.
   3. Select the platform access role that you want to assign to the users. It can be **Administrator**, **Editor**, **Operator**, or **Viewer**.
5. Click **Invite users**.

## Results

After the added users accept your invitation, they can log in to the {{site.data.keyword.vmwaresolutions_short}} console and switch to your account. To do so, in their profile settings, users click their user account icon from the {{site.data.keyword.vmwaresolutions_short}} console banner. Then, the added users can collaborate and share the services and resources available in your specified account.

### Related links

* [Inviting users and assigning access](/docs/iam?topic=iam-iamuserinv)
* [Managing identity and access](/docs/iam?topic=iam-getstarted)
* [Managing users and access](/docs/iam/iamusermanage.html)
* [What is IAM](/docs/iam?topic=iam-iamoverview)
* [Migrating pre-V2.5 vCenter Server instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-migrating-pre-v2-5-vcenter-server-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 vCenter Server with Hybridity Bundle instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-migrating-pre-v2-5-vcenter-server-with-hybridity-bundle-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 Cloud Foundation instances to IBM Cloud accounts](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-migrating-pre-v2-5-cloud-foundation-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 NetApp ONTAP Select instances to IBM Cloud accounts](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-migrating-pre-v2-5-netapp-ontap-select-instances-to-ibm-cloud-accounts)
* [Migrating pre-V2.5 VMware Federal instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-migrating-pre-v2-5-vmware-federal-instances-to-ibm-cloud-accounts)
