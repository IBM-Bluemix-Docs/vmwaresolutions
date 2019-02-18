---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

#	Host Profiles

vCenter has a feature that is called Host Profiles. This feature creates a profile that captures a pre-configured and validated reference host configuration and helps a system administrator manage the host configurations in a cluster. Host Profiles provide an automated and centrally managed mechanism for host configuration and configuration compliance. Host Profiles enable the configuration to be treated as a managed object, which has a catalog of parameters to configure; networking, storage, security, and other host-level parameters. These Host Profiles can be applied to individual hosts, a cluster, or all the hosts and clusters associated to a host profile.

As more VMware vCenter Server on {{site.data.keyword.cloud}} vSphere ESXi hosts are deployed by the IC4VS automation that deployed the original cluster, there are less configuration drift than with manual methods of adding hosts. However, system administrator actions, besides the automation can make the hosts configuration different. For example, more NFS storage is added or extra VLANs are added. The use of Host Profiles to validate the configuration of a new host by checking compliance of this host against an existing host is a valid use case of this tool within {{site.data.keyword.cloud_notm}}.

To add more hosts to your vCenter Server cluster, see [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-instances).

Note:
*	For instances deployed at, or upgraded to, V2.1 or higher, newly deployed ESXi servers and clusters are patched with recent, but not necessarily the most recent ESXi updates from VMware.
*	You're responsible for all other updates to VMware components, including ensuring that newly deployed ESXi servers and clusters have all the most recent updates you require.

We advise that after a new host is added into the cluster, that it is placed in Maintenance Mode so that it can be reviewed for compliance drift and remediated before you host any workloads.

The following sequence is required to check compliance:
1.	Create a Host Profile from an existing host.
2.	Attach the new host to the Host Profile.
3.	Check the compliance of the new host with the Host Profile.
4.	Review compliance failures and remediate.

##	Creating a host profile from an existing host

1.	From the vSphere Web Client Home, click **Policies and Profiles**.
2.	Click **Host Profiles** and navigate to the Host Profiles view.
3.	Click the **Extract Profile from a Host icon**.
4.	Select an existing host that acts as the reference host and click **Next**.
5.	Enter the name and enter a description for the new profile and click **Next**.
6.	Review the summary information for the new profile and click **Finish**.
7.	The new profile appears in the profile list.

##	Attaching the new host to the host profile

1.	From the **Profile List** in the Host Profiles main view, select the Host Profile that was previously created to be applied to the new host.
2.	Click the **Attach/Detach a host profile to hosts and clusters icon**.
3.	Select the new host from the expanded list and click **Attach**.
4.	The new host is added to the Attached Entities list.
5.	Click **Next** and then click **Finish**.

##	Checking the compliance of the new host with the host profile

1.	Navigate to the Host Profile that was previously completed.
2.	Click the Check **Host Profile Compliance icon**.
3.	In the **Objects tab**, the compliance status is updated as; _Compliant, Unknown, or _Non-compliant_. A non-compliant status indicates a discovered and specific inconsistency between the profile and the new host.

##	Reviewing compliance failures and remediation

1. To see more detail on compliance failures, select the **Host Profile** from the **Objects** tab that is used in the compliance check.
2. In order to see specific detail on which parameters differ between the host that failed compliance and the Host Profile, click the **Monitor tab** and select the **Compliance view**.
3. Expand the object hierarchy and select the failing host.
4. The differing parameters are displayed in the Compliance window, under the hierarchy.
5. Review the parameters and understand why the new host can vary from the reference host. For parameters where the compliance isn't acceptable, remediate before moving the new host from maintenance mode. For example, where configuration drift is caused by system administrator action.

### Related links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
