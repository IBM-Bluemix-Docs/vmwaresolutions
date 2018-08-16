---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Offering comparison chart

Review the following chart to understand the differences in functions support for VMware Cloud Foundation instances, VMware vCenter Server instances, VMware vCenter Server with Hybridity Bundle instances, and VMware vSphere clusters.

Table 1. Supported functions for Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle, and vSphere clusters

| Function                          | Cloud Foundation    | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Powered by {{site.data.keyword.IBM}} advanced automation <sup>1</sup> | Yes | Yes | Yes | No. Self-built and configured |
| Storage options        | vSAN                | vSAN or Shared File-level Storage (NFS) | vSAN | vSAN or Shared File-level Storage (NFS) |
| Number of ESXi servers in initial cluster | 4 | 4 for vSAN and a minimum of 2 (3 recommended) for NFS | 4 | 1 to scale an existing cluster, 4 for new vSAN cluster, and a minimum of 3 for new cluster with NFS |
| Maximum number of ESXi servers <sup>2</sup> | 32 per cluster      | 59 per cluster     | 59 per cluster | 60 per cluster     |
| Cloud automated multi-site deployment | Supported for new instances that are deployed in V2.0 or later | Supported for new instances that are deployed in V2.0 or later | Supported | Supported. Automated configuration not included |
| Add ESXi servers              | Supported           | Supported | Supported | Supported. Automated configuration not included |
| Remove ESXi servers           | Supported           | Supported | Supported | Supported. Automated configuration not included |
| Multi-cluster support         | Five clusters | Ten clusters | Ten clusters | Supported. Automated configuration not included |
| Client-managed updating and patching of VMware stack | VMware updates | Not included | Not included | Not included |
| Backup and restore            | Manually using IBM Spectrum Protect Plus or Veeam | Manually using IBM Spectrum Protect Plus or Veeam | Manually using IBM Spectrum Protect Plus or Veeam | Backup and restore solution not included |
| Software-defined networking   | NSX Enterprise   | NSX Base, Advanced, or Enterprise | NSX Advanced or Enterprise | NSX Standard, Base, or Enterprise. Automated configuration not included |
| BYOL for vSphere and vSAN | Fully supported per cluster   | Fully supported per cluster     | Not supported | Supported |
| BYOL for vCenter and NSX | Fully supported per instance   | Fully supported per instance     | Not supported | Supported |
| NSX license upgrade options           | None   | Upgrade available from NSX Base to Advanced or Enterprise, and from NSX Advanced to Enterprise. Upgrade to the vCenter Server with Hybridity Bundle is available. | Upgrade available from NSX Advanced to Enterprise  | None |
| vSAN license editions         | vSAN Advanced or Enterprise  | vSAN Advanced or Enterprise  | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise  |
| Add-on services               | Supported, not including HCX on {{site.data.keyword.cloud_notm}}.  | Supported, not including HCX on {{site.data.keyword.cloud_notm}}. Upgrade to the vCenter Server with Hybridity Bundle is available. | Supported, including HCX on {{site.data.keyword.cloud_notm}}. | Not supported by the automation of this solution, but you can bring and install your own software. |

**Notes**:

<sup>1</sup> According to a validated design and with verification during deployment.

<sup>2</sup> You can increase the number of ESXi servers in a vSAN cluster to a maximum of 64. For more information, see _How many ESXi servers can I add to a cluster?_ in [FAQ about ESXi servers](faq_esxi.html).

### Related links

* [FAQ](faq.html)
* [Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server Hybridity overview](../vcenter/vc_hybrid_overview.html)
* [VMware vSphere overview](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation BOM](../sddc/sd_bom.html)
* [vCenter Server BOM](../vcenter/vc_bom.html)
* [VMware vSphere BOM](../vsphere/vs_bom.html)
