---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Post-deployment considerations for your VMware instance

{{site.data.keyword.vmwaresolutions_full}}, VMware vCenter Server, and VMware Cloud Foundation offerings are not managed services. You are responsible for the configuration, security, management, and monitoring of all software components. With complete administrative access to the solution, you have great power and flexibility that requires significant technical, administrative, and operational expertise across various domains. Managing a VMware instance in the {{site.data.keyword.cloud_notm}} requires the same planning and expertise as planning for an on-premises instance. Software-defined technologies such as VMware NSX and VMware vSAN greatly simplify some aspects of instance management, but might require new skills and tools to be properly managed and operated. Combining the power, speed, and reliability of {{site.data.keyword.cloud_notm}} automated VMware deployment with the appropriate operational planning and testing ensures quick and successful navigation to hybrid cloud.

Review the following considerations to understand your responsibilities for managing and operating the instance before and after it has been deployed.

The following list is not exhaustive. For more information, see [IBM-managed services](../../services/managing_imi.html).
{:note}

## IBM Cloud account access

To manage access to your {{site.data.keyword.cloud_notm}} account, permit other members of your team to access your instance in the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Inviting users to access services and resources](../../vmonic/iamuserinvite.html).

## Limitations

Familiarize yourself with the following limitations for your instance:

- [Impacts of changing vCenter artifacts](../../vcenter/vcenter_chg_impact.html)
- [Networking considerations and limitations](../../vcenter/vc_networkingonvcenterserver.html)
- [Frequently asked questions](../../vmonic/faq.html)

## Network design and connectivity

Complete the following steps to manage access to your {{site.data.keyword.cloud_notm}} network and to your VMware management components and to plan your {{site.data.keyword.cloud_notm}} network topology.

- Access instance management endpoints by using the [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/vpn-access) or your [{{site.data.keyword.cloud_notm}} Direct-Link connection](https://www.ibm.com/cloud/direct-link).
- Devise a strategy for public network connectivity from within your instance. Your options include: the sample customer VMware NSX Edge Services Gateway (ESG), gateway appliances such as Vyatta and FortiGate, and proxy servers deployed in the {{site.data.keyword.cloud_notm}} network or on your own network accessed through DirectLink.
- Plan whether to deploy your workload on {{site.data.keyword.cloud_notm}} VLANs with [{{site.data.keyword.cloud_notm}} portable IP addresses](https://console.cloud.ibm.com/docs/infrastructure/subnets/getting-started.html) or [on NSX logical switches (VXLANs) using your own IP addresses](../nsx/nsx_overview.html). Note that using NSX software-defined networking (SDN) gives you the greatest flexibility to manage and secure your workload network in the {{site.data.keyword.cloud_notm}}.
- Use NSX ESGs, [IBM Cloud Vyatta](https://console.cloud.ibm.com/catalog/infrastructure/virtual-router-appliance), and DirectLink peering to plan for connectivity to workloads (Network Address Translation, Virtual Private Network, routing).
- If implementing Cross-vCenter NSX, ensure that your local segment ID ranges are not overlapping before deploying any local workloads.

## Security planning and hardening

You are responsible for securing, encrypting, and monitoring your VMware instance and workloads to meet your corporate, industry, and regulatory standards. Complete the following steps to ensure proper security.

- Change all passwords displayed in the {{site.data.keyword.vmwaresolutions_short}} console and use your own password management system. Note that IBM retains distinct user IDs needed for ongoing automation and support.
- Review password policies, such as complexity and expiration period, across all components.
- Review encryption settings across all components.
- Plan and implement appropriate physical or virtual firewall solutions, such as NSX Distributed Firewall (DFW), NSX ESGs, [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html), and [IBM Cloud Vyatta](https://console.cloud.ibm.com/catalog/infrastructure/virtual-router-appliance).
- Plan and implement appropriate application load balancing and security solutions, such as [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html).
- Plan and implement appropriate security information and event management (SIEM) solutions, such as [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence).
- Plan and implement appropriate vulnerability scanning.
- Plan and implement appropriate change management, approval, auditing, and access control for your instance, using solutions such as [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html).

## Customization

Complete the following steps to customize the base VMware instance installation to fit your requirements.

- Use your own certificate authority (CA) to generate certificates for components such as vCenter, VMware Platform Services Controller (PSC), and NSX Manager.
- Configure deployed services. For example:
  - For HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, configure AD integration, access control, Simple Mail Transfer Protocol (SMTP) settings, and compliance policies.
  - For Zerto on {{site.data.keyword.cloud_notm}}, plan for IP addressing and routing of Zerto Virtual Replication Appliance (VRA) communications since network address translator (NAT) traversal is not supported. Consider either tunneling or redeployment of your VRAs for appropriate addressing and routing.
  - For backup services such as Veeam on {{site.data.keyword.cloud_notm}} and IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}, configure your backup job, optionally configure additional storage, and configure monitoring alerts.
  - For networking and security services such as F5 on {{site.data.keyword.cloud_notm}} and FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, configure network interfaces, certificates, high availability (HA) configuration, and rules according to your network topology and other requirements.

## Active Directory

Complete the following steps to ensure proper single sign-on (SSO) configuration and management.

- Configure the Active Directory (AD) server update and reboot schedule.
- If you have chosen the option to deploy AD servers into the vSphere cluster, provide Microsoft Windows licensing and activation for the servers to ensure compliance and availability.
- Establish mutual trust between the instance and your on-premises AD server.
- Integrate NSX VPN, if applicable, with AD SSO.
- Integrate ESXi hosts with AD SSO.

## Maintenance planning

Complete the following steps to ensure proper planning for software maintenance.

- [Set up VMware Update Manager (VUM)](../vum/vum-intro.html) through a proxy to obtain VMware updates.
- If applicable, set up vSAN through a proxy to maintain the vSAN Hardware Compatibility List (HCL) database.
- Plan regular maintenance for VMware components that are not supported by VUM. For example, VMware vCenter, PSC, and NSX.
- Review vSphere Enhanced vMotion Compatibility (EVC) configuration. Your cluster might not be configured with EVC enabled if the current version of vSphere does not support EVC for your hardware level.
- Plan regular maintenance for add-on services such as Veeam on {{site.data.keyword.cloud_notm}}, Zerto on {{site.data.keyword.cloud_notm}}, and F5 on {{site.data.keyword.cloud_notm}}.

## Monitoring

Ensure to plan for and implement the following solutions for monitoring your instance and instance components.

- A logging server that includes log forwarding or collection for all instance components and adequate log retention.
- An alert infrastructure, including configuration of the SMTP server and short message service (SMS) gateway, as needed.
- Proactive monitoring of hosts, drives, management software, and network.
- vSAN monitoring, if applicable.
- Capacity monitoring and planning. You can [add and remove clusters](../../vcenter/vc_addingviewingclusters.html) and [add and remove hosts](../../vcenter/vc_addingremovingservers.html) to your instance from the {{site.data.keyword.vmwaresolutions_short}} console.
- Monitoring your backup infrastructure and backup jobs.

## Business continuity and availability

Your VMware instance is running on Bare Metal Servers in the {{site.data.keyword.cloud_notm}}. Complete the following steps to ensure that you make adequate plans for high availability and business continuity.

- Review vSphere HA and vSphere Distributed Resource Scheduler (DRS) configuration against your requirements.
- Review network and storage I/O control configuration against your requirements.
- Configure the virtual machine startup order against your requirements.
- Configure resource pools, as needed, for management and workload.
- Plan, implement, and monitor a backup solution for both [instance management components](solution_backingup.html) and workload.
- Plan for high availability of instance management, including the possibility of multiple instances, multiple clusters, vCenter HA, and PSC HA.
- Plan for business continuity for your workloads using solutions such as [Zerto Disaster Recovery](../../services/addingzertodr.html), [Veeam backup and replication](../../services/veeam_considerations.html), and [IBM Spectrum Protect Plus](../../services/spp_considerations.html).

## Storage planning

In addition to capacity planning, complete the following to ensure that your storage configuration meets your performance and availability requirements.

- Storage performance depends on various factors, including RAID configuration and disk striping; network configuration; block size; configured IOPS (input/output operations per second) for network-attached storage; VM hardware configuration and method of storage attachment; clustering and replication methods; and use of storage policies such as encryption, deduplication, and compression. Plan time to test and tune your configuration to meet your storage performance needs.
- Review your vSAN storage policy
  - RAID-1 provides better performance and smaller windows of susceptibility to sequential failure, such as shorter rebuild time, than RAID-5. However, RAID-5 has less storage overhead.
  - RAID-6 provides protection against dual failures, but requires a minimum of six hosts compared to four hosts for RAID-5.
- To add more storage to your vSAN cluster, you must add new hosts to the cluster or add {{site.data.keyword.cloud_notm}} Endurance NFS storage instead. Adding disks to the existing hosts is not currently supported.
- If you mount additional {{site.data.keyword.cloud_notm}} Endurance NFS storage to your cluster, ensure that you follow the architecture guidance and configure host routes to the storage using the `SDDC-DPortGroup-NFS` port group addresses. You must authorize these addresses, rather than the hosts themselves, to the storage. For more information, see [Attached storage infrastructure management](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing).

In addition, see the developerWorks recipe showing how to [add more endurance storage to your VMware cluster](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/) using IBM Spectrum Protect Plus as an example.

### Related links

* [Solution overview](solution_overview.html)
* [Design overview](design_overview.html)
* [Scaling capacity](solution_scaling.html)
