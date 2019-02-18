---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust KeyControl on IBM Cloud overview

The HyTrust KeyControl on {{site.data.keyword.cloud}} service simplifies the management of encrypted workloads. This service automates and simplifies the lifecycle of encryption keys, includes key storage, key distribution, key rotation, and key revocation. Using FIPS 140-2 compliant encryption, enterprises can easily manage encryption keys at scale.

This service is available only to instances that are running vSphere 6.5 and that are deployed in or upgraded to  V2.5 and later. The current HyTrust KeyControl version that is installed is 4.2.
{:note}

## Technical specifications for HyTrust KeyControl on IBM Cloud

The following components are ordered and included in the HyTrust KeyControl on {{site.data.keyword.cloud_notm}} service:

### HyTrust KeyControl appliance

* CPU: 2 vCPU
* RAM: 8 GB
* Disk: 20 GB VMDK resident on vSAN in converged cluster
* Network: Placed on VLAN-backed private portable network specified for management

### High availability

By default, two KeyControl appliances are deployed in an active-active clustered configuration.

Optionally, you can specify to deploy two KeyControl appliances in a stand-alone unclustered configuration.

### Licenses and fees

A HyTrust KeyControl license is ordered for each instance installation.

## Considerations when you remove HyTrust KeyControl on IBM Cloud

Before you remove the HyTrust KeyControl on {{site.data.keyword.cloud_notm}} service, ensure that you decouple all clients from using KeyContol. After you remove the service, the keys might be deleted and you might be locked out of your VMs.

### Related links

* [Ordering HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-hytrust-keycontrol-on-ibm-cloud)
* [Managing HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing-hytrust-keycontrol-on-ibm-cloud)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [HyTrust website](https://www.hytrust.com/)
