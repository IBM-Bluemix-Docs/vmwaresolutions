---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Preparing the installation environment

The installation of VMware HCX on IBM Cloud has the following software requirements:
* vSphere 5.5 U3, or vSphere 6.0u2 or higher.
* If NSX is used, version 6.2.2 or higher. NSX is required for policy migration.
* To use cross-cloud vMotion, the same affinity restrictions apply across clouds as they do on-premises. For more information, see the [VMware EVC and CPU Compatibility FAQ](http://bit.ly/2vK6Sp5).

## Configuring network connectivity

HCX must traverse the public internet and private lines, and connect to data center components, such as networks, switches, and port groups.
* [Port access requirements](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-port-access-requirements) lists ports that must be opened so that HCX virtual appliances can install successfully.
* Both the on-premises vSphere environment and the VCF/VCS HCX Cloud environment must permit Network Time Protocol (NTP) clock synchronization among vSphere on-premises devices and the VCF/VCS HCX devices. UDP port 123 must be accessible to HCX virtual appliances and networks.

## On-premises environment

Before you install HCX, verify that your environment can support the tasks that you want to accomplish. The on-premises environment must support the following tasks before HCX can be installed.
* Virtual Center with vSphere 5.5 Update 3 or 6.0 Update 2.
* vMotion and policy migration features require NSX version 6.2.2 or higher.
* A vSphere service account with the Administrator vCenter Server system role assigned to it.
* In the vCenter, enough disk space for the HCX appliances to be installed.
* Sufficient IP addresses for the on-premises VMs provisioned during the installation.
* Ports and firewalls opened as required as documented in Port Access Requirements.
* If the single sign-on (SSO) server is remote, the URL of the vCenter, external SSO Server, or Platform Services Controller (PSC) that runs the external lookup service must be identified. When the HCX Manager is registered with the vCenter, this URL must be supplied.
* If a vCenter does not have its own internal instance of the lookup service, it might be for one of the following reasons:
  * vCenter 6.0u2 is running an external Platform Services Controller.
  * The vCenter is in linked mode (where the secondary vCenter uses the SSO service from the primary vCenter or an external SSO service).

## Verifying Layer 2 installation environment

Layer 2 network stretching has the following requirements:
* A vSphere Enterprise Plus edition.
* The vSphere vCenter must meet the following requirements to support Layer 2 extension:
  * vSphere Enterprise Plus license
  * Must have a vSphere Distributed Switch (vDS). The distributed switch is available with vSphere Enterprise Plus Edition.
  * When installed, the on-premises Layer 2 concentrator service appliance must have access to a vNIC port and any VLANs to be stretched.
  * If the network is to be stretched over the public internet or a VPN (on an alternative path) the L2C virtual machine in VCF/VCS requires an IP address. The remote IP address is required to configure the Layer 2 concentrator.
  * If multiple Layer 2 concentrators are wanted, each must have an IP address on-premises and in the cloud.

### Related links

* [Installing and configuring HCX on the source](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-installing-and-configuring-hcx-on-the-source)
* [VMware EVC and CPU Compatibility FAQ](http://bit.ly/2vK6Sp5)
