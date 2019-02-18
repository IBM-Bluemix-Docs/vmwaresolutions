---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-01"

---

#	Upgrading

Upgrading HCX is a simple process that uses the client web user interface (UI) on the client-side
HCX manager update and the cloud web UI on the cloud side HCX manager
update. You must upgrade both sides as any fleet component
updates cause both to redeploy the fleet components with the
level of code that the manager has installed. If VMware support asks for the
System ID, provide both the client and cloud side. Use SSH into the HCX manager (client or cloud) and run `cat
/common/location` to locate the System ID.

## Related links

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
