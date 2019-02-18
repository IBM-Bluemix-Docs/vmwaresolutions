---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud overview

The HyTrust CloudControl on {{site.data.keyword.cloud}} service enforces and controls compliance against security standards that includes role-based access control (RBAC), approval, and auditing. When the service is combined with HyTrust DataControl, the service ensures that virtual machines and workload data don't leave a particular region, cluster, or ESXi server within the {{site.data.keyword.CloudDataCent_notm}}.

This service is available only to instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later. The current HyTrust CloudControl version that is installed is 5.4.0.
{:note}

## Technical specifications for HyTrust CloudControl on IBM Cloud

The following components are ordered and included in the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service:

### HyTrust CloudControl appliance

* CPU: 4 vCPU
* RAM: 16 GB
* Disk: 70 GB VMDK resident on vSAN in converged cluster
* Network: Placed on VLAN-backed private portable network specified for management

### High availability

Two CloudControl appliances are deployed in an active-passive configuration.

### Licenses and fees

Per-host license: A HyTrust CloudControl license is ordered for each host in the environment.

## Considerations when you remove HyTrust CloudControl on IBM Cloud

Before you remove the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from HyTrust CloudControl.

### Related links

* [Ordering HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-hytrust-cloudcontrol-on-ibm-cloud)
* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-hytrust-cloudcontrol-on-ibm-cloud)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [HyTrust website](https://www.hytrust.com/)
