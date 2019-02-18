---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Offering comparison chart

Review the following chart to understand the differences in functions support for VMware Cloud Foundation instances, VMware vCenter Server instances, VMware vCenter Server with Hybridity Bundle instances, and VMware vSphere clusters.

Table 1. Supported functions for Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle, and vSphere clusters

| Function | Cloud Foundation | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:---|:---|:---|:---|:--- |
| Powered by {{site.data.keyword.IBM}} advanced automation <sup>1</sup> | Yes | Yes | Yes | No. Self-built and configured |
| Storage options | vSAN | vSAN or Shared File-level Storage (NFS) | vSAN | vSAN or Shared File-level Storage (NFS) |
| Number of ESXi servers in initial cluster | 4 | 4 for vSAN and a minimum of 2 (3 recommended) for NFS | 4 | 1 to scale an existing cluster, 4 for new vSAN cluster, and a minimum of 3 for new cluster with NFS |
| Maximum number of ESXi servers <sup>2</sup> | 32 per cluster | 59 per cluster | 59 per cluster | 60 per cluster |
| Cloud automated multi-site deployment | Supported for new instances that are deployed in V2.0 or later | Supported for new instances that are deployed in V2.0 or later | Supported | Supported. Automated configuration not included |
| Add ESXi servers | Supported | Supported | Supported | Supported. Automated configuration not included |
| Remove ESXi servers | Supported | Supported | Supported | Supported. Automated configuration not included |
| Multi-cluster support | Five clusters | Maximum number depends on VMware sizing guidelines | Maximum number depends on VMware sizing guidelines | Supported. Automated configuration not included |
| Client-managed updating and patching of VMware stack | Automation-assisted updates:<br/>SDDC Manager | Client-managed updates:<br/>Native VMware tools (VMware Update Manager) | Client-managed updates:<br/>Native VMware tools (VMware Update Manager) | Client-managed updates:<br/>Native VMware tools (VMware Update Manager) |
| Backup and restore | Manually using IBM Spectrum Protect Plus or Veeam | Manually using IBM Spectrum Protect Plus or Veeam | Manually using IBM Spectrum Protect Plus or Veeam | Backup and restore solution not included |
| Software-defined networking | NSX Enterprise | NSX Base, Advanced, or Enterprise | NSX Advanced or Enterprise | NSX Standard, Base, or Enterprise. Automated configuration not included |
| BYOL for vSphere and vSAN | Fully supported per cluster | Fully supported per cluster | Not supported | Supported |
| BYOL for vCenter and NSX | Fully supported per instance | Fully supported per instance | Not supported | Supported |
| NSX license upgrade options | None | Upgrade available from NSX Base to Advanced or Enterprise, and from NSX Advanced to Enterprise. Upgrade to the vCenter Server with Hybridity Bundle is available. | Upgrade available from NSX Advanced to Enterprise  | None |
| vSAN license editions | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise  |
| Add-on services | Supported, not including HCX on {{site.data.keyword.cloud_notm}}. | Supported, not including HCX on {{site.data.keyword.cloud_notm}}. Upgrade to the vCenter Server with Hybridity Bundle is available. | Supported, including HCX on {{site.data.keyword.cloud_notm}}. | Not supported by the automation of this solution, but you can bring and install your own software. |

## Notes

<sup>1</sup> According to a validated design and with verification during deployment.

<sup>2</sup> You can increase the number of ESXi servers in a vSAN cluster to a maximum of 64. For more information, see _How many ESXi servers can I add to a cluster?_ in [FAQ about ESXi servers](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq-about-esxi-servers).

### Related links

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-general-faq-about-ibm-cloud-for-vmware-solutions)
* [Cloud Foundation overview](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cloud-foundation-overview)
* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-overview)
* [vCenter Server Hybridity overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-with-hybridity-bundle-overview)
* [VMware vSphere overview](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-on-ibm-cloud-overview)
* [Cloud Foundation BOM](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cloud-foundation-bill-of-materials)
* [vCenter Server BOM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter-server-bill-of-materials)
* [VMware vSphere BOM](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vmware-vsphere-bill-of-materials)
