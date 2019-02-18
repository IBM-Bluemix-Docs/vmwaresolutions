---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:faq: data-hd-content-type='faq'}

# Networking considerations for Cloud Foundation instances

Review the following information for details about networking considerations and requirements for your Cloud Foundation instances. Ensure that you meet the requirements so that your instance functions properly.

## Networking components for Cloud Foundation instances
{: faq}

To review the networking components that are included in your Cloud Foundation instance, see [Technical specifications for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cloud-foundation-overview#technical-specifications-for-cloud-foundation-instances).

## Firewall considerations

If you're using firewalls, you must configure rules for all communications from the {{site.data.keyword.IBM}} CloudDriver virtual server instance (VSI) and the SDDC Manager virtual machines (VMs). These rules must allow all protocols to communicate on the IP addresses `10.0.0.0/8` and `161.26.0.0/16`. Examples of such firewalls are NSX Distributed Firewalls (DFW) or Vyatta firewalls.

## Using VMware NSX with your VMs

During Cloud Foundation instance deployment, VMware NSX is ordered, installed, licensed, and configured in your instance. Also, NSX Manager, NSX Controllers, and NSX Transport Zone are set up, and each ESXi server is configured with the NSX components.

However, if your workload VMs need to communicate with each other and to access the internet, it is your responsibility to configure NSX for use by your VMs.

For more information about how to set up NSX, see the following topics:
* For a primary (single) Cloud Foundation instance, see [Setting up NSX for workload VMs on VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* For a multi-site Cloud Foundation instance, see [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.

## Considerations when you change passwords for NSX components

Review the following considerations before you change the passwords for the NSX Manager, NSX Controllers, and NSX Edge:
* Do not change the NSX Manager password. You can find this password on the **Summary** page of the instance in the {{site.data.keyword.vmwaresolutions_short}} console.
* You can change passwords for NSX Controllers. For instructions on how to change passwords for NSX Controllers, see [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Do not change the password for the management VMware NSX Edge Services Gateway (ESG).

### Related links

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
