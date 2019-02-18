---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Networking services on IBM Cloud

Networking services on {{site.data.keyword.cloud}} consists of two pairs of VMware NSX Edge Services Gateways (ESGs) for communication between the {{site.data.keyword.cloud_notm}} and either the public internet or customer on-premises network through a Virtual Private Network (VPN). These ESGs are segregated to support internal {{site.data.keyword.cloud_notm}} management function and egress traffic, ingress of customer-related network traffic.

The following graphic is a simplified network diagram, which depicts the pair of management and the pair of workload ESGs. It also shows an NSX Distributed Logical Router (DLR) and workload VXLAN. These components are intended to be an initial landing point for customer workloads without requiring the specific knowledge to set them up within NSX. A DLR is typically employed to route traffic between VMware Cloud Foundation or VMware vCenter Server and East-West traffic, between separate layer 2 networks within the instance. This behavior is in contrast to an ESG, which functions to facilitate North-South network traffic that traverses in and out of the Cloud Foundation or vCenter Server instance.

Figure 1. Cloud networking services on Cloud Foundation

![Cloud networking services on Cloud Foundation](cloudnetworkingservicesdiagram.svg "Cloud networking services on Cloud Foundation")

While a single ESG might suffice for both management and customer workload traffic, the separation of management and customer traffic is a design decision made to prevent accidental misconfiguration of the management ESG.

Misconfiguration or disabling of the management ESG doesn't keep the Cloud Foundation or vCenter Server instance from functioning, but disables all portal management functions.
{:note}

## IBM management services NSX Edge

The IBM management ESG is a dedicated NSX Edge cluster for {{site.data.keyword.cloud_notm}} management network traffic only. It isn't intended for traffic traversal of any component that is not deployed and managed by Cloud Foundation or vCenter Server automation.

The management ESG provides a communication path between add-on services virtual machines (VMs) residing within Cloud Foundation or vCenter Server instances and the IBM Automation infrastructure in the {{site.data.keyword.cloud_notm}} as shown for Cloud Foundation in the following graphic.

Figure 2. Management edge communications on Cloud Foundation

![Management edge communications on Cloud Foundation](mgmtvmcommunication.svg "Management Edge Communication on Cloud Foundation")

As a result of the light communication between certain add-on services VMs and their corresponding licensing and metering systems, the NSX ESGs are sized in a large configuration in an active-passive high availability (HA) pair and deployed on the management resource pool of the Cloud Foundation converged cluster or the vCenter Server cluster. The following table provides a summary of the IBM management NSX ESG deployment.

Table 1. IBM management NSX ESG specifications

| IBM management NSX Edge | vCPU | Memory | Disk size | Storage location |
|:----------------------- |:---- |:------ |:--------- |:---------------- |
| IBM Management NSX ESG 1 | 2 | 1 GB | 1 GB | vSAN data store (Cloud Foundation); Shared Attached Storage for Management (vCenter Server) |
| IBM Management NSX ESG 2 | 2 | 1 GB | 1 GB | vSAN data store (Cloud Foundation); Shared Attached Storage for Management (vCenter Server) |

### Management services

Outbound access is required to the following services:

* Zerto Virtual Manager. If installed, Zerto on {{site.data.keyword.cloud_notm}} requires outbound access to the internet for licensing activation and usage reporting.
* Veeam backup and replication. If installed, Veeam on {{site.data.keyword.cloud_notm}} requires outbound access to the internet for downloading product and license updates.
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} requires outbound access to the internet for licensing activation and licensing monitoring.
* F5 on {{site.data.keyword.cloud_notm}} requires outbound access to the internet for licensing activation.

### Edge interfaces

The configuration of ESG interfaces defines what L2 networks the ESG has access to. For Cloud Foundation and vCenter Server lifecycle management, it's required that specific VMs placed on the management VLAN are allowed to traverse to the public VLAN. The following interfaces are defined on deployment:

Table 2. NSX ESG interface configuration

| Interface | Interface type | Connected to | Description |
|:--------- |:-------------- |:------------ |:----------- |
| Public Uplink | Uplink | **SDDC-DportGroup-External** | Public internet-facing interface |
| Private Uplink | Uplink | **SDDC-DportGroup-Mgmt** | Internal private network facing interface |
| Internal | Internal | Workload HA VXLAN | Internal interface used for ESG HA pair heartbeat; portgroup on **SDDC-Dswitch-Private** |

### Subnets

The following subnets are used for the purposes of the Management ESG:

Table 3. NSX ESX IP configuration

| Interface | Interface type | IP v4 subnet type | Range | Description |
|:--------- |:-------------- |:----------------- |:----- |:----------- |
| Public Uplink | Uplink | {{site.data.keyword.cloud_notm}} portable public | /30 – renders one assignable IP address | Public internet facing interface |
| Private Uplink | Uplink | {{site.data.keyword.cloud_notm}} portable private (existing management) | /26 – renders 61 assignable IP addresses | Internal private network facing interface |
| Internal | Internal | Link local | 169.254.0.0/16 | Internal interface used for ESG HA pair communication |

### Network Address Translation definitions

Network Address Translation (NAT) is employed on the Management ESG for the means of allowing network traffic to traverse between one IP address space and another. This is typically done to conserve internet routable IP addresses or to conceal internal IP addresses from public ones for security reasons. NAT is also used to allow for Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) port redirection. Management traffic is always initiated from inside the Cloud Foundation and vCenter Server instance, requiring that only a source NAT (SNAT) is defined on the Management ESG. An individual SNAT isn't created for each internal VM hosting a service that needs to egress from the instance.

Table 4. NSX ESG NAT configuration

| Applied on interface | Source IP range | Translated source IP |
|:-------------------- |:--------------- |:-------------------- |
| Public Uplink | Individual IP addresses on the Management Portable /26 | {{site.data.keyword.cloud_notm}} portable public |

### Routing

Since services within VMs required to traverse through the Management ESG might also need to get to {{site.data.keyword.cloud_notm}} services within the customer {{site.data.keyword.cloud_notm}} private network, the following configuration is required to achieve this communication.

While it's difficult to predict which destination IP range is needed as a destination for internet facing connections, any service that is deployed by and managed by {{site.data.keyword.cloud_notm}} points to the Management ESG as its default gateway. A static route is required to force traffic across the {{site.data.keyword.cloud_notm}} BCR for the services required external network connections.

The following configurations are recommended for any service that is using the management ESG to traverse out of a Cloud Foundation or vCenter Server instance:
* The default gateway is a management ESG.
* A static route is required for internal {{site.data.keyword.cloud_notm}} destinations.

If there's a need for the service or VM to access the customer ESG, then static routes must be maintained within the individual service or VM and pointed to the customer ESG.

No automatic routing protocols are configured for the Management ESG currently.

### VXLAN definitions

The Management HA pair requires a network for the connection of the internal interfaces. Use an existing vSwitch, port group, or VXLAN. For this design, a dedicated VXLAN is created for the HA heartbeat communication of the Management ESG HA pair.

Table 5. NSX ESG VXLAN definitions

| NSX ESG VXLAN definitions | Transport zone | Type |
|:------------------------- |:-------------- |:---- |
| Mgmt HA | transport-1 | global |

### Firewall rules

By default, the Management ESG is configured to deny all traffic.

**Deny:** To drop all traffic with no response when that traffic isn't allowed to traverse the firewall by any previous (higher in the order) rule or rule set. Automatic rule generation is selected to allow for control traffic to the ESG pair.

The following firewall rules are set, in addition to the automatically generated rules:

Table 6. NSX ESG firewall configuration

| Service | Source | Destination | Protocol | Action |
|:------- |:------ |:----------- |:-------- |:------ |
| Zerto on {{site.data.keyword.cloud_notm}} | Zerto Management VM | Any | Port 443 | Allow |
| Veeam on {{site.data.keyword.cloud_notm}} | Veeam Backup and Replication VM | Any | Port 443 | Allow |
| FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} | Service VMs | Any | Port 443 | Allow |
| F5 on {{site.data.keyword.cloud_notm}} | Service VMs | Any | Port 443 | Allow |
| Any | Any | Any | Any | Deny |

## IBM workload NSX edge

The IBM workload ESG is part of a simple topology that is intended for workload network communication. The following section describes the design intent of where to attach workloads to a network within a Cloud Foundation or vCenter Server instance. This is a starting point for attaching on-premises networks and IP spaces to a particular Cloud Foundation or vCenter Center instance and is the basis for a true Hybrid Cloud architecture.

A customer network that is attached to both the public and private {{site.data.keyword.cloud_notm}} networks allows for workload access to and from internet facing traffic, but also allows for a site-to-site VPN to be created from either public or private {{site.data.keyword.cloud_notm}} networks. This allows for drastically decreased time to value with regards to connecting to on-premises networks since it can take months to bring up a dedicated wide area network (WAN) due to customer security requirements. However, after a dedicated link is in place, the VPN can be flipped over to traverse that link without affecting the overlay network inside the VPN tunnel or within the Cloud Foundation or vCenter Server instance. After this is done, the public interface for the workload ESG can be removed if needed from a security perspective.

The topology in the following figure consists of the following NSX components:
* NSX Edge appliance (ESG)
* Distributed Logical Router (DLR)
* VXLAN (L2 over L3)

Figure 3. Example network flow diagram

![Network flow diagram](customer_network_flow_diagram.svg "Network flow diagram")

### Edge interfaces for the IBM workload NSX edge

As with the management ESG, the configuration of ESG interfaces defines what L2 networks the ESG has access to. Part of the design intent of the workload topology is to achieve a software-defined networking (SDN) overlay to isolate workloads from the underlying {{site.data.keyword.cloud_notm}} address space. This design is the basis for achieving BYOIP design. Therefore, the following interfaces are defined on deployment:

Table 7. Workload Edge interface configuration

| Interface | Interface type | Connected to | Description |
|:--------- |:-------------- |:------------ |:----------- |
| Public Uplink | Uplink | SDDC-DportGroup-External | Public internet-facing interface |
| Private Uplink | Uplink | SDDC-DportGroup-Mgmt | Internal private network-facing interface |
| Transit Uplink | Uplink | Workload-Trasit | Transit VXLAN between the Workload ESG and the Workload DLR |
| Internal | Internal | Workload HA VXLAN | Internal interface used for ESG HA pair heartbeat |

In this design, a DLR is employed to allow for potential East-West routing between local workload connected L2 networks. As this topology is intended to be a simple example, only one L2 network that is intended for workloads is described. Adding more security zones can be achieved by adding more VXLANs attached to new interfaces on the DLR. The following table shows the DLR interfaces to configure:

Table 8. DLR interfaces

| Interface | Interface type | Connected to | Description |
|:--------- |:-------------- |:------------ |:----------- |
| Transit Uplink | Uplink | Workload-Trasit | Transit VXLAN between the Workload ESG and the Workload DLR |
| Workload Uplink | Uplink | Workload | VXLAN for Workload connections |
| Internal | Internal | Workload HA VXLAN | Internal interface used for ESG HA pair heartbeat |

### Subnets for the IBM workload NSX edge

The following subnets are used for the purposes of the Workload ESG:

Table 9. DLR and Workload ESG IP configuration

| Interface | Interface type | IP v4 subnet type | Range | Description |
|:--------- |:-------------- |:----------------- |:----- |:----------- |
| Public Uplink (ESG) | Uplink | {{site.data.keyword.cloud_notm}} portable public | /30 – renders one assignable IP address | Public internet-facing interface (customer can order more IP addresses separately) |
| Private Uplink (ESG) | Uplink | {{site.data.keyword.cloud_notm}} portable private (existing management) | /26 – renders 61 assignable IP addresses | Internal private network-facing interface |
| Internal (ESG and DLR) | Internal | Link local | 169.254.0.0/16 | Internal interface used for ESG HA pair communication |
| Transit Uplink (ESG and DLR) | Uplink | Assigned by customer | TBD | Transit network connection for ESG to DLR |
| Workload (DLR) | Uplink | Assigned by customer | TBD | Workload subnet |

### NAT definitions for the IBM workload NSX edge

NAT is employed on the Workload ESG for the means of allowing network traffic to traverse between one IP address space and another. For the workload ESG, NAT is required not only to allow for communication to internet destinations, but also to communicate to any {{site.data.keyword.cloud_notm}} sourced IP ranges. For this design, workload traffic is allowed to exit to the internet, but not to the management or any {{site.data.keyword.cloud_notm}} networks. As such, only a SNAT need be defined on the Workload ESG. The entire workload portable subnet is configured to traverse through the SNAT.

While it is possible to use NAT to allow for workload communication across multiple instances of Cloud Foundation or vCenter Server, doing this becomes impractical when many workloads need to be connected across instances. For examples of using advanced NSX capabilities to create an L2 overly transit network across Cloud Foundation or vCeter Server instances, see [Multi-site architecture](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-multi-site-architecture).

Table 10. Workload ESG NAT rules

| Applied on interface | Source IP range | Translated source IP | NAT Enabled or Disabled |
|:-------------------- |:--------------- |:-------------------- |:----------------------- |
| Public Uplink (Workload ESG) | Customer defined | {{site.data.keyword.cloud_notm}} portable public IP | Customer defined (default disabled) |

### Routing for the IBM workload NSX edge

Within this design, the only requirement for workloads that traverse the DLR to the workload ESG is to access the internet. The Workload ESG needs to understand the path to the workload VXLAN and any future workload VXLAN/subnets created behind the DLR. While this can be achieved through static routes on the ESG, the intent of the workload topology is that of a demonstrated best practice design. Therefore, Open Shortest Path First (OSPF) is configured between the Workload ESG and the downstream DLR.

For more information about the configuration, see [Configure OSPF Protocol](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-6E985577-3629-42FE-AC22-C4B56EFA8C9B.html).

Table 11. Dynamic routing

| Area | OSPF type | OSPF interface IP | OSPF authentication |
|:---- |:--------- |:----------------- |:------------------- |
| 51 | stub | Assign an IP for each the DLR and ESG on the transit RFC1918 network | None |

### Firewall rules for the IBM workload NSX edge

By default, the Workload ESG is configured to deny all traffic.

**Deny:** To drop all traffic with no response when that traffic isn't allowed to traverse the firewall by any previous (higher in the order) rule or rule set. Automatic rule generation is selected to allow for control traffic to the ESG pair.

The following firewall rules are set, in addition to the automatically generated rules.

Table 12. Workload ESG firewall rules

| Service | Source | Destination | Protocol | Action |
|:------- |:------ |:----------- |:-------- |:------ |
| Workloads | Workload subnet | Any | Any | Allow |
| Any | Any | Any | Any | Deny |

### VXLAN definitions for the IBM workload NSX edge

The Workload topology ESG and DLR HA pairs require L2 segments (VXLAN) for the connection of the internal interfaces, data transit between the two, and for workloads.

Table 13. Workload ESG internal interfaces

| VXLAN name | Cloud Foundation or vCenter Server transport zone | Type |
|:---------- |:------------------------------------------------- |:---- |
| Workload HA | transit-1 | Global |
| Workload transit | transit-1 | Global |
| Workload | transit-1 | Global |

### ESG DLR settings for the IBM workload NSX edge

By default, logging is enabled on all new NSX Edge appliances. The default logging level is NOTICE.

### Related links

* [NSX Edge Services Gateway design](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx-edge-services-gateway-design)
* [Multi-site architecture](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-multi-site-architecture)
