---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-01"

---

# HCX	removal

HCX removal assumes that stretched networks are no longer in use. Use the following procedure to remove HCX.

1. Unstretch all stretched networks.
2. In the client user interface (UI), delete any L2C appliances. Wait for the L2C appliances to disappear from the web UI.
3. Delete the CGW. This also removes the WAN Opt. Wait for the CGW and WAN Opt appliances to be removed.
4. Shutdown and delete the HCX Manager Appliance virtual machines (VMs) from the client and
cloud side.
5. Remove the HCX ESG from NSX cloud side.
6. Use the vCenter Mob browser to remove the HCX snap-in.

## Related links

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
