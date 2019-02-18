---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-04"

---

# Scale
After the deployment of the initial hosts, the user can
scale out the compute capacity from within the {{site.data.keyword.vmwaresolutions_full}} console. This scale out of the environment follows one of three paths:
- Addition of new sites managed by separate vCenter Servers
- Addition of new clusters
- Addition of new hosts to an existing cluster

## Multi–site deployments

{{site.data.keyword.vmwaresolutions_short}} can use the {{site.data.keyword.cloud_notm}} world–wide data center
presence and integrated network backbone to allow for various cross–geographies use cases to be deployed and functioning within a
fraction of the time it would take to build such an infrastructure from
scratch. The following details define a multi–site
deployment:

- An initial or primary VMware deployment that contains a new DNS/AD root
domain, sub–domain, SSO domain, and SSO site name to be provided
- Single or multiple secondary sites that are provisioned into the
primary sites SSO domain that requires the following configuration:
    - New SSO site name
    - New DNS site / subdomain that is tied to the root of the primary domain
    - DNS and AD replication setup between the secondary and primary
site AD VMs
    - PSC deployed and configured to replicate with the primary site PSC
- vCenter setup with Enhanced Linked Mode to the primary site vCenter

Additionally, the NSX manager in secondary sites can be set up as
secondary NSX managers to the primary site’s NSX manager. This is a
manual process that needs to be performed by the user.

## Scale out with new cluster

The user can scale out the compute capacity by
creating a new cluster from within the console, ordering the hosts, and
the new hosts are automatically added to the new cluster. This option
creates an additional, separate cluster in the environment and gives
users the ability to physically and logically segregate management
workloads from application workloads, the ability to segregate workloads
based on other characteristics (such as Microsoft SQL database cluster),
and the ability to deploy applications in highly available topologies.
If the initial cluster will be converted into a
management–only cluster, then the migration of existing workloads
involves manual steps to be taken by the user. This can involve either
the reattachment of data stores to the new cluster or alternately
storage migration. IP addresses of the workloads might
need to be changed if the new cluster resides in a different {{site.data.keyword.cloud_notm}} pod or is assigned a different VLAN ID and that VM directly
uses {{site.data.keyword.cloud_notm}} IP space.

## Scale out existing cluster
The user can scale out an existing cluster by ordering hosts from within
the console and the new hosts are automatically added to the cluster.
Users might need to adjust the HA reservation policy for the
cluster based on their reservation requirements.

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity
Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview) 
