---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# About NSX Edge Services Gateway

The VMware NSX Edge Services Gateway (ESG) solution is an extension of the VMware Cloud Foundation on {{site.data.keyword.cloud}} and the vCenter Server on {{site.data.keyword.cloud_notm}} offerings that are currently available on the {{site.data.keyword.cloud_notm}}. The solution architecture for Cloud Foundation and vCenter Server details the components of the solution and the high-level configuration of each component in the design.

For more information about the Cloud Foundation and vCenter Server design, see [Solution overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-overview-of-ibm-cloud-for-vmware-solutions).

## Overview of NSX Edge Services Gateway

The NSX Edge Services Gateway connects isolated, stub networks to shared (uplink) networks by providing common gateway services such as Dynamic Host Configuration Protocol (DHCP), Virtual Private Network (VPN), Network Address Translation (NAT), dynamic routing, and load balancing. Common deployments of NSX Edge include demilitarized zone (DMZ), VPN Extranets, and multi-tenant Cloud environments where the NSX Edge creates virtual boundaries for each tenant, workload, or management component. The following features are available within the NSX Edge Service Gateway.

Table 1. Features available with the NSX Edge Service Gateway

| Feature | Description |
|:------- |:----------- |
| NSX Edge Service Routing | Provides the necessary forwarding information between layer 2 broadcast domains, allowing you to decrease layer 2 broadcast domains and improve network efficiency and scale. NSX extends this intelligence to where the workloads reside for doing East-West routing. This allows more direct virtual machine to virtual machine communication without the costly or timely need to extend hops. At the same time, NSX also provides North-South connectivity, enabling tenants to access public networks. |
| Firewall | The supported rules of the firewall include IP 5-tuple configuration with IP and port ranges for stateful inspection for all protocols. |
| NAT | Provides separate controls for Source and Destination IP addresses and port translation. |
| DHCP | Provides configuration of IP pools, gateways, DNS servers, and search domains. |
| Site-to-Site VPN | Uses standardized IPSec protocol settings to inter-operate with all major VPN vendors. |
| L2VPN | Stretches L2 networks across L3 topologies. |
| SSL VPN-Plus |  SSL VPN-Plus enables remote users to connect securely to private networks behind an NSX Edge gateway. |
| Load Balancing | Provides simple and dynamically configurable virtual IP addresses and server groups. |
| High Availability | Ensures an active NSX Edge on the network in case the primary NSX Edge virtual machine is unavailable. |

### Related links

* [Solution overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-overview-of-ibm-cloud-for-vmware-solutions)
