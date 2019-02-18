---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Cloud Foundation Bill of Materials

Review the Bill of Materials (BOM) information for VMware Cloud Foundation instances.

## VLANs BOM for Cloud Foundation instances

The following table details the BOM information for the Cloud Foundation VLANs.

Table 1. BOM for the VLANs in Cloud Foundation instances

| VLAN      | Type      | Details      |
|:----------|:----------|:-------------|
| VLAN1     | Public, Primary | Assigned to physical ESXi servers for public network access. Not used after initial deployment. Available for internet access. |
| VLAN2     | Private A, Primary | Assigned by {{site.data.keyword.cloud}} to physical ESXi servers. Used by the management interface for VMware vSphere management traffic.<br><br>Assigned to VMs (virtual machines) that function as management components.<br><br>Assigned to VMware NSX VTEP (VXLAN Tunnel Endpoint) |
| VLAN3     | Private B, Portable | Assigned to VMware vSAN, if used.<br><br>Assigned to VMware NFS, if used.<br><br>Assigned to VMware vSphere vMotion. |

## Software BOM for Cloud Foundation instances

The following table details the BOM information for Cloud Foundation software components.

Table 2. BOM for the software components in Cloud Foundation instances

| Manufacturer | Component                                | Version      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 Update EP11 (build 6.5.0-10719125) |
| VMware       | vCenter Server Appliance                 | 6.5 U2c (build 6.5.0-9451637) |
| VMware       | Platform Services Controller             | 6.5 U2c (build 6.5.0-9451637) |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.4.1        |
| VMware       | SDDC Manager                             | 2.4          |
| Microsoft    | Windows Server Standard edition (64-bit) | 2012R2       |

## Advanced configuration settings for ESXi servers

Review the following table for an overview of the advanced configuration settings that are applied on the ESXi servers. The settings are different depending on whether the Cloud Foundation instance is deployed in (or upgraded to) V2.2 or later from a previous (V2.1 or earlier) release.

Table 3. ESXi servers advanced configuration settings for Cloud Foundation instances and clusters

| Configuration setting | If newly deployed in V2.2 or later  | If upgraded from V2.1 or earlier |   
|:------------- |:------------- |:------------- |
| TCP/IP Heap Size | **TcpipHeapSize** = 32 | Not set |
| TCP/IP Heap Maximum | **TcpipHeapMax** = 1536 | Not set |  
| Maximum of Volumes | **MaxVolumes** = 256 | Both **/NFS/MaxVolumes** and **/NFS41/MaxVolumes** = 256 |  
| Heartbeat Maximum Failures | **HeartbeatMaxFailures** = 10 | Not set |  
| Heartbeat Frequency | **HeartbeatFrequency** = 12 | Not set |  
| Heartbeat Timeout | **HeartbeatTimeout** = 5 | Not set |
| Maximum Queue Depth | **MaxQueueDepth** = 64 | Not set |
| Queue Full Sample Size | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Queue Full Threshold | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

### Notes

* The **MaxVolumes** setting is required for the IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service because the service might use more than the default number of NFS mounts on the ESXi server.
* A value of **Not set** for a configuration setting indicates that the new setting is not automatically applied because it requires rebooting the ESXi servers, which might be disruptive.

  It is recommended that you change the **Not set** configuration settings to the new values for consistency across all instances and to allow adequate support for storage expansion. IBM plans to test only with these new settings for all {{site.data.keyword.vmwaresolutions_short}} V2.2 and later releases.

  For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

### Related links

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Cloud Foundation overview](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-cloud-foundation-overview)
* [Planning Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-requirements-and-planning-for-cloud-foundation-instances)
