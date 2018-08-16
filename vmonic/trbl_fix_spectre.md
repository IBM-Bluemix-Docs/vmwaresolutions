---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Addressing Spectre and Meltdown vulnerabilities

To address the Spectre and Meltdown vulnerabilities, you must apply a number of patches in a specific order.

## Updating the firmware

For the most recent information about updating the firmware, see [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Updating instances that were deployed in V2.0 or later

Instances from V2.0 or later were deployed with VMware vSphere 6.5 and VMware vCenter Server 6.5. Both these software components require patching.

### vCenter Server instances that were deployed in V2.0 or later

#### For VMware vSphere 6.5

* For all your new V2.3 instances, vSphere will be deployed with the following patches applied: ESXi650-201712101-SG, ESXi650-201803401-BG, and ESXi650-201803402-BG.  
* For all your existing instances deployed before V2.3, all new clusters and ESXi servers will be updated with the following patches: ESXi650-201712101-SG, ESXi650-201803401-BG, and ESXi650-201803402-BG.
* For all your existing ESXi servers, and for any clusters or ESXi servers that you continue to deploy before you upgrade to V2.3, you must apply the following patches: ESXi650-201712101-SG, ESXi650-201803401-BG, and ESXi650-201803402-BG from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch).

#### For VMware vCenter Server 6.5

* For all your new V2.3 instances, vCenter Server will be deployed with the vCenter 6.5 U1g patch applied.
* For all existing instances deployed before V2.3, you must apply the vCenter 6.5 U1g patch from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch).

### Cloud Foundation instances that were deployed in V2.0 or later

To apply the required patches for VMware vSphere 6.5 and VMware vCenter Server 6.5, you must upgrade your Cloud Foundation instances to the current V2.3 version.

For all your existing instances and ESXi servers, you will be prompted to apply the patches (ESXi650-201712101-SG, ESXi650-201803401-BG, and ESXi650-201803402-BG for vSphere and vCenter 6.5 U1g for vCenter Server) on the **Update and Patch** page from the {{site.data.keyword.vmwaresolutions_full}} console. For more information, see [Applying updates to Cloud Foundation instances](../sddc/sd_applyingupdates.html).

### VMware vSphere clusters that were deployed in V2.0 or later

For VMware vSphere 6.5, you must apply the following patches: ESXi650-201712101-SG, ESXi650-201803401-BG, and ESXi650-201803402-BG, from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your vSphere clusters and ESXi servers, newly deployed or existing.

For VMware vCenter Server 6.5, you must apply the vCenter 6.5 U1g patch from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your vCenter servers, newly deployed or existing.

## Instances that were deployed in V1.9 or earlier

Cloud Foundation instances, vCenter Server instances, and VMware vSphere clusters from V1.9 or earlier, were deployed with VMware vSphere 6.0 and VMware vCenter Server 6.0.

### vCenter Server instances that were deployed in V1.9 or earlier

For both VMware vSphere 6.0 and VMware vCenter Server 6.0, you must apply the patches (ESXi600-201711101-SG, ESXi600-201803401-BG, and ESXi600-201803402-BG for vSphere and vCenter 6.0 U3e for vCenter Server) from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your instances and ESXi servers, newly deployed or existing.

### Cloud Foundation instances that were deployed in V1.9 or earlier

Updates for these instances will be available when the necessary vendor updates upon which these instances depend are released.

### VMware vSphere clusters that were deployed in V1.9 or earlier

For both VMware vSphere 6.0 and VMware vCenter Server 6.0, you must apply the patches (ESXi600-201711101-SG, ESXi600-201803401-BG, and ESXi600-201803402-BG for vSphere and vCenter 6.0 U3e for vCenter Server) from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your vSphere clusters and ESXi servers, newly deployed or existing.

### Related links

* [Applying updates to Cloud Foundation instances](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware Product Patches site](https://my.vmware.com/group/vmware/patch)
