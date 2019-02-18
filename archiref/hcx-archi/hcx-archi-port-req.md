---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# VMware HCX on IBM Cloud port access requirements

HCX must traverse the public internet and private lines, and connect to data center components, such as networks, switches, and port groups.

The following table lists ports that must be opened so that Hybrid Cloud Services virtual appliances can install successfully. Both the vSphere environment and the IBM Cloud environment must permit Network Time Protocol (NTP) clock synchronization among vSphere on-premises devices and the IBM Cloud devices. UDP port 123 must be accessible to Hybrid Cloud Services virtual appliances and networks. Installed NTP Servers can be specified when the Hybrid Cloud Services Appliance is installed.

Table 1. Port access requirements

| Source | Target       | Port | Protocol | Purpose         | Services |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | Customer DNS | 53   | TCP/UDP  | Name resolution | DNS      |
| HCX    | NSX LB in IBM Cloud | 443 | TCP | Registration service | HTTPS |
| HCX    | vCenter in IBM Cloud | 443 | TCP | HCX REST service | HTTPS |
| HCX    | PSC in IBM Cloud | 443 | TCP | HCX REST service | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | Registration service | HTTPS |
| Web Browser | HCX | 9443 | TCP | HCX Virtual Appliance Management Interface for HCX system configuration | HTTPS |
| Admin network | HCX | 22 | SSH | Administrator SSH access to Hybrid Cloud Services | SSH |
| HCX | ESXi Hosts | 902 | TCP | Send management and provisioning instructions from HCX to ESXi Hosts in IBM Cloud. | Internal |
| HCX | vCenter SSO Server | 7444 | TCP | vSphere Lookup Service |  |
| HCX | NTP Servers | 123 | UDP | Time synchronization | |
| HCX | Syslog |   | User configured | Connection between HCX (the client) and the Syslog server. Values for the Syslog port and protocol are specified in the vSphere Web Client. For example, port 514 for UDP protocol. | |
| HCX | Cloud Gateway | 8123 | TCP | Send host-based replication service instructions to the Hybrid Cloud Gateway. | HTTP |
| HCX | Cloud Gateway | 9443 | TCP | Send management instructions to the local Hybrid Cloud Gateway by using the REST API. | HTTP</br>HTTPS |
| Cloud Gateway | L2C | 443 | TCP | Send management instructions from Cloud Gateway to L2C when L2C uses the same path as the Hybrid Cloud Gateway. | HTTP</br>HTTPS |
| Cloud Gateway | L2C | 8443 | TCP | Bidirectional management instructions from Cloud Gateway to L2C, when L2C uses an alternative data path. | HTTP</br>HTTPS |
| L2C | L2C (remote) | 443 | TCP | Bidirectional management instructions from Cloud Gateway to L2C, when L2C uses an alternative data path. | HTTP</br>HTTPS |
| Cloud Gateway | ESXi hosts | 80, 902  | TCP | Management and OVF deployment | Internal |
| ESXi Hosts | Cloud Gateway | 31031, 44046 | TCP | Internal host-based replication traffic | Internal |
| Cloud Gateway | ESXi hosts | 8000  | TCP | vMotion (zero downtime migration) |  |
| Cloud Gateway (local) | Cloud Gateway</br>(remote) | 4500  | UDP | Internet key exchange (IKEv2) to encapsulate workloads for the bidirectional tunnel | IPSEC |
| Cloud Gateway (local) | Cloud Gateway</br>(remote) | 500  | UDP | Internet key exchange (ISAKMP) for the bidirectional tunnel | IPSEC |

### Related links

* [Installing and configuring HCX on the source](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-installing-and-configuring-hcx-on-the-source)
