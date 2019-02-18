---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-05"

---

# Glossary of HCX components and terms

HCX consists of a cloud side (target) and one or more clients
(source). An instance of HCX must be deployed per vCenter, even if the
vCenters where HCX is deployed are linked in the same SSO domain on the
client or cloud side. Configurations that are supported by HCX are, one-to-one,
one-to-many, many-to-one, and many-to-many.

## 	Cloud side and client side

HCX has the concept of cloud side (target) and client side (source).
- Cloud side - vCenter Server on 	{{site.data.keyword.cloud}} with Hybridity Bundle. The cloud
side of HCX is the slave instance of an HCX client to cloud
relationship. It is controlled by the client side.
- Client side - Any vSphere instances meeting the prerequisites
for installation and operation. The client side of HCX is the master that
controls the cloud side slave instance through its vCenter web client user interface (UI)
snap-in.

## HCX manager
- The cloud side HCX manager is the first part of an HCX install
deployed on the cloud side by the {{site.data.keyword.vmwaresolutions_short}} automation.
Initially it is a single deployed OVA image file specific to the cloud
side along with an NSX edge load balancer-firewall that is
configured specifically for the HCX role. The HCX manager is configured
to listen for incoming client-side registration, management, and control
traffic.
- The client-side HCX manager is a client-side specific OVA image file that provides the UI functionality for managing and operating HCX. The
client-side HCX manager is responsible for registration with the cloud
side HCX manager and creating a management plane between the client and
cloud side. Furthermore, it is responsible for deploying fleet
components on the client side and instructing the cloud side to do the
same.

## Fleet components

HCX Fleet components are responsible for creating the data and control
planes between client and cloud side. Deployed as virtual machines (VMs) in mirrored pairs,
the fleet consists of the following components:

- Cloud Gateway (CGW) - The Cloud Gateway is an optional component
responsible for creating encrypted tunnels that support vMotion and
replication (bulk migration) traffic. Only one pair exists per linked
HCX site.
- Layer 2 Concentrator (L2C) - The Layer 2 Concentrator is an optional
component responsible for creating encrypted tunnels for the data and
control plane corresponding to stretched layer 2 traffic. Each L2C pair
can handle up to 4096 stretched networks. More L2C pairs are
deployed as needed. The bandwidth capability is limited to ~4 Gbps, so if
the external bandwidth capacity is greater than 4 Gbps, then using
more L2C pairs allows greater utilization of the underlying
network.
- WAN Optimizer - HCX includes an optionally deployed Silver Peak™ WAN
optimization appliance. It is deployed as a VM appliance. When deployed,
the CGW tunnel traffic is redirected to traverse the WAN Optimizer pair.
Since the WAN optimizer significantly decreases traffic across the WAN
(typically 3:1 to 6:1 observed) while increasing connection reliability,
it is recommended to always deploy the WAN optimizer with the CGW. The
added benefit of deploying the WAN optimizer is extended to limiting the
WAN bandwidth consumed by VM migration traffic. The WAN optimizer
management interface is not configured by default.
- Proxy ESX host - Whenever the CGW is configured to connect to the cloud
side HCX site, a proxy ESXi host appears in the vCenter outside of any
cluster. This ESXi host has the same management and vMotion IP address
as the corresponding CGW appliance. This allows for the vSphere
environment at both the client and cloud side to function as if it is
performing a local vMotion. Benefits to this method:
    - The management IP ranges on either side might be overlapping
with no loss in functionality.
    - The cloud side has no vSphere visibility into the client side making it more secure.


## HCX user portals

- Client web UI – The HCX client web portal is the main UI for HCX. Once the client-side HCX manager is installed, it
shows up as a snap-in to the vCenter web UI. It controls remote cloud
HCX registration (site pairing), fleet component deployment, network stretching, and VM migration into and out of the Cloud.

- Cloud side UI – The cloud side HCX UI is accessible through the public
registration URL given for HCX client registration. By default, it
uses the cloud side vSphere SSO login (` administrator@vsphere.local`). It is typically used for upgrading the
installation and modifying some network configuration. It is also used
to build virtual networks within HCX.

- Client / Cloud HCX manager appliance management UI – Access the
appliance management UI for either the cloud or the client side through the
VM private IP address as viewed in vCenter.
`https://<hcxmanager_IP>:9443`. The ID (typically “admin”) and password
are provided through the {{site.data.keyword.vmwaresolutions_short}} portal. The management UI is
used start and stop HCX Manager services, configure log monitoring,
basic networking configuration, manual upgrades, support log gathering
when the web UI is not functioning, registration with vSphere components
(vCenter, PSC, NSX Manager) and certificate management.

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
