---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# All-in-one deployment

An automated deployment and configuration of a single virtual machine (VM) that hosts all the RiskForesight application components. This deployment model is suitable for small deployments, up to 100 assets with 7 - 30 days of indexing. The “all-in-one” VM details are shown in the following table:

Table 1. All-in-one parameters

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|1|
|vCPU	|16|
|RAM	|32 GB|
|Disk	|80 GB|
|OS	|CentOS 7|
|Installed Application Components|	UI, App, Plugins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Index Datastore, Remote Collector|

The additional Remote Collector VM details are shown in the following table.

Table 2. Remote collector

|Parameter	|Value|
|---|---|
|VM qty	|As required|
|vCPU	|8|
|RAM	|8 GB|
|Disk	|1 TB|
|OS	|CentOS 7|
|Installed Application Components	|Remote Collector|

### Related Links

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
