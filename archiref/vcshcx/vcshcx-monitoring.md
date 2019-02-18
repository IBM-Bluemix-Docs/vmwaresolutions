---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Monitoring parameters and components

## Using the WAN Optimizer for monitoring

The Silver Peak WAN optimization appliance that is deployed as part of
HCX does not get its management interface configured. The web user interface (UI) is a
valuable tool to use when you base line traffic throughput and throttling
network migration bandwidth use.

Only the HCX CGW Gateway WAN tunnel traffic flows through the WAN
Optimizer appliance. Therefore, it cannot monitor stretched L2 traffic.
{:note}

### Configuring the UI

Outside of configuring an IP address for the web UI, do not make configuration
changes to the WAN Optimizer appliance unless directed by
{{site.data.keyword.IBM}} or VMware support staff.   

To configure the WAN Opt web UI:
1.	Find the WAN Opt virtual machine (VM) appliance within the vCenter client.
2.	Open up a console to the VM that uses the vCenter client.
3.	Within the console, click **F4** to configure the management interface.
4.	Select to configure a static IP.
5.	Use an IP address on the management {{site.data.keyword.cloud}} assigned portable IP
range and default gateway.
6.	Click **Apply** on the next screen to save.
7.  Click edit settings for the WAN Opt VM within the vCenter console.
8.	Select **Connected at Power On** and **Connected for Network Adapter 1**.
9.	Click **OK** to save.
10.	Find the CGW-<xxx>-WANOPT in vCenter.
11.	Edit settings on the VM.
12.	Click the check box to connect Network adapter 1.
13.	Click **OK**.
14.	Go to `https://<configured_WAN_OPT_IP>`.
15.	Log in with the `admin` default user and the `admin` password.

You can now use the WAN Opt web UI to monitor throughput
rates, compression ratios, and set bandwidth restrictions.

### Migration bandwidth throttling

Before you migrate VMs, perform an assessment of the network link that is used. Work with the networking
engineers for the network that contains the source instance of vSphere or
review weekly and monthly traffic use. Limit available bandwidth for migrations if that traffic
traverses over a link that is critical to your business,
especially if that link is less than 1 Gbps. Use the
side with the most constrained bandwidth, which is typically the
client side.

Do so when you deploy the fleet components in the HCX Client
UI, but post deployment requires you go into the WAN opt UI.

Changes are lost if you redeploy the HCX CGW from the HCX web UI.
This sets bandwidth limits for the migration traffic only. Stretched L2
traffic is not affected by this setting.
{:note}

1.	Log in to the wan opt web UI.
2.	From the **Configuration** tab, select **Shaper** from the drop-down menu.
3.	In the max bandwidth box, set the maximum bandwidth available to the
wan opt appliance in kbps. Do not exceed the max bandwidth of the WAN
link.     
  - To set for Mbps (base 10) = Mbps x 1000
  - To set for Gbps = 1000^2 = Gbps x 1000^2
  - Default = 10 Gbps (10000000)
4.	Click **Apply**.

For stretched L2 bandwidth throttling, QoS can be employed for UDP 500
and 4500 for the tunnel traffic between the L2C appliances.

## Monitoring HCX components

Monitor HCX components such as HCX Manager, Cloud Gateway, WAN opt, and the Layer 2
Concentrator operations in the following ways:

- Configure HCX Manager to send logs to a syslog server. Use
the HCX manager appliance management utility to run the `https://<hcxhostname or
IP>:9443` command.
- Set up a ping to a VM that is migrated before network swing
for each stretched L2 network.
- Monitor the HCX component VM health with VMware vRealize Operations
Manager or other VMware VM monitoring tools.

## Bandwidth use

Use the following methods to monitor bandwidth use and latency.

- vMotion Traffic is best accomplished by using the WAN Opt web UI. The WAN
Opt dramatically reduces the traffic that is going over the WAN and reduces
packet loss by sending redundant packets. It has been observed that the
typic ratio LAN to WAN bandwidth use is ~ 3:1 (350 Mbps LAN =
90-120Mbps WAN).

- Replication-based (bulk) migration of VMs within HCX results in
VMs being moved thick. While this cannot be desirable, the WAN opt UI
reveals a high ratio between LAN and WAN when you move
“empty” disk data. Conversely, it is observed that when
non-compressible data is migrated, such as DB data and digital media, WAN
use is at its highest as it comes closer to LAN input
use.

Observations:
- vMotion of a VM within HCX results in no more than the throughput
of the vMotion network to a single ESX host.
- As bulk migration can have multiple migrations in flight
simultaneously, it achieves higher bandwidth use than a
vMotion migration. The ratio observed at a customer side with 1 Gbps
vMotion links to the ESX hosts was: Eight replications = bandwidth
use of 1 vMotion.
- Moving empty space on disk results in displaying a high LAN use with a
high ratio and subsequently low WAN use. Note that 1 Gbps seems
to be the limit. Indeed, in this particular case the vMotion network is
only capable of 1 Gbps which is the bottleneck.
- vMotion migration of a multi TB Oracle DB. With a WAN link of 1 Gbps,
the limitation is the vMotion network of 1 Gbps.

## Stretched Layer 2 traffic

The HCX fleet component Layer 2 Concentrator has a bandwidth limitation
of ~4 Gbps aggregate for all L2 network traffic that traverses it. Individual
stretched networks have a bandwidth limit of ~ 1 Gbps or less
depending on the traffic type. It is possible to have many stretched L2
networks across a single L2C pair (theoretical allowable max of 4096
networks per L2C pair). While the L2C is engineered to detect and
protect small traffic flows to not be overcame by large flows within the
same L2C pair, it can be advantageous to identify if this situation is
occurring and bring up more L2Cs to increase overall bandwidth
capability. Deploying multiple L2Cs can also be advantageous where
multiple paths exist between the customer site and {{site.data.keyword.cloud}}, such as direct link and internet, such that both can be used, given that you
have more than one network to spread across them. A single network cannot be made redundant or given increased bandwidth across multiple L2C
pairs.

Monitor the traffic across all interfaces that use the Monitoring tab of
the L2C VM. If the total data rate is approaching 8 Gbps (4 Gbps in / out)
consider adding another L2 pair and redistribute stretched networks to
rebalance.


## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
