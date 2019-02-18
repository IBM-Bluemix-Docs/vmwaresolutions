---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Step 2 – Virtual machine deployment
The {{site.data.keyword.vmwaresolutions_full}} automation requests an additional portable private IP subnet and the “all-in-one” virtual machine (VM) is configured with an IP address from this subnet so that the Caveonix RiskForesight components can:

- Connect to vCenter and NSX Manager through the BCR.
- Connect to Remote Collectors, either on VXLANs or hosted off-premise.
- Allow the client to manage the IP address space when scaling up.


### Related Links

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
