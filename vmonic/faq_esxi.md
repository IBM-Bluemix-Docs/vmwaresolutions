---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# FAQ about ESXi servers

Find answers to frequently asked questions about the ESXi servers managed on the {{site.data.keyword.vmwaresolutions_full}} console.

## How many ESXi servers can I add to my instance?
{: faq}

* For vCenter Server instances, you can expand the default cluster to have up to 51 ESXi servers. Each of the non-default clusters can be expanded to have up to 59 ESXi servers. Since you can add up to 10 clusters to an instance, each deployed instance can have a maximum of 51 + 9x59 = 582 ESXi servers across all clusters.
* For Cloud Foundation instances, the standard configuration has four ESXi servers. You can add a maximum of 28 servers (to a total of 32 servers). For Cloud Foundation instances in a multi-site configuration, you can have a maximum of 128 ESXi servers across all instances.

  If your Cloud Foundation configuration requires a multi-site deployment with more than 128 ESXi servers, [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support) for assistance.
  {:note}

## How many ESXi servers can I add to a cluster?

For instances deployed in V2.2 and later, you can add a maximum of 51 ESXi servers to an initial cluster and a maximum of 59 ESXi servers to the added clusters.

For instances deployed in V2.1 or earlier, you must enable the necessary vSAN support to increase the cluster size beyond 32. Complete the following steps to enable the necessary vSAN support:

1. On each deployed ESXi server, run the following commands:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Restart each ESXi server. For more information, see [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081).
3. You might need to increase the size of the vCenter Server to accommodate the added virtual machines and ESXi servers.
4. Open an IBM Support ticket to indicate that you applied the vSAN changes manually by completing steps 1 - 3. In the ticket, request that your upgraded instance is enabled for ESXi servers beyond 32.

## Can I change the ESXi server names and IP addresses?

The ESXi server names and IP addresses cannot be changed because they are registered for Windows DNS resolution. Changes might result in failure during deployment or failure of vCenter Server functions.

Don't use the **Rename Device** feature on the {{site.data.keyword.cloud_notm}} user interface to change ESXi server names. This function changes the FQDN of the ESXi server, but the configured vCenter Server and the Windows VSI host registrations will be incorrect and might cause failures.
{:note}

## Can I disable root access on my ESXi servers?

It is recommended to keep root access enabled on ESXi servers, otherwise failure in the {{site.data.keyword.vmwaresolutions_short}} functions might occur.

If necessary, you can disable root access after the ESXi servers have a status of **Ready to Use** on the {{site.data.keyword.vmwaresolutions_short}} console.

You must re-enable root access for subsequent automation operations, for example, when you add or remove file shares or when you install add-on services, such as Zerto on {{site.data.keyword.cloud_notm}}.

## Can I add static routes on my ESXi servers to mount storage from other locations?

You can add static routes for storage but you must do it with extreme care. Otherwise, the existing shares might become unmounted.

Adding static routes for vMotion is not supported. Changes in vMotion subnet configuration might result in failure in the {{site.data.keyword.vmwaresolutions_short}} functions.
{:note}

### Related links

* [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-expanding-and-contracting-capacity-for-vcenter-server-instances)
* [Expanding and contracting capacity for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-expanding-and-contracting-capacity-for-cloud-foundation-instances)
* [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-vcenter-server-instances)
* [Adding, viewing, and deleting clusters for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-viewing-and-deleting-clusters-for-cloud-foundation-instances)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-contacting-ibm-support)
