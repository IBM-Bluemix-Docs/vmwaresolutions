---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Step 4 - Application setup

After the virtual machines (VMs) are deployed and the application components are installed, the Caveonix RiskForesight solution is available to be set up for the Service Provider and the first Tenant or Organization.

The Service Provider is the top-level organization and there are one or more Tenant/Organization serviced by the Service Provider. The Service Provider assigns Assets that are collected from vCenter to the Tenant or Organizations, who then assign them to Applications or Sub-applications. These Applications are then subject to a compliance regime.

This step is initially completed by the IC4VS automation that uses information that is supplied by the client during the ordering process and default information. The setup process can be started by the client, post deployment, to modify the Service Provider or Tenant Organization as required post installation.

The Service Provider setup has eight substeps:
-	Step 1: Organization Detail - Add the details for the over-all parent organization for your cloud service provider. This organization can have multiple physical locations and multiple data centers. Organizations for your tenants and sub-organizations for your service provider are added later.
-	Step 2: Locations – Map the infrastructure into RiskForesight "Locations” as the Assets are grouped by location, cloud provider, and asset repository.
-	Step 3: Environments - Optional. Environments are a way to group assets. For example, DevOps, DR Site, Production.
-	Step 4: Cloud Provider - Add the “providers” that provide the infrastructure that your application runs on.
-	Step 5: Asset Repositories - An Asset Repository associates a set of assets with an Organization, a Cloud Provider, and a Location.
-	Step 6: Organizations - Create sub-organization for your own operations and additional organizations - one for each of your service provider tenants. Each tenant must go through their own set-up process - including creating their own sub-organizations.
-	Step 7: Organization Users - Create and assign Users to Tenant Organizations and Sub-Organizations of the Service Provider.
-	Step 8: Task Scheduler – Configure tasks to; Synchronize with the Asset Repository, Perform SCAP Vulnerability and Compliance scans, Collect NSX network flows, Collect information about the software that is running on monitored Assets, Collect sys log and system events for Assets.

The Tenant or Organization Setup has seven substeps:

-	Step 1: Organization - Add details for your primary organization. You can also create sub-organizations. Use organizations to segment your users, or as one of the ways to group your assets. You can create more organizations with one of your existing organizations as parent. When you create a new organization, you can select the "Business Impact Value", which is used to generate cyber risk scores.
-	Step 2: Organization Assets - New assets / workloads are automatically grouped by location, cloud provider, and asset repository. Assets can be assigned to only one organization at a time. The Service Provider needs to assign assets to an organization.
-	Step 3: Associate Environment and Location – Optional. Environments are defined by the Service Provider.
-	Step 4 and 5: Create Sub-Applications or Applications – Used to group assets across locations and organizations and see their associated flows and policies. Create applications that match business and IT services. For example, Application=SAP, Sub-Applications=SAP Front End, SAP Middle Tier, and SAP Back End. Business impact value corresponds to an Application, compliance regimes apply to an application.
-	Step 6: Remote Access - Remote Access is required to run scans on assets, can be a default service account or an asset-specific account.
-	Step 7: Task Scheduler - Schedule scans to run on a periodic basis. The types of tasks include; SCAP Scan-Vulnerability, SCAP Scan-XCCDF, NSX Flow Scan, Software Scan, Log Extract Scan.

The following information is collected from the user at time of order and is used to in the application setup.

Table 1. Information collected from the user

|Setup stage |Parameter |
|---|---|
|Organization / Asset Repositories  |Organization Name |
|Organization |Phone Number |
|Organization |Email |
|Organization / Asset Repositories |Address Line 1 |
|Cloud Provider/ Asset Repositories |Name |
|Cloud Provider |Description |
|Cloud Provider |POC email |
|Cloud Provider |Type|
|Cloud Provider |POC Name |
|Cloud Provider |POC Phone |

The following default information is used in the application setup.

Table 2. Default information used in application setup

|Setup stage |Parameter |
|---|---|
|Environment |Environment Name is set to “Initial”|
|Environment | Score is set to 5|
|Asset Repository |Two Asset Repositories are configured; vCenter and NSX Manager. Host URL set to https://*vCenter fqdn* and https://*NSX Manager fqdn*|
|Asset Repository |Two Asset Repositories are configured; vCenter and NSX Manager, both use the same user name. User name set to vCenter administrator user name|
|Asset Repository |Two Asset Repositories are configured; vCenter and NSX Manager, both use the same password. Password is set to vCenter administrator password
|Asset Repository |Two Asset Repositories are configured; vCenter and NSX Manager, both use the same password. Type is set to vCenter for one repository and NSX for the other
|Task |Four tasks are set up; Asset Scan, NSX Flows, VMware Infrastructure Scan, and VMware Vulnerability. ScanName is set to DC1AssetScan, NSXFlows, VMWInfraScan, VMWVulnScan |
|Task |Four tasks are set up; Asset Scan, NSX Flows, VMware Infrastructure Scan, and VMware Vulnerability. Type is set to vCenter, NSX, VMWareInfrastructureScan, VMWareVulnerabilityScan |
|Task |Schedule is set to Hourly for DC1AssetScan and Daily for the others |

## Related Links

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
