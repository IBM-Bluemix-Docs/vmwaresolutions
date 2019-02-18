---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Troubleshooting HCX on IBM Cloud

## Cloud registration fails

* Hybrid Cloud Services does not retry if credentials are incorrect. The credentials must authenticate before Hybrid Cloud Services attempts to log in and start the cloud registration.
* Cloud registration can fail if the credentials are mistyped or if the VCF/VCS Hybrid Cloud Services Cloud credentials are changed after Hybrid Cloud Services registers with VCF/VCS Hybrid Cloud Services Cloud, causing a mismatch.
* To update the credentials in the web client, go to the Hybrid Cloud Services Getting Started tab, and under **Basic tasks** choose **Register new Cloud**.

## Duplicate MAC address

After migration, there might be communication problems among your virtual machines. When the MAC address is retained during a migration, a duplicate MAC address might inadvertently be created.

The MAC address for the migrated virtual machine can be changed to resolve this problem.

1. In the vSphere client, power off the virtual machine.
2. In the inventory, right-click the virtual machine and choose **Edit Settings** from the menu.
3. On the **Virtual Hardware** tab, expand the Network adapter.
4. Next to the MAC Address text box, choose **Manual** from the menu.
5. Specify a unique MAC address and click **OK**.
6. Check to see whether the unique MAC address solves the communication problem.

## High host resource consumption

In rare cases, if all service virtual appliances reside on the same host, the Hybrid Cloud Services service virtual machines can exhaust a host's CPU and disk resources.

Some users have seen this issue when all virtual appliances were installed on one physical host. Given this configuration, performance degrades when the following things happen concurrently:
* The network has high latency, or packet loss, or both. Migration or data transport is slow when you use the public internet or a busy network.
* The WAN Optimizer is consuming bandwidth to encrypt and compress (or decrypt and decompress) large workloads.
* There is high application traffic between on-premises VMs and migrated VMs.

To resolve the problem, follow these steps:

1. Before you change the data center configuration, review the requirements to steady state support.
2. Contact steady state support if resources are being exhausted. They can advise how to reconfigure the environment with a minimum amount of downtime.

### Related links

* [Registering HCX Manager with vCenter](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-registering-hcx-manager-with-vcenter)
* [Modifying or uninstalling HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-modifying-or-uninstalling-hcx)
