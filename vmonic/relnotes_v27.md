---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V2.7

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## SAP-certified 6140 server support

Starting with the V2.7 release, the following new {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU models are available for deployment for VMware vCenter Server on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 192 GB RAM
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.2 GHz / 384 GB RAM
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 768 GB RAM

For more information, see the *{{site.data.keyword.baremetal_short_sing}} settings* section in:
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vcenter-server-instances#bare-metal-server-settings)
* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-ordering-new-vsphere-clusters#bare-metal-server-settings)

## Updates for add-on services

### IBM Cloud Private Hosted

The {{site.data.keyword.cloud_notm}} Private Hosted service is now available to VMware vCenter Server with Hybridity Bundle instances, in addition to VMware vCenter Server instances that are deployed in (or upgraded to) V2.5 and later releases. You can now order a vCenter Server instance or a vCenter Server with Hybridity Bundle instance with the service included. You can also add the service to an existing vCenter Server instance or a vCenter Server with Hybridity Bundle instance after initial deployment.

For more information, see the following topics:
* [{{site.data.keyword.cloud_notm}} Private Hosted overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ibm-cloud-private-hosted-overview)
* [Ordering {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-ibm-cloud-private-hosted)

### Mission Critical VMware on IBM Cloud

The Mission Critical VMware on {{site.data.keyword.cloud_notm}} service is now available to instances that are deployed in, or upgraded to, V2.7 or later releases.

Mission Critical VMware on {{site.data.keyword.cloud_notm}} delivers a multi-zone cloud architecture to help enterprises prevent downtime for cloud applications and to automate failovers within a cloud region. With this cloud architecture, you can achieve a higher availability and failover success rate than most VMware clients can achieve with on-premises environments or competing cloud platforms.

For more information, see [Mission Critical VMware on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mission-critical-vmware-on-ibm-cloud-overview).

### F5 on IBM Cloud

Now when you order the F5 on {{site.data.keyword.cloud_notm}} service, you can select whether you want F5 to apply license over public network or over private network with a proxy server. For more information, see [Ordering F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-f5-on-ibm-cloud).

### FortiGate Virtual Appliance on IBM Cloud

In 3Q 2018, Fortinet changed their subscription bundles. For more information, see [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-fortigate-virtual-appliance-on-ibm-cloud).

For FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service that is deployed in V2.7 and later Cloud Foundation instances and vCenter Server instances, FortiOS 6.0.3 is provisioned.

When you order FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, you can select whether you want FortiGuard to apply license and security updates over public network or over private network with a proxy server. For more information, see [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-fortigate-virtual-appliance-on-ibm-cloud).

### Zerto on IBM Cloud service component updates

For the Zerto on {{site.data.keyword.cloud_notm}} service that is deployed in V2.7 and later Cloud Foundation instances and vCenter Server instances, Zerto Virtual Replication 6.0 update 3 is provisioned. For more information, see [Zerto on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto-on-ibm-cloud-overview).

### KMIP for VMware on IBM Cloud integration with IBM Cloud Activity Tracker

In addition to VMware instance events, events for KMIP for VMware on {{site.data.keyword.cloud_notm}}, such as key creation, key deletion, and key access, are now integrated with your {{site.data.keyword.cloud_notm}} Activity Tracker instance. For more information about KMIP for WMware on {{site.data.keyword.cloud_notm}}, see [KMIP for VMware on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services/kmip_considerations.html).

### KMIP for VMware on IBM Cloud - Deprecated

(Updated on December 14, 2018) The current version of KMIP for VMware on {{site.data.keyword.cloud_notm}} is being deprecated. For more information, [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support).
{:deprecated}

## New and updated documentation

### Reference architecture documentation

The following technical documents are now available in the *Reference* section of the user documentation:

* [NSX Edge Services Gateway solution architecture](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-about-nsx-edge-services-gateway)
* [VMware Update Manager guide](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vmware-update-manager-introduction)
* [vCenter Server networking guide](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcenter-server-networking-introduction)
* [vCenter Server and {{site.data.keyword.cloud_notm}} Private guide](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction)
* [vCenter Server and IBM Kubernetes service guide](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcenter-server-and-ibm-cloud-kubernetes-service-introduction)
* [VMware and Skate Advisor Concept Car guide](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vmware-and-skate-advisor-concept-car-introduction)
* [VMware - The modernization journey of Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-modernization-journey)

## User interface updates and enhancements

The user interface is updated and provides the following enhancements:

* The **Customized** tab where you specify CPU model and RAM for {{site.data.keyword.baremetal_short_sing}} settings when you order instances is now split into the **Skylake** and **Broadwell** tabs based on the server type to help you in server selection.
* The **Preconfigured** options for Bare Metal Server configuration are not available anymore.
* The **Type** column is now included in the **vCenter Server Instances** table on the **Deployed Instances** page to identify vCenter Server, vCenter Server with Hybridity Bundle, and vCenter Limited Test Drive instances.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
