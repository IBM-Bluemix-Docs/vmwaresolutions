---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted overview

The {{site.data.keyword.cloud}} Private Hosted service automatically deploys {{site.data.keyword.cloud_notm}} Private Hosted on your VMware vCenter Server instances. This service brings the power of microservices and containers to your VMware environment on {{site.data.keyword.cloud_notm}}. With this service, you can extend the same familiar VMware and {{site.data.keyword.cloud_notm}} Private operational model and tools from on-premises into the {{site.data.keyword.cloud_notm}}.

This service is available to the following instances:
* vCenter Server instances that are deployed in or upgraded to V2.5 and later
* vCenter Server with Hybridity Bundle instances that are deployed in or upgraded to V2.7 and later
{:note}

## Technical specifications for IBM Cloud Private Hosted

The following table lists the minimum requirements to order the IBM Cloud Private Hosted service for the **Production-Ready** environment and the **Development/Test** environment.

Table 1. Minimum requirements for Production-Ready and Development/Test environments

|Environment | Cores | Memory (GB) | Hosts | Storage (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| Production-Ready | 52 | 640 | 3 | 8,000 |
| Development/Test | 30 | 200 | 3 | 4,000 |

### Resource requirements for IBM Cloud Private Hosted

The following tables list the resource requirements of the {{site.data.keyword.cloud_notm}} Private Hosted service in Production-Ready and Development/Test environments.

Table 2. {{site.data.keyword.cloud_notm}} Private Hosted resource requirements in Production-Ready environment

| Node type  | CPU cores   |  Memory (GB) | Disk 1 (GB) | Disk 2 (GB) | Number of VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Boot       | 12 | 24 | 100 | 1 | 1 |   
| Management | 8 | 64 | 500 | 3 | 3 |
| Master     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Worker     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability advisor | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap {{site.data.keyword.icpfull_notm}}/CAM | 24 | 44 | 250 | 1 | 1 |
| NFS server | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0.5 | 0.5 | 2 |
| Documented constraints | 52 | 640 |  | 8,000 |   |

Table 3. {{site.data.keyword.cloud_notm}} Private Hosted resource requirements in Development/Test environment

| Node type  | CPU cores   |  Memory (GB) | Disk 1 (GB) | Disk 2 (GB) | Number of VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Boot       | 12 | 24 | 100 | 1 | 1 |   
| Management | 8 | 16 | 150 | 1 | 1 |
| Master     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Worker     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability advisor | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap {{site.data.keyword.icpfull_notm}}/CAM | 24 | 44 | 250 | 1 | 1 |
| NFS server | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0.5 | 0.5 | 2 |
| Documented constraints | 30 | 200 |  | 4,000 |  |

### Formulas for calculating IBM Cloud Private Hosted space requirements

The following formulas are used to calculate the space requirements for IBM Cloud Private and the management overheads.

#### Formula 1

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

Table 4. Description of variables in Formula 1

| Variables	| Description |	Unit |	vSAN example | NFS example |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	The number of actual cores available for workloads and services in the environment |	Cores |	38	| 43 |
| HostCount	| The number of hosts in the default cluster	| Hosts | 4	| 4 |
| HostCoreCount	| The number of raw cores available in each host in the default cluster |	Cores |	16 | 16 |
| HostOverheadCores	| The number of cores that are reserved by the ESXi server as overhead, which equals 0.1 cores	| Cores	| 0.1 |	0.1 |
| MgmtOverheadCores | The number of cores reserved by the vCenter Server management components (vCenter Server, PSC, AD/DNS, Edges), which equals five cores	| Cores	| 5	| 5 |
| vSphereHAHostTolerance |	The number of hosts to tolerate in the vSphere HA configuration, which equals one host |	Hosts	 | 1 | 1 |
| HostVsanOverheadCorePercentage | The percentage of a host's cores used by vSAN, which equals 10% or equals 0% if the host is non-vSAN | % | 10% |	0% |

#### Formula 2

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

Table 5. Description of variables in Formula 2

| Variables	| Description |	Unit |	vSAN example | NFS example |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| The number of GB of memory available for workloads and services in the environment | GB | 	693	| 860 |
| HostCount	| The number of hosts in the default cluster | Hosts  | 6	| 6 |
| HostMemory |	The number of raw GBs of memory available in each host in the default cluster |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | The number of GB of a capacity of each vSAN capacity SSD disk on this host, which equals 960, 1,946, or 3,891, or equals 0 GB if the host is non-vSAN | GB |	960 | 0 |
| HostOverheadMemory |	The number of GB of memory that is reserved by the ESXi server as overhead, which equals 4.6 GB |	GB	| 4.6 |	4.6 |
| MgmtOverheadMemory |	The number of GB of memory reserved by the vCenter Server management components (vCenter Server, PSC, AD/DNS, Edges), which equals 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance | The number of hosts to tolerate in the vSphere HA configuration, which equals one host | Hosts	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | The number of GB of memory reserved by vSAN management (represented as percentage of one of the capacity vSAN disks), which equals 2.75% |	% | 2.75%	| 2.75% |
| HostVsanOverheadMemory | The number of GB of memory reserved by vSAN management regardless of disk size, which equals 7 GB or equals 0 GB if the host is non-vSAN	| GB |  7	| 0 |

## Considerations when you install IBM Cloud Private Hosted

* Gather the required license before you install the {{site.data.keyword.cloud_notm}} Private Hosted service. You are recommended to ensure that your license can support not only the initial {{site.data.keyword.cloud_notm}} Private Hosted deployment, but also the future {{site.data.keyword.cloud_notm}} Private Hosted size expansion in your infrastructure.
* For the {{site.data.keyword.cloud_notm}} Private Hosted deployments in Production-Ready environment, 64 GB RAM per host is not supported. Therefore, you must select an option that is higher than 64 GB for **RAM**.
* Before the {{site.data.keyword.cloud_notm}} Private Hosted service is installed in your environment, a check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit. If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email. To install the service, you must increase the capacity in your default cluster by either adding more hosts or by freeing up RAM, CPU, or disk space, and then add the service again in the console. After that, you can remove the existing service in the **Capacity Validation Failed** state by clicking the **Delete** icon next to it.

## Considerations when you remove IBM Cloud Private Hosted

* {{site.data.keyword.cloud_notm}} deletes only the virtual machines (VMs) that were deployed during the initial installation of the {{site.data.keyword.cloud_notm}} Private Hosted service. Any node that is deployed postinstallation will not be cleaned up.
* {{site.data.keyword.cloud_notm}} will delete the VXLAN, DLR, and the edge gateway that was created during the initial deployment of the {{site.data.keyword.cloud_notm}} Private Hosted service. The VMs that you deployed on VXLAN will lose connectivity after the removal of the {{site.data.keyword.cloud_notm}} Private Hosted service is started.

### Related links

* [Ordering IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-ibm-cloud-private-hosted)
* [vCenter Server and IBM Cloud Private guide](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction)
* [Open a Ticket for IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=en_US)
