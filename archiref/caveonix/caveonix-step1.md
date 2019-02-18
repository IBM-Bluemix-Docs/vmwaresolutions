---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Step 1 – Initial planning and prerequisites
Each Caveonix RiskForesight application component is loosely coupled, but centrally managed. Therefore, they can be deployed in an “all-in-one” virtual machine (VM) deployment pattern or the application components can be “scaled-out” and deployed on multiple VMs for higher availability,  performance, and capacity.

Deployment patterns are based on both availability requirements and sizing for data retention. RiskForesight deployment nodes can be characterized as:

-	Base VMs – The base VMs host the application components that do not scale due to data retention. These components are; RiskForesight UI, RiskForesight App, RiskForesight Plugins, Central Collector, Remote Collector, Index Datastore, Messaging Datastore, and Relational Datastore.
-	Scale-out VMs – The scale-out VMs, the database and the data index, scale according to the number of Assets and the required data retention that creates demand for more scale-out hard disk space and hence more scale-out VMs.

There are three Caveonix RiskForesight deployment models:

-	“All-in-one” – An automated deployment and configuration of 1 VM that hosts all the application components:
  - All application components installed on one VM.
  - Remote Collectors can be installed on separate VMs.
  - Small deployments – up to 100 assets with 7 - 30 days of indexing.
-	Partial Distributed – After the automated deployment is completed, you can manually scale-out by increasing RAM and disk in the initial VM and add three scale-out VM.
  - UI, App, Plugins, Central Collector, Remote Collector, Index Datastore, Messaging Datastore, and Relational Datastore deployed on one VM.
  - Remote Collectors installed on separate VMs.
  -	Index Data Nodes deployed on separate VMs.
  -	Small-to-medium deployments – up to 500 assets with 30 days of indexing.
- Fully Distributed - Add more base VMs and scale-out VMs according to the number of assets and data retention requirements:
  - Application components distributed onto separate VMs to facilitate scaling.
  -	Required deployment pattern as number of assets increases in the range 500 - 100,000.
  -	Remote Collectors installed on separate VMs.
  -	UI on multiple VMs.
  -	App and Plugins on multiple VMs.
  -	Central Collector configured in a Cluster.
  -	Relational Datastore deployed in a Primary / Secondary model.
  -	Messaging Datastore deployed in a cluster.
  -	Index Datastore that is deployed with Master and Data Nodes.
  -	More Data Nodes that are used for Scale Out as number of assets increases.

All components must have an FQDN and registered in DNS before any VM deployment. This step is carried out by the IC4VS automation for the initial "all-in-one" deployment, but is a client responsibility when scaling the deployment.

### Related Links

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
